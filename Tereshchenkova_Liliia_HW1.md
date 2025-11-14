# Скрипт создания базы данных через терминал Docker
# psql -U postgres
psql (14.19 (Debian 14.19-1.pgdg13+1))
Type "help" for help.

postgres=# \l
                                 List of databases
   Name    |  Owner   | Encoding |  Collate   |   Ctype    |   Access privileges   
-----------+----------+----------+------------+------------+-----------------------
 postgres  | postgres | UTF8     | en_US.utf8 | en_US.utf8 | 
 template0 | postgres | UTF8     | en_US.utf8 | en_US.utf8 | =c/postgres          +
           |          |          |            |            | postgres=CTc/postgres
 template1 | postgres | UTF8     | en_US.utf8 | en_US.utf8 | =c/postgres          +
           |          |          |            |            | postgres=CTc/postgres
(3 rows)

postgres=# create database cycle_shop;
CREATE DATABASE
postgres=# \l
                                 List of databases
    Name    |  Owner   | Encoding |  Collate   |   Ctype    |   Access privileges   
------------+----------+----------+------------+------------+-----------------------
 cycle_shop | postgres | UTF8     | en_US.utf8 | en_US.utf8 | 
 postgres   | postgres | UTF8     | en_US.utf8 | en_US.utf8 | 
 template0  | postgres | UTF8     | en_US.utf8 | en_US.utf8 | =c/postgres          +
            |          |          |            |            | postgres=CTc/postgres
 template1  | postgres | UTF8     | en_US.utf8 | en_US.utf8 | =c/postgres          +
            |          |          |            |            | postgres=CTc/postgres
(4 rows)

postgres=# \q
# psql -d cycle_shop -U postgres
psql (14.19 (Debian 14.19-1.pgdg13+1))
Type "help" for help.

# DDL создания таблиц и сиквенсов
-- public.brands_seq definition

-- DROP SEQUENCE public.brands_seq;

CREATE SEQUENCE public.brands_seq
	INCREMENT BY 1
	MINVALUE 1
	MAXVALUE 9223372036854775807
	START 1
	CACHE 1
	NO CYCLE;


-- public.countries_seq definition

-- DROP SEQUENCE public.countries_seq;

CREATE SEQUENCE public.countries_seq
	INCREMENT BY 1
	MINVALUE 1
	MAXVALUE 9223372036854775807
	START 1
	CACHE 1
	NO CYCLE;


-- public.customers_seq definition

-- DROP SEQUENCE public.customers_seq;

CREATE SEQUENCE public.customers_seq
	INCREMENT BY 1
	MINVALUE 1
	MAXVALUE 9223372036854775807
	START 1
	CACHE 1
	NO CYCLE;


-- public.genders_seq definition

-- DROP SEQUENCE public.genders_seq;

CREATE SEQUENCE public.genders_seq
	INCREMENT BY 1
	MINVALUE 1
	MAXVALUE 9223372036854775807
	START 1
	CACHE 1
	NO CYCLE;


-- public.job_industry_categories_seq definition

-- DROP SEQUENCE public.job_industry_categories_seq;

CREATE SEQUENCE public.job_industry_categories_seq
	INCREMENT BY 1
	MINVALUE 1
	MAXVALUE 9223372036854775807
	START 1
	CACHE 1
	NO CYCLE;


-- public.job_titles_seq definition

-- DROP SEQUENCE public.job_titles_seq;

CREATE SEQUENCE public.job_titles_seq
	INCREMENT BY 1
	MINVALUE 1
	MAXVALUE 9223372036854775807
	START 1
	CACHE 1
	NO CYCLE;


-- public.order_statuses_seq definition

-- DROP SEQUENCE public.order_statuses_seq;

CREATE SEQUENCE public.order_statuses_seq
	INCREMENT BY 1
	MINVALUE 1
	MAXVALUE 9223372036854775807
	START 1
	CACHE 1
	NO CYCLE;


-- public.product_classes_seq definition

-- DROP SEQUENCE public.product_classes_seq;

