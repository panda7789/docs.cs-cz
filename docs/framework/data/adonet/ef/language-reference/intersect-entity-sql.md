---
title: Průsečík (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 93c6fe33-f341-4b52-911e-adf503891951
ms.openlocfilehash: a943de89de37d00cc2a643b443da7ef1fd3380b9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250602"
---
# <a name="intersect-entity-sql"></a>Průsečík (Entity SQL)
Vrátí kolekci všech jedinečných hodnot, které jsou vráceny výrazy dotazu na levé a pravé straně operandu INTERSECT. Všechny výrazy musí být stejného typu nebo společného základního nebo odvozeného typu jako `expression`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression INTERSECT expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz dotazu, který vrátí kolekci pro porovnání s kolekcí vrácenou z jiného výrazu dotazu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Kolekce stejného typu nebo společného základního nebo odvozeného typu jako `expression`.  
  
## <a name="remarks"></a>Poznámky  
 Průsečík je jeden ze [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sad operátorů. Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátory set jsou vyhodnocovány zleva doprava. Informace o prioritách pro [!INCLUDE[esql](../../../../../../includes/esql-md.md)] množinové operátory naleznete v tématu [Except](except-entity-sql.md).  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz pomocí operátoru INTERSECT vrátí kolekci všech jedinečných hodnot, které jsou vráceny výrazy dotazu na levé a pravé straně operandu INTERSECT. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:  
  
 [!code-csharp[DP EntityServices Concepts 2#INTERSECT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#intersect)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
