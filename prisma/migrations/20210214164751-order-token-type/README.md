# Migration `20210214164751-order-token-type`

This migration has been generated by rahuldamodar94 at 2/14/2021, 4:47:51 PM.
You can check out the [state of the schema](./schema.prisma) after the migration.

## Database Steps

```sql
ALTER TABLE "public"."orders" ADD COLUMN "token_type" text   DEFAULT E'ERC721';
```

## Changes

```diff
diff --git schema.prisma schema.prisma
migration 20210212100046-erc1155..20210214164751-order-token-type
--- datamodel.dml
+++ datamodel.dml
@@ -3,9 +3,9 @@
 }
 datasource db {
   provider = "postgresql"
-  url = "***"
+  url      = env("DATABASE_URL")
 }
 model bids {
   active    Boolean? @default(true)
@@ -95,10 +95,11 @@
   id             Int             @default(autoincrement()) @id
   maker_address  Int?
   min_price      String
   price          String
-  price_per_unit String?
-  quantity       String?
+  price_per_unit String?         
+  quantity       String?         
+  token_type     String?         @default("ERC721")
   usd_price      Float?
   signature      String?
   status         Int?            @default(0)
   taker_address  Int?
```

