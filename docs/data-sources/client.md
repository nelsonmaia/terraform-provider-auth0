---
page_title: "Data Source: auth0_client"
description: |-
  Data source to retrieve a specific Auth0 application client by client_id or name.
---

# Data Source: auth0_client

Data source to retrieve a specific Auth0 application client by `client_id` or `name`.

## Example Usage

```terraform
# An Auth0 Client loaded using its name.
data "auth0_client" "some-client-by-name" {
  name = "Name of my Application"
}

# An Auth0 Client loaded using its ID.
data "auth0_client" "some-client-by-id" {
  client_id = "abcdefghkijklmnopqrstuvwxyz0123456789"
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Optional

- `client_id` (String) The ID of the client. If not provided, `name` must be set.
- `name` (String) The name of the client. If not provided, `client_id` must be set.

### Read-Only

- `addons` (List of Object) Addons enabled for this client and their associated configurations. (see [below for nested schema](#nestedatt--addons))
- `allowed_clients` (List of String) List of applications ID's that will be allowed to make delegation request. By default, all applications will be allowed.
- `allowed_logout_urls` (List of String) URLs that Auth0 may redirect to after logout.
- `allowed_origins` (List of String) URLs that represent valid origins for cross-origin resource sharing. By default, all your callback URLs will be allowed.
- `app_type` (String) Type of application the client represents. Possible values are: `native`, `spa`, `regular_web`, `non_interactive`, `sso_integration`. Specific SSO integrations types accepted as well are: `rms`, `box`, `cloudbees`, `concur`, `dropbox`, `mscrm`, `echosign`, `egnyte`, `newrelic`, `office365`, `salesforce`, `sentry`, `sharepoint`, `slack`, `springcm`, `zendesk`, `zoom`.
- `callbacks` (List of String) URLs that Auth0 may call back to after a user authenticates for the client. Make sure to specify the protocol (https://) otherwise the callback may fail in some cases. With the exception of custom URI schemes for native clients, all callbacks should use protocol https://.
- `client_aliases` (List of String) List of audiences/realms for SAML protocol. Used by the wsfed addon.
- `client_authentication_methods` (Set of Object) Defines client authentication methods. (see [below for nested schema](#nestedatt--client_authentication_methods))
- `client_metadata` (Map of String) Metadata associated with the client, in the form of an object with string values (max 255 chars). Maximum of 10 metadata properties allowed. Field names (max 255 chars) are alphanumeric and may only include the following special characters: `:,-+=_*?"/\()<>@ [Tab] [Space]`.
- `client_secret` (String, Sensitive) Secret for the client. Keep this private. To access this attribute you need to add the `read:client_keys` scope to the Terraform client. Otherwise, the attribute will contain an empty string.
- `compliance_level` (String) Defines the compliance level for this client, which may restrict it's capabilities. Can be one of `none`, `fapi1_adv_pkj_par`, `fapi1_adv_mtls_par`.
- `cross_origin_auth` (Boolean) Whether this client can be used to make cross-origin authentication requests (`true`) or it is not allowed to make such requests (`false`).
- `cross_origin_loc` (String) URL of the location in your site where the cross-origin verification takes place for the cross-origin auth flow when performing authentication in your own domain instead of Auth0 Universal Login page.
- `custom_login_page` (String) The content (HTML, CSS, JS) of the custom login page.
- `custom_login_page_on` (Boolean) Indicates whether a custom login page is to be used.
- `default_organization` (List of Object) Configure and associate an organization with the Client (see [below for nested schema](#nestedatt--default_organization))
- `description` (String) Description of the purpose of the client.
- `encryption_key` (Map of String) Encryption used for WS-Fed responses with this client.
- `form_template` (String) HTML form template to be used for WS-Federation.
- `grant_types` (List of String) Types of grants that this client is authorized to use.
- `id` (String) The ID of this resource.
- `initiate_login_uri` (String) Initiate login URI. Must be HTTPS or an empty string.
- `is_first_party` (Boolean) Indicates whether this client is a first-party client.Defaults to true from the API
- `is_token_endpoint_ip_header_trusted` (Boolean) Indicates whether the token endpoint IP header is trusted. Requires the authentication method to be set to `client_secret_post` or `client_secret_basic`. Setting this property when creating the resource, will default the authentication method to `client_secret_post`. To change the authentication method to `client_secret_basic` use the `auth0_client_credentials` resource.
- `jwt_configuration` (List of Object) Configuration settings for the JWTs issued for this client. (see [below for nested schema](#nestedatt--jwt_configuration))
- `logo_uri` (String) URL of the logo for the client. Recommended size is 150px x 150px. If none is set, the default badge for the application type will be shown.
- `mobile` (List of Object) Additional configuration for native mobile apps. (see [below for nested schema](#nestedatt--mobile))
- `native_social_login` (List of Object) Configuration settings to toggle native social login for mobile native applications. Once this is set it must stay set, with both resources set to `false` in order to change the `app_type`. (see [below for nested schema](#nestedatt--native_social_login))
- `oidc_backchannel_logout_urls` (Set of String) Set of URLs that are valid to call back from Auth0 for OIDC backchannel logout. Currently only one URL is allowed.
- `oidc_conformant` (Boolean) Indicates whether this client will conform to strict OIDC specifications.
- `oidc_logout` (List of Object) Configure OIDC logout for the Client (see [below for nested schema](#nestedatt--oidc_logout))
- `organization_require_behavior` (String) Defines how to proceed during an authentication transaction when `organization_usage = "require"`. Can be `no_prompt` (default), `pre_login_prompt` or  `post_login_prompt`.
- `organization_usage` (String) Defines how to proceed during an authentication transaction with regards to an organization. Can be `deny` (default), `allow` or `require`.
- `refresh_token` (List of Object) Configuration settings for the refresh tokens issued for this client. (see [below for nested schema](#nestedatt--refresh_token))
- `require_proof_of_possession` (Boolean) Makes the use of Proof-of-Possession mandatory for this client.
- `require_pushed_authorization_requests` (Boolean) Makes the use of Pushed Authorization Requests mandatory for this client. This feature currently needs to be enabled on the tenant in order to make use of it.
- `session_transfer` (List of Object) (see [below for nested schema](#nestedatt--session_transfer))
- `signed_request_object` (Set of Object) Configuration for JWT-secured Authorization Requests(JAR). (see [below for nested schema](#nestedatt--signed_request_object))
- `signing_keys` (List of Map of String) List containing a map of the public cert of the signing key and the public cert of the signing key in PKCS7.
- `sso` (Boolean) Applies only to SSO clients and determines whether Auth0 will handle Single Sign-On (true) or whether the identity provider will (false).
- `sso_disabled` (Boolean) Indicates whether or not SSO is disabled.
- `token_endpoint_auth_method` (String) The authentication method for the token endpoint. Results include `none` (public client without a client secret), `client_secret_post` (client uses HTTP POST parameters), `client_secret_basic` (client uses HTTP Basic), Managing a client's authentication method can be done via the `auth0_client_credentials` resource.
- `token_exchange` (List of Object) Allows configuration for token exchange (see [below for nested schema](#nestedatt--token_exchange))
- `web_origins` (List of String) URLs that represent valid web origins for use with web message response mode.

<a id="nestedatt--addons"></a>
### Nested Schema for `addons`

Read-Only:

- `aws` (List of Object) (see [below for nested schema](#nestedobjatt--addons--aws))
- `azure_blob` (List of Object) (see [below for nested schema](#nestedobjatt--addons--azure_blob))
- `azure_sb` (List of Object) (see [below for nested schema](#nestedobjatt--addons--azure_sb))
- `box` (List of Object) (see [below for nested schema](#nestedobjatt--addons--box))
- `cloudbees` (List of Object) (see [below for nested schema](#nestedobjatt--addons--cloudbees))
- `concur` (List of Object) (see [below for nested schema](#nestedobjatt--addons--concur))
- `dropbox` (List of Object) (see [below for nested schema](#nestedobjatt--addons--dropbox))
- `echosign` (List of Object) (see [below for nested schema](#nestedobjatt--addons--echosign))
- `egnyte` (List of Object) (see [below for nested schema](#nestedobjatt--addons--egnyte))
- `firebase` (List of Object) (see [below for nested schema](#nestedobjatt--addons--firebase))
- `layer` (List of Object) (see [below for nested schema](#nestedobjatt--addons--layer))
- `mscrm` (List of Object) (see [below for nested schema](#nestedobjatt--addons--mscrm))
- `newrelic` (List of Object) (see [below for nested schema](#nestedobjatt--addons--newrelic))
- `office365` (List of Object) (see [below for nested schema](#nestedobjatt--addons--office365))
- `rms` (List of Object) (see [below for nested schema](#nestedobjatt--addons--rms))
- `salesforce` (List of Object) (see [below for nested schema](#nestedobjatt--addons--salesforce))
- `salesforce_api` (List of Object) (see [below for nested schema](#nestedobjatt--addons--salesforce_api))
- `salesforce_sandbox_api` (List of Object) (see [below for nested schema](#nestedobjatt--addons--salesforce_sandbox_api))
- `samlp` (List of Object) (see [below for nested schema](#nestedobjatt--addons--samlp))
- `sap_api` (List of Object) (see [below for nested schema](#nestedobjatt--addons--sap_api))
- `sentry` (List of Object) (see [below for nested schema](#nestedobjatt--addons--sentry))
- `sharepoint` (List of Object) (see [below for nested schema](#nestedobjatt--addons--sharepoint))
- `slack` (List of Object) (see [below for nested schema](#nestedobjatt--addons--slack))
- `springcm` (List of Object) (see [below for nested schema](#nestedobjatt--addons--springcm))
- `sso_integration` (List of Object) (see [below for nested schema](#nestedobjatt--addons--sso_integration))
- `wams` (List of Object) (see [below for nested schema](#nestedobjatt--addons--wams))
- `wsfed` (List of Object) (see [below for nested schema](#nestedobjatt--addons--wsfed))
- `zendesk` (List of Object) (see [below for nested schema](#nestedobjatt--addons--zendesk))
- `zoom` (List of Object) (see [below for nested schema](#nestedobjatt--addons--zoom))

<a id="nestedobjatt--addons--aws"></a>
### Nested Schema for `addons.aws`

Read-Only:

- `lifetime_in_seconds` (Number)
- `principal` (String)
- `role` (String)


<a id="nestedobjatt--addons--azure_blob"></a>
### Nested Schema for `addons.azure_blob`

Read-Only:

- `account_name` (String)
- `blob_delete` (Boolean)
- `blob_name` (String)
- `blob_read` (Boolean)
- `blob_write` (Boolean)
- `container_delete` (Boolean)
- `container_list` (Boolean)
- `container_name` (String)
- `container_read` (Boolean)
- `container_write` (Boolean)
- `expiration` (Number)
- `signed_identifier` (String)
- `storage_access_key` (String)


<a id="nestedobjatt--addons--azure_sb"></a>
### Nested Schema for `addons.azure_sb`

Read-Only:

- `entity_path` (String)
- `expiration` (Number)
- `namespace` (String)
- `sas_key` (String)
- `sas_key_name` (String)


<a id="nestedobjatt--addons--box"></a>
### Nested Schema for `addons.box`

Read-Only:



<a id="nestedobjatt--addons--cloudbees"></a>
### Nested Schema for `addons.cloudbees`

Read-Only:



<a id="nestedobjatt--addons--concur"></a>
### Nested Schema for `addons.concur`

Read-Only:



<a id="nestedobjatt--addons--dropbox"></a>
### Nested Schema for `addons.dropbox`

Read-Only:



<a id="nestedobjatt--addons--echosign"></a>
### Nested Schema for `addons.echosign`

Read-Only:

- `domain` (String)


<a id="nestedobjatt--addons--egnyte"></a>
### Nested Schema for `addons.egnyte`

Read-Only:

- `domain` (String)


<a id="nestedobjatt--addons--firebase"></a>
### Nested Schema for `addons.firebase`

Read-Only:

- `client_email` (String)
- `lifetime_in_seconds` (Number)
- `private_key` (String)
- `private_key_id` (String)
- `secret` (String)


<a id="nestedobjatt--addons--layer"></a>
### Nested Schema for `addons.layer`

Read-Only:

- `expiration` (Number)
- `key_id` (String)
- `principal` (String)
- `private_key` (String)
- `provider_id` (String)


<a id="nestedobjatt--addons--mscrm"></a>
### Nested Schema for `addons.mscrm`

Read-Only:

- `url` (String)


<a id="nestedobjatt--addons--newrelic"></a>
### Nested Schema for `addons.newrelic`

Read-Only:

- `account` (String)


<a id="nestedobjatt--addons--office365"></a>
### Nested Schema for `addons.office365`

Read-Only:

- `connection` (String)
- `domain` (String)


<a id="nestedobjatt--addons--rms"></a>
### Nested Schema for `addons.rms`

Read-Only:

- `url` (String)


<a id="nestedobjatt--addons--salesforce"></a>
### Nested Schema for `addons.salesforce`

Read-Only:

- `entity_id` (String)


<a id="nestedobjatt--addons--salesforce_api"></a>
### Nested Schema for `addons.salesforce_api`

Read-Only:

- `client_id` (String)
- `community_name` (String)
- `community_url_section` (String)
- `principal` (String)


<a id="nestedobjatt--addons--salesforce_sandbox_api"></a>
### Nested Schema for `addons.salesforce_sandbox_api`

Read-Only:

- `client_id` (String)
- `community_name` (String)
- `community_url_section` (String)
- `principal` (String)


<a id="nestedobjatt--addons--samlp"></a>
### Nested Schema for `addons.samlp`

Read-Only:

- `audience` (String)
- `authn_context_class_ref` (String)
- `binding` (String)
- `create_upn_claim` (Boolean)
- `destination` (String)
- `digest_algorithm` (String)
- `include_attribute_name_format` (Boolean)
- `issuer` (String)
- `lifetime_in_seconds` (Number)
- `logout` (List of Object) (see [below for nested schema](#nestedobjatt--addons--samlp--logout))
- `map_identities` (Boolean)
- `map_unknown_claims_as_is` (Boolean)
- `mappings` (Map of String)
- `name_identifier_format` (String)
- `name_identifier_probes` (List of String)
- `passthrough_claims_with_no_mapping` (Boolean)
- `recipient` (String)
- `sign_response` (Boolean)
- `signature_algorithm` (String)
- `signing_cert` (String)
- `typed_attributes` (Boolean)

<a id="nestedobjatt--addons--samlp--logout"></a>
### Nested Schema for `addons.samlp.logout`

Read-Only:

- `callback` (String)
- `slo_enabled` (Boolean)



<a id="nestedobjatt--addons--sap_api"></a>
### Nested Schema for `addons.sap_api`

Read-Only:

- `client_id` (String)
- `name_identifier_format` (String)
- `scope` (String)
- `service_password` (String)
- `token_endpoint_url` (String)
- `username_attribute` (String)


<a id="nestedobjatt--addons--sentry"></a>
### Nested Schema for `addons.sentry`

Read-Only:

- `base_url` (String)
- `org_slug` (String)


<a id="nestedobjatt--addons--sharepoint"></a>
### Nested Schema for `addons.sharepoint`

Read-Only:

- `external_url` (List of String)
- `url` (String)


<a id="nestedobjatt--addons--slack"></a>
### Nested Schema for `addons.slack`

Read-Only:

- `team` (String)


<a id="nestedobjatt--addons--springcm"></a>
### Nested Schema for `addons.springcm`

Read-Only:

- `acs_url` (String)


<a id="nestedobjatt--addons--sso_integration"></a>
### Nested Schema for `addons.sso_integration`

Read-Only:

- `name` (String)
- `version` (String)


<a id="nestedobjatt--addons--wams"></a>
### Nested Schema for `addons.wams`

Read-Only:

- `master_key` (String)


<a id="nestedobjatt--addons--wsfed"></a>
### Nested Schema for `addons.wsfed`

Read-Only:



<a id="nestedobjatt--addons--zendesk"></a>
### Nested Schema for `addons.zendesk`

Read-Only:

- `account_name` (String)


<a id="nestedobjatt--addons--zoom"></a>
### Nested Schema for `addons.zoom`

Read-Only:

- `account` (String)



<a id="nestedatt--client_authentication_methods"></a>
### Nested Schema for `client_authentication_methods`

Read-Only:

- `private_key_jwt` (Set of Object) (see [below for nested schema](#nestedobjatt--client_authentication_methods--private_key_jwt))
- `self_signed_tls_client_auth` (Set of Object) (see [below for nested schema](#nestedobjatt--client_authentication_methods--self_signed_tls_client_auth))
- `tls_client_auth` (Set of Object) (see [below for nested schema](#nestedobjatt--client_authentication_methods--tls_client_auth))

<a id="nestedobjatt--client_authentication_methods--private_key_jwt"></a>
### Nested Schema for `client_authentication_methods.private_key_jwt`

Read-Only:

- `credentials` (List of Object) (see [below for nested schema](#nestedobjatt--client_authentication_methods--private_key_jwt--credentials))

<a id="nestedobjatt--client_authentication_methods--private_key_jwt--credentials"></a>
### Nested Schema for `client_authentication_methods.private_key_jwt.credentials`

Read-Only:

- `algorithm` (String)
- `created_at` (String)
- `credential_type` (String)
- `expires_at` (String)
- `id` (String)
- `key_id` (String)
- `name` (String)
- `updated_at` (String)



<a id="nestedobjatt--client_authentication_methods--self_signed_tls_client_auth"></a>
### Nested Schema for `client_authentication_methods.self_signed_tls_client_auth`

Read-Only:

- `credentials` (List of Object) (see [below for nested schema](#nestedobjatt--client_authentication_methods--self_signed_tls_client_auth--credentials))

<a id="nestedobjatt--client_authentication_methods--self_signed_tls_client_auth--credentials"></a>
### Nested Schema for `client_authentication_methods.self_signed_tls_client_auth.credentials`

Read-Only:

- `created_at` (String)
- `credential_type` (String)
- `id` (String)
- `name` (String)
- `updated_at` (String)



<a id="nestedobjatt--client_authentication_methods--tls_client_auth"></a>
### Nested Schema for `client_authentication_methods.tls_client_auth`

Read-Only:

- `credentials` (List of Object) (see [below for nested schema](#nestedobjatt--client_authentication_methods--tls_client_auth--credentials))

<a id="nestedobjatt--client_authentication_methods--tls_client_auth--credentials"></a>
### Nested Schema for `client_authentication_methods.tls_client_auth.credentials`

Read-Only:

- `created_at` (String)
- `credential_type` (String)
- `id` (String)
- `name` (String)
- `subject_dn` (String)
- `updated_at` (String)




<a id="nestedatt--default_organization"></a>
### Nested Schema for `default_organization`

Read-Only:

- `disable` (Boolean)
- `flows` (List of String)
- `organization_id` (String)


<a id="nestedatt--jwt_configuration"></a>
### Nested Schema for `jwt_configuration`

Read-Only:

- `alg` (String)
- `lifetime_in_seconds` (Number)
- `scopes` (Map of String)
- `secret_encoded` (Boolean)


<a id="nestedatt--mobile"></a>
### Nested Schema for `mobile`

Read-Only:

- `android` (List of Object) (see [below for nested schema](#nestedobjatt--mobile--android))
- `ios` (List of Object) (see [below for nested schema](#nestedobjatt--mobile--ios))

<a id="nestedobjatt--mobile--android"></a>
### Nested Schema for `mobile.android`

Read-Only:

- `app_package_name` (String)
- `sha256_cert_fingerprints` (List of String)


<a id="nestedobjatt--mobile--ios"></a>
### Nested Schema for `mobile.ios`

Read-Only:

- `app_bundle_identifier` (String)
- `team_id` (String)



<a id="nestedatt--native_social_login"></a>
### Nested Schema for `native_social_login`

Read-Only:

- `apple` (List of Object) (see [below for nested schema](#nestedobjatt--native_social_login--apple))
- `facebook` (List of Object) (see [below for nested schema](#nestedobjatt--native_social_login--facebook))
- `google` (List of Object) (see [below for nested schema](#nestedobjatt--native_social_login--google))

<a id="nestedobjatt--native_social_login--apple"></a>
### Nested Schema for `native_social_login.apple`

Read-Only:

- `enabled` (Boolean)


<a id="nestedobjatt--native_social_login--facebook"></a>
### Nested Schema for `native_social_login.facebook`

Read-Only:

- `enabled` (Boolean)


<a id="nestedobjatt--native_social_login--google"></a>
### Nested Schema for `native_social_login.google`

Read-Only:

- `enabled` (Boolean)



<a id="nestedatt--oidc_logout"></a>
### Nested Schema for `oidc_logout`

Read-Only:

- `backchannel_logout_initiators` (List of Object) (see [below for nested schema](#nestedobjatt--oidc_logout--backchannel_logout_initiators))
- `backchannel_logout_urls` (Set of String)

<a id="nestedobjatt--oidc_logout--backchannel_logout_initiators"></a>
### Nested Schema for `oidc_logout.backchannel_logout_initiators`

Read-Only:

- `mode` (String)
- `selected_initiators` (Set of String)



<a id="nestedatt--refresh_token"></a>
### Nested Schema for `refresh_token`

Read-Only:

- `expiration_type` (String)
- `idle_token_lifetime` (Number)
- `infinite_idle_token_lifetime` (Boolean)
- `infinite_token_lifetime` (Boolean)
- `leeway` (Number)
- `policies` (Set of Object) (see [below for nested schema](#nestedobjatt--refresh_token--policies))
- `rotation_type` (String)
- `token_lifetime` (Number)

<a id="nestedobjatt--refresh_token--policies"></a>
### Nested Schema for `refresh_token.policies`

Read-Only:

- `audience` (String)
- `scope` (List of String)



<a id="nestedatt--session_transfer"></a>
### Nested Schema for `session_transfer`

Read-Only:

- `allowed_authentication_methods` (Set of String)
- `can_create_session_transfer_token` (Boolean)
- `enforce_device_binding` (String)


<a id="nestedatt--signed_request_object"></a>
### Nested Schema for `signed_request_object`

Read-Only:

- `credentials` (List of Object) (see [below for nested schema](#nestedobjatt--signed_request_object--credentials))
- `required` (Boolean)

<a id="nestedobjatt--signed_request_object--credentials"></a>
### Nested Schema for `signed_request_object.credentials`

Read-Only:

- `algorithm` (String)
- `created_at` (String)
- `credential_type` (String)
- `expires_at` (String)
- `id` (String)
- `key_id` (String)
- `name` (String)
- `updated_at` (String)



<a id="nestedatt--token_exchange"></a>
### Nested Schema for `token_exchange`

Read-Only:

- `allow_any_profile_of_type` (List of String)


