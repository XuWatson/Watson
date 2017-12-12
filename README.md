	private  HttpSession session=ServletActionContext.getRequest().getSession();
	private String dt =new SimpleDateFormat("yyyyMMddHHmmss").format(Calendar.getInstance().getTime());
	private  HttpServletRequest request=(HttpServletRequest)ActionContext.getContext().get(ServletActionContext.HTTP_REQUEST);

	public String init(DataAgent da) throws Exception {
		//企业信息列表
		IDataTable table = da.buildTable("companyInfoList");
				if (table == null) {
					table = new ClientDataTable();
					table.setInitHandle(this);
					da.setPageProperty("companyInfoList", table);
					table.openDataRule("drGetCmpInfo","");
				}else {
					da.refreshTable(table);
				}
		if (da.getDataAgentCallType().equals("1"))
			return "data";
		else
			return "success";
	}	
