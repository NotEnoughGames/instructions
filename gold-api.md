# NotEnoughGames 黄金 API

我们将 NotEnoughGames 的 API 分为[普通 API](https://github.com/NotEnoughGames/metadata-server) 与黄金 API 两种。前者的生产版本以 AGPL-3.0 开源在 GitHub 上，而后者为我们的私有代码。

黄金 API 主要提供对中文元数据的批量访问。NotEnoughGames 在此秉承着开放的原则提供 API 访问参考。若您需要对应的完整数据库，亦可联系 `notenoughgames@public.oott123.com` 说明来意，我们将尽力协助。

请注意我们的开放 API 仅供非商业使用，并不提供任何可用性保证。

## API 参考

API 访问端点： https://meta.notenough.games

### POST /gold/meta/bulk

批量获取中文元数据。

#### 请求格式

```http
POST /gold/meta/bulk HTTP/1.1
Host: meta.notenough.games
Content-Type: application/json

{
    "appIds": [10, 20, 4000]
}
```

请求体为 json 格式，其中包含 appIds 字段，字段内容为数字数组，含义为 steam appid。

请注意单次请求不能超过 100 个；除此之外没有任何限制。

### 返回格式

```json
[
	{
		"appId": 10,
		"cowlevelTitle": "反恐精英 Counter-Strike",
		"keylolTitle": "反恐精英",
		"stdbcnTitle": "反恐精英",
		"heyboxTitle": "反恐精英",
		"bingtranslateTitle": "反罢工"
	},
	{
		"appId": 20,
		"cowlevelTitle": null,
		"keylolTitle": "军团要塞",
		"stdbcnTitle": "军团要塞：经典版",
		"heyboxTitle": "军团要塞：经典版",
		"bingtranslateTitle": "团队堡垒经典"
	},
	{
		"appId": 30,
		"cowlevelTitle": null,
		"keylolTitle": "胜利之日",
		"stdbcnTitle": "胜利之日",
		"heyboxTitle": "胜利之日",
		"bingtranslateTitle": "失败之日"
	},
	{
		"appId": 4000,
		"cowlevelTitle": "盖瑞模组 Garry's Mod",
		"keylolTitle": "盖瑞模组",
		"stdbcnTitle": "盖瑞模组",
		"heyboxTitle": "盖瑞模组",
		"bingtranslateTitle": "加里的国防部"
	}
]
```

返回各个第三方的中文译名。请注意，数组顺序并不一定和提交的一致，并且并不是每个 appId 都有对应记录。