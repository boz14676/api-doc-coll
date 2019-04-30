# 获取设置的menu
#API文档/文件权限 

获取任务类型

**URL** : `/api/v2/pts/fprivilege/get_info`

**Auth required** : YES

**Data constraints**

```json
{
    "subjects": "Array 期望返回的主题 [ftypes, menu]"
    "project_id": "Integer 项目ID Optional"
}
```

>  `$subject` 为”menu”时，返回参数为 `menu`   
>  `$subject` 为”ftypes”时，返回参数为 `ftypes` ，`project_id` 可以为空。  

**Data example**

```json
{
}
```

## Success Response

**Code** : `200 OK`

**Content example**

`ftypes` 是每个项目阶段都有的文件类型，属于 `key-value` 结构。`key` 为每个独立 `ftypes` 元素的ID，可用于文件权限设置/获取接口的 `ftype ` 属性，`value` 用于展示文本。

```json

    ftypes: {
        "input": "输入",
        "output": "输出",
        "engineering": "工程",
        "reference": "参考",
    },
    menu: [
        {"name": "任务类型1", "_child": [{"pts_token": "xx_xxx", "name": "任务阶段1"},]},
        {"name": "任务类型2", "_child": [{"pts_token": "xx_xxx", "name": "任务阶段3"},]},
    ]
}
```

## Error Response

**Condition** : If 'username' and 'password' combination is wrong.

**Code** : `400 BAD REQUEST`

**Content** :

```json
{
    "non_field_errors": [
        "Unable to login with provided credentials."
    ]
}
```
