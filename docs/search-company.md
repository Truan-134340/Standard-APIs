# SearchCompany
Search company by indicator

<table>
<tr>
<td style="vertical-align: top; width: 50%">

<h2>Search Company Input Indicators</h2>

| Field Name | Data Type | Description_EN |
|-----------|-----------|----------------|
| IsinCode | string | International Securities Identification Number |
| OrganizationName | string | Full name of company |
| TaxCode | string | Multiple TaxCode can be submitted per API call |
| EnterpriseCode | string | EnterpriseCode |
| Ticker | string | Stock code of company |
| Page | integer | Page number. Default: 1 |
| PageSize | integer | Number of records per page. Default: 100 |

</td>

<td style="vertical-align: top; width: 50%">

<h2>Query Param</h2>

<div id="search-company-ui">

<label>
  IsinCode:<br/>
  <input type="text" placeholder="string">
</label>
<br/><br/>

<label>
  OrganizationName:<br/>
  <input type="text" placeholder="string">
</label>
<br/><br/>

<label>
  TaxCode:<br/>
  <input type="text" placeholder="string">
</label>
<br/><br/>

<label>
  Ticker:<br/>
  <input type="text" placeholder="string">
</label>

<label>
  EnterpriseCode:<br/>
  <input type="text" placeholder="string">
</label>
<br/><br/>

<label>
  Page:<br/>
  <input type="text" placeholder="string">
</label>
<br/><br/>

<label>
  PageSize:<br/>
  <input type="text" placeholder="string">
</label>
</div>

</td>
</tr>
</table>


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
