# Digital-ocean

Clojure interface for Digital Ocean

```
[digitalocean "1.2"]
```

## V2 API

### Authentication

You can pass in an OAuth token directly to every function.

You can get a token from your Digital Ocean account user settings.

### Getting started

```clojure
(ns myproject
  (:require [digitalocean.v2.core :as do]))

(defonce token "YOURAUTHTOKEN")

```

### Droplets

Get all droplets

```clojure
(do/droplets token)
```

Get a droplet by ID

```clojure
(do/get-droplet token 123)
```

Boot up a new droplet. All droplets require an image id to boot from.

Note that certain fields are required. See the Digital Ocean API V2 docs for all params

```clojure
(do/create-droplet token nil
  {:name "ubuntu-s-1vcpu-2gb-lon1-01"
   :region "lon1"
   :size "s-1vcpu-2gb"
   :image "ubuntu-16-04-x64"
   :tags ["web"]
  })
```

Delete a droplet by ID

```clojure
(do/delete-droplet token 123)
```

### Domains

Get all

```clojure
(do/domains token)
```

Get one domain by name

```clojure
(do/get-domain token "fshionable.com")
```

### Domain records

Get records for a domain

```clojure
(do/records token "fshionable.com")
```

## Images

Get all images

```clojure
(do/images token)
```

### Keys

```clojure

;; Get all keys
(do/keys token)

;; Create a new one
(do/create-key token nil {
  :name "Blah"
  :public_key "Blah"})

```

### Regions

Get all regions

```clojure
(do/regions token)
```

### Sizes

Get all sizes

```clojure
(do/sizes token)
```

## License

Copyright © 2014 Owain Lewis

Distributed under the Eclipse Public License, the same as Clojure.