CREATE SEQUENCE public.product_classes_seq
	INCREMENT BY 1
	MINVALUE 1
	MAXVALUE 9223372036854775807
	START 1
	CACHE 1
	NO CYCLE;


-- public.product_items_seq definition

-- DROP SEQUENCE public.product_items_seq;

CREATE SEQUENCE public.product_items_seq
	INCREMENT BY 1
	MINVALUE 1
	MAXVALUE 9223372036854775807
	START 1
	CACHE 1
	NO CYCLE;


-- public.product_lines_seq definition

-- DROP SEQUENCE public.product_lines_seq;

CREATE SEQUENCE public.product_lines_seq
	INCREMENT BY 1
	MINVALUE 1
	MAXVALUE 9223372036854775807
	START 1
	CACHE 1
	NO CYCLE;


-- public.product_sizes_seq definition

-- DROP SEQUENCE public.product_sizes_seq;

CREATE SEQUENCE public.product_sizes_seq
	INCREMENT BY 1
	MINVALUE 1
	MAXVALUE 9223372036854775807
	START 1
	CACHE 1
	NO CYCLE;


-- public.products_seq definition

-- DROP SEQUENCE public.products_seq;

CREATE SEQUENCE public.products_seq
	INCREMENT BY 1
	MINVALUE 1
	MAXVALUE 9223372036854775807
	START 1
	CACHE 1
	NO CYCLE;


-- public.states_seq definition

-- DROP SEQUENCE public.states_seq;

CREATE SEQUENCE public.states_seq
	INCREMENT BY 1
	MINVALUE 1
	MAXVALUE 9223372036854775807
	START 1
	CACHE 1
	NO CYCLE;


-- public.wealth_segments_seq definition

-- DROP SEQUENCE public.wealth_segments_seq;

CREATE SEQUENCE public.wealth_segments_seq
	INCREMENT BY 1
	MINVALUE 1
	MAXVALUE 9223372036854775807
	START 1
	CACHE 1
	NO CYCLE;

-- Drop table

-- DROP TABLE public.countries;

CREATE TABLE public.countries (
	id int4 DEFAULT nextval('countries_seq'::regclass) NOT NULL,
	"name" varchar NULL,
	CONSTRAINT countries_pk PRIMARY KEY (id)
);

-- Drop table

-- DROP TABLE public.customers;

CREATE TABLE public.customers (
	id int4 DEFAULT nextval('customers_seq'::regclass) NOT NULL,
	first_name varchar NOT NULL,
	last_name varchar NULL,
	gender_id int4 NULL,
	birthday date NULL,
	job_title_id int4 NULL,
	wealth_segment_id int4 NULL,
	address text NULL,
	postcode varchar NULL,
	state_id int4 NULL,
	deceased_indicator bool NULL,
	owns_car bool NULL,
	property_valuation int4 NULL,
	CONSTRAINT customers_pk PRIMARY KEY (id)
);

-- Drop table

-- DROP TABLE public.genders;

CREATE TABLE public.genders (
	id int4 DEFAULT nextval('genders_seq'::regclass) NOT NULL,
	"name" varchar NULL,
	CONSTRAINT genders_pk PRIMARY KEY (id)
);

-- Drop table

-- DROP TABLE public.job_industry_categories;

CREATE TABLE public.job_industry_categories (
	id int4 DEFAULT nextval('genders_seq'::regclass) NOT NULL,
	"name" varchar NULL,
	CONSTRAINT job_industry_categories_pk PRIMARY KEY (id)
);

-- Drop table

-- DROP TABLE public.job_titles;

CREATE TABLE public.job_titles (
	id int4 DEFAULT nextval('genders_seq'::regclass) NOT NULL,
	job_industry_category_id int4 NULL,
	"name" varchar NULL,
	CONSTRAINT job_titles_pk PRIMARY KEY (id)
);

-- Drop table

-- DROP TABLE public.order_statuses;

