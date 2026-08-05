# 岗位胜任力模型面试系统

这是一个可安装的 Web App（PWA），包含岗位 Brief、胜任力模型、结构化面试题库、面试评价与决策汇总。

## 发布到 GitHub Pages

1. 在 GitHub 新建一个仓库。
2. 将本目录内的全部文件上传到仓库的 `main` 分支。
3. 打开仓库的 **Settings → Pages**。
4. 在 **Build and deployment** 中将 **Source** 设为 **Deploy from a branch**，选择 `main` 和 `/(root)`。
5. 等待 GitHub Pages 完成发布，页面中会显示访问地址。

发布后，可在手机或电脑浏览器中打开网址，并选择“添加到主屏幕”或“安装应用”。

## 岗位 JD 批量导入

页面支持导入 JSON 或 CSV。字段包括：`jobName`、`industry`、`responsibility`、`company`、`team`、`goals`、`constraints`。其中只有 `jobName` 为必填；`responsibility` 也可使用 `jd` 或 `description`。

外部系统也可以调用浏览器端接口：

```js
window.InterviewBriefAPI.importJobs([
  {
    jobName: "招聘经理",
    responsibility: "负责招聘规划、关键岗位交付和招聘渠道建设。",
    goals: "提升关键岗位到岗率并缩短招聘周期。"
  }
]);
```

`InterviewBriefAPI.getJobs()` 可读取已导入岗位，`InterviewBriefAPI.getSavedBrief()` 可读取已保存的岗位 Brief。

> 当前版本将岗位 Brief 和导入的岗位库保存在当前设备的浏览器本地存储中，不会上传到服务器。正式接入企业后端时，可在此浏览器端接口之上增加鉴权和服务器数据同步。
