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
      <input id="IsinCode" type="text" placeholder="string" style="width:100%; padding:6px; border:1px solid #ccc; border-radius:4px;">
    </label><br/><br/>

    <label>OrganizationName<br/>
      <input id="OrganizationName" type="text" placeholder="string" style="width:100%; padding:6px; border:1px solid #ccc; border-radius:4px;">
    </label><br/><br/>

    <label>TaxCode<br/>
      <input id="TaxCode" type="text" placeholder="string" style="width:100%; padding:6px; border:1px solid #ccc; border-radius:4px;">
    </label><br/><br/>

    <label>Ticker<br/>
      <input id="Ticker" type="text" placeholder="string" style="width:100%; padding:6px; border:1px solid #ccc; border-radius:4px;">
    </label><br/><br/>

    <label>EnterpriseCode<br/>
      <input id="EnterpriseCode" type="text" placeholder="string" style="width:100%; padding:6px; border:1px solid #ccc; border-radius:4px;">
    </label><br/><br/>

    <label>Page<br/>
      <input id="Page" type="number" placeholder="1" style="width:100%; padding:6px; border:1px solid #ccc; border-radius:4px;">
    </label><br/><br/>

    <label>PageSize<br/>
      <input id="PageSize" type="number" placeholder="100" style="width:100%; padding:6px; border:1px solid #ccc; border-radius:4px;">
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

<script>
(function () {
  const BASE = "https://bidf.fiingroup.vn/api/v1/Standard";
  const PATH = "/SearchCompany";

  function val(id) {
    const el = document.getElementById(id);
    return el ? el.value.trim() : "";
  }

  function buildUrl() {
    const params = new URLSearchParams();

    // chỉ add nếu có value (tránh gửi query rỗng)
    const IsinCode = val("IsinCode");
    const OrganizationName = val("OrganizationName");
    const TaxCode = val("TaxCode");
    const Ticker = val("Ticker");
    const EnterpriseCode = val("EnterpriseCode");
    const Page = val("Page");
    const PageSize = val("PageSize");

    if (IsinCode) params.set("IsinCode", IsinCode);
    if (OrganizationName) params.set("OrganizationName", OrganizationName);
    if (TaxCode) params.set("TaxCode", TaxCode);
    if (Ticker) params.set("Ticker", Ticker);
    if (EnterpriseCode) params.set("EnterpriseCode", EnterpriseCode);
    if (Page) params.set("Page", Page);
    if (PageSize) params.set("PageSize", PageSize);

    const qs = params.toString();
    return BASE + PATH + (qs ? ("?" + qs) : "");
  }

  async function run() {
    const statusEl = document.getElementById("tryStatus");
    const resultEl = document.getElementById("tryResult");
    const btn = document.getElementById("btnTry");

    const url = buildUrl();

    // (Tuỳ chọn) nếu API cần Bearer token: lưu token trong localStorage rồi đọc ra
    // localStorage.setItem("api_token", "YOUR_TOKEN");
    const token = localStorage.getItem("api_token"); // để trống nếu không dùng auth

    statusEl.textContent = "Calling: " + url;
    resultEl.style.display = "none";
    resultEl.textContent = "";
    btn.disabled = true;
    btn.style.opacity = "0.6";

    try {
      const headers = {
        "Accept": "application/json"
      };
      if (token) headers["Authorization"] = "Bearer " + token;

      const resp = await fetch(url, { method: "GET", headers });

      const text = await resp.text(); // đọc thô để tránh lỗi JSON parse
      statusEl.textContent = "HTTP " + resp.status;

      // hiển thị đẹp nếu là JSON
      let pretty = text;
      try { pretty = JSON.stringify(JSON.parse(text), null, 2); } catch(e) {}

      resultEl.textContent = pretty;
      resultEl.style.display = "block";
    } catch (e) {
      statusEl.textContent = "ERROR: " + (e && e.message ? e.message : e);
      resultEl.textContent =
        "Nếu bạn thấy lỗi CORS (blocked by CORS policy) thì cần backend bật CORS cho domain docs.";
      resultEl.style.display = "block";
    } finally {
      btn.disabled = false;
      btn.style.opacity = "1";
    }
  }

  document.addEventListener("DOMContentLoaded", function () {
    const btn = document.getElementById("btnTry");
    if (btn) btn.addEventListener("click", run);
  });
})();
</script>