CREATE TABLE public.order_statuses (
	id int4 DEFAULT nextval('order_statuses_seq'::regclass) NOT NULL,
	"name" varchar NOT NULL,
	CONSTRAINT order_statuses_pk PRIMARY KEY (id),
	CONSTRAINT order_statuses_unique UNIQUE (name)
);

-- Drop table

-- DROP TABLE public.product_classes;

CREATE TABLE public.product_classes (
	id int4 DEFAULT nextval('product_classes_seq'::regclass) NOT NULL,
	"name" varchar NOT NULL,
	CONSTRAINT product_classes_pk PRIMARY KEY (id),
	CONSTRAINT product_classes_unique UNIQUE (name)
);

-- Drop table

-- DROP TABLE public.product_items;

CREATE TABLE public.product_items (
	id int4 DEFAULT nextval('product_items_seq'::regclass) NOT NULL,
	product_id int4 NOT NULL,
	brand_id int4 NOT NULL,
	product_line_id int4 NULL,
	product_class_id int4 NULL,
	product_size_id int4 NULL,
	standard_cost numeric NULL,
	CONSTRAINT product_items_pk PRIMARY KEY (id),
	CONSTRAINT product_items_unique UNIQUE (product_id, brand_id, product_line_id, product_class_id, product_size_id, standard_cost),
	CONSTRAINT product_items_brands_fk FOREIGN KEY (brand_id) REFERENCES public.brands(id) ON DELETE RESTRICT,
	CONSTRAINT product_items_product_classes_fk FOREIGN KEY (product_class_id) REFERENCES public.product_classes(id) ON DELETE RESTRICT,
	CONSTRAINT product_items_product_lines_fk FOREIGN KEY (product_line_id) REFERENCES public.product_lines(id) ON DELETE RESTRICT,
	CONSTRAINT product_items_product_sizes_fk FOREIGN KEY (product_size_id) REFERENCES public.product_sizes(id) ON DELETE RESTRICT,
	CONSTRAINT product_items_products_fk FOREIGN KEY (product_id) REFERENCES public.products(id)
);

-- Drop table

-- DROP TABLE public.product_lines;

CREATE TABLE public.product_lines (
	id int4 DEFAULT nextval('product_lines_seq'::regclass) NOT NULL,
	"name" varchar NOT NULL,
	CONSTRAINT product_lines_pk PRIMARY KEY (id),
	CONSTRAINT product_lines_unique UNIQUE (name)
);

-- Drop table

-- DROP TABLE public.product_sizes;

CREATE TABLE public.product_sizes (
	id int4 DEFAULT nextval('product_sizes_seq'::regclass) NOT NULL,
	"name" varchar NOT NULL,
	CONSTRAINT product_sizes_pk PRIMARY KEY (id),
	CONSTRAINT product_sizes_unique UNIQUE (name)
);

-- Drop table

-- DROP TABLE public.products;

CREATE TABLE public.products (
	id int4 DEFAULT nextval('products_seq'::regclass) NOT NULL,
	CONSTRAINT products_pk PRIMARY KEY (id)
);

-- Drop table

-- DROP TABLE public.states;

CREATE TABLE public.states (
	id int4 NULL,
	country_id int4 NULL,
	"name" varchar NULL
);

-- Drop table

-- DROP TABLE public.tmp_source_customers;

CREATE TABLE public.tmp_source_customers (
	customer_id varchar(255) NULL,
	first_name varchar(255) NULL,
	last_name varchar(255) NULL,
	gender varchar(255) NULL,
	dob varchar(255) NULL,
	job_title varchar(255) NULL,
	job_industry_category varchar(255) NULL,
	wealth_segment varchar(255) NULL,
	deceased_indicator varchar(255) NULL,
	owns_car varchar(255) NULL,
	address varchar(255) NULL,
	postcode varchar(255) NULL,
	state varchar(255) NULL,
	country varchar(255) NULL,
	property_valuation varchar(255) NULL
);

-- Drop table

-- DROP TABLE public.tmp_source_data;

