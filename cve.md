---
title: CVE Data Report
---
## CVE Data Report

CVE data can be collected by searching using the web interface or programmatically via the API provided by NVD.

Web-Based Search:
* [www.cvedetails.com](www.cvedetails.com) provides an easy-to-use web interface to CVE vulnerability data.  CVE vulnerability data are taken from National Vulnerability Database (NVD) XML feeds provided by the National Institute of Standards and Technology.
* This data can be searched by using keywords for the critical assets such as "SQL Database", "Oracle Database" or using the vendor and products names.
* The data search result can be sorted based on CVSS score, published date or complexity and can be downloaded for use by the AI4Cyber platform.

API Driven Search:
* [https://nvd.nist.gov/vuln/data-feeds](https://nvd.nist.gov/vuln/data-feeds) provides a detailed API documentation for accessing CVE data programmatically through API calls.
* We can collect CVE data through API call to the NVD vulnerability rest services by using the following URLs to search by using the critical assets as a key word or using a particular CVE id for details:
** [https://services.nvd.nist.gov/rest/json/cves/1.0?keyword=database](https://services.nvd.nist.gov/rest/json/cves/1.0?keyword=database)
** [https://services.nvd.nist.gov/rest/json/cve/1.0/CVE-2021-1636](https://services.nvd.nist.gov/rest/json/cve/1.0/CVE-2021-1636)

<table id="cve" class="display" style="width:100%"></table>

<script>
$(document).ready(function() {
    $('#cve').dataTable( {
        "ajax": {
            url: "{{ '/cve_data.json' | relative_url }}",
            dataSrc: ''
        },
        columns: [
            { data: 'Product', title: 'Product' },
            { data: 'CVE ID', title: 'CVE ID' },
            { data: 'Vulnerability Types(s)', title: 'Vulnerability Type(s)' },
            { data: 'Publish Date', title: 'Publish Date' },
            { data: 'Score', title: 'Score' },
            { data: 'Complexity', title: 'Complexity' },
            { data: 'Description',
              title: 'Description',
              render: function (data, type) {
                return type === 'display' && data.length > 40 ? 
                                '<span title="'+data+'">'+data.substr(0,38)+'...</span>' : 
                                data;
                }
            },
        ]
    } );
})
</script>
