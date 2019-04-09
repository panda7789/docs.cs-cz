---
title: MULTISET (Entity SQL)
ms.date: 03/30/2017
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
ms.openlocfilehash: d4293b8e027f7f0f7eabac7ad9c8a9852ddd3a80
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178474"
---
# <a name="multiset-entity-sql"></a>MULTISET (Entity SQL)
Vytvoří instanci multisady ze seznamu hodnot. Všechny hodnoty v konstruktor MULTISET musí být kompatibilní `T`. Multiset – prázdný konstruktory nejsou povolené.  
  
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
 Kolekce typu MULTIMNOŽINA\<T >.  
  
## <a name="remarks"></a>Poznámky  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nabízí tři druhy konstruktory: řádek konstruktory, konstruktory objektu a konstruktory multiset (nebo kolekce). Další informace najdete v tématu [vytváření typů](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).  
  
 Konstruktor multiset vytvoří instanci multisady ze seznamu hodnot. Všechny hodnoty v konstruktoru musí být kompatibilní.  
  
 Například následující výraz vytvoří multiset celých čísel.  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
>  Multiset – vnořené literály jsou podporovány pouze při zabalení multiset má jeden prvek multiset –; například `{{1, 2, 3}}`. Pokud multiset zabalení má více elementů multiset – (například `{{1, 2}, {3, 4}}`), vnořené multiset – literály nejsou podporovány.  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá operátor MULTISET k vytvoření instance multisady ze seznamu hodnot. Dotaz je založen na modelu Sales AdventureWorks. Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:  
  
1.  Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTISET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiset)]  
  
## <a name="see-also"></a>Viz také:

- [Vytváření typů](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)
- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