CREATE TABLE public.tmp_source_data (
	transaction_id varchar(255) NULL,
	product_id varchar(255) NULL,
	customer_id varchar(255) NULL,
	transaction_date varchar(255) NULL,
	online_order varchar(255) NULL,
	order_status varchar(255) NULL,
	brand varchar(255) NULL,
	product_line varchar(255) NULL,
	product_class varchar(255) NULL,
	product_size varchar(255) NULL,
	list_price varchar(255) NULL,
	standard_cost varchar(255) NULL
);

-- Drop table

-- DROP TABLE public.transactions;

CREATE TABLE public.transactions (
	id int4 NOT NULL,
	customer_id int4 NOT NULL,
	product_item_id int4 NULL,
	created_at date NOT NULL,
	online_order bool DEFAULT true NOT NULL,
	order_status_id int4 NOT NULL,
	list_price numeric NOT NULL,
	CONSTRAINT transactions_pk PRIMARY KEY (id),
	CONSTRAINT transactions_customers_fk FOREIGN KEY (customer_id) REFERENCES public.customers(id),
	CONSTRAINT transactions_order_statuses_fk FOREIGN KEY (order_status_id) REFERENCES public.order_statuses(id),
	CONSTRAINT transactions_product_items_fk FOREIGN KEY (product_item_id) REFERENCES public.product_items(id) ON DELETE RESTRICT
);

-- Drop table

-- DROP TABLE public.transactions;

CREATE TABLE public.transactions (
	id int4 NOT NULL,
	customer_id int4 NOT NULL,
	product_item_id int4 NULL,
	created_at date NOT NULL,
	online_order bool DEFAULT true NOT NULL,
	order_status_id int4 NOT NULL,
	list_price numeric NOT NULL,
	CONSTRAINT transactions_pk PRIMARY KEY (id),
	CONSTRAINT transactions_customers_fk FOREIGN KEY (customer_id) REFERENCES public.customers(id),
	CONSTRAINT transactions_order_statuses_fk FOREIGN KEY (order_status_id) REFERENCES public.order_statuses(id),
	CONSTRAINT transactions_product_items_fk FOREIGN KEY (product_item_id) REFERENCES public.product_items(id) ON DELETE RESTRICT
);

-- Drop table

-- DROP TABLE public.transactions;

CREATE TABLE public.transactions (
	id int4 NOT NULL,
	customer_id int4 NOT NULL,
	product_item_id int4 NULL,
	created_at date NOT NULL,
	online_order bool DEFAULT true NOT NULL,
	order_status_id int4 NOT NULL,
	list_price numeric NOT NULL,
	CONSTRAINT transactions_pk PRIMARY KEY (id),
	CONSTRAINT transactions_customers_fk FOREIGN KEY (customer_id) REFERENCES public.customers(id),
	CONSTRAINT transactions_order_statuses_fk FOREIGN KEY (order_status_id) REFERENCES public.order_statuses(id),
	CONSTRAINT transactions_product_items_fk FOREIGN KEY (product_item_id) REFERENCES public.product_items(id) ON DELETE RESTRICT
);

-- Drop table

-- DROP TABLE public.transactions;

CREATE TABLE public.transactions (
	id int4 NOT NULL,
	customer_id int4 NOT NULL,
	product_item_id int4 NULL,
	created_at date NOT NULL,
	online_order bool DEFAULT true NOT NULL,
	order_status_id int4 NOT NULL,
	list_price numeric NOT NULL,
	CONSTRAINT transactions_pk PRIMARY KEY (id),
	CONSTRAINT transactions_customers_fk FOREIGN KEY (customer_id) REFERENCES public.customers(id),
	CONSTRAINT transactions_order_statuses_fk FOREIGN KEY (order_status_id) REFERENCES public.order_statuses(id),
	CONSTRAINT transactions_product_items_fk FOREIGN KEY (product_item_id) REFERENCES public.product_items(id) ON DELETE RESTRICT
);

ALTER TABLE public.transactions ADD CONSTRAINT transactions_customers_fk FOREIGN KEY (customer_id) REFERENCES customers(id);

ALTER TABLE public.transactions ADD CONSTRAINT transactions_order_statuses_fk FOREIGN KEY (order_status_id) REFERENCES order_statuses(id);

