# SearchCompany
Search company by indicator

## Thông tin API

| Thuộc tính | Giá trị |
|-----------|---------|
| Method    | GET |
| Endpoint  | `/api/v1/Standard/SearchCompany` |
| Auth      | Bearer token |

---

## Query Param

<div id="search-company-ui">
  <label>
    Indicator:
    <input id="indicator-input" type="text" placeholder="Nhập indicator..." />
  </label>
  <br/><br/>
  <label>
    Bearer Token:
    <input id="token-input" type="password" placeholder="Nhập token (nếu cần)..." />
  </label>
  <br/><br/>
  <button id="call-btn">Gọi API</button>

  <h3>Kết quả</h3>
  <pre id="result-box">{ }</pre>
</div>

<script>
document.getElementById('call-btn').addEventListener('click', async () => {
  const indicator = document.getElementById('indicator-input').value.trim();
  const token = document.getElementById('token-input').value.trim();

  if (!indicator) {
    alert('Vui lòng nhập indicator');
    return;
  }

  const url = 'https://your-domain.com/api/v1/Standard/SearchCompany'
            + '?indicator=' + encodeURIComponent(indicator);

  const headers = {
    'Accept': 'application/json'
  };
  if (token) {
    headers['Authorization'] = 'Bearer ' + token;
  }

  try {
    const res = await fetch(url, { headers });
    const text = await res.text();
    let data;
    try {
      data = JSON.parse(text);
    } catch {
      data = text;
    }

    document.getElementById('result-box').textContent =
      typeof data === 'string'
        ? data
        : JSON.stringify(data, null, 2);
  } catch (err) {
    document.getElementById('result-box').textContent = 'Error: ' + err;
  }
});
</script>
