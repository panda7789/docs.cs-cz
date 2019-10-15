---
title: NAVIGACE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
ms.openlocfilehash: 09128a367a02e1f9b206a9cc068987166c76381b
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319545"
---
# <a name="navigate-entity-sql"></a>NAVIGACE (Entity SQL)

Přejde přes vztah navázaný mezi entitami.

## <a name="syntax"></a>Syntaxe

```sql
navigate(instance-expression, [relationship-type], [to-end [, from-end] ])
```

## <a name="arguments"></a>Arguments

`instance-expression` instance entity.

`relationship-type` název typu relace ze souboru CSDL (konceptuální schéma Definition Language). @No__t-0 je kvalifikován jako \<namespace >. název typu \<relationship >.

`to` konci relace.

@no__t – 0 začátku relace.

## <a name="return-value"></a>Návratová hodnota

Pokud mohutnost pro končí 1, návratová hodnota bude `Ref<T>`. Pokud mohutnost, která má končit, je n, návratová hodnota bude `Collection<Ref<T>>`.

## <a name="remarks"></a>Poznámky

Relace jsou konstrukce první třídy v model EDM (Entity Data Model) (EDM). Vztahy lze navázat mezi dvěma nebo více typy entit a uživatelé mohou procházet relaci z jednoho elementu end (entity) na jiný. `from` a `to` jsou podmíněně volitelné, pokud v rámci vztahu nedochází k nejednoznačnosti v překladu názvů.

NAVIGACE je platná v prostoru O a C.

Obecná forma pro navigační konstrukce je následující:

Navigate (`instance-expression`, `relationship-type`, [`to-end` [, `from-end`]])

Příklad:

```sql
Select o.Id, navigate(o, OrderCustomer, Customer, Order)
From LOB.Orders as o
```

Kde OrderCustomer je `relationship` a zákazník a objednávka jsou `to-end` (zákazník) a `from-end` (objednávka) vztahu. Pokud OrderCustomer byl vztah n:1, pak je výsledný typ výrazu Navigate ref @ no__t-0Customer >.

Jednodušší tvar tohoto výrazu je následující:

```sql
Select o.Id, navigate(o, OrderCustomer)
From LOB.Orders as o
```

Podobně v dotazu následujícího formuláře by výraz Navigate vytvořil kolekci < ref @ no__t-0Order > >.

```sql
Select c.Id, navigate(c, OrderCustomer, Order, Customer)
From LOB.Customers as c
```

Výrazem instance musí být typ entity nebo ref.

## <a name="example"></a>Příklad

Následující Entity SQL dotaz používá operátor navigace k přechodu mezi vztahem vytvořeným mezi typy entit adresa a SalesOrderHeader. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:

1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).

2. Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:

 [!code-sql[DP EntityServices Concepts#NAVIGATE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#navigate)]

## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
- [Postupy: procházení vztahů pomocí operátoru navigace](navigate-entity-sql.md)