ALTER TABLE public.transactions ADD CONSTRAINT transactions_product_items_fk FOREIGN KEY (product_item_id) REFERENCES product_items(id) ON DELETE RESTRICT;

-- Drop table

-- DROP TABLE public.transactions;

CREATE TABLE public.transactions (
	id int4 NOT NULL,
	customer_id int4 NOT NULL,
	product_item_id int4 NULL,
	created_at date NOT NULL,
	online_order bool DEFAULT true NOT NULL,
	order_status_id int4 NOT NULL,
	list_price numeric NOT NULL,
	CONSTRAINT transactions_pk PRIMARY KEY (id),
	CONSTRAINT transactions_customers_fk FOREIGN KEY (customer_id) REFERENCES public.customers(id),
	CONSTRAINT transactions_order_statuses_fk FOREIGN KEY (order_status_id) REFERENCES public.order_statuses(id),
	CONSTRAINT transactions_product_items_fk FOREIGN KEY (product_item_id) REFERENCES public.product_items(id) ON DELETE RESTRICT
);

-- Drop table

-- DROP TABLE public.transactions;

CREATE TABLE public.transactions (
	id int4 NOT NULL,
	customer_id int4 NOT NULL,
	product_item_id int4 NULL,
	created_at date NOT NULL,
	online_order bool DEFAULT true NOT NULL,
	order_status_id int4 NOT NULL,
	list_price numeric NOT NULL,
	CONSTRAINT transactions_pk PRIMARY KEY (id),
	CONSTRAINT transactions_order_statuses_fk FOREIGN KEY (order_status_id) REFERENCES public.order_statuses(id),
	CONSTRAINT transactions_product_items_fk FOREIGN KEY (product_item_id) REFERENCES public.product_items(id) ON DELETE RESTRICT
);

-- Drop table

-- DROP TABLE public.transactions;

CREATE TABLE public.transactions (
	id int4 NOT NULL,
	customer_id int4 NOT NULL,
	product_item_id int4 NULL,
	created_at date NOT NULL,
	online_order bool DEFAULT true NOT NULL,
	order_status_id int4 NOT NULL,
	list_price numeric NOT NULL,
	CONSTRAINT transactions_pk PRIMARY KEY (id),
	CONSTRAINT transactions_customers_fk FOREIGN KEY (customer_id) REFERENCES public.customers(id),
	CONSTRAINT transactions_order_statuses_fk FOREIGN KEY (order_status_id) REFERENCES public.order_statuses(id),
	CONSTRAINT transactions_product_items_fk FOREIGN KEY (product_item_id) REFERENCES public.product_items(id) ON DELETE RESTRICT
);

-- Drop table

-- DROP TABLE public.transactions;

CREATE TABLE public.transactions (
	id int4 NOT NULL,
	customer_id int4 NOT NULL,
	product_item_id int4 NULL,
	created_at date NOT NULL,
	online_order bool DEFAULT true NOT NULL,
	order_status_id int4 NOT NULL,
	list_price numeric NOT NULL,
	CONSTRAINT transactions_pk PRIMARY KEY (id),
	CONSTRAINT transactions_customers_fk FOREIGN KEY (customer_id) REFERENCES public.customers(id),
	CONSTRAINT transactions_order_statuses_fk FOREIGN KEY (order_status_id) REFERENCES public.order_statuses(id),
	CONSTRAINT transactions_product_items_fk FOREIGN KEY (product_item_id) REFERENCES public.product_items(id) ON DELETE RESTRICT
);

-- Drop table

-- DROP TABLE public.transactions;

CREATE TABLE public.transactions (
	id int4 NOT NULL,
	customer_id int4 NOT NULL,
	product_item_id int4 NULL,
	created_at date NOT NULL,
	online_order bool DEFAULT true NOT NULL,
	order_status_id int4 NOT NULL,
	list_price numeric NOT NULL,
	CONSTRAINT transactions_pk PRIMARY KEY (id),
	CONSTRAINT transactions_customers_fk FOREIGN KEY (customer_id) REFERENCES public.customers(id),
	CONSTRAINT transactions_order_statuses_fk FOREIGN KEY (order_status_id) REFERENCES public.order_statuses(id),
	CONSTRAINT transactions_product_items_fk FOREIGN KEY (product_item_id) REFERENCES public.product_items(id) ON DELETE RESTRICT
);

