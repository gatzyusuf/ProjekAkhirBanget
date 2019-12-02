<html>
<head>
<script type="text/javascript">
	function hello() {
		$.ajax(
			{
				type: "GET",
				url : "https://adfk9kd4t1.execute-api.us-east-1.amazonaws.com/api",
				crossDomain : true,
				contentType: "application/json",
				success: function(data, status){
					dataMahasiswa = JSON.parse(data.body)
					$('#jsonTable').css("visibility", "visible").css("border", "1px solid green");
					$('#jsonTableContent').html("");
					var rows = "";
					
					for (var counter = 0; counter < dataMahasiswa.length; counter++) {
						console.log(dataMahasiswa[counter])
						rows = rows + "<tr><td>" + dataMahasiswa[counter][0] + "</td><td>" + dataMahasiswa[counter][1] + "</td></tr>";
					}
					$('#jsonTableContent').html(rows);
					$('th').css("border", "1px solid green");
				}
			}
		)
	}
</script>
<script src="https://code.jquery.com/jquery-3.1.1.min.js" type="text/javascript"></script>
</head>
<body>
	<input type="button" value="Render JSON" id="Render JSON" onclick="return hello();"/>
	<br/>
	<table id="jsonTable" style="visibility:hidden">
		<thead>
			<tr>
				<!-- The JSON downloaded from the URL above provides four attributes.-->
				<th>NIP</th>
				<th>Nama</th>
			</tr>
		</thead>
		<tbody id="jsonTableContent" ></tbody>
	</table>
</body>
</html>
