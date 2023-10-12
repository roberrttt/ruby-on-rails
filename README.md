# ruby-on-rails

To create a dropdown menu in a Ruby on Rails application, I have used HTML and Ruby code within. Here's an example of how I created a simple dropdown menu:

First, I am going to define a variable in my controller to hold the options for the dropdown. For this example, let's say I have a PostsController with a new action:

# app/controllers/posts_controller.rb

class PostsController < ApplicationController
  def new
    @categories = ["Technology", "Travel", "Food", "Sports"]
    # Other new action code here
  end
end

In my view file (e.g., app/views/posts/new.html.erb), I created the dropdown menu using a select tag:

<!-- app/views/posts/new.html.erb -->

<%= form_for @post do |f| %>
  <div class="field">
    <%= f.label :title %>
    <%= f.text_field :title %>
  </div>

  <div class="field">
    <%= f.label :category %>
    <%= f.select :category, @categories, prompt: "Select a category" %>
  </div>

  <div class="actions">
    <%= f.submit %>
  </div>
<% end %>

  In this code, I am using the form_for helper to generate a form for creating a new post. Inside the form, I have created a dropdown menu for the category field using f.select. The @categories variable is passed to the select helper as the collection of options, and prompt sets the default prompt option.

In your controller, you'll need to handle the form submission by creating a create action:

# app/controllers/posts_controller.rb

class PostsController < ApplicationController
  # ...

  def create
    @post = Post.new(post_params)
    if @post.save
      # Handle successful post creation
    else
      render 'new'
    end
  end

  private

  def post_params
    params.require(:post).permit(:title, :category)
  end
end

Make sure you have a Post model defined with title and category attributes.
    
