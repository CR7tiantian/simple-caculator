<!DOCTYPE html>
<html>
<head>
  <title>简易计算器</title>
    <meta charset="UTF-8">
</head>
<style type="text/css">
    #result {
        width: 400px;
        height:  100px;
        background-color: black;
        color: white;
        font-size: 35px;
        text-align: right;
    };
    table {
        border-collapse: collapse;
        border-spacing:0px;
    };
</style>
<body>
<div style="width:400px;height:100px;margin:0px 20px">
    <input type="text" id="result">
</div>
<div style="width:400px;height:200px margin:0px 20px" >
    <table  style="width:400px;height:300px; margin:0px 20px" cellpadding="0" cellspacing="0">
        <tr>
            <td><input type="button" class="reset" id="reset" value="C" style="width:100%;height:100%;font-size:35px;"></td>
            <td><input type="button" class="reverse" id="reverse" value="-" style="width:100%;height:100%;font-size:35px;"></td>
            <td><input type="button" class="persent" id="persent" value="%" style="width:100%;height:100%;font-size:35px;"></td>
            <td><input type="button" class="division" id="division" value="÷" style="width:100%;height:100%;font-size:35px;color:white;background-color:orange;" ></td>         
        </tr>
        <tr>
            <td><input type="button" class="number" id="7" value="7" style="width:100%;height:100%;font-size:35px;"></td>
            <td><input type="button" class="number" id="8" value="8" style="width:100%;height:100%;font-size:35px;"></td>
            <td><input type="button" class="number" id="9" value="9" style="width:100%;height:100%;font-size:35px;"></td>
            <td><input type="button" class="multiply" id="multiply" value="×" style="width:100%;height:100%;font-size:35px;color:white;background-color:orange;" ></td>
        </tr>
        <tr>
            <td><input type="button" class="number" id="4" value="4" style="width:100%;height:100%;font-size:35px;"></td>
            <td><input type="button" class="number" id="5" value="5" style="width:100%;height:100%;font-size:35px;"></td>
            <td><input type="button" class="number" id="6" value="6" style="width:100%;height:100%;font-size:35px;"></td>
            <td><input type="button" class="reduce" id="reduce" value="－" style="width:100%;height:100%;font-size:35px;color:white;background-color:orange;"  ></td>
        </tr>
        <tr>
            <td><input type="button" class="number" id="1" value="1"  style="width:100%;height:100%;font-size:35px;"></td>
            <td><input type="button" class="number" id="2" value="2" style="width:100%;height:100%;font-size:35px;"></td>
            <td><input type="button" class="number" id="3" value="3" style="width:100%;height:100%;font-size:35px;"></td>
            <td><input type="button" class="sum" id="sum" value="+" style="width:100%;height:100%;font-size:35px;color:white;background-color:orange;" ></td>
        </tr>
        <tr>
            <td  colspan="2"><input type="button" class="number" id="0" value="0" style="width:100%;height:100%;font-size:35px;"></td>
            <td><input type="button" class="dot" id="dot" value="." style="width:100%;height:100%;font-size:35px;"></td>
            <td><input type="button" class="number" id="equal" value="=" style="width:100%;height:100%;font-size:35px;color:white;background-color:orange;" ></td>
        </tr>

    </table>
</div>
<script type="text/javascript" src="js文件/简易计算器.js"></script>
</body>
</html>

// js部分
var result = document.getElementById("result");
var dot = document.getElementById("dot");
var sum = document.getElementById("sum");
var reduce = document.getElementById("reduce");
var multiply = document.getElementById("multiply");
var division = document.getElementById("division");
var equal = document.getElementById("equal");
var flag = 1;	//为0时清除文本框内容
result.focus();

//  点击数字出现在文本框
var click = function(event) {
	if (flag === 0) {
		result.value = "";
	}
	flag = 1;
  result.value = result.value + event.target.value;
    return result.value;
};

//  点击数字按钮函数
function count() {
    for (var i = 0; i < 10; i++) {
        document.getElementById(i).onclick = click;
    }
};
count();

//  清零按钮函数
document.getElementById("reset").onclick = function() {
    result.value = ""
};

//  "."按钮
dot.onclick = function() {
	if (flag === 0) {
		result.value = "";
	}
	flag = 1;
	if (result.value =="") {
		result.value = "0" + result.value;
	}
    result.value = result.value + dot.value;
};

//  加法
sum.onclick = function() {
    var result1 = result.value;
    result.value = "";
    count();
    equal.onclick = function() {
        var result2 = result.value;
        result.value = Number(result1) + Number(result2);
        flag = 0;
    }
};

//  减法
reduce.onclick = function() {
    var result1 = result.value;
    result.value = "";
    count();
    equal.onclick = function() {
        var result2 = result.value;
        result.value = Number(result1) - Number(result2);
        flag = 0;
    }
};

// 乘法
multiply.onclick = function() {
    var result1 = result.value;
    result.value = "";
    count();
    equal.onclick = function() {
        var result2 = result.value;
        result.value = Number(result1) * Number(result2);
        flag = 0;

    }
};

// 除法
division.onclick = function() {
    var result1 = result.value;
    result.value = "";
    count();
    equal.onclick = function() {
        var result2 = result.value;
        if (result2 === "0") {
            result.value = "错误";
        } else {
            result.value = Number(result1) / Number(result2);
            flag = 0;
        }
    }
};

//  百分号
persent.onclick = function() {
    if (result.value !== "") {
        result.value = Number(result.value) / 100
    }
};

// 负号
reverse.onclick = function() {
    if (result.value !== "") {
        result.value = -Number(result.value);
    }
}






