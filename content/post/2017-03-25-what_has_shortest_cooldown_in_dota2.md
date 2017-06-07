---

title: 'Dota 2里，什么技能的冷却时间最短？'
author: HeYSH
type: post
date: 2017-03-25T13:13:15+00:00
url: /2017/03/25/what_has_shortest_cooldown_in_dota2/
aliases:
  - /2017/03/25/what_has_shortest_cooldown_in_dota2/
dsq_thread_id:
  - "5664702825"
categories:
  - 未分类

---
答案是各种法球\~开玩笑的\~

最近沉迷Dota2的一个RPG： [Legends of Dota:Redux](https://steamcommunity.com/sharedfiles/filedetails/?id=717356279)（当然是人机），在挑技能的时候常常需要一些短cd的技能，但是[wiki](http://dota2.gamepedia.com/Abilities)里居然没有技能冷却时间的排序！

所以我就自己排了一个：<https://gist.github.com/heyeshuang/8499513305ff5c92b16329f57a0f29c6>

数据来源是客户端里面`\dota2\steamapps\common\dota 2 beta\game\dota\scripts\npc\npc\_abilities.txt`，在下可不是页游玩家！

这个文件看起来特别像是JSON，但是是用空格分割的，而且还有\\\\注释。本来把这东西转换成JSON才是工作的大头，可是我懒了：找到了另一个玩家的[Dota 2 items.txt/npc\_abilities.txt to xml/json tool v1.1](http://uglyvpn.com/2015/03/01/dota-2-items-txt-to-xmljson-tool/)，然后就是简单的排序了\~

另外，除了法球，还有许多技能也是0秒CD的哦，比如幽鬼的降临什么的\~



``` json
{
  "Name": " reality",
  "HeroName": "spectre",
  "ID": "5338",
  "Cooldown": 0.0
},
```