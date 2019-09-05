---
title: Přeskočit (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: 19d3001fb8f226b02f16167dfb51ce1caa80ba3b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249224"
---
# <a name="skip-entity-sql"></a>Přeskočit (Entity SQL)

Fyzické stránkování můžete provádět pomocí dílčí klauzule SKIP v klauzuli ORDER BY. Klauzuli SKIP nelze použít odděleně od klauzule ORDER BY.

## <a name="syntax"></a>Syntaxe

```
[ SKIP n ]
```

## <a name="arguments"></a>Arguments

`n` \
Počet položek, které se mají přeskočit

## <a name="remarks"></a>Poznámky

Pokud je v klauzuli ORDER BY přítomna dílčí klauzule SKIP Expression, výsledky se seřadí podle specifikace řazení a sada výsledků bude zahrnovat řádky začínající z dalšího řádku hned za výrazem SKIP. Například PŘESKOČENí 5 přeskočí prvních pět řádků a vrátí se z šestého řádku předá.

> [!NOTE]
> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Dotaz je neplatný, pokud je ve stejném výrazu dotazu přítomen modifikátor Top a dílčí klauzule Skip. Dotaz by měl být přepsán změnou HORNÍho výrazu na výraz LIMIT.

> [!NOTE]
> V SQL Server 2000 mohou vracet nesprávné výsledky pomocí příkazu přeskočit s řazením na jiné než klíčové sloupce. Pokud neklíčový sloupec obsahuje duplicitní data, může být vynecháno více než zadaný počet řádků. Je to kvůli tomu, jak je PŘESKOČENí přeloženo pro SQL Server 2000. Například v následujícím kódu může být vynecháno více než pět řádků, pokud `E.NonKeyColumn` má duplicitní hodnoty:
>
> `SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L`

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Dotaz na[postupy: Stránka prostřednictvím výsledků](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) dotazu používá operátor ORDER by s skipem k určení pořadí řazení používaného u objektů vrácených v příkazu SELECT.

## <a name="see-also"></a>Viz také:

- [ORDER BY](order-by-entity-sql.md)
- [Postupy: Stránka prostřednictvím výsledků dotazu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))
- [Stránkování](paging-entity-sql.md)
- [TOP](top-entity-sql.md)
