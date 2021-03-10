# Remember to change the path first
INIT_RESULT = initial_test/tsung.log
PAGE_RESULT = with_pagination/20210309-2305/tsung.log
VERT_RESULT = vert_scale_m5_xlarge/20210309-2315/tsung.log
HORI_RESULT = hori_scale_4x_m5_xlarge/20210309-2350/tsung.log

COMP_OK_CONF = tsplot_configs/normal.conf
COMP_ERROR_CONF = tsplot_configs/error.conf

BOTTLE_OK_CONF = tsplot_configs/bottle_normal.conf
BOTTLE_ERROR_CONF = tsplot_configs/bottle_error.conf

plot:
	mkdir comparisons
	tsplot -d comparisons/init_page_200 without_pagination $(INIT_RESULT) with_pagination $(PAGE_RESULT) -c $(COMP_OK_CONF)
	tsplot -d comparisons/init_page_500 without_pagination $(INIT_RESULT) with_pagination $(PAGE_RESULT) -c $(COMP_ERROR_CONF)

	tsplot -d comparisons/page_vert_200 c5.large $(PAGE_RESULT) m5.xlarge $(VERT_RESULT) -c $(COMP_OK_CONF)
	tsplot -d comparisons/page_vert_500 c5.large $(PAGE_RESULT) m5.xlarge $(VERT_RESULT) -c $(COMP_ERROR_CONF)

	tsplot -d comparisons/vert_hori  1_m5.xlarge $(VERT_RESULT) 4_m5.xlarge $(HORI_RESULT) -c $(COMP_OK_CONF)
	tsplot -d comparisons/vert_hori  1_m5.xlarge $(VERT_RESULT) 4_m5.xlarge $(HORI_RESULT) -c $(COMP_ERROR_CONF)

	tsplot -d comparisons/bottle_200 "" $(INIT_RESULT) -c $(BOTTLE_OK_CONF)
	tsplot -d comparisons/bottle_500 "" $(INIT_RESULT) -c $(BOTTLE_ERROR_CONF)