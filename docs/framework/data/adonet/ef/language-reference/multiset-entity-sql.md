---
title: MULTISET (Entity SQL)
ms.date: 03/30/2017
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
ms.openlocfilehash: eb676feeb168e1fb184f3869a18e138bff34211b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929344"
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
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]poskytuje tři druhy konstruktorů: konstruktory řádků, konstruktory objektů a konstruktory multiset (nebo Collection). Další informace naleznete v tématu [sestavování typů](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).  
  
 Konstruktor multiset vytvoří instanci multiset ze seznamu hodnot. Všechny hodnoty v konstruktoru musí být kompatibilního typu.  
  
 Například následující výraz vytvoří multiset celých čísel.  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
> Vnořené literály multiset jsou podporovány pouze v případě, že multiset zalamování má jeden prvek multiset; například `{{1, 2, 3}}`. Pokud má multiset zalamování více prvků multiset (například `{{1, 2}, {3, 4}}`), vnořené literály multiset nejsou podporovány.  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá operátor MULTISET k vytvoření instance MULTISET ze seznamu hodnot. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTISET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiset)]  
  
## <a name="see-also"></a>Viz také:

- [Vytváření typů](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)
- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
