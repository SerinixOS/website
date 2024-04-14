---
title: Testing the Blogging System
author: Adrian Vovk
modified_date: 2021-04-25
---

This blog post is just here to make sure that the blog is working correctly. It's
also a test for all of the markdown elements we'd want in a blog post to make sure
that they get themed correctly. There's nothing to read here, but it's pretty
awesome that Jekyll can turn markdown documents like this into full articles! 

## Here's a heading

That was a heading. Really cool, right? Anyway, here's so more markdown content for ya:

Here's an unordered list:
- First element
- Second element
- Third element

Here's an ordered list:
1. First element
2. Second element
3. Third element

Here's some code:
```vala
int main(string[] args) {
    Gtk.init(ref args);
    
    var window = new Gtk.Window("Title");    
    var label = new Gtk.Label("Hello World!");
    window.add(label);
    window.show_all();
    
    Gtk.main();
    return 0;
}
```

Here's some checkboxes:
- [ ] Asdf
- [x] Asdf

Here's a [link](https://gitlab.com/carbonOS) to the git repo of carbonOS!

Here's some *italics*, **bold**, and ~~strikethrough~~

Here are some keyboard instructions: <kbd title="The windows key">Super</kbd> + <kbd>E</kbd>

---

# Header 1
## Header 2
### Header 3
#### Header 4
##### Header 5
###### Header 6
