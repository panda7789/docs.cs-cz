---
title: LIMIT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
ms.openlocfilehash: 432dfe2c8b2b87daf885be6de4da9bbeaaa37638
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250448"
---
# <a name="limit-entity-sql"></a>LIMIT (Entity SQL)
Fyzické stránkování lze provést pomocí dílčí klauzule LIMIT v klauzuli ORDER BY. LIMIT nelze použít odděleně od klauzule ORDER BY.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a>Arguments  
 `n`  
 Počet položek, které budou vybrány.  
  
 Pokud je dílčí klauzule výrazu omezení přítomna v klauzuli ORDER BY, dotaz se seřadí podle specifikace řazení a výsledný počet řádků bude omezen výrazem LIMIT. Například omezení 5 omezí výsledek sady výsledků na 5 instancí nebo řádků. LIMIT je funkčně ekvivalentní k hodnotě TOP s výjimkou, která omezuje omezení vyžaduje, aby klauzule ORDER BY byla k dispozici. Klauzuli SKIP a LIMIT lze použít nezávisle spolu s klauzulí ORDER BY.  
  
> [!NOTE]
> Dotaz Entity SQL se považuje za neplatný, pokud je ve stejném výrazu dotazu přítomný modifikátor TOP a SKIP – dílčí klauzule. Dotaz by měl být přepsán změnou výrazu TOP na výraz omezení.  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá operátor ORDER BY s LIMITem k určení pořadí řazení používaného u objektů vrácených v příkazu SELECT. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:  
  
 [!code-csharp[DP EntityServices Concepts 2#LIMIT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#limit)]  
  
## <a name="see-also"></a>Viz také:

- [ORDER BY](order-by-entity-sql.md)
- [Postupy: Stránka prostřednictvím výsledků dotazu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))
- [Stránkování](paging-entity-sql.md)
- [TOP](top-entity-sql.md)
