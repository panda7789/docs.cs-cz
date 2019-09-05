---
title: V (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
ms.openlocfilehash: 5a07ee79d5452da4341d391fae7c997c33b603a2
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250664"
---
# <a name="in-entity-sql"></a>V (Entity SQL)
Určuje, zda hodnota odpovídá jakékoli hodnotě v kolekci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a>Arguments  
 `value`  
 Libovolný platný výraz, který vrací hodnotu, která se má shodovat.  
  
 MĚNÍ  
 Určuje, že `Boolean` výsledek z má být negace.  
  
 `expression`  
 Libovolný platný výraz, který vrátí kolekci pro otestování shody. Všechny výrazy musí být stejného typu nebo společného základního nebo odvozeného typu jako `value`.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`Pokud je hodnota v kolekci nalezena; hodnota null, pokud má hodnotu null nebo je kolekce null; v opačném případě. `false` Použití operátoru NOT v negaci výsledků v.  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá operátor IN k určení, zda hodnota odpovídá jakékoli hodnotě v kolekci. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:  
  
 [!code-csharp[DP EntityServices Concepts 2#IN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#in)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