-- Drop table

-- DROP TABLE public.transactions;

CREATE TABLE public.transactions (
	id int4 NOT NULL,
	customer_id int4 NOT NULL,
	product_item_id int4 NULL,
	created_at date NOT NULL,
	online_order bool DEFAULT true NOT NULL,
	order_status_id int4 NOT NULL,
	list_price numeric NOT NULL,
	CONSTRAINT transactions_pk PRIMARY KEY (id),
	CONSTRAINT transactions_customers_fk FOREIGN KEY (customer_id) REFERENCES public.customers(id),
	CONSTRAINT transactions_order_statuses_fk FOREIGN KEY (order_status_id) REFERENCES public.order_statuses(id),
	CONSTRAINT transactions_product_items_fk FOREIGN KEY (product_item_id) REFERENCES public.product_items(id) ON DELETE RESTRICT
);

-- Drop table

-- DROP TABLE public.transactions;

CREATE TABLE public.transactions (
	id int4 NOT NULL,
	customer_id int4 NOT NULL,
	product_item_id int4 NULL,
	created_at date NOT NULL,
	online_order bool DEFAULT true NOT NULL,
	order_status_id int4 NOT NULL,
	list_price numeric NOT NULL,
	CONSTRAINT transactions_pk PRIMARY KEY (id),
	CONSTRAINT transactions_customers_fk FOREIGN KEY (customer_id) REFERENCES public.customers(id),
	CONSTRAINT transactions_order_statuses_fk FOREIGN KEY (order_status_id) REFERENCES public.order_statuses(id),
	CONSTRAINT transactions_product_items_fk FOREIGN KEY (product_item_id) REFERENCES public.product_items(id) ON DELETE RESTRICT
);

-- Drop table

-- DROP TABLE public.wealth_segments;

CREATE TABLE public.wealth_segments (
	id int4 DEFAULT nextval('genders_seq'::regclass) NOT NULL,
	"name" varchar NULL,
	CONSTRAINT wealth_segments_pk PRIMARY KEY (id)
);
# Загрузка данных из CSV файла
cycle_shop=# \copy tmp_source_data FROM '/tmp/customer_and_transaction.csv' WITH CSV HEADER DELIMITER ',';
COPY 20000
cycle_shop=# select * from tmp_source_data;
cycle_shop=# \q
cycle_shop=# \copy tmp_source_customers FROM '/tmp/customer.csv' WITH CSV HEADER DELIMITER ',';
COPY 4000
cycle_shop=# 

# DML загрузки данных в таблицы и нормализация

## Транзакции
### 1НФ
Таблица соответствует 1НФ. Все атрибуты в таблице быть простые, все сохраняемые данные на пересечении столбцов и строк — содержать лишь скалярные значения.
### 2НФ
Отношения будут соответствовать 2НФ, если сама БД находится в 1НФ, а каждый столбец, который не является ключом, зависит от первичного ключа.
Изначально таблица транзакций не находится в 2НФ. Для приведения к 2НФ выделим таблицы transactions и product_items. В product_items будем писать все возможные конфигурации product_id, brand, product_line, product_class, product_size, standard_cost.
### 3НФ
Приведение к 3НФТаблица должна находиться в 2НФ, плюс любой столбец, который не является ключом, должен зависеть лишь от первичного ключа.
Для приведения к 3НФ выделим справочники: products, brands, product_lines, product_classes, product_sizes, order_statuses.

В таблице products будет присутствовать id=0, что в целом не очень хорошо для ключа. Видимо, это какой-то обобщенный продукт.

При загрузке данных наблюдаем, что результат следующего запроса пуст.

```select * from tmp_source_data where brand is null and standard_cost is not null```

