rails new rails-sample
vim config/database.yml
vim config/route.rb
rake db:create
rake routes


api/v1/products_controller.rbを作る

application_controller.rbはAPIでやる共通処理を書く

includeはconcernから
-> before_actionとかやる

→skip_before_actionは、親クラスのbefor_actionを消す


app/models/product.rb
→activerecord::Baseを継承

db/migrate/0001_hgoehgoe.rb
→ActiveRecord::Migration
→t.timestrmapsはcreate_atとupdated_atを勝手に作ってくれる

rake db:migrate

Productモデルはproductsテーブルと繋がる
→複数形と単数系をいい感じにしてくれる
```
(default)~/workspace/rails-sample(master ✗) rails c
Running via Spring preloader in process 30270
Loading development environment (Rails 4.2.5.1)
irb(main):001:0> 'category'.pluralize
=> "categories"
irb(main):002:0> 'categories’.sigularize
```
```
(default)~/workspace/rails-sample(master ✗) rails c
Running via Spring preloader in process 31132
Loading development environment (Rails 4.2.5.1)
irb(main):001:0> Product.create(name: 'hoge')
   (0.2ms)  BEGIN
  SQL (2.7ms)  INSERT INTO "products" ("name", "created_at", "updated_at") VALUES ($1, $2, $3) RETURNING "id"  [["name", "hoge"], ["created_at", "2016-02-11 06:52:57.700830"], ["updated_at", "2016-02-11 06:52:57.700830"]]
   (0.4ms)  COMMIT
=> #<Product id: 1, name: "hoge", created_at: "2016-02-11 06:52:57", updated_at: "2016-02-11 06:52:57">
irb(main):002:0>
```

```
class Api::V1::ProductsController < ApplicationController
  def index
    render json: {status: :ok, data: Product.all}
  end
end

```

routeで404,500のrender方法を書く


