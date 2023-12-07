![Tests](https://github.com/Cringe-Studio/strapi-auto-uuid/actions/workflows/main.yml/badge.svg)

# Strapi Auto UUID Plugin

The Strapi Auto UUID Plugin is a custom plugin for Strapi that automatically generates a unique UUID for your content.

## Installation

To install the Strapi Auto UUID Plugin, simply run one of the following command:

```
pnpm add strapi-auto-uuid
```
```
npm install strapi-auto-uuid
```
```
yarn add strapi-auto-uuid
```

## Usage

Once the plugin is installed, you can add a new custom type to your Strapi content types, no configuration needed. The custom type uses the Strapi UID structure, ensuring that each UUID generated is unique.

You can create new records via the Admin panel, API or GraphQL, and the plugin will automatically generate a UUID for each new record created.

## Example

Here's an example of how to use the Strapi Auto UUID Plugin:

1. Install the plugin using `npm install strapi-auto-uuid`
2. Find the `schema.json` file for the model you want to add the plugin to. You can find this in `src\api\<modelName>\content-types\<modelName>\schema.json` i.e.

      ![sample json schema file location](<Screen Shot 2023-12-07 at 12.27.39 AM.png> "Schema file location") 
3. Add the custom type AutoUUID as shown below. (TIP: You can change "uuid" to whatever name you like.)

```javascript
module.exports = {
  attributes: {
    title: {
      type: 'string',
      required: true,
    },
    uuid: {
      type: "customField",
      customField: "plugin::field-uuid.uuid"
    },
  },
};
```

4. When you create a new record in this model via the Strapi API or GraphQL, the plugin will automatically generate a unique UUID for the `uuid` field.

That's it! With the Strapi Auto UUID Plugin, you can easily add UUIDs to your Strapi content without having to worry about generating them yourself.


Note: If you are currently using the `@bn-digital/strapi-plugin-field-uuid` plugin, the `strapi-auto-uuid` plugin can be used as a replacement without requiring any code changes. Simply install `strapi-auto-uuid`  and remove `@bn-digital/strapi-plugin-field-uuid`. The Strapi Auto UUID Plugin provides the same functionality as the `@bn-digital/strapi-plugin-field-uuid` plugin, in addition it supports uuid generation automatically via api or graphql and is actively maintained.

## License
This plugin is licensed under the MIT License. See the LICENSE file for more information.
