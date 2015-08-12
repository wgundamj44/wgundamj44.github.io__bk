---
layout: post
title: Some project notes
category: [tech]
tags: [docker django javascript]
---
I've been doing my current project for two months, and I feel it is time for some notes.

## Develop enviroment with Docker
I used docker-compose to build my develop enviroment. The project consists of MySQL, django and celery(RabbitMQ). So my docker-compose.yml will be something like:

## The project structure of Django

## The ORM of Django

## Try out react in frontend
The original front end is django template + jQuery + bootstrap. Without any framework to manage the code structure, there were nearly no reusable UI components. We had to implement every page from scratch. More importantly, without certain patterns, the implementations of front end logic differed greatly from one another even for similar logics.

The project is a business management site, the pages are mainly the CRUD of different business objects, eg. a list for all the objects, a modal dialog for detail of an object, a modal for update or create object, a modal for delete confirm. It's clear that UI elements can be reused somehow. For example, the boostrap modal:
{% highlight html %}
<div class="modal fade">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <button type="button" class="close" data-dismiss="modal" aria-label="Close"><span aria-hidden="true">&times;</span></button>
        <h4 class="modal-title">Modal title</h4>
      </div>
      <div class="modal-body">
        <p>One fine body&hellip;</p>
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-default" data-dismiss="modal">Close</button>
        <button type="button" class="btn btn-primary">Save changes</button>
      </div>
    </div><!-- /.modal-content -->
  </div><!-- /.modal-dialog -->
</div><!-- /.modal -->
{% endhighlight %}
This structure is common among all objects, the difference is the title, the content and footer. The old way will be copy this structure, then write the contents in title, content and footer. Consider after copied this structure for near a hundred times, then one day we need to add a new css class in every modal... What a desperate work.. How about we write only one copy of this structure and generate the contents dynamicaly. With react, this is a very trival work.

Another problem is that, the UI elements will effect each other. eg. When radio button A is checked, the textinput B should show, so we listen for A's change event, and change B accordingly. When UI grows complexly, element by C, D... will also effect B, 