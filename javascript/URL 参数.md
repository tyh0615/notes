## js获取url的多个参数

```
help_center?uid=$uid&phone=14786151457&nickname=username

function GetRequest() {  
    var url = location.search;
    var theRequest = new Object();  
    if (url.indexOf("?") != -1) {  
        var str = url.substr(1);  
        strs = str.split("&");  
        for (var i = 0; i < strs.length; i++) {  
            theRequest[strs[i].split("=")[0]] = unescape(strs[i].split("=")[1]);  
        }  
    }  
    return theRequest;  
}
var request = new Object();  
request = GetRequest();  
var uid = request['uid'];  
var phone = request['phone'];  
var nickname = request['nickname'];  
```

## js获取url的单个参数并请求数据

```
$(function() {
        function GetQueryString(item_id) {
            var reg = new RegExp("(^|&)" + item_id + "=([^&]*)(&|$)", "i");
            var r = window.location.search.substr(1).match(reg);
            if (r != null) return (r[2]);
            return null;
        }
        var item_id = GetQueryString("item_id");
        if (item_id != null) {
            var item_id_ = decodeURIComponent(item_id);
            $.post(
                'https://www.lzcke.com/index.php/Api/Franchisee/store_proposal?item_id=' + item_id_, 
                { franchisee_id: item_id_ },
                function(data) {
                    $data = JSON.parse(data);
                    for (var i in $data.msg) {
                        $('#imgBox').html($data.msg[i]);
                    }
                }
            )
        }
    })
```

