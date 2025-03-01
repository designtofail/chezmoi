# `onepasswordDocument` *uuid* [*vault-uuid* [*account-name*]]

`onepasswordDocument` returns a document from
[1Password](https://1password.com/) using the [1Password
CLI](https://support.1password.com/command-line-getting-started/) (`op`).
*uuid* is passed to `op get document $UUID` and the output from `op` is
returned. The output from `op` is cached so calling `onepasswordDocument`
multiple times with the same *uuid* will only invoke `op` once. If the optional
*vault-uuid* is supplied, it will be passed along to the `op get` call, which
can significantly improve performance. If the optional *account-name* is
supplied, it will be passed along to the `op get` call, which will help it look
in the right account, in case you have multiple accounts (e.g., personal and
work accounts). If there is no valid session in the environment, by default you
will be interactively prompted to sign in.

!!! example

    ```
    {{- onepasswordDocument "$UUID" -}}
    {{- onepasswordDocument "$UUID" "$VAULT_UUID" -}}
    {{- onepasswordDocument "$UUID" "$VAULT_UUID" "$ACCOUNT_NAME" -}}
    {{- onepasswordDocument "$UUID" "" "$ACCOUNT_NAME" -}}
    ```