Значит в таблице transactions будем допускать пустое значение ключа product_item_id для таких транзакций.
select 
count(*) as cnt,
count(distinct product_id) as product_ids,
count(distinct customer_id) as customer_ids,
count(distinct order_status) as order_statuses,
count(distinct brand) as brands,
count(distinct product_line) as product_lines,
count(distinct product_class) as product_classes,
count(distinct product_size) as product_sizes,
count(distinct list_price) as list_prices,
count(distinct standard_cost )  as standard_costs
from tmp_source_data;
insert into brands(name) (select distinct brand from tmp_source_data tsd);

insert into products(id) (select distinct product_id::INTEGER from tmp_source_data);

insert into product_lines(name) (select distinct product_line from tmp_source_data where product_line is not null);

insert into product_classes(name) (select distinct product_class from tmp_source_data where product_class is not null);

insert into order_statuses(name) (select distinct order_status from tmp_source_data);

-- Заменим значения на S/M/L так как в product_classes уже используется medium.
insert into product_sizes(name) (select 
distinct case product_size when 'large' then 'L' when 'medium' then 'M' when 'small' then 'S' end
from tmp_source_data where product_size is not null);

-- Заполним конфигурации продуктов
insert into product_items(product_id, brand_id, product_line_id, product_class_id, product_size_id, standard_cost)
(select distinct t.product_id::INTEGER, 
brands.id, 
product_lines.id, 
product_classes.id, 
product_sizes.id, 
replace(standard_cost, ',', '.')::NUMERIC
from tmp_source_data t
left join brands on brands.name = coalesce(t.brand, 'Unknown')
left join product_lines on product_lines.name = t.product_line
left join product_classes on product_classes.name = t.product_class
left join product_sizes on product_sizes.name = case t.product_size when 'large' then 'L'
when 'medium' then 'M'
when 'small' then 'S'
end);

-- Загрузим транзакции. Поле list_price оставляем в этой таблице, так как оно явно не зависит от конфигурации продукта
insert into transactions(id, customer_id, product_item_id, created_at, online_order, order_status_id, list_price)
(select 
t.transaction_id::INTEGER, 
t.customer_id::INTEGER, 
product_items.id, 
to_date(t.transaction_date, 'mm/dd/yyyy'),
case t.online_order when 'True' then TRUE else FALSE end,
order_statuses.id,
replace(t.list_price, ',', '.')::NUMERIC
from tmp_source_data t
left join brands on brands.name = coalesce(t.brand, 'Unknown')
left join product_lines on product_lines.name = t.product_line
left join product_classes on product_classes.name = t.product_class
left join product_sizes on product_sizes.name = case t.product_size when 'large' then 'L'
when 'medium' then 'M'
when 'small' then 'S'
end
left join products on products.id = t.product_id::INTEGER
left join order_statuses on order_statuses.name = t.order_status
left join product_items on product_items.standard_cost = replace(t.standard_cost, ',', '.')::NUMERIC and products.id = product_items.product_id and product_sizes.id = product_size_id and brands.id = brand_id and product_classes.id = product_class_id)
## Покупатели
### 1НФ
Таблица соответствует 1НФ. Все атрибуты в таблице быть простые, все сохраняемые данные на пересечении столбцов и строк — содержать лишь скалярные значения.
### 2НФ
Отношения будут соответствовать 2НФ, если сама БД находится в 1НФ, а каждый столбец, который не является ключом, зависит от первичного ключа.
Таблица покупателей также не находится в 2НФ. Выделим из нее штат, гендер, финансовые сегменты, профессии.
## 3НФ
Приведение к 3НФТаблица должна находиться в 2НФ, плюс любой столбец, который не является ключом, должен зависеть лишь от первичного ключа.
Выделим в отдельный справочник категории профессий и страны. Соеденим таблицы ключами.

select 
count(*) as cnt,
count(distinct gender) as gender,
count(distinct job_title) as job_title,
count(distinct job_industry_category) as job_industry_category,
count(distinct wealth_segment) as wealth_segment,
count(distinct state) as state,
count(distinct country) as country
from tmp_source_customers order by 1;

