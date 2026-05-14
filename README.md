# MyBatis 日志格式化工具

一款在线 MyBatis SQL 日志解析与格式化工具，可智能识别日志中的 SQL 语句，自动拼接参数，生成可执行的完整 SQL。

## 功能特性

- **智能解析** - 自动识别 `Preparing`、`Parameters`、`Columns`、`Row` 等 MyBatis 日志元素
- **参数自动拼接** - 将 `?` 占位符替换为实际参数值
- **语法高亮** - SQL 关键字、字符串、数字等分类着色
- **多格式支持** - 支持 SELECT、INSERT、UPDATE、DELETE 语句类型识别
- **查询结果展示** - 解析并展示查询返回的列名和数据行
- **一键复制** - 单条或批量复制格式化后的 SQL
- **响应式布局** - 支持桌面端和移动端使用

## 支持的日志格式

### 标准 Spring Boot + MyBatis 日志

```
2024-01-15 10:23:45.123 DEBUG 12345 --- [nio-8080-exec-1] c.e.m.mapper.UserMapper.selectById     : ==>  Preparing: SELECT * FROM user WHERE id = ?
2024-01-15 10:23:45.145 DEBUG 12345 --- [nio-8080-exec-1] c.e.m.mapper.UserMapper.selectById     : ==> Parameters: 1001(Long)
2024-01-15 10:23:45.178 DEBUG 12345 --- [nio-8080-exec-1] c.e.m.mapper.UserMapper.selectById     : <==      Total: 1
```

### 支持的日志标记

| 标记 | 说明 | 示例 |
|------|------|------|
| `==> Preparing:` | SQL 语句 | `==> Preparing: SELECT * FROM user WHERE id = ?` |
| `==> Parameters:` | 参数列表 | `==> Parameters: 1001(Long), 'test'(String)` |
| `<== Columns:` | 查询结果列名 | `<== Columns: id, name, email` |
| `<== Row:` | 查询结果行数据 | `<== Row: 1, John, john@example.com` |
| `<== Total:` | 查询返回总数 | `<== Total: 10` |
| `<== Updates:` | 影响行数 | `<== Updates: 1` |

## 使用方法

### 方式一：直接打开

直接在浏览器中打开 `index.html` 文件即可使用。

### 方式二：本地服务

```bash
# 使用 Python
python -m http.server 8080

# 使用 Node.js (npx)
npx serve .

# 使用 PHP
php -S localhost:8080
```

然后访问 `http://localhost:8080`

## 使用示例

### 1. 粘贴日志

将 MyBatis 日志内容粘贴到左侧输入框。

### 2. 点击格式化

点击「格式化」按钮或直接粘贴（自动触发）。

### 3. 查看结果

- **格式化 SQL** - 查看带语法高亮的完整 SQL 语句
- **原始日志** - 查看原始日志高亮版本

### 4. 复制使用

点击单条 SQL 的「复制」按钮，或使用「复制全部」复制所有语句。

## 参数类型支持

工具自动识别以下 Java 类型并正确格式化：

| 类型 | 格式化结果 |
|------|-----------|
| `String` | `'value'` |
| `Long`, `Integer` | `123` |
| `null` | `NULL` |
| `Date`, `Timestamp` | `'2024-01-15'` |
| `Boolean` | `1` / `0` |

## 技术栈

- 纯前端实现，无需后端
- 原生 JavaScript，无依赖
- Google Fonts (Inter, JetBrains Mono)

## License

MIT
