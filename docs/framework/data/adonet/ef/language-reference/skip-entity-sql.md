---
title: Přeskočit (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: 75140384823588b8f6785de00b0ab3cd17314a3f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319344"
---
# <a name="skip-entity-sql"></a>Přeskočit (Entity SQL)

Fyzické stránkování můžete provádět pomocí dílčí klauzule SKIP v klauzuli ORDER BY. Klauzuli SKIP nelze použít odděleně od klauzule ORDER BY.

## <a name="syntax"></a>Syntaxe

```sql
[ SKIP n ]
```

## <a name="arguments"></a>Arguments

`n` \
Počet položek, které se mají přeskočit

## <a name="remarks"></a>Poznámky

Pokud je v klauzuli ORDER BY přítomna dílčí klauzule SKIP Expression, výsledky se seřadí podle specifikace řazení a sada výsledků bude zahrnovat řádky začínající z dalšího řádku hned za výrazem SKIP. Například PŘESKOČENí 5 přeskočí prvních pět řádků a vrátí se z šestého řádku předá.

> [!NOTE]
> Dotaz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] je neplatný, je-li ve stejném výrazu dotazu přítomen jak modifikátor TOP, tak dílčí klauzule SKIP. Dotaz by měl být přepsán změnou HORNÍho výrazu na výraz LIMIT.

> [!NOTE]
> V SQL Server 2000 mohou vracet nesprávné výsledky pomocí příkazu přeskočit s řazením na jiné než klíčové sloupce. Pokud neklíčový sloupec obsahuje duplicitní data, může být vynecháno více než zadaný počet řádků. Je to kvůli tomu, jak je PŘESKOČENí přeloženo pro SQL Server 2000. Například v následujícím kódu může být vynecháno více než pět řádků, pokud `E.NonKeyColumn` má duplicitní hodnoty:
>
> ```sql
> SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L
> ```

Dotaz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] v tématu [Postupy: stránka prostřednictvím výsledků dotazu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) používá operátor ORDER by with Skip k určení pořadí řazení používaného u objektů vrácených v příkazu SELECT.

## <a name="see-also"></a>Viz také:

- [ORDER BY](order-by-entity-sql.md)
- [Postupy: stránka prostřednictvím výsledků dotazu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))
- [Stránkování](paging-entity-sql.md)
- [TOP](top-entity-sql.md)
