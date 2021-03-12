# Remember to change the path first
INIT_RESULT = fixed/tsung.log
PAGE_RESULT = with_pagination/tsung.log
VERT_RESULT = c5_xlarge/tsung.log
HORI_RESULT = hori/tsung.log
CACH_RESULT = with_cache/tsung.log
DXLA_RESULT = 2xlarge/tsung.log
QXLA_RESULT = 4xlarge/tsung.log

COMP_OK_CONF = tsplot_configs/normal.conf
COMP_ERROR_CONF = tsplot_configs/error.conf

BOTTLE_OK_CONF = tsplot_configs/bottle_normal.conf
BOTTLE_ERROR_CONF = tsplot_configs/bottle_error.conf

VERT_CMP_OK = tsplot_configs/vert_cmp_normal.conf
VERT_CMP_ERROR = tsplot_configs/vert_cmp_error.conf

plot:
	rm -rf comparisons
	mkdir comparisons
	tsplot -d comparisons/init_page_200 without_pagination $(INIT_RESULT) with_pagination $(PAGE_RESULT) -c $(COMP_OK_CONF)
	tsplot -d comparisons/init_page_500 without_pagination $(INIT_RESULT) with_pagination $(PAGE_RESULT) -c $(COMP_ERROR_CONF)

	tsplot -d comparisons/page_cach_200 without_caching $(PAGE_RESULT) with_caching $(CACH_RESULT) -c $(COMP_OK_CONF)
	tsplot -d comparisons/page_cach_500 without_caching $(PAGE_RESULT) with_caching $(CACH_RESULT) -c $(COMP_ERROR_CONF)

	tsplot -d comparisons/scale_cmp_200 4_m5.xlarge $(HORI_RESULT) c5.xlarge $(VERT_RESULT) c5.2xlarge $(DXLA_RESULT) c5.4xlarge $(QXLA_RESULT) -c $(VERT_CMP_OK)
	tsplot -d comparisons/scale_cmp_500 4_m5.xlarge $(HORI_RESULT) c5.xlarge $(VERT_RESULT) c5.2xlarge $(DXLA_RESULT) c5.4xlarge $(QXLA_RESULT) -c $(VERT_CMP_ERROR)

	tsplot -d comparisons/bottle_200 "" $(INIT_RESULT) -c $(BOTTLE_OK_CONF)
	tsplot -d comparisons/bottle_500 "" $(INIT_RESULT) -c $(BOTTLE_ERROR_CONF)
