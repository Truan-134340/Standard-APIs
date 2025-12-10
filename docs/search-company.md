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

<h2>Response</h2>
<h1 class="AccordionToggle2c6jPP7vVvLS APIResponseSchemaPicker-option-toggle1Rk-RliJASLl "><button aria-controls="AccordionPanel-3ac4f4cc-5ba4-4888-b8d8-dd14ec6637bc" aria-expanded="false" id="AccordionPanel-3ac4f4cc-5ba4-4888-b8d8-dd14ec6637bc-toggle" type="button"><div><div class="APIResponseSchemaPicker-label3XMQ9E-slNcS"><code class="APIResponseSchemaPicker-label-text3bDdrQX1B-h4 HTTPStatus HTTPStatus_2"><span aria-hidden="false" aria-label="200" class="HTTPStatus-chit" role="img"></span></code> 200</div><div class="rm-Markdown markdown-body APIResponseSchemaPicker-description19iNatTizvwb" data-testid="RDMD"><p>Successful response</p></div></div><div class="AccordionToggle-icon-slot1bf45OBGkGPr"><span class="IconWrapper Icon-wrapper2z2wVIeGsiUy"><svg fill="none" viewBox="0 0 24 24" class="Icon Icon3_D2ysxFZ_ll Icon-svg2Lm7f6G9Ly5a AccordionToggle-iconDAVsqS10Xl8E" data-name="chevron-right" role="img" aria-label="Chevron" style="--icon-color: inherit; --icon-size: inherit; --icon-stroke-width: 2px;"><path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" d="m9 18 6-6-6-6" class="icon-stroke-width"></path></svg></span></div></button></h1>
