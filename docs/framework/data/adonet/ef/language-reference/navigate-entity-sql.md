---
title: NAVIGACE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
ms.openlocfilehash: 2c6c2ae4c593da1d5fe8cdf3015eb0e31e4b12b5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249942"
---
# <a name="navigate-entity-sql"></a>NAVIGACE (Entity SQL)

Přejde přes vztah navázaný mezi entitami.

## <a name="syntax"></a>Syntaxe

```
navigate(instance-expression, [relationship-type], [to-end [, from-end] ])
```

## <a name="arguments"></a>Arguments

`instance-expression`Instance entity

`relationship-type`Název typu relace ze souboru CSDL (konceptuální schéma Definition Language). Je kvalifikován jako \<obor názvů >.\< `relationship-type` název typu vztahu >.

`to`Konec relace.

`from`Začátek vztahu

## <a name="return-value"></a>Návratová hodnota

Pokud mohutnost pro končí 1, návratová hodnota bude `Ref<T>`. Pokud mohutnost, která má končit, je n, návratová hodnota bude `Collection<Ref<T>>`.

## <a name="remarks"></a>Poznámky

Relace jsou konstrukce první třídy v model EDM (Entity Data Model) (EDM). Vztahy lze navázat mezi dvěma nebo více typy entit a uživatelé mohou procházet relaci z jednoho elementu end (entity) na jiný. `from`a `to` jsou podmíněně nepovinné, pokud v rámci vztahu nedochází k nejednoznačnosti v překladu názvů.

NAVIGACE je platná v prostoru O a C.

Obecná forma pro navigační konstrukce je následující:

Navigate (`instance-expression`, `relationship-type`, [ `to-end` [, `from-end` ]])

Příklad:

```sql
Select o.Id, navigate(o, OrderCustomer, Customer, Order)
From LOB.Orders as o
```

Kde OrderCustomer je `relationship`, a zákazník a objednávka `to-end` jsou (zákazník) a `from-end` (objednávka) vztahu. Pokud byl OrderCustomer relace typu n:1, pak je výsledným typem výrazu Navigate odkaz\<Customer >.

Jednodušší tvar tohoto výrazu je následující:

```sql
Select o.Id, navigate(o, OrderCustomer)
From LOB.Orders as o
```

Podobně v dotazu následujícího formuláře by výraz Navigate vytvořil kolekci < ref\<> >.

```sql
Select c.Id, navigate(c, OrderCustomer, Order, Customer)
From LOB.Customers as c
```

Výrazem instance musí být typ entity nebo ref.

## <a name="example"></a>Příklad

Následující Entity SQL dotaz používá operátor navigace k přechodu mezi vztahem vytvořeným mezi typy entit adresa a SalesOrderHeader. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:

1. Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.

2. Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:

 [!code-csharp[DP EntityServices Concepts 2#NAVIGATE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#navigate)]

## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
- [Postupy: Navigace v relacích pomocí operátoru navigace](navigate-entity-sql.md)
