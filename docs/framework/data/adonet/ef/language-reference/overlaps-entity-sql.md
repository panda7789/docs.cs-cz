---
title: PŘEKRYVy (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41743e89-79cb-4d7b-8a27-355b45024b61
ms.openlocfilehash: fef90beebf1c2723c767eaf5155542ad40d5fcb8
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249725"
---
# <a name="overlaps-entity-sql"></a>PŘEKRYVy (Entity SQL)
Určuje, zda dvě kolekce mají společné prvky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression OVERLAPS expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz dotazu, který vrátí kolekci pro porovnání s kolekcí vrácenou z jiného výrazu dotazu. Všechny výrazy musí být stejného typu nebo společného základního nebo odvozeného typu jako `expression`.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`Pokud mají dvě kolekce společné prvky; v opačném případě. `false`  
  
## <a name="remarks"></a>Poznámky  
 PŘEKRYVy poskytují funkčně ekvivalentní následujícímu:  
  
 `EXISTS ( expression INTERSECT expression )`  
  
 Překrytí je jedním z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] množinových operátorů. Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátory set jsou vyhodnocovány zleva doprava. Informace o prioritách pro [!INCLUDE[esql](../../../../../../includes/esql-md.md)] množinové operátory naleznete v tématu [Except](except-entity-sql.md).  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá operátor překrytí k určení, zda dvě kolekce mají společnou hodnotu. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Pro zkompilování a spuštění použijte následující postup:  
  
1. Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:  
  
 [!code-csharp[DP EntityServices Concepts 2#OVERLAPS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#overlaps)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
