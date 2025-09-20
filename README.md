# hanzi-student-portal
A simple Flask-based student login portal for Hanzi Tuition
High-level Flow (整体流程)

Client (Browser / App 前端)
```bash
→ FastAPI (API + Validation 接口与校验层)
→ Service Layer (Business Logic 业务服务层)
→ Repository / ORM (数据访问层：SQLModel/SQLAlchemy)
→ Database (DB 数据库：SQLite/MySQL/PostgreSQL)
```

flowchart LR
```bash
  A[Client 前端<br/>Browser / Mobile] --> B[FastAPI API<br/>Routing + Validation]
  B --> C[Service 业务服务层<br/>rules, calculations]
  C --> D[Repository 仓储层<br/>SQLModel / SQLAlchemy]
  D --> E[(Database 数据库)]
  B <-- JWT/Auth --- A

  ```

What each layer does (每层做什么)

Client (前端)
```bash
EN: Forms, dashboards, upload/download, calls REST endpoints.

中：表单、看板、上传下载，通过 REST 调用后端接口。

Example: POST /auth/login, GET /policies?status=active
```
FastAPI (API + Validation)
```bash
EN: Define routes; validate inputs (Pydantic); auth (Basic/JWT); rate limiting & error handling.

中：定义路由；校验请求数据；鉴权（Basic/JWT）；限流与错误处理。

Example:

@app.post("/quotes/") validate quote request JSON

@app.get("/employees/{id}") validate path/query
```

Service Layer (业务服务层)

```bash
EN: Core rules—e.g., plan selection logic, premium calculation, eligibility, workflow.

中：业务规则——如方案匹配、保费计算、资格判断、流程编排。

Example: select_best_plan(employee_profile, insurers) returns ranked options.
```

Repository / ORM (数据访问层)
```bash
EN: SQLModel sessions; CRUD for employees, policies, quotes, claims.

中：SQLModel 会话；对员工、保单、报价、理赔做增删改查。

Example: EmployeeRepo.get_by_id(id), QuoteRepo.create(quote)
```

Database (数据库)
```bash
EN: Tables & relations (schemas) for Employees, Policies, Plans, Insurers, Quotes, Claims, Users.

中：表结构与关联：员工、保单、方案、保险公司、报价、理赔、用户。```
