# BiliBiliDailyBonus-LoonFix

这是一个基于 [ClydeTime/BiliBili](https://github.com/ClydeTime/BiliBili) 的个人修订版。

保留原脚本用途与作者署名，本仓库只做两类调整：

- 修正 Loon 场景下“实际已经投币，但脚本按失败处理”的判定问题
- 增加投币接口返回日志与二次复核记录，便于确认真实返回

订阅地址：

- 插件订阅：`https://raw.githubusercontent.com/WenJiazhi/BiliBiliDailyBonus-LoonFix/main/BiliBiliDailyBonus.plugin`

当前投币确认逻辑：

- 先看投币接口返回的 `code/message`
- 如果接口返回不符合成功条件，再查询 `x/member/web/exp/reward`
- 只要今日投币经验值确实增长，就按成功处理
- 同时记录最近一次投币返回：`code`、`message`、`data`、复核前后经验值、是否复核成功
