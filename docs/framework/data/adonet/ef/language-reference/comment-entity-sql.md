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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1ed1c70687b1a4aec542aff5046b237fa4710fa4
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="---comment-entity-sql"></a><span data-ttu-id="375b9-102">--(Komentář) (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="375b9-102">-- (Comment) (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="375b9-103">dotazy může obsahovat komentáře.</span><span class="sxs-lookup"><span data-stu-id="375b9-103"> queries can contain comments.</span></span> <span data-ttu-id="375b9-104">Dvě pomlčky (`--`) spustit řádek poznámky.</span><span class="sxs-lookup"><span data-stu-id="375b9-104">Two dashes (`--`) start a comment line.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="375b9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="375b9-105">Syntax</span></span>  
  
```  
-- text_of_comment  
```  
  
## <a name="arguments"></a><span data-ttu-id="375b9-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="375b9-106">Arguments</span></span>  
 `text_of_comment`  
 <span data-ttu-id="375b9-107">Je řetězec znaků, který obsahuje text poznámky.</span><span class="sxs-lookup"><span data-stu-id="375b9-107">Is the character string that contains the text of the comment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="375b9-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="375b9-108">Example</span></span>  
 <span data-ttu-id="375b9-109">Následující dotaz Entity SQL demonstruje použití komentáře.</span><span class="sxs-lookup"><span data-stu-id="375b9-109">The following Entity SQL query demonstrates how to use comments.</span></span> <span data-ttu-id="375b9-110">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="375b9-110">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="375b9-111">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="375b9-111">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="375b9-112">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="375b9-112">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="375b9-113">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="375b9-113">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a><span data-ttu-id="375b9-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="375b9-114">See Also</span></span>  
 [<span data-ttu-id="375b9-115">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="375b9-115">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="375b9-116">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="375b9-116">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
