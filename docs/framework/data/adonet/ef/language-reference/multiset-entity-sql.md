---
title: MULTISET (Entity SQL)
ms.date: 03/30/2017
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
ms.openlocfilehash: 222be86db434b5d41c7b0536d271a3750b6afbe8
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319587"
---
# <a name="multiset-entity-sql"></a>MULTISET (Entity SQL)
Vytvoří instanci multiset ze seznamu hodnot. Všechny hodnoty v konstruktoru MULTISET musí být kompatibilního typu `T`. Prázdné konstruktory multiset nejsou povoleny.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
MULTISET ( expression [{, expression }] )  
-- or  
{ expression [{, expression }] }  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Libovolný platný seznam hodnot.  
  
## <a name="return-value"></a>Návratová hodnota  
 Kolekce typu MULTISET\<T >.  
  
## <a name="remarks"></a>Poznámky  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] poskytuje tři druhy konstruktorů: konstruktory řádků, konstruktory objektů a konstruktory multiset (nebo Collection). Další informace naleznete v tématu [sestavování typů](constructing-types-entity-sql.md).  
  
 Konstruktor multiset vytvoří instanci multiset ze seznamu hodnot. Všechny hodnoty v konstruktoru musí být kompatibilního typu.  
  
 Například následující výraz vytvoří multiset celých čísel.  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
> Vnořené literály multiset jsou podporovány pouze v případě, že multiset zalamování má jeden prvek multiset; například `{{1, 2, 3}}`. Pokud má multiset zalamování více prvků multiset (například `{{1, 2}, {3, 4}}`), vnořené literály multiset nejsou podporovány.  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá operátor MULTISET k vytvoření instance MULTISET ze seznamu hodnot. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#MULTISET](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#multiset)]  
  
## <a name="see-also"></a>Viz také:

- [Vytváření typů](constructing-types-entity-sql.md)
- [Reference k Entity SQL](entity-sql-reference.md)
