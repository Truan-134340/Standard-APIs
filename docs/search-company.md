# Search Company API

Mô tả: API tìm kiếm doanh nghiệp theo indicator/param bạn dùng.
Search Company Input Indicators

| Field Name        | Data Type             | Description_VN           |
|-------------|-------------------|-----------------|
| IsinCode  | string         | Mã chứng khoán quốc tế      |
| OrganizationName  | string         | Tên đầy đủ của công ty      |
| TaxCode  | string         | Mã số thuế      |


## Thử API

<div id="swagger-ui-search-company"></div>

<script>
window.onload = function () {
  const ui = SwaggerUIBundle({
    url: "../openapi.yaml",   // dùng chung file spec
    dom_id: "#swagger-ui-search-company",
    deepLinking: true,
  });

  // Sau khi render xong, ẩn tất cả operation KHÔNG phải SearchCompany
  setTimeout(() => {
    document.querySelectorAll('.opblock').forEach(block => {
      if (!block.textContent.includes('/api/v1/Standard/SearchCompany')) {
        block.style.display = 'none';
      }
    });
  }, 800);
};
</script>

# Search Company API_Output
| Field Name        | Data Type             | Description_VN           |
|-------------|-------------------|-----------------|
| IsinCode  | string         | Mã chứng khoán quốc tế      |
| OrganizationName  | string         | Tên đầy đủ của công ty      |
| TaxCode  | string         | Mã số thuế      |
