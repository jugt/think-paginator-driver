# ThinkPHP ORM 分页驱动库

内含以下前端框架的分页驱动

* [JugtUI](#JugtUI)


## 安装
```
composer require jugt/think-paginator-driver:dev-main
```

## 配置

### 1.服务提供定义文件里重新绑定服务
编辑`app/provider.php`文件，在该文件里重新绑定`think\Paginator`分页服务，该方法适用于ThinkPHP6，全局生效。
```php
return [
    'think\Paginator' => \jugt\thinkPaginatorDriver\JugtUI::class
];
```

### 2.公共函数文件里绑定服务
编辑`app/common.php`文件，在该文件里重新绑定`think\Paginator`分页服务，该方法适用于ThinkPHP6，全局生效。

如果想单应用生效，请在应用的公共函数文件里重新绑定`think\Paginator`分页服务，如：`app/admin/common.php`。

```php
// 设置服务注入
\think\facade\App::bind('think\Paginator', \jugt\thinkPaginatorDriver\JugtUI::class);
```

如果只想一个地方生效，可以在进行分页查询前，使用该代码重新绑定`think\Paginator`分页服务。

```
// 设置服务注入
\think\facade\App::bind('think\Paginator', \jugt\thinkPaginatorDriver\JugtUI::class);

// 获取users表数据并进行分页
$list = \think\facade\Db::table('users')->paginate();
```

### 3.配置文件里定义分页类
编辑`config/paginate.php`文件，修改`type`配置项的值为`\jugt\thinkPaginatorDriver\JugtUI::class`，该方法仅适用于ThinkPHP5.1.
```php
return [
    'type' => \jugt\thinkPaginatorDriver\JugtUI::class,
];
```

## 已支持的前端框架

### JugtUI
```php
\think\facade\App::bind('think\Paginator', \jugt\thinkPaginatorDriver\JugtUI::class);
```

## 说明
在bigDream/thinkPaginatorDriver 上修改，二次发布。
[https://github.com/big-dream/think-paginator-driver][1]

## 其它
你所用的前端框架不在这里？欢迎提交PR，或者在Issues里告诉我。
[1]: https://github.com/big-dream/think-paginator-driver