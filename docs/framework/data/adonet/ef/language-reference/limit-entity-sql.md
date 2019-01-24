---
title: LIMIT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
ms.openlocfilehash: 3c38fd3fc20ad19bdeeca5c02c25de6c8269def6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54493817"
---
# <a name="limit-entity-sql"></a>LIMIT (Entity SQL)
Fyzické stránkování lze provést pomocí dílčí klauzuli LIMIT v klauzuli ORDER by. OMEZENÍ nemůže být použita samostatně z klauzule ORDER by.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a>Arguments  
 `n`  
 Počet položek, které bude vybrána.  
  
 Pokud dílčí klauzuli LIMIT výrazu je přítomna v klauzuli ORDER BY, dotazu budou seřazeny podle specifikace řazení a výsledný počet řádků se omezí výrazu omezení. LIMIT 5, omezí výsledek nastavena na 5 instancí nebo řádků. LIMIT je funkčně srovnatelný s nejvyšší s tím rozdílem, že LIMIT vyžaduje klauzuli ORDER by nacházet. Přeskočit a LIMIT je možné nezávisle na sobě spolu s klauzulí ORDER BY.  
  
> [!NOTE]
>  Dotazu Entity Sql se budou považovat za modifikátor neplatný, pokud je to hlavní a dílčí klauzuli SKIP je k dispozici ve stejném výrazu dotazu. Dotaz by měl být přepsán změnou výraz TOP na LIMITU výrazu.  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá operátor klauzule ORDER BY s LIMITEM k určení pořadí řazení použít u objektů vrácených v příkazu SELECT. Dotaz je založen na modelu Sales AdventureWorks. Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:  
  
1.  Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#LIMIT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#limit)]  
  
## <a name="see-also"></a>Viz také:
- [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- [Postupy: Stránkovat výsledky dotazu](https://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)
- [Stránkování](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)
- [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
