*   `nil.to_query("key")` now returns `key`.

    Previously it would return `key=`, preventing round tripping with `Rack::Utils.parse_nested_query`.

    *Erol Fornoles*

*   Avoid wrapping redis in a `ConnectionPool` when using `ActiveSupport::Cache::RedisCacheStore` if the `:redis`
    option is already a `ConnectionPool`.

    *Joshua Young*

*   Alter `ERB::Util.tokenize` to return :PLAIN token with full input string when string doesn't contain ERB tags.

    *Martin Emde*

*   Fix a bug in `ERB::Util.tokenize` that causes incorrect tokenization when ERB tags are preceeded by multibyte characters.

    *Martin Emde*

*   Add `ActiveSupport::Testing::NotificationAssertions` module to help with testing `ActiveSupport::Notifications`.

    *Nicholas La Roux*, *Yishu See*, *Sean Doyle*

*   `ActiveSupport::CurrentAttributes#attributes` now will return a new hash object on each call.

    Previously, the same hash object was returned each time that method was called.

    *fatkodima*

*   `ActiveSupport::JSON.encode` supports CIDR notation.

    Previously:

    ```ruby
    ActiveSupport::JSON.encode(IPAddr.new("172.16.0.0/24")) # => "\"172.16.0.0\""
    ```

    After this change:

    ```ruby
    ActiveSupport::JSON.encode(IPAddr.new("172.16.0.0/24")) # => "\"172.16.0.0/24\""
    ```

    *Taketo Takashima*

*   Make `ActiveSupport::FileUpdateChecker` faster when checking many file-extensions.

    *Jonathan del Strother*

*   `Post.set_callback(:update, :before, :do_something, if: proc(&:run_callback?))` now doesn't raise an error.

    Previously it would raise an error because the `if` condition was a symbolProc.

    *Radamés Roriz*

Please check [8-0-stable](https://github.com/rails/rails/blob/8-0-stable/activesupport/CHANGELOG.md) for previous changes.
