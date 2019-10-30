---
title: --(Komentář) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5d9de735-2099-47f1-b7e7-60856f494924
ms.openlocfilehash: 43b8cdbf5dbca8822645c27711f6984b8d741ea7
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040276"
---
# <a name="---comment-entity-sql"></a>--(Komentář) (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazy mohou obsahovat komentáře. Dvě pomlčky (`--`) spustí řádek komentáře.  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp  
-- text_of_comment  
```  
  
## <a name="arguments"></a>Arguments  
 `text_of_comment`  
 Je řetězec znaků, který obsahuje text komentáře.  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz ukazuje, jak používat komentáře. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled Entity SQL](entity-sql-overview.md)
- [Reference k Entity SQL](entity-sql-reference.md)
