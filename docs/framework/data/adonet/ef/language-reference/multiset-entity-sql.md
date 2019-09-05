---
title: MULTISET (Entity SQL)
ms.date: 03/30/2017
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
ms.openlocfilehash: 8e02d2d3171c9f08333ecef7ee22e65100bdf822
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250096"
---
# <a name="multiset-entity-sql"></a>MULTISET (Entity SQL)
Vytvoří instanci multiset ze seznamu hodnot. Všechny hodnoty v konstruktoru MULTISET musí být kompatibilního typu `T`. Prázdné konstruktory multiset nejsou povoleny.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
MULTISET ( expression [{, expression }] )  
or  
{ expression [{, expression }] }  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný seznam hodnot.  
  
## <a name="return-value"></a>Návratová hodnota  
 Kolekce typu MULTISET\<T >.  
  
## <a name="remarks"></a>Poznámky  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]poskytuje tři druhy konstruktorů: konstruktory řádků, konstruktory objektů a konstruktory multiset (nebo Collection). Další informace naleznete v tématu [sestavování typů](constructing-types-entity-sql.md).  
  
 Konstruktor multiset vytvoří instanci multiset ze seznamu hodnot. Všechny hodnoty v konstruktoru musí být kompatibilního typu.  
  
 Například následující výraz vytvoří multiset celých čísel.  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
> Vnořené literály multiset jsou podporovány pouze v případě, že multiset zalamování má jeden prvek multiset; například `{{1, 2, 3}}`. Pokud má multiset zalamování více prvků multiset (například `{{1, 2}, {3, 4}}`), vnořené literály multiset nejsou podporovány.  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá operátor MULTISET k vytvoření instance MULTISET ze seznamu hodnot. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTISET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiset)]  
  
## <a name="see-also"></a>Viz také:

- [Vytváření typů](constructing-types-entity-sql.md)
- [Reference k Entity SQL](entity-sql-reference.md)
