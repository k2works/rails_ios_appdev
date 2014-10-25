RailsとiPhoneではじめるアプリケーション開発
===
# 目的
# 前提
| ソフトウェア     | バージョン    | 備考         |
|:---------------|:-------------|:------------|
| OS X           |10.8.5        |             |
|           　　　|        |             |

+ [AWS Elastic Beanstalk入門](https://github.com/k2works/aws_elasticbeanstalk_introduction)

# 構成
+ [環境セットアップ](#1)
+ [Railsアプリケーション作成１](#2)
+ [Railsアプリケーション作成２](#3)
+ [iOSアプリケーション作成](#4)
+ [アプリケーション実装１](#5)
+ [アプリケーション実装２](#6)
+ [アプリケーション実装３](#7)

# 詳細
## <a name="1">環境セットアップ</a>
### AWS ElasticBeanstalkセットアップ
```bash
$ git init
$ git add . && git commit -m "Setup"
$ eb init
To get your AWS Access Key ID and Secret Access Key,
  visit "https://aws-portal.amazon.com/gp/aws/securityCredentials".
Enter your AWS Access Key ID (current value is "AKIAI*****2VVHQ"):
Enter your AWS Secret Access Key (current value is "YH6xQ*****pKQPG"):
Select an AWS Elastic Beanstalk service region.
Available service regions are:
1) US East (Virginia)
2) US West (Oregon)
3) US West (North California)
4) EU West (Ireland)
5) Asia Pacific (Singapore)
6) Asia Pacific (Tokyo)
7) Asia Pacific (Sydney)
8) South America (Sao Paulo)
Select (1 to 8): 6
Enter an AWS Elastic Beanstalk application name (auto-generated value is "rails_ios_appdev"): travelphoto
Enter an AWS Elastic Beanstalk environment name (auto-generated value is "travelphoto-env"): production
Select an environment tier.
Available environment tiers are:
1) WebServer::Standard::1.0
2) Worker::SQS/HTTP::1.0
Select (1 to 2): 1
Select a solution stack.
Available solution stacks are:
1) 64bit Amazon Linux 2014.09 v1.0.8 running PHP 5.5
2) 64bit Amazon Linux 2014.03 v1.0.7 running PHP 5.5
3) 32bit Amazon Linux 2014.03 v1.0.7 running PHP 5.5
4) 64bit Amazon Linux 2014.09 v1.0.8 running PHP 5.4
5) 64bit Amazon Linux 2014.03 v1.0.7 running PHP 5.4
6) 32bit Amazon Linux 2014.03 v1.0.7 running PHP 5.4
7) 32bit Amazon Linux running PHP 5.3
8) 64bit Amazon Linux running PHP 5.3
9) 64bit Amazon Linux 2014.09 v1.0.8 running Node.js
10) 64bit Amazon Linux 2014.03 v1.0.7 running Node.js
11) 32bit Amazon Linux 2014.03 v1.0.7 running Node.js
12) 64bit Windows Server 2008 R2 running IIS 7.5
13) 64bit Windows Server 2012 running IIS 8
14) 64bit Windows Server 2012 R2 running IIS 8.5
15) 64bit Windows Server Core 2012 R2 running IIS 8.5
16) 64bit Amazon Linux 2014.09 v1.0.8 running Tomcat 7 Java 7
17) 64bit Amazon Linux 2014.09 v1.0.8 running Tomcat 7 Java 6
18) 64bit Amazon Linux 2014.03 v1.0.7 running Tomcat 7 Java 7
19) 32bit Amazon Linux 2014.03 v1.0.7 running Tomcat 7 Java 7
20) 64bit Amazon Linux 2014.03 v1.0.7 running Tomcat 7 Java 6
21) 32bit Amazon Linux 2014.03 v1.0.7 running Tomcat 7 Java 6
22) 32bit Amazon Linux running Tomcat 7
23) 64bit Amazon Linux running Tomcat 7
24) 32bit Amazon Linux running Tomcat 6
25) 64bit Amazon Linux running Tomcat 6
26) 64bit Amazon Linux 2014.03 v1.0.7 running Python 2.7
27) 32bit Amazon Linux 2014.03 v1.0.7 running Python 2.7
28) 64bit Amazon Linux 2014.03 v1.0.7 running Python
29) 32bit Amazon Linux 2014.03 v1.0.7 running Python
30) 32bit Amazon Linux running Python
31) 64bit Amazon Linux running Python
32) 64bit Amazon Linux 2014.03 v1.0.7 running Ruby 2.1 (Puma)
33) 64bit Amazon Linux 2014.03 v1.0.7 running Ruby 2.1 (Passenger Standalone)
34) 64bit Amazon Linux 2014.03 v1.0.7 running Ruby 2.0 (Puma)
35) 64bit Amazon Linux 2014.03 v1.0.7 running Ruby 2.0 (Passenger Standalone)
36) 64bit Amazon Linux 2014.03 v1.0.7 running Ruby 1.9.3
37) 32bit Amazon Linux 2014.03 v1.0.7 running Ruby 1.9.3
38) 64bit Amazon Linux 2014.09 v1.0.8 running Docker 1.2.0
39) 64bit Amazon Linux 2014.03 v1.0.7 running Docker 1.0.0
Select (1 to 39): 32
Select an environment type.
Available environment types are:
1) LoadBalanced
2) SingleInstance
Select (1 to 2): 2
Create an RDS DB Instance? [y/n]: y
Create an RDS BD Instance from (current value is "[No snapshot]"):
1) [No snapshot]
2) awseb-e-vzbkgpnmei-stack-snapshot-awsebrdsdatabase-r4ao2mhl20ij
3) vps-final-snapshot
4) [Other snapshot]
Select (1 to 4): 1
Enter an RDS DB master password:
Retype password to confirm:
If you terminate your environment, your RDS DB Instance will be deleted and you will lose your data.
Create snapshot? [y/n]: n
Attach an instance profile (current value is "[Create a default instance profile]"):
1) [Create a default instance profile]
2) aws-elasticbeanstalk-ec2-role
3) [Other instance profile]
Select (1 to 3): 1
Updated AWS Credential file at "/Users/k2works/.elasticbeanstalk/aws_credential_file".
$ eb start
The current branch "wip" is not associated with an Elastic Beanstalk environment. Call "eb branch" to set up a new environment for this branch.
Proceeding with default settings.
Starting application "travelphoto".
Would you like to deploy the latest Git commit to your environment? [y/n]: n
Waiting for environment "production" to launch.
2014-10-13 22:26:52	INFO	createEnvironment is starting.
2014-10-13 22:26:57	INFO	Using elasticbeanstalk-ap-northeast-1-262470114399 as Amazon S3 storage bucket for environment data.
2014-10-13 22:27:25	INFO	Created EIP: 54.248.73.119
2014-10-13 22:27:26	INFO	Created security group named: awseb-e-2826yjwn63-stack-AWSEBSecurityGroup-1GANUPH3WB1G3
2014-10-13 22:27:36	INFO	Creating RDS database named: aae1fp3qmgm3p8. This may take a few minutes.
2014-10-13 22:34:56	INFO	Created RDS database named: aae1fp3qmgm3p8
2014-10-13 22:36:20	INFO	Waiting for EC2 instances to launch. This may take a few minutes.
2014-10-13 22:39:42	INFO	Application available at production-xq3iyx4hip.elasticbeanstalk.com.
2014-10-13 22:39:42	INFO	Successfully launched environment: production
Application is available at "production-xq3iyx4hip.elasticbeanstalk.com".
```
## <a name="2">Railsアプリケーション作成１</a>
### Railsアプリセットアップ
```bash
$ rvm --create --versions-conf use 2.1.1@travelphoto
$ gem install rails --no-rdoc --no-ri
$ rails new .
```
### シークレットキーを環境変数に追加
```bash
$ rake secret
112767213828f8a99d48601b9e007ee816aeceb475b7d7d97d7dd6ee618aa69b9f83b781ef3050dc3a0617f80b6d330469fec432341fb60cd9a6b9dd20630267
```
_.elasticbeanstalk/optionsettings.production_
```
・・・
[aws:elasticbeanstalk:application:environment]
BUNDLE_WITHOUT=test:development
PARAM1=
PARAM2=
PARAM3=
PARAM4=
PARAM5=
RACK_ENV=production
RAILS_SKIP_ASSET_COMPILATION=false
RAILS_SKIP_MIGRATIONS=false
SECRET_KEY_BASE=112767213828f8a99d48601b9e007ee816aeceb475b7d7d97d7dd6ee618aa69b9f83b781ef3050dc3a0617f80b6d330469fec432341fb60cd9a6b9dd20630267
・・・
```
### データベースの設定
_config/database.yml_
```
・・・
production:
  adapter: mysql2
  encoding: utf8
  database: <%= ENV['RDS_DB_NAME'] %>
  username: <%= ENV['RDS_USERNAME'] %>
  password: <%= ENV['RDS_PASSWORD'] %>
  host: <%= ENV['RDS_HOSTNAME'] %>
  port: <%= ENV['RDS_PORT'] %>
・・・
```
#### タイムゾーンの設定
_config/application.rb_
```
config.time_zone = 'Tokyo'
```

### プラグインの設定
#### hamlの設定
```bash
$ rake haml:replace_erbs
```
#### deviseの設定
```bash
$ rails g devise:install
```
_config/environments/development.rb_  
_config/environments/test.rb_
の末尾に以下を追加

```ruby
config.action_mailer.default_url_options = { host: 'localhost', port: 3000 }
```

_app/views/layouts/application.html.haml_

```
%body
  %p.notice
    = notice
  %p.alert
    = alert
  = yield
```
#### rails_adminの設定

```bash
$ rails g rails_admin:install
           ?  Where do you want to mount rails_admin? Press <enter> for [admin] > rails_admin
       route  mount RailsAdmin::Engine => '/rails_admin', as: 'rails_admin'
   identical  config/initializers/rails_admin.rb
```

#### RSpecのインストール
```bash
$ rails g rspec:install
```

### モデルの作成

#### Userモデルの作成
```bash
$ rails g devise User
```

_app/models/user.rb_

```ruby
class User < ActiveRecord::Base
  # Include default devise modules. Others available are:
  # :confirmable, :lockable, :timeoutable and :omniauthable
  devise :database_authenticatable, :registerable,
         :recoverable, :rememberable, :trackable, :validatable,
         :token_authenticatable, :confirmable
end
```

_db/migrate/20141013154437_devise_create_users.rb_

```ruby
class DeviseCreateUsers < ActiveRecord::Migration
  def change
    create_table(:users) do |t|
・・・
      ## Confirmable
      t.string   :confirmation_token
      t.datetime :confirmed_at
      t.datetime :confirmation_sent_at
      t.string   :unconfirmed_email # Only if using reconfirmable
・・・
    add_index :users, :confirmation_token,   unique: true
・・・
  end
end
```

_config/initializers/devise.rb_
```ruby
Devise::TokenAuthenticatable.setup do |config|
  config.token_authentication_key = :other_key_name
end
```

#### Travelモデルの作成
```bash
$ rails g model Travel title:text startdate:date enddate:date user:references
```

#### Albumモデルの作成
```bash
$ rails g model Album title:text travel:references
```

#### Photモデルの作成
```bash
$ rails g model Photo title:string comment:text user:references album:references
$ rails g paperclip Photo image
$ rake db:migrate
```

_app/models/photo.rb_

```bash
class Photo < ActiveRecord::Base
  belongs_to :user
  belongs_to :album
  has_attached_file :image, :style => { :thumb => ["64x64",:png] }
end
```

_app/models/user.rb_
```
class User < ActiveRecord::Base
・・・
  has_many :photos
end
```

_app/models/album.rb_
```bash
class Album < ActiveRecord::Base
  belongs_to :travel
  has_many :photos
end
```

#### Travelモデルの修正
```bash
$ rails g migration AddPhotoIdToTravel photo_id:integer
```

_db/migrate/20141013161228_add_photo_id_to_travel.rb_

```ruby
class AddPhotoIdToTravel < ActiveRecord::Migration
  def change
    add_column :travels, :photo_id, :integer
    add_index :travels, :photo_id
  end
end
```

_app/models/photo.rb_

```ruby
class Photo < ActiveRecord::Base
  belongs_to :user
  belongs_to :album
  has_one :travel
  has_attached_file :image, :style => { :thumb => ["64x64",:png] }
end
```

_app/models/photo.rb_

```ruby
class Travel < ActiveRecord::Base
  has_many :albums

  belongs_to :user
  belongs_to :cover_photo, :class_name => "Photo", :foreign_key => "photo_id"
end
```

#### Friendモデルの作成

```bash
$ rails g model Friend user:references following:references
$ rake db:migrate
```

_app/models/friend.rb_
```bash
class Friend < ActiveRecord::Base
  belongs_to :user
  belongs_to :following, :class_name => "User"
end
```

_app/models/user.rb_

```ruby
class User < ActiveRecord::Base
・・・
  has_many :photos
  has_many :friends
  has_many :followings, :through => :friends
end
```

#### usernameの追加
```bash
$ rails g migration AddUsernameToUser username:string
```

_db/migrate/20141013163119_add_username_to_user.rb_

```ruby
class AddUsernameToUser < ActiveRecord::Migration
  def change
    add_column :users, :username, :string
    add_index :users, :username
  end
end
```

_app/models/user.rb_

```ruby
class User < ActiveRecord::Base
・・・

  validates_uniqueness_of :username
end
```
```bash
$ rake db:migrate
```
### 本番環境更新

```
$ git add . && git commit -m "Setup Rails"
$ eb update
$ git aws.push
```

## <a name="3">Railsアプリケーション作成２</a>
### Controllerの作成
_config/routes.rb_

```ruby
resources :photos
resources :photo
```

#### TopController
```bash
rails g controller Top index
```
_config/routes.rb_
```ruby
root :to => "top#index"
```
#### TravelController
_config/routes.rb_
```ruby
resources :travel
```

```bash
$ rails g controller Travel index create new edit show update destroy
```

#### TravelControllerのアクション

### ツールの導入
#### Factory GirlとDatabase Cleanerのインストール
_Gemfile_
```ruby
gem 'factory_girl_rails'
gem 'database_cleaner'
```

#### Database Cleanerの設定
_spec/spec_helper.rb_
```ruby
  config.before(:suite) do
    DatabaseCleaner.strategy = :transaction
    DatabaseCleaner.clean_with(:truncation)
  end

  config.around(:each) do |example|
    DatabaseCleaner.cleaning do
      example.run
    end
  end
```

#### Factory Girlでのモデル作成

```bash
$ rails g factory_girl:model User email password username
```

_spec/factories/users.rb_
```ruby
FactoryGirl.define do
  factory :user do
    sequence(:email){|n| "test#{n}@example.com"}
    password "password"
    sequence(:username){|n| "test#{n}"}
  end
end
```

```bash
$ rails g factory_girl:model Travel title startdate:date enddate:date user_id:integer
```

_spec/factories/travels.rb_
```ruby
FactoryGirl.define do
  factory :travel do
    sequence(:title){|n| "travel#{n}"}
    startdate Date.today - 3.days
    enddate Date.today
    user_id { User.all.to_a.map(&:id).sample }
  end
end
```

```bash
$ rails g factory_girl:model Album title:string
```

_spec/factories/albums.rb_

```ruby
FactoryGirl.define do
  factory :album do
    sequence(:title){|n| "album#{n}"}
    travel_id { Travel.all.to_a.map(&:id).sample }
  end
end
```

```bash
$ rails g factory_girl:model Photo user_id:integer album_id:integer comment:string
```

_spec/factories/photos.rb_

```ruby
FactoryGirl.define do
  factory :photo do
    album_id { Album.all.to_a.map(&:id).sample }
    user_id { Album.find(album_id).travel.user.id }
    image { File.open("app/assets/images/rails.png") }
    sequence(:comment){|n| "comment#{n}"}
  end
end
```

### Controllerの調整
_spec/controllers/travel_controller_spec.rb_
```ruby
config.include Devise::TestHelpers, :type => :controller
```

#### POSTを伴わないテストのspecファイル作成
WIP:[Rspecでsign_out系のテストがうまく動かない](https://github.com/k2works/rails_ios_appdev/issues/2)

_spec/controllers/travel_controller_spec.rb_
```ruby
require 'rails_helper'

RSpec.describe TravelController, :type => :controller do


  before(:all) do
    @user = FactoryGirl.create(:user)
    @user.confirm!
    @different_user = FactoryGirl.create(:user)
    @different_user.confirm!
    FactoryGirl.create(:travel, :user => @user)
    10.times{FactoryGirl.create(:travel)}
  end

  describe "#index" do
    it "show all data when user don't logged in" do
      travels = Travel.all
      get :index
      expect(assigns(:travels)).to match_array travels
    end
    it "show all data when user logged in" do
      sign_in :user, @user
      travels = Travel.all
      get :index
      expect(assigns(:travels)).to match_array travels
    end
    it "show user data when requested with user_id" do
      travels = Travel.where(user_id: @user.id)
      get :index,{:user_id => @user.id}
      expect(assigns(:travels)).to match_array travels
    end
  end

  describe "#show" do
    it "assigns the requested travel as @travel" do
      travel = Travel.first
      get :show, {:id => travel.id}
      expect(assigns(:travel)).to eq travel
    end
  end

  describe "#new" do
    it "access to new, does not work without a signed in user" do
      sign_out :user
      get :new
      response.should redirect_to(new_user_session_path)
    end
    it "assigns as new travel as @travel when sign in" do
      sign_in :user, @user
      get :new
      expect(assigns(:travel)).to be_a_new(Travel)
    end
  end

  describe "#edit" do
    it "access to edit, does not work without a signed in user" do
      sign_out :user
      travel = @user.travels.first
      get :edit,{ :id => travel.id }
      response.should redirect_to(new_user_session_path)
    end

    it "assign as edit travel as @travel when sign in" do
      sign_in :user, @different_user
      travel = @user.travels.first
      get :edit ,{:id => travel.id}
      response.should redirect_to(travel)
    end
  end
end
```
#### POSTを伴うテストのspecファイル作成

```ruby
require 'rails_helper'

RSpec.describe TravelController, :type => :controller do

・・・

  before(:each) do
    @travel_params = {title: "タイトル",startdate: "2013-01-01",enddate: "2013-12-31"}
  end

  describe "#POST create" do
    describe "without login" do
      it "should be redirect to login page" do
        sign_out :user
        post :create
        response.should redirect_to(new_user_session_path)
      end
    end
    describe "with login" do
      it " create new Travel" do
        sign_in :user,@user
        expect {
          post :create,:travel_params => @travel_params
        }.to change(Travel, :count).by(1)
      end

      it "create new travel s @travel" do
        sign_in :user,@user
        post :create, :travel_params => @travel_params
        expect(assigns(:travel)).to be_a(Travel)
      end

      it "dosen't create new travel with invaild params" do
        sign_in :user,@user
        Travel.any_instance.stub(:save).and_return(false)
        post :create, :travel_params => @travel_params
        expect(assigns(:travel)).to be_a_new(Travel)
      end

      it "doesn't create new travel with invaild params" do
        sign_in :user,@user
        Travel.any_instance.stub(:save).and_return(false)
        post :create,:travel_params => @travel_params
        expect(response).to render_template("new")
      end
    end

    describe "#POST update" do
      describe "without login" do
        it "should be redirect to login page" do
          sign_out :user
          travel = @user.travels.first
          post :update,{id: travel.id}
          response.should redirect_to(new_user_session_path)

        end
      end

      describe "another user" do
        it "should be redirect to another page" do
          sign_in :user,@different_user
          travel = @user.travels.first
          post :update,{id: travel.id, travel_params: @travel_params}
          response.should redirect_to(travel)
        end
      end

      describe "with vaild params" do
        it "asigns the requested travel as @travel" do
          sign_in :user,@user
          travel = @user.travels.first
          post :update, {id: travel.id, travel_params: @travel_params}
          assigns(:travel).should eq(travel)
        end

        it "redirects to the travel" do
          sign_in :user,@user
          travel = @user.travels.first
          put :update, {id: travel.id,travel_params: @travel_params}
          response.should redirect_to(travel)
        end
      end

      describe "with invalid params" do
        it "assings the travel as @travel" do
          sign_in :user,@user
          travel = @user.travels.first
          Travel.any_instance.stub(:save).and_return(false)
          put :update, {id: travel.id,travel_params: @travel_params}
          expect(assigns(:travel)).to eq travel

        end

        it "re-renders the 'edit' template" do
          sign_in :user,@user
          travel = @user.travels.first
          Travel.any_instance.stub(:save).and_return(false)
          put :update, {id: travel.id,travel_params: @travel_params}
          expect(response).to render_template("edit")
        end
      end
    end

    describe "DELETE destroy" do
      describe "without login" do
        it "should be redirect to login page" do
          sign_out :user
          travel = @user.travels.first
          delete :update,{id: travel.id}
          response.should redirect_to(new_user_session_path)
        end
      end

      describe "another user" do
        it "should be redirect to another page" do

          sign_in :user, @different_user
          travel = @user.travels.first
          delete :update,  {id: travel.id,travel_params: @travel_params}
          response.should redirect_to(travel)

        end
      end

      it "destroys the requested Travel" do
        sign_in :user,@user
        travel = @user.travels.first
        expect {
          delete :destroy, {id: travel.id}
        }.to change(Travel, :count).by(-1)
      end

      it "redirects to the travels list" do
        sign_in :user,@user
        travel = FactoryGirl.create(:travel)
        delete :destroy, {id: travel.id}
        response.should redirect_to(travel_url)
      end
    end
  end

  before(:each) do
    @travel = @user.travels.first
    @album = FactoryGirl.create(:album, travel: @travel)
    @photo = FactoryGirl.create(:photo,album: @album,user: @user)
    @travel.cover_photo = @photo
    @travel.save
  end

  describe "GET cover_photo" do
    it "should be return cover_photo" do
      travel = @user.travels.first
      get :cover_photo, {id: travel.id}
      expect(assigns(:photo)).to eq @photo
    end
  end

  describe "POST cover_photo" do
    it "access to cover_photo does not work without a signed in user" do
      sign_out :user
      post :cover_photo, {id: @travel.id, photo_id: @photo.id}
      response.should redirect_to(new_user_session_path)
    end

    it "access to edit, does not work sign in as another user" do
      sign_in :user, @different_user
      post :cover_photo,{id: @travel.id, photo_id: @photo.id}
      response.should redirect_to(@travel)
    end

    it "should be set cover_photo" do
      sign_in :user,@user
      @travel.cover_photo = nil
      @travel.save
      post :cover_photo, {id: @travel.id, photo_id: @photo.id}
      expect(Travel.find(@travel.id).cover_photo.id).to eq @photo.id
    end
  end
end
```


### Controllerの作成２
#### AlbumController
_config/routes.rb_

```ruby
resources :album
```

```bash
$ rails g controller Album index create new edit show update destroy
```

#### PhotoController
_config/routes.rb_

```ruby
resources :photo, only: [:index,:show,:new,:create,:destroy]
```

```bash
$ rails g controller Phot index create new show destroy
```
### devise viewのカスタマイズ
_config/initializers/devise.rb_

```ruby
config/initializers/devise.rb
```

```bash
$ rails g devise:views users
$ rake haml:replace_erbs
```

_app/views/users/registrations/new.html.haml_

```haml
%h2 Sign up
= form_for(resource, as: resource_name, url: registration_path(resource_name)) do |f|
  = devise_error_messages!
  %div
    = f.label :email
    %br/
    = f.email_field :email, autofocus: true
  %div
    = f.label :password
    %br/
    = f.password_field :password, autocomplete: "off"
  %div
    = f.label :password_confirmation
    %br/
    = f.password_field :password_confirmation, autocomplete: "off"
  %div
    = f.label :username
    %br/
    = f.text_field :username

  %div= f.submit "Sign up"
= render "users/shared/links"
```

_app/views/users/registrations/edit.html.haml_

```haml
%h2
  Edit #{resource_name.to_s.humanize}
= form_for(resource, as: resource_name, url: registration_path(resource_name), html: { method: :put }) do |f|
  = devise_error_messages!
  %div
    = f.label :email
    %br/
    = f.email_field :email, autofocus: true
  - if devise_mapping.confirmable? && resource.pending_reconfirmation?
    %div
      Currently waiting confirmation for: #{resource.unconfirmed_email}
  %div
    = f.label :password
    %i (leave blank if you don't want to change it)
    %br/
    = f.password_field :password, autocomplete: "off"
  %div
    = f.label :password_confirmation
    %br/
    = f.password_field :password_confirmation, autocomplete: "off"
  %div
    = f.label :current_password
    %i (we need your current password to confirm your changes)
    %br/
    = f.password_field :current_password, autocomplete: "off"
  %div
    = f.label :username
    %br/
    = f.text_field :username

  %div= f.submit "Update"
%h3 Cancel my account
%p
  Unhappy? #{button_to "Cancel my account", registration_path(resource_name), data: { confirm: "Are you sure?" }, method: :delete}
= link_to "Back", :back
```

#### AlbumController
```bash
$ rails g controller Album index create new edit show update destroy
```

### devise viewのカスタマイズ
_config/initializers/devise.rb_

```ruby
config.scoped_views = true
```

```bash
$ rails g devise:views users
$ rake haml:replace_erbs
```

_app/views/users/registrations/new.html.haml_
```
%h2 Sign up
= form_for(resource, as: resource_name, url: registration_path(resource_name)) do |f|
  = devise_error_messages!
  %div
    = f.label :email
    %br/
    = f.email_field :email, autofocus: true
  %div
    = f.label :password
    %br/
    = f.password_field :password, autocomplete: "off"
  %div
    = f.label :password_confirmation
    %br/
    = f.password_field :password_confirmation, autocomplete: "off"
  %div
    = f.label :username
    %br/
    = f.text_field :username

  %div= f.submit "Sign up"
= render "users/shared/links"
```

_app/views/users/registrations/edit.html.haml_

```
%h2
  Edit #{resource_name.to_s.humanize}
= form_for(resource, as: resource_name, url: registration_path(resource_name), html: { method: :put }) do |f|
  = devise_error_messages!
  %div
    = f.label :email
    %br/
    = f.email_field :email, autofocus: true
  - if devise_mapping.confirmable? && resource.pending_reconfirmation?
    %div
      Currently waiting confirmation for: #{resource.unconfirmed_email}
  %div
    = f.label :password
    %i (leave blank if you don't want to change it)
    %br/
    = f.password_field :password, autocomplete: "off"
  %div
    = f.label :password_confirmation
    %br/
    = f.password_field :password_confirmation, autocomplete: "off"
  %div
    = f.label :current_password
    %i (we need your current password to confirm your changes)
    %br/
    = f.password_field :current_password, autocomplete: "off"
  %div
    = f.label :username
    %br/
    = f.text_field :username

  %div= f.submit "Update"
%h3 Cancel my account
%p
  Unhappy? #{button_to "Cancel my account", registration_path(resource_name), data: { confirm: "Are you sure?" }, method: :delete}
= link_to "Back", :back
```

## <a name="4">iOSアプリケーション作成</a>
### Xcodeでプロジェクトを新規作成する

### ストーリーボードなしのEmpty Applicationを作成する
1. XCode6でSingle View Applicationを作る
1. Main.stroyboardとLanchScreen.xibを削除する
1. Info.plistファイル内エントリーの"Main storyboard file base name"と "Launch screen interface file base name"を削除する。
1. AppDelegate.mファイルを開いて以下の用に編集する

```
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
{
    self.window = [[UIWindow alloc] initWithFrame:[[UIScreen mainScreen] bounds]];
    // Override point for customization after application launch.
    self.window.backgroundColor = [UIColor whiteColor];
    [self.window makeKeyAndVisible];
    return YES;
}
```

### pod installを実行する
_ios_app/travelphoto/Podfile_

```
platform :ios, '6.0'

pod 'DCIntrospect'
pod 'GHUnitIOS'
pod 'BlocksKit'
pod 'Underscore.m'
pod 'AQGridView'
pod 'QuickDialog'
pod 'JASidePanels'
pod 'OCCalendar'
pod 'SDWebImage'
pod 'SVProgressHUD'
pod 'Reachability'
pod 'AFNetworking'
pod 'MagicalRecord'
pod 'NoticeView'
pod 'ELCImagePickerController'
```

```bash
$ cd ios_app/travelphoto
$ pod install
```

### QuartzCore frameworkの追加
![001](https://farm4.staticflickr.com/3950/15338971647_b127852ca6.jpg)
### travelphoto-Prefix.pchの追加
_HelloWorld/HelloWorld/HelloWorld-Prefix.pch_
_ios_app/travelphoto/travelphoto/travelphoto-Prefix.pch_
```
#import <UIKit/UIKit.h>
#import <Foundation/Foundation.h>
#import "DCIntrospect.h"
```
### AppDelegate.mの修正
_HelloWorld/HelloWorld/AppDelegate.m_
_ios_app/travelphoto/travelphoto/AppDelegate.m_

```
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    self.window = [[UIWindow alloc] initWithFrame:[[UIScreen mainScreen] bounds]];
    _topViewController = [[TopViewController alloc]init];
    self.window.rootViewController = _topViewController;
    [self.window makeKeyAndVisible];
#if TARGET_IPHONE_SIMULATOR
    [[DCIntrospect sharedIntrospector]start];
#endif
    return YES;
}
```

## <a name="5">アプリケーション実装１</a>
## <a name="6">アプリケーション実装２</a>
## <a name="7">アプリケーション実装３</a>

# 参照
* [RailsとiPhoneではじめるアプリケーション開発](http://www.amazon.co.jp/Rails%E3%81%A8iPhone%E3%81%A7%E3%81%AF%E3%81%98%E3%82%81%E3%82%8B%E3%82%A2%E3%83%97%E3%83%AA%E3%82%B1%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3%E9%96%8B%E7%99%BA-%E6%A0%97%E7%94%B0-%E7%94%B1%E8%8F%9C/dp/4844334476)
