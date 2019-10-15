---
title: LIMIT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
ms.openlocfilehash: 275b22686c6c932b2a9e4b20973ac07e99d47e14
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319619"
---
# <a name="limit-entity-sql"></a>LIMIT (Entity SQL)
Fyzické stránkování lze provést pomocí dílčí klauzule LIMIT v klauzuli ORDER BY. LIMIT nelze použít odděleně od klauzule ORDER BY.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
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
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#LIMIT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#limit)]  
  
## <a name="see-also"></a>Viz také:

- [ORDER BY](order-by-entity-sql.md)
- [Postupy: stránka prostřednictvím výsledků dotazu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))
- [Stránkování](paging-entity-sql.md)
- [TOP](top-entity-sql.md)
