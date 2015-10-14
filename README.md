# medio

> rustlang bindings to [Medium.com](https://medium.com/) api

# usage

To get started, you'll want grab an integration token from you're medium.com accounts [settings](https://medium.com/me/settings)
page.

```rust
extern crate hyper;
extern crate medio;
use std::default::Default;

fn main() {
    let client = hyper::Client::new();
    let medium = medio::Medium::new(
        &client,
        Some("t0k3n")
    );
    // fetch a reference to authenticated user info
    let me = medium.me().unwrap();
    medium.users(&me.id).post(
        &NewPost {
           title: "hello rust",
           content: &format(
              r#" # hello medium.
                    meet rust.
                    love @{}.
                "#, me.username
           ),
           tags: Some(vec!["rust"]),
           ..Default::default()
        }
    );
}

```

Doug Tangren (softprops) 2015