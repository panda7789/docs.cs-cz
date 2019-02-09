---
title: Přeskočit (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: b17f73f97d32f151ed4f51b025c0c5a7a97393bb
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2019
ms.locfileid: "55904179"
---
# <a name="skip-entity-sql"></a>Přeskočit (Entity SQL)
Fyzické stránkování můžete provádět pomocí dílčí klauzuli SKIP v klauzuli ORDER by. SKIP nelze použít samostatně z klauzule ORDER BY.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ SKIP n ]  
```  
  
## <a name="arguments"></a>Arguments  
 `n`  
 Počet položek pro přeskočení.  
  
## <a name="remarks"></a>Poznámky  
 Pokud výraz dílčí klauzuli SKIP je přítomna v klauzuli ORDER BY, výsledky budou seřazeny podle specifikace řazení a sada výsledků zahrne řádky začínající od na další řádek hned po výrazu SKIP. Například přeskočit 5 přeskočte prvních pět řádků, který se vrátí z řádku šestého vpřed.  
  
> [!NOTE]
>  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Dotaz není platný, pokud modifikátorem hlavní a dílčí klauzuli SKIP jsou k dispozici ve stejném výrazu dotazu. Dotaz by měl být přepsán změnou výraz TOP na výrazu omezení.  
  
> [!NOTE]
>  V [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)], pomocí přeskočit s klauzulí ORDER BY v neklíčových sloupců může vrátit nesprávné výsledky. Větší než zadaný počet řádků se možná přeskočí, pokud neklíčový sloupec v sobě obsahuje duplicitní data. Je to kvůli jak SKIP je přeložen pro [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)]. Například v následujícím kódu více než pět řádků se možná přeskočí, pokud `E.NonKeyColumn` obsahují duplicitní hodnoty:  
>   
>  `SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L`  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Dotazování v [jak: Stránka přes výsledky dotazu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) používá operátor klauzule ORDER BY s PŘESKOČENÍM k určení pořadí řazení použít u objektů vrácených v příkazu SELECT.  
  
## <a name="see-also"></a>Viz také:
- [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- [Postupy: Stránkovat výsledky dotazu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))
- [Stránkování](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)
- [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
