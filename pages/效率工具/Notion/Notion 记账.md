包括两个 Database
- Transactions 交易记录表: 时间、账户、金额
    - table - 按源账户分组, 不包含已归档记录
    - board - 按源账户、时间分组, 不包含已归档记录: 方便获知每个月每个账户下的支出情况
    - board - 按目的账户、时间分组: 方便获知每个月的支出类别
- Accounts 账户表: 分资产、负债、收入、支出、权益五大类, 参考 _[Beancount](https://beancount.github.io/docs/)_、_GnuCash_
    - table
    - board

>[!note] (Assets + Expenses) + (Liabilities + Income) + Equity = 0
> -   资产: 主要是支付账户
> - 负债: 用负值表示
> - 收入: 用负值表示 (收入 → 资产)
> - 支出: 用正值表示
> - 权益: 初始净值 (暂不记录), 权益 → 资产
> 
> 不考虑符号的情况下:
> 资产 = 负债 + 权益 (等号可以理解为来源)
>  对于每个账户: 期初余额 + 收入 - 支出 = 期末余额

![](../../../resources/attachments/Notion%20记账-20220928.png)