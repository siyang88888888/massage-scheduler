# Massage Scheduler Starter

这是云同步正式版的起步项目。需要 Supabase 数据库。

## Supabase SQL
在 Supabase SQL Editor 运行：

```sql
create table if not exists orders (
  id uuid primary key default gen_random_uuid(),
  created_at timestamp with time zone default now(),
  shop text not null,
  phone_tail text,
  people int not null,
  duration int not null,
  start_time text not null,
  status text default 'scheduled',
  assigned text[] default '{}',
  base_fee numeric default 0,
  extra_fee numeric default 0,
  tip numeric default 0,
  base_pay_method text default 'card',
  extra_pay_method text default 'cash',
  tip_pay_method text default 'cash'
);

alter table orders enable row level security;
create policy "public read" on orders for select using (true);
create policy "public insert" on orders for insert with check (true);
create policy "public update" on orders for update using (true);
create policy "public delete" on orders for delete using (true);
```
