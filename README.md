# Flask Debug Project(Individual)

The purpose of this project is meant to test students debugging skills with Flask

There are roughly 15-20 bugs produced inside of this project. All of the bugs have been encountered before. There are some bugs that are similar but have now taken a different "type" of bug.

Once a working app is produced, commit the project to a personal seperate github repository.

Debug list
1. templates folder location: Move the templates folder under debug_project_app folder
2. models.py
2-1. Need to intend the set_password function
3. routes.py
3-1. import db (from debug_project_app.models import db, User, Post, check_password_hash)
3-2. post = Post.query.all() (in home() function)
3-3. post = PostForm() (in post() function)
3-4. request.method == 'POST' (in post() function)
3-4. email = form.email.data (in register() function)
3-5. user_id = current_user.id (in post() function)
3-6. in post_detail function, we need to query to get the post owner's name
    ownername = User.query.get(post.user_id).username
    return render_template('post_detail.html', post = post, postowner=ownername)
4. post_detail.html
4-1. url_for('home')
4-2. This post belongs to: {{ postowner }}
4-3. Title: {{ post.title }}
4-4. {{ post.content }}
4-5. Date Created: {{ post.date_created }}
4-6. If the current user is not the owner of the post, we need to prevent the current user update or delete the post. So, {%if post.user_id == current_user.id %} update button, delete button {% endif %}