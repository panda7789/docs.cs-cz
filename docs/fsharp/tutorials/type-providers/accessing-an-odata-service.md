---
title: 'Návod: Přístup ke službě OData s použitím zprostředkovatelů typů (F#)'
description: 'Další informace o použití F # odataservice – poskytovatel typů v F # 3.0 k vygenerování typů klientů pro službu OData a dotazů datových kanálů, které služba poskytuje.'
keywords: 'Visual f #, f #, funkční programování'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 0adae84c-b0fa-455f-994b-274ecdc6df30
ms.openlocfilehash: 750407c36a989cece30c0c0654ff905c8eee3b33
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/10/2018
---
# <a name="walkthrough-accessing-an-odata-service-by-using-type-providers"></a>Návod: Přístup ke službě OData s použitím zprostředkovatelů typů

> [!NOTE]
Tento průvodce byl vytvořen pro F # 3.0 a budou aktualizovány.  V tématu [FSharp.Data](https://fsharp.github.io/FSharp.Data/) pro různé platformy, aktuální typ poskytovatele.

> [!NOTE]
Rozhraní API referenčních odkazů se dostanete na webu MSDN.  Referenční dokumentace rozhraní API docs.microsoft.com není dokončena.

OData, což znamená, protokol, je protokol pro přenos dat přes Internet. Mnoho poskytovatelů dat vystavit přístup k jejich datům tím, že publikujete webovou službu OData. Můžete přístup k datům z jakéhokoli zdroje OData v F # 3.0 pomocí datových typů, jsou automaticky generované `ODataService` typ poskytovatele. Další informace o protokolu OData najdete v tématu https://msdn.microsoft.com/library/da3380cc-f6da-4c6c-bdb2-bb86afa59d62.

Tento postup vám ukáže, jak používat F # odataservice – poskytovatel typů ke generování typů klientů pro službu OData a dotazů datových kanálů, které služba poskytuje.

Tento návod znázorňuje následující úkoly, které je nutné z důvodu správné funkčnosti provést v tomto pořadí:


- Konfigurace projektu klienta pro službu OData
<br />

- Přístup k typy OData
<br />

- Dotazování služby OData
<br />

- Ověření požadavků OData
<br />


## <a name="configuring-a-client-project-for-an-odata-service"></a>Konfigurace projektu klienta pro službu OData
V tomto kroku nastavíte projektu pro použití OData typ poskytovatele.


#### <a name="to-configure-a-client-project-for-an-odata-service"></a>Ke konfiguraci projektu klienta pro službu OData

- Otevřete projekt konzolové aplikace v F # a pak přidejte odkaz na `System.Data.Services.Client` sestavení rozhraní.
<br />

- V části `Extensions`, přidejte odkaz na `FSharp.Data.TypeProviders` sestavení.
<br />

## <a name="accessing-odata-types"></a>Přístup k typy OData
V tomto kroku vytvoříte typ zprostředkovatele, který poskytuje přístup k typy a dat pro služby OData.


#### <a name="to-access-odata-types"></a>Pro přístup k typy OData

- V editoru kódu otevřete soubor zdroje F # a zadejte následující kód.
<br />

```fsharp
open Microsoft.FSharp.Data.TypeProviders


type Northwind = ODataService<"https://services.odata.org/Northwind/Northwind.svc/">

let db = Northwind.GetDataContext()
let fullContext = Northwind.ServiceTypes.NorthwindEntities()
```

V tomto příkladu jste vyvolat poskytovatel typů F # a pokyn k tvorbě sadu typů, které jsou založeny na identifikátoru URI protokolu OData, který jste zadali. K dispozici jsou dva objekty obsahující informace o datech; jedna je zjednodušená data kontextu, `db` v příkladu. Tento objekt obsahuje pouze typy dat, které jsou spojeny s databází, které zahrnují typy tabulek a kanálů. Druhý objekt, `fullContext` v tomto příkladu je instance `System.Data.Linq.DataContext` a obsahuje mnoho dalších vlastností, metod a události.
<br />


## <a name="querying-an-odata-service"></a>Dotazování služby OData
V tomto kroku použijete F # – výrazy dotazů k dotazování na službu OData.


#### <a name="to-query-an-odata-service"></a>K dotazování služby OData

1. Teď, když jste nastavili typ zprostředkovatele, se můžete dotazovat služby OData.
<br />  OData podporuje pouze podmnožinu operace dostupné dotazů. Podporovány jsou následující operace a jejich odpovídající klíčová slova:
<br />
  - projekce (`select`)
<br />

  - filtrování (`where`, pomocí pomocí řetězce a datum operace)
<br />

  - stránkování (`skip`, `take`)
<br />

  - řazení (`orderBy`, `thenBy`)
<br />

  - `AddQueryOption` a `Expand`, které jsou specifické pro OData operace
