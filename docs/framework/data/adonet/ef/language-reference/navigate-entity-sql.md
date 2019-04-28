---
title: NAVIGATE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
ms.openlocfilehash: 993c07b824d30c89773c5cfea90c7c194c6b3869
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760412"
---
# <a name="navigate-entity-sql"></a>NAVIGATE (Entity SQL)

Přejde přes vztahu mezi entitami.

## <a name="syntax"></a>Syntaxe

```
navigate(instance-expression, [relationship-type], [to-end [, from-end] ])
```

## <a name="arguments"></a>Arguments

`instance-expression` Instance entity.

`relationship-type` Název typu relace ze souboru Konceptuální schéma definici jazyka (CSDL). `relationship-type` Je kvalifikovány jako \<oboru názvů >.\< Název typu vztahu >.

`to` Konci vztahu.

`from` Začátek relace.

## <a name="return-value"></a>Návratová hodnota

Pokud Kardinalita do konce je 1, bude návratovou hodnotou `Ref<T>`. Pokud se Kardinalita ukončení je n, bude návratovou hodnotou `Collection<Ref<T>>`.

## <a name="remarks"></a>Poznámky

Relace jsou prvotřídní konstrukce v [!INCLUDE[adonet_edm](../../../../../../includes/adonet-edm-md.md)] (EDM). Vztah lze navázat mezi dva nebo více typů entit a uživatelé mohou přejít přes vztah konce (entita). `from` a `to` jsou podmíněně volitelné, pokud nedochází k nejednoznačnosti v překlad v rámci relace.

NAVIGOVAT je platný v prostoru O a C.

Obecný tvar konstrukci navigace je následující:

přejděte (`instance-expression`, `relationship-type`, [ `to-end` [, `from-end` ]])

Příklad:

```sql
Select o.Id, navigate(o, OrderCustomer, Customer, Order)
From LOB.Orders as o
```

Kde je OrderCustomer `relationship`, a odběratele a objednávky `to-end` (zákazníka) a `from-end` (pořadí) vztahu. Pokud byl OrderCustomer relaci n: 1, je výsledný typ výraz navigate Ref\<zákazníků >.

Jednodušší formu tento výraz je následující:

```sql
Select o.Id, navigate(o, OrderCustomer)
From LOB.Orders as o
```

Podobně v dotazu má následující formu, výraz navigate byste mohli vytvořit kolekci < Ref\<pořadí >>.

```sql
Select c.Id, navigate(c, OrderCustomer, Order, Customer)
From LOB.Customers as c
```

Výraz instance musí být typu entity nebo ref.

## <a name="example"></a>Příklad

Následující dotaz Entity SQL používá operátor NAVIGOVAT přejít přes vztahu mezi adresu a SalesOrderHeader typy entit. Dotaz je založen na modelu Sales AdventureWorks. Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:

1. Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).

2. Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:

 [!code-csharp[DP EntityServices Concepts 2#NAVIGATE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#navigate)]

## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Postupy: Procházení relací pomocí navigačního operátoru](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)
