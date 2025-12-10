# SearchCompany
Search company by indicator

<div style="display: flex; gap: 20px;">

  <div style="flex: 1;">
    <h2>**Search Company Input Indicators**</h2>

    | Field Name | Data Type | Description |
    |-----------|-----------|-------------|
    | IsinCode | string | International Securities Identification Number |
    | OrganizationName | string | Full name of company |
    | TaxCode | string | Multiple TaxCode can be submitted per call |
    | EnterpriseCode | string | EnterpriseCode |
    | Ticker | string | Stock code |
    | Page | integer | Page number |
    | PageSize | integer | Records per page |
  </div>

  <div style="flex: 1;">
    <h2>**Query Param**</h2>
    <label>
        IsinCode:
        <input id="indicator-input" type="text" placeholder="string" />
      </label>
      <br/><br/>
      <label>
        OrganizationName:
        <input id="token-input" type="text" placeholder="string" />
      </label>
      <br/><br/>
      <label>
        TaxCode:
        <input id="token-input" type="text" placeholder="string" />
      </label>
      <br/><br/>
      <label>
        Ticker:
        <input id="token-input" type="text" placeholder="string" />
      </label>
      <br/><br/>
      <label>
        EnterpriseCode:
        <input id="token-input" type="text" placeholder="string" />
      </label>
      <br/><br/>
      <label>
        Page:
        <input id="token-input" type="password" placeholder="integer" />
      </label>
      <br/><br/>
      <label>
        PageSize:
        <input id="token-input" type="password" placeholder="integer" />
    </label><br/><br/>
    
  </div>
  
</div>

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
