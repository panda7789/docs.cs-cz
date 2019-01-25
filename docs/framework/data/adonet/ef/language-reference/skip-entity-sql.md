---
title: Přeskočit (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: 467329f74304b64c7fc7ada2920751aba744f76e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54637635"
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
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Dotazování v [to](https://msdn.microsoft.com/library/bb738702\(v=vs.100\).aspx#_ESQL) příklad používá operátor klauzule ORDER BY s PŘESKOČENÍM k určení pořadí řazení použít u objektů vrácených v příkazu SELECT.  
  
## <a name="see-also"></a>Viz také:
- [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- [Postupy: Stránkovat výsledky dotazu](https://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)
- [Stránkování](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)
- [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
