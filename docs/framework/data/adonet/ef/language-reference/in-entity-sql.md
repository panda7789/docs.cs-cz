---
title: V (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
ms.openlocfilehash: e46db63600b6baa03697615a2f5eb9240f55d15e
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833696"
---
# <a name="in-entity-sql"></a>V (Entity SQL)
Určuje, zda hodnota odpovídá jakékoli hodnotě v kolekci.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a>Arguments  
 `value`  
 Libovolný platný výraz, který vrací hodnotu, která se má shodovat.  
  
 MĚNÍ  
 Určuje, že výsledkem operátoru `Boolean` je negace.  
  
 `expression`  
 Libovolný platný výraz, který vrátí kolekci pro otestování shody. Všechny výrazy musí být stejného typu nebo společného základního nebo odvozeného typu jako `value`.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`, pokud je hodnota v kolekci nalezena; hodnota null, pokud má hodnotu null nebo je kolekce null; v opačném případě `false`. Použití operátoru NOT v negaci výsledků v.  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá operátor IN k určení, zda hodnota odpovídá jakékoli hodnotě v kolekci. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#IN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#in)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
