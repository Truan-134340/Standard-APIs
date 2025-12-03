# Search Company API

Mô tả: API tìm kiếm doanh nghiệp theo indicator/param bạn dùng.

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
