# MY-SYSTEM-<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>简易管理网站 - 手机清理</title>
    <style>
        /* 样式区 */
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            display: flex;
            align-items: center;
            justify-content: center;
            height: 100vh;
            background-color: #f7f9fc;
        }
        
        .admin-container {
            width: 350px;
            padding: 20px;
            background-color: #ffffff;
            box-shadow: 0px 4px 12px rgba(0, 0, 0, 0.1);
            border-radius: 10px;
        }

        h1 {
            color: #333;
            font-size: 22px;
            text-align: center;
        }

        .input-group {
            margin-top: 15px;
            display: flex;
            flex-direction: column;
        }

        .input-group label {
            font-size: 14px;
            color: #666;
        }

        .input-group input {
            padding: 10px;
            border-radius: 5px;
            border: 1px solid #ddd;
            margin-top: 5px;
            font-size: 16px;
        }

        .input-group button {
            margin-top: 15px;
            padding: 12px;
            border: none;
            border-radius: 5px;
            background-color: #4CAF50;
            color: white;
            font-size: 16px;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .input-group button:hover {
            background-color: #45a049;
        }

        .output {
            margin-top: 20px;
            padding: 10px;
            background-color: #e8f5e9;
            border: 1px solid #4CAF50;
            border-radius: 5px;
            color: #333;
            font-size: 16px;
            text-align: center;
        }

        .alert {
            color: #ff0000;
            font-size: 14px;
            margin-top: 10px;
            text-align: center;
        }

        .cleaning-status {
            margin-top: 20px;
            padding: 10px;
            background-color: #fbe9e7;
            border: 1px solid #f44336;
            color: #d32f2f;
            border-radius: 5px;
            font-size: 16px;
        }
    </style>
</head>
<body>

<div class="admin-container">
    <h1>简易管理面板</h1>

    <!-- 输入和按钮区域 -->
    <div class="input-group">
        <label for="admin-input">输入内容：</label>
        <input type="text" id="admin-input" placeholder="输入一些内容">
        <button onclick="displayContent()">提交内容</button>
    </div>

    <!-- 显示提交的内容 -->
    <div class="output" id="output-display">显示内容将在这里</div>

    <!-- 提示区域 -->
    <div class="alert" id="alert-message" style="display: none;">权限不足，无法操作。</div>

    <!-- 清理操作按钮 -->
    <div class="input-group">
        <button onclick="startCleaning()">开始扫描与清理</button>
    </div>

    <!-- 清理状态区域 -->
    <div id="cleaning-status" class="cleaning-status" style="display: none;">
        清理完成！系统已经优化。
    </div>
</div>

<script>
    let hasAdminRights = true;  // 设置最高权限变量

    function displayContent() {
        if (hasAdminRights) {
            const inputContent = document.getElementById("admin-input").value;
            const outputDisplay = document.getElementById("output-display");
            const alertMessage = document.getElementById("alert-message");

            if (inputContent) {
                // 防止XSS攻击：对输入进行HTML转义
                const safeContent = inputContent.replace(/</g, "&lt;").replace(/>/g, "&gt;");
                outputDisplay.textContent = safeContent;
                alertMessage.style.display = "none";
            } else {
                alert("请输入内容！");
            }
        } else {
            const alertMessage = document.getElementById("alert-message");
            alertMessage.style.display = "block";
            alertMessage.textContent = "权限不足，无法操作。";
        }
    }

    function startCleaning() {
        // 模拟清理操作
        const cleaningStatus = document.getElementById("cleaning-status");

        // 显示清理中状态
        cleaningStatus.style.display = "block";
        cleaningStatus.textContent = "正在扫描并清理系统...";

        // 模拟清理延时
        setTimeout(function() {
            // 模拟完成清理
            cleaningStatus.textContent = "清理完成！系统已经优化。";
        }, 2000);  // 模拟2秒的清理过程
    }
</script>

</body>
</html>