<br />

  Další informace najdete v tématu [LINQ aspekty &#40;služby WCF Data Services&#41;](https://msdn.microsoft.com/library/ee622463.aspx).
<br />  Pokud chcete všechny položky v kanálu nebo tabulky, použijte nejjednodušší forma výrazu dotazu, jako v následujícím kódu:
<br />

```fsharp
query {
  for customer in db.Customers do
  select customer
} |> Seq.iter (fun customer ->
                  printfn "ID: %s\nCompany: %s" customer.CustomerID customer.CompanyName
                  printfn "Contact: %s\nAddress: %s" customer.ContactName customer.Address
                  printfn "         %s, %s %s" customer.City customer.Region customer.PostalCode
                  printfn "%s\n" customer.Phone)
```

2. Zadejte pole nebo sloupce, které chcete pomocí řazené kolekce členů po vyberte – klíčové slovo.
<br />

```fsharp
  query { 
    for cat in db.Categories do
    select (cat.CategoryID, cat.CategoryName, cat.Description)
  } |> Seq.iter (fun (id, name, description) ->
                    printfn "ID: %d\nCategory: %s\nDescription: %s\n" id name description)
```

3. Zadat podmínky, a to pomocí `where` klauzule.
<br />

```fsharp
query {
  for employee in db.Employees do
  where (employee.EmployeeID = 9)
  select employee
} |> Seq.iter (fun employee ->
                  printfn "Name: %s ID: %d" (employee.FirstName + " " + employee.LastName) (employee.EmployeeID))
```

4. Zadejte podmínku podřetězec do dotazu pomocí `System.String.Contains(System.String)` metoda. Následující dotaz vrátí všechny produkty, které mají "Chef" v jejich názvy. Všimněte si také použití `System.Nullable<'T>.GetValueOrDefault()`. `UnitPrice` Je hodnota Null, musíte buď získat hodnotu pomocí `Value` vlastnost, nebo musí volat `System.Nullable<'T>.GetValueOrDefault()`.
<br />

```fsharp
query { 
  for product in db.Products do
  where (product.ProductName.Contains("Chef"))
  select product
} |> Seq.iter (fun product ->
                  printfn "ID: %d Product: %s" product.ProductID product.ProductName
                  printfn "Price: %M\n" (product.UnitPrice.GetValueOrDefault()))
```

5. Použití `System.String.EndsWith(System.String)` metoda k určení, že řetězec končí určité dílčí řetězec.
<br />

```fsharp
query {
  for product in db.Products do
  where (product.ProductName.EndsWith("u"))
  select product
} |> Seq.iter (fun product ->
                  printfn "ID: %d Product: %s" product.ProductID product.ProductName
                  printfn "Price: %M\n" (product.UnitPrice.GetValueOrDefault()))
```

6. Kombinovat podmínky v where klauzule pomocí `&&` operátor.
<br />

```fsharp
// Open this module to use the nullable operators ?> and ?<.
open Microsoft.FSharp.Linq.NullableOperators

let salesIn1997 = query { 
  for sales in db.Category_Sales_for_1997 do
  where (sales.CategorySales ?> 50000.00M && sales.CategorySales ?< 60000.0M)
  select sales }

salesIn1997
|> Seq.iter (fun sales ->
                printfn "Category: %s Sales: %M" sales.CategoryName (sales.CategorySales.GetValueOrDefault()))
```

Operátory `?>` a `?<` jsou operátory s povolenou hodnotou Null. Můžete použít úplnou sadu s možnou hodnotou Null operátory rovnosti a porovnání. Další informace najdete v tématu [LINQ.nullableoperators – modul](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.nullableoperators-module-%5bfsharp%5d).
<br />

7. Použít `sortBy` dotazu operátor k určení pořadí a použijte `thenBy` chcete zadat jinou úroveň řazení. Všimněte si také řazené kolekce členů v vyberte část dotazu. Proto dotazu má řazené kolekce členů jako typ elementu.
<br />

```fsharp
printfn "Freight for some orders: "

query { 
  for order in db.Orders do
  sortBy (order.OrderDate.Value)
  thenBy (order.OrderID)
  select (order.OrderDate, order.OrderID, order.Customer.CompanyName)
} |> Seq.iter (fun (orderDate, orderID, company) ->
                  printfn "OrderDate: %s" (orderDate.GetValueOrDefault().ToString())
                  printfn "OrderID: %d Company: %s\n" orderID company)
```

8. Ignorovat zadaný počet záznamů pomocí operátoru přeskočit a použití operátoru proveďte k určení počtu vrácených záznamů. Tímto způsobem můžete implementovat stránkování na datové kanály.
<br />

```fsharp
printfn "Get the first page of 2 employees."

query { 
  for employee in db.Employees do
  take 2
  select employee
} |> Seq.iter (fun employee ->
                  printfn "Name: %s ID: %d" (employee.FirstName + " " + employee.LastName) (employee.EmployeeID)) 

printfn "Get the next 2 employees."

query { 
  for employee in db.Employees do
  skip 2
  take 2
  select employee
} |> Seq.iter (fun employee ->
                  printfn "Name: %s ID: %d" (employee.FirstName + " " + employee.LastName) (employee.EmployeeID))
```

## <a name="verifying-the-odata-request"></a>Ověření žádost OData
Každý dotaz OData je přeložit na konkrétní URI požadavku OData. Můžete ověřit, že identifikátor URI, třeba pro ladění účely, přidáním obslužné rutiny události pro `SendingRequest` událostí na úplné datový objekt kontextu.


#### <a name="to-verify-the-odata-request"></a>Chcete-li ověřit žádost OData

- K ověření identifikátoru URI požadavku OData, použijte následující kód:
<br />

```fsharp
// The DataContext property returns the full data context.
db.DataContext.SendingRequest.Add (fun eventArgs -> printfn "Requesting %A" eventArgs.Request.RequestUri)
```

Výstup jako předchozí kód je:
<br />`requesting https://services.odata.org/Northwind/Northwind.svc/Orders()?$orderby=ShippedDate&amp;$select=OrderID,ShippedDate`


## <a name="see-also"></a>Viz také
[Výrazy dotazu](../../language-reference/query-expressions.md)

[Aspekty LINQ (služby WCF Data Services)](https://msdn.microsoft.com/library/ee622463.aspx)

[Odataservice – zprostředkovatel typu (F #)](https://msdn.microsoft.com/visualfsharpdocs/conceptual/odataservice-type-provider-%5bfsharp%5d)
