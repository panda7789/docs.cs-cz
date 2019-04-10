---
title: EXISTUJE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d28ead43-4afb-4bdc-af64-efd2e05005d7
ms.openlocfilehash: 72d96c5f24fcedf870370de3792680831145a454
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59311133"
---
# <a name="exists-entity-sql"></a>EXISTUJE (Entity SQL)
Určuje, zda je kolekce prázdná.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[NOT] EXISTS ( expression )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz, který vrátí kolekci.  
  
 NOT  
 Určuje, že bude výsledek EXISTS negovat.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` Pokud kolekce není prázdná. v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 EXISTS je jedním z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] množinové operátory. Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sadu operátorů jsou vyhodnocovány zleva doprava. Priorita informace pro [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nastavit operátory, naleznete v tématu [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá operátor EXISTS k určení, zda kolekce je prázdná. Dotaz je založen na modelu Sales AdventureWorks. Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:  
  
1. Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#EXISTS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#exists)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
