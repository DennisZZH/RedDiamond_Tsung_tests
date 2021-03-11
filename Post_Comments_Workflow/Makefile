# Remember to change the path first
INIT_RESULT = logs/init_tsung.log
PAGE_RESULT = logs/pagination_tsung.log
VERT_RESULT = logs/vert_tsung.log
HORI_RESULT = logs/hori_tsung.log
CACH_RESULT = logs/cache_tsung.log
DXLA_RESULT = logs/2xlarge_tsung.log
QXLA_RESULT = logs/4xlarge_tsung.log

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

	tsplot -d comparisons/init_cach_200 without_caching $(INIT_RESULT) with_caching $(CACH_RESULT) -c $(COMP_OK_CONF)
	tsplot -d comparisons/init_cach_500 without_caching $(INIT_RESULT) with_caching $(CACH_RESULT) -c $(COMP_ERROR_CONF)

	tsplot -d comparisons/page_vert_200 c5.large $(PAGE_RESULT) m5.xlarge $(VERT_RESULT) -c $(COMP_OK_CONF)
	tsplot -d comparisons/page_vert_500 c5.large $(PAGE_RESULT) m5.xlarge $(VERT_RESULT) -c $(COMP_ERROR_CONF)

	tsplot -d comparisons/vert_hori_200  1_m5.xlarge $(VERT_RESULT) 4_m5.xlarge $(HORI_RESULT) -c $(COMP_OK_CONF)
	tsplot -d comparisons/vert_hori_500  1_m5.xlarge $(VERT_RESULT) 4_m5.xlarge $(HORI_RESULT) -c $(COMP_ERROR_CONF)

	tsplot -d comparisons/vert_cmp_200 c5.large $(INIT_RESULT) m5.xlarge $(VERT_RESULT) m5.2xlarge $(DXLA_RESULT) m5.4xlarge $(QXLA_RESULT) -c $(VERT_CMP_OK)
	tsplot -d comparisons/vert_cmp_500 c5.large $(INIT_RESULT) m5.xlarge $(VERT_RESULT) m5.2xlarge $(DXLA_RESULT) m5.4xlarge $(QXLA_RESULT) -c $(VERT_CMP_ERROR)

	tsplot -d comparisons/bottle_200 "" $(INIT_RESULT) -c $(BOTTLE_OK_CONF)
	tsplot -d comparisons/bottle_500 "" $(INIT_RESULT) -c $(BOTTLE_ERROR_CONF)