-- Приведем гендеры к единообразию
update tmp_source_customers set gender = case  when gender in ('Femal', 'F', 'Female') then 'Female'
when gender in ('M', 'Male') then 'Male' else null end;

-- Приведем булевы значения к единообразию
update tmp_source_customers set owns_car = case owns_car when 'No' then 'N' else 'Y' end;

-- Наполнение таблиц
insert into genders(name) (select distinct gender from tmp_source_customers where gender is not null);

insert into countries(name) (select distinct country from tmp_source_customers);

insert into states(name, country_id) (select distinct state, countries.id from tmp_source_customers join countries on countries.name = tmp_source_customers.country);

insert into job_industry_categories(name) (select distinct job_industry_category from tmp_source_customers);

insert into job_titles(name, job_industry_category_id) (select distinct job_title, job_industry_categories.id from tmp_source_customers join job_industry_categories on job_industry_categories.name = tmp_source_customers.job_industry_category);

insert into wealth_segments(name) (select distinct wealth_segment from tmp_source_customers);
insert into customers(id, first_name, last_name, 
gender_id, birthday, job_title_id, wealth_segment_id, 
address, postcode, state_id, deceased_indicator, owns_car, property_valuation)
(select 
tmp_source_customers.customer_id::INTEGER, 
tmp_source_customers.first_name, tmp_source_customers.last_name, 
genders.id, 
to_date(tmp_source_customers.dob, 'yyyy-mm-dd'),
job_titles.id, wealth_segments.id, 
tmp_source_customers.address, tmp_source_customers.postcode, states.id, 
case tmp_source_customers.deceased_indicator when 'Y' then true else false end, 
case tmp_source_customers.owns_car when 'Y' then true else false end,
tmp_source_customers.property_valuation::INTEGER
from tmp_source_customers 
left join genders on genders.name = tmp_source_customers.gender
left join states on states.name = tmp_source_customers.state
left join countries on countries.name = tmp_source_customers.country and states.country_id = countries.id
left join job_industry_categories on job_industry_categories.name = tmp_source_customers.job_industry_category
left join job_titles on job_titles.name = tmp_source_customers.job_title and job_titles.job_industry_category_id = job_industry_categories.id
left join wealth_segments on wealth_segments.name = tmp_source_customers.wealth_segment)
# Добавим связку транзакций и покупателей
Добавим внешний ключ и увидим, что одного кастомера нет в справочнике.

ALTER TABLE public.transactions ADD CONSTRAINT transactions_product_items_fk FOREIGN KEY (product_item_id) REFERENCES product_items(id) ON DELETE RESTRICT;

Добавим запись о нем как о неизвестном, чтобы сохранить транзакцию.
    ERROR: insert or update on table "transactions" violates foreign key constraint "transactions_customers_fk"
  Detail: Key (customer_id)=(5034) is not present in table "customers".

insert into customers(id, first_name) values (5034, 'Undefined');
# Проверка
-- Проверим различия в ключевых данных

with new_table as (select t.id::VARCHAR, 
t.customer_id::VARCHAR, 
coalesce(product_items.product_id,0)::VARCHAR,
product_lines.name,
product_classes.name,
product_sizes.name,
order_statuses.name
from transactions t
left join product_items on product_items.id = t.product_item_id
left join brands on brands.id = product_items.brand_id
left join product_lines on product_lines.id = product_items.product_line_id
left join product_classes on product_classes.id = product_items.product_class_id
left join product_sizes on product_sizes.id = product_items.product_size_id
left join order_statuses on order_statuses.id = t.order_status_id),
old_table as (select transaction_id,customer_id,product_id , product_line, product_class, 
case product_size when 'large' then 'L'
when 'medium' then 'M'
when 'small' then 'S' end,
order_status
from tmp_source_data)
select * from new_table
EXCEPT
select * from old_table
union
select * from old_table
EXCEPT
select * from new_table

-- Теперь таблицу tmp_source_data можно удалить
drop table tmp_source_data;

```python

```
