```html
<!--#include("/common/action_banner.html"){}-->
<div class="am-g am-g-panel">
	<form id="editForm" name="editForm" action="" class="am-form" method="post" form-validation>
		<input type="hidden" name="sysUserWork.id" value="${sysUserWork.id!}" />
		<input type="hidden" name="sysUserWork.user_id"	value="${sysUserWork.user_id!}" />
		<div class="am-panel-group" id="user-info-main">
			<div class="am-panel am-panel-default">
				<div class="am-panel-hd">
					<h4 class="am-panel-title" data-am-collapse="{parent: '#user-info-main', target: '#user-info-base'}">用户基本信息</h4>
				</div>
				<div id="user-info-base" class="am-panel-collapse am-collapse am-in">
					<div class="am-panel-bd">
						<input type="hidden" name="sysUser.id" value="${sysUser.id!}" />
						<div class="am-g am-g-normal">
							<div class="am-u-lg-2 am-u form_title required">用户名</div>
							<div class="am-u-lg-4 am-u form_content">
								${sysUser.title!}<input type="hidden" name="sysUser.title" value="${sysUser.title!}" />
							</div>
							<div class="am-u-lg-2 am-u form_title required">姓名</div>
							<div class="am-u-lg-4 am-u form_content">${sysUser.user_name!}</div>
						</div>

						<div class="am-g am-g-normal">
							<div class="am-u-lg-2 am-u form_title">手机</div>
							<div class="am-u-lg-4 am-u form_content">${sysUser.mobile!}</div>
							<div class="am-u-lg-2 am-u form_title">邮箱</div>
							<div class="am-u-lg-4 am-u form_content">${sysUser.email!}</div>
						</div>
					</div>
				</div>
			</div>
		</div>
		<div class="am-panel-group" id="user-work-main">
			<div class="am-panel am-panel-default">
				<div class="am-panel-hd">
					<h4 class="am-panel-title" data-am-collapse="{parent: '#user-work-main', target: '#user-work-base'}">用户工作信息</h4>
				</div>
				<div id="user-work-base" class="am-panel-collapse am-collapse am-in">
					<div class="am-g am-g-normal">
						<div class="am-u-lg-2 am-u form_title required">工作部门</div>
						<div class="am-u-lg-4 am-u form_content">
							<div id="deptSelect" class="am-input-group">
								<input type="text" name="work_dept_name" class="am-form-field am-input-sm" placeholder="工作部门"	value="${sysUserWork.dept_name!}" readonly> 
								<input type="hidden" name="sysUserWork.dept_code" placeholder="工作部门" value="${sysUserWork.dept_code!}" data-rule="工作部门:required">
								<span class="am-input-group-btn">
									<button class="am-btn am-btn-default" type="button" style="height: 32px;">
										<span class="am-icon-search" style="position: relative; top: -3px;"></span>
									</button>
								</span>
							</div>
						</div>
						<div class="am-u-lg-2 am-u form_title required">工作职位</div>
						<div class="am-u-lg-4 am-u form_content">
							<select name="sysUserWork.user_position">
								<!--#for(ctSysPosition in ctSysPositions!){print("<option value=" + ctSysPosition.id + " "+ decode(sysUserWork.user_position!,ctSysPosition.id!,"selected","") +">"+  ctSysPosition.title + "</option>");}-->
							</select>
						</div>
					</div>
					<div class="am-g am-g-normal">
						<div class="am-u-lg-2 am-u form_title">角色有效日期</div>
						<div class="am-u-lg-4 am-u form_content">
							<input type="text" name="validdate" class="am-form-field am-input-sm " placeholder="有效日期" value="${sysUserRole.validdate!,'yyyy-MM-dd'}" data-rule="date;" wd-laydate>
						</div>
						<!--#if(has(viewMode) && viewMode == "dialogSave"){-->
						<div class="am-u-lg-2 am-u form_title required">默认工作</div>
						<div class="am-u-lg-4 am-u form_content">
							<label class="am-radio-inline"><input type="radio" name="sysUserWork.default_flag" value="1" data-am-ucheck
								data-rule="checked"> 是</label> 
							<label class="am-radio-inline"><input type="radio" name="sysUserWork.default_flag" value="0"
								data-am-ucheck data-rule="checked"> 否</label>
						</div>
						<!--#} else {-->
						<div class="am-u-lg-2 am-u form_title required">默认工作</div>
						<div class="am-u-lg-4 am-u form_content">
							<!--#if(has(sysUserWork) && sysUserWork.default_flag == 1){-->
							<span class="am-icon-check"></span>
							<!--#} else {-->
							<span class="am-icon-times"></span>
							<!--#}-->
						</div>
						<!--#}-->
					</div>
					<div class="am-g am-g-normal">
						<div class="am-u-lg-2 am-u form_title">最后修改</div>
						<div class="am-u-lg-4 am-u form_content">${sysUserWork.lm_user!}${sysUserWork.lm_time!,"yyyy-MM-dd HH:mm:ss"}</div>
						<div class="am-u-lg-2 am-u form_title"></div>
						<div class="am-u-lg-4 am-u form_content"></div>
					</div>
				</div>
			</div>
		</div>
		
		<div class="am-panel-group" id="user-role-info" style="height: auto; overflow-y: auto;">
			<div class="am-panel am-panel-default">
				<div class="am-panel-hd">
					<h4 class="am-panel-title" data-am-collapse="{parent: '#user-role-info', target: '#user-role-base'}">用户角色信息</h4>
				</div>
				<div id="user-role-base" class="am-panel-collapse am-collapse am-in">
					<table class="am-table am-table-bordered am-table-hover am-text-nowrap am-scrollable-horizontal">
					<thead>
					<tr>
						<th>角色</th>
						<th>
						<input type="button" id="addUserRole" value="添加角色" class='am-btn am-btn-primary am-btn-xs'/>
						</th>
					</tr>
				    </thead>
				    <tbody id="role">
						<!--#for(role in roles){-->
							<!--#if(role.work_id != null){  -->
							<tr>
				            <td>${role.role_name} <input type="hidden" name="sysUserWorkRoles" value="${role.id}" data-rule='required'></td>
				            <td>
				            	<input type="button" name="role_delete" class="am-btn am-btn-danger am-btn-xs" value="${_res['admin.global.button.del']}"/>
				            </td>
					        </tr>
							<!--#}-->
						<!--#}-->
					</tbody>
					</table>
				</div>
			</div>
		</div>
		
		<div class="am-g am-g-normal am-text-center">
			<!--#if(has(viewMode)){-->
			<!--#if(viewMode == "dialogSave"){-->
			<a id="saveBtn" href='javascript:;' load-form='/sys/ctSysUser/workSave' load-param='${sysUser.id}' class='am-btn am-btn-secondary am-btn-sm dnu'>${_res["admin.global.button.save"]}</a>
			<!--#} else if(viewMode == "dialogUpdate"){-->
			<a href='javascript:;' load-form='/sys/ctSysUser/workUpdate' load-param='${sysUser.id}' class='am-btn am-btn-secondary am-btn-sm dnu'>${_res["admin.global.button.update"]}</a>
			<!--#} }-->
			<a href='javascript:;' load-action='/sys/ctSysUser/updateLoad' load-param='${sysUser.id}' class='am-btn am-btn-default am-btn-sm dnu'>${_res["admin.global.button.back"]}</a>
		</div>
	</form>
</div>

<div id="role_list" style="display:none;overflow-y:auto;height:420px" class="am-form dnu">
	<div class="am-u-lg-2 am-u-sm-4 form_title ">搜索</div>
	<div class="am-u-lg-4 am-u-sm-8 form_content">
		<input id="search_role" type="text" class="am-form-field am-input-sm " placeholder="角色名" value="" >
	</div>
	<table class="am-table am-table-striped am-table-bordered am-table-compact am-text-nowrap am-table-hover">
					<thead>
					<tr>
						<th></th>
						<th>角色</th>
					</tr>
				    </thead>
				    <tbody>
						<!--#for(role in roles){-->
							<tr role_name=${role.role_name}>
								<!--#if(role.work_id != null){ -->
								<td><input type="checkbox" disabled="true"/></td>
								<!--#}else{ -->
								<td><input type="checkbox"/></td>
								<!--#}-->
					            <td style="display: none;">${role.id}</td>
					            <td>${role.role_name}</td>
					        </tr>
						<!--#}-->
					</tbody>
	</table>
</div>
<div id="departmentTree" class="ztree am-scrollable-horizontal dnu"></div>
<script>
Loader.sync([
$ctx+'/js/jquery.ztree.min.js',
$ctx+'/js/ztree_util.js',
$ctx+'/js/page.js',
], function() {
	PageJS.ctSysUserUserWork([<!--#for(dept in departments){print("{ id:'" + dept.dept_code + "', pId:'" + dept.parent_dept + "', name:'" + dept.dept_name + "', pk:'" + dept.id + "'},");}-->]);
});

$("#addUserRole").click(function(){
	var index = layer.open({
		type : 1,
		area : [ '600px', '500px' ],
		btn : [ 'YES', 'NO' ],
		title : "添加角色",
		shade : 0.3,
		content : $("#role_list"),
		yes : function(index){
	
				var html = '';
				$(":checkbox:checked").each(function(){
					var role_id = $(this).parent().next().text();
					var role_name = $(this).parent().next().next().text();
					html += "<tr>" + "<td>"+ role_name + "<input type='hidden' name='sysUserWorkRoles' value='"+  role_id +"'/>" + "</td>"+ "<td>" + "<input type='button' name='role_delete' class='am-btn am-btn-danger am-btn-xs' value='${_res['admin.global.button.del']}'/>" + "</td>" + "</tr>"
					if(role_id == '1631965027006367'){
						layer.open({
							title : '提示信息',
							icon : 7,
							content : "该权限需要配置sk值"
						});
					}
				});
			$("#role").append(html);
			$(":checkbox:checked").attr("disabled",true);
			$(":checkbox:checked").attr("checked",false);
			layer.close(index);
		}
	});
});

//弹框搜索功能
$("#search_role").on("keyup",function(){
	var $this = $(this);
	var val = $this.val();
	$("tr[role_name]").hide();
	if(val==''){
		$("tr").show()
	}else{
		$("tr[role_name*='"+val+"']").show();
	}
});

//删除一个角色后，layer窗口的列表对应的角色可以被选择
$(document).on("click", "input[name='role_delete']", function(){
	var role_id = '';
	role_id = $(this).parent().prev().children().val();
	$("tr[role_name]").each(function(){
		if($(this).children(":eq(1)").text() == role_id){
			$(this).children(":eq(0)").children().attr("disabled",false);
		}
	});
	$(this).parent().parent().remove();
});

</script>
```

