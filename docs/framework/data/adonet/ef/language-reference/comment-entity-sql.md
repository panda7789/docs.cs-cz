---
title: "--(Komentář) (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5d9de735-2099-47f1-b7e7-60856f494924
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 483e1c69aea94375983acd840f84512de54bc746
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="---comment-entity-sql"></a><span data-ttu-id="cc64c-102">--(Komentář) (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="cc64c-102">-- (Comment) (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cc64c-103">dotazy může obsahovat komentáře.</span><span class="sxs-lookup"><span data-stu-id="cc64c-103"> queries can contain comments.</span></span> <span data-ttu-id="cc64c-104">Dvě pomlčky (`--`) spustit řádek poznámky.</span><span class="sxs-lookup"><span data-stu-id="cc64c-104">Two dashes (`--`) start a comment line.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc64c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc64c-105">Syntax</span></span>  
  
```  
-- text_of_comment  
```  
  
## <a name="arguments"></a><span data-ttu-id="cc64c-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="cc64c-106">Arguments</span></span>  
 `text_of_comment`  
 <span data-ttu-id="cc64c-107">Je řetězec znaků, který obsahuje text poznámky.</span><span class="sxs-lookup"><span data-stu-id="cc64c-107">Is the character string that contains the text of the comment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc64c-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="cc64c-108">Example</span></span>  
 <span data-ttu-id="cc64c-109">Následující dotaz Entity SQL demonstruje použití komentáře.</span><span class="sxs-lookup"><span data-stu-id="cc64c-109">The following Entity SQL query demonstrates how to use comments.</span></span> <span data-ttu-id="cc64c-110">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="cc64c-110">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="cc64c-111">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="cc64c-111">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="cc64c-112">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="cc64c-112">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="cc64c-113">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="cc64c-113">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a><span data-ttu-id="cc64c-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="cc64c-114">See Also</span></span>  
 [<span data-ttu-id="cc64c-115">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="cc64c-115">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="cc64c-116">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="cc64c-116">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
