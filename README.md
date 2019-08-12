# OPES Ecosystem Community Node Information Standard
**JSON Standard for Community Node Information on the OPES Ecosystem Blockchain**

This is a proposed standard for an OPES Ecosystem Community Node to publish as
the URL field of the `createcn` action on the `opes.system` contract.

The current revision is compliant with the JSON schema Draft v7 -
http://json-schema.org/specification.html

One can specify under nodes/node_type the location of the infra structure node.
Data aggregates are adviced to use the sourced data from opes.one. For more
information on this, look at http://github.com/opespe.

- community_node_account_name: Name of community node account
- org: [Object]
  - display_name: Community node/organization name
  - summary: Short description of the activity
  - website: Community Node website, must have OPES in the domain name.
  - pledge_to_opes_ecosystem: Full link to where it is,
  - email: Contact email
  - branding: {Object} - Logo images, must be in a perfect sphere.
      - sphere_256: Entire url to image 256x256px
      - sphere_1024: Entire url to image 1024x1024px
      - sphere_svg: Entire url to image svg
   - location: {Object} - Organization location
      - name: Location in human readable format [City, State]
      - country: Country code [XX] in accordance to [ISO 3166-1 alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2)
      - latitude: Latitude in decimal degrees
      - longitude: Longitude in decimal degrees
    },
  - social: {Object} - NOT THE ENTIRE URL, only usernames on social networks, 
    - linkedin: Username
    - instagram: Username
    - snapchat: Username
    - steemit: Username without @
    - twitter: Username
    - youtube: Channel address
    - facebook: Page/group address
    - github: Username
    - reddit: Username
    - keybase: Username
    - telegram: Username
    - wechat: Username
- nodes: [Array]
    - location: Node location
        - region: Node location in human readable format [City, State]
        - country: Node country code [XX]
        - latitude: Node latitude in decimal degrees
        - longitude: Node longitude in decimal degrees
    - node_type: Type of service `infra/full/query/seed`
        - infra: Your Infrastructure Node 
        - full: Node with full history
        - query: Node that provides HTTP(S) API to the public
        - seed: Node that provides P2P and/or BNET to the public
    - p2p_endpoint: Node P2P endpoint `host:port`
    - bnet_endpoint: Node BNET endpoint `host:port`
    - api_endpoint: Node HTTP endpoint `http://host:port`
    - ssl_endpoint: Node HTTPS endpoint `https://host:port`

### How to use it if you are a Community Node
Create a file named, preferably named `cn.json`, and make it available online.
For example at `http://yourwebsite.com/cn.json`, or if you want to seperate it from your
website, your could host in on your github at for example
`https://github.com/youraccount/cnrepo/cn.json`. 

When you register your
community node using the `opes.system.creatcn` action, or update the information using the
`system.updatecninfo`, make sure the `resourcedesc` field should be filled with
the final location of your created `cn.json`. **Remember to store the full url, preferably secured with ssl**.

Many services will use the information stored in your community node info file. Making it an important step
in being known as a community node.

### Useful Links
One can check for data validity using: https://www.jsonschemavalidator.net/.
To find the latitude and longitude for your location, on can use https://www.latlong.net/.
