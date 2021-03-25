# Migration `20200520194434-price-float-to-string`

This migration has been generated by Manthankumar Satani at 5/20/2020, 7:44:34 PM.
You can check out the [state of the schema](./schema.prisma) after the migration.

## Database Steps

```sql
ALTER TABLE "public"."orders" DROP COLUMN "min_price",
ADD COLUMN "min_price" text  NOT NULL ,
DROP COLUMN "price",
ADD COLUMN "price" text  NOT NULL ,
DROP COLUMN "taker_amount",
ADD COLUMN "taker_amount" text   ;
```

## Changes

```diff
diff --git schema.prisma schema.prisma
migration 20200520185646-added-name-to-tokens..20200520194434-price-float-to-string
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
@@ -85,14 +85,14 @@
   erc20tokens_id Int
   expiry_date    DateTime?
   id             Int         @default(autoincrement()) @id
   maker_address  Int
-  min_price      Float
-  price          Float
+  min_price      String
+  price          String
   signature      String?
   status         Int?        @default(0)
   taker_address  Int?
-  taker_amount   Float?
+  taker_amount   String?
   tokens_id      Int
   txhash         String?
   type           String
   updated        DateTime    @default(now())
```

