# SearchCompany
Search company by indicator
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

<h2>Query Params</h2>
<div style="display:flex; gap:24px;">

  <div style="flex:1;">
    <h3>Query Params</h3>

    <label>IsinCode<br/>
      <input type="text" placeholder="string" style="width:100%; padding:6px; border:1px solid #ccc; border-radius:4px;">
    </label><br/><br/>

    <label>OrganizationName<br/>
      <input type="text" placeholder="string" style="width:100%; padding:6px; border:1px solid #ccc; border-radius:4px;">
    </label><br/><br/>

    <label>TaxCode<br/>
      <input type="text" placeholder="string" style="width:100%; padding:6px; border:1px solid #ccc; border-radius:4px;">
    </label><br/><br/>

    <label>Ticker<br/>
      <input type="text" placeholder="string" style="width:100%; padding:6px; border:1px solid #ccc; border-radius:4px;">
    </label><br/><br/>

    <label>EnterpriseCode<br/>
      <input type="text" placeholder="string" style="width:100%; padding:6px; border:1px solid #ccc; border-radius:4px;">
    </label><br/><br/>

    <label>Page<br/>
      <input type="number" placeholder="1" style="width:100%; padding:6px; border:1px solid #ccc; border-radius:4px;">
    </label><br/><br/>

    <label>PageSize<br/>
      <input type="number" placeholder="100" style="width:100%; padding:6px; border:1px solid #ccc; border-radius:4px;">
    </label>

  </div>

</div>
<!-- TRY BOX -->
<div style="display:flex; align-items:center; gap:16px; margin: 12px 0;">
  <button id="btnTry"
    style="margin-left:auto; padding:14px 24px; border:2px solid red; background:white; color:red; font-size:22px; cursor:pointer;">
    try
  </button>
</div>

<div id="tryStatus" style="margin: 8px 0; font-weight:600;"></div>

<pre id="tryResult" style="white-space:pre-wrap; border:1px solid #eee; padding:12px; border-radius:6px; display:none;"></pre>

<h2>Response</h2>

<!-- 200 OK -->
<details>
  <summary style="display:flex; align-items:center; gap:10px; cursor:pointer; padding:6px 0;">
    <span style="background:#d1fae5; color:#065f46; padding:4px 10px; border-radius:6px; font-weight:600;">
      200
    </span>
    <span>Successful response</span>
  </summary>

  <pre>
{
  "data": [],
  "page": 1,
  "pageSize": 20,
  "totalRecords": 0
}
  </pre>
</details>

<!-- 400 Bad Request -->
<details>
  <summary style="display:flex; align-items:center; gap:10px; cursor:pointer; padding:6px 0;">
    <span style="background:#fee2e2; color:#991b1b; padding:4px 10px; border-radius:6px; font-weight:600;">
      400
    </span>
    <span>Bad Request</span>
  </summary>

  <pre>
{
  "errorCode": "INVALID_PARAMETER",
  "message": "One or more parameters are invalid."
}
  </pre>
</details>

<!-- 500 Internal Server Error -->
<details>
  <summary style="display:flex; align-items:center; gap:10px; cursor:pointer; padding:6px 0;">
    <span style="background:#fca5a5; color:#7f1d1d; padding:4px 10px; border-radius:6px; font-weight:600;">
      500
    </span>
    <span>Internal Server Error</span>
  </summary>

  <pre>
{
  "errorCode": "INTERNAL_ERROR",
  "message": "Unexpected error occurred. Please try again later."
}
  </pre>
</details>

👉 See full API and Try It console in the API Reference:
[Search Company API](docs/search-company.yaml)
