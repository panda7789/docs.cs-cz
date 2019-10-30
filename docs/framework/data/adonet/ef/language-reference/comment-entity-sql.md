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
# <a name="---comment-entity-sql"></a><span data-ttu-id="7b114-102">--(Komentář) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="7b114-102">-- (Comment) (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="7b114-103">dotazy mohou obsahovat komentáře.</span><span class="sxs-lookup"><span data-stu-id="7b114-103">queries can contain comments.</span></span> <span data-ttu-id="7b114-104">Dvě pomlčky (`--`) spustí řádek komentáře.</span><span class="sxs-lookup"><span data-stu-id="7b114-104">Two dashes (`--`) start a comment line.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b114-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b114-105">Syntax</span></span>  
  
```csharp  
-- text_of_comment  
```  
  
## <a name="arguments"></a><span data-ttu-id="7b114-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="7b114-106">Arguments</span></span>  
 `text_of_comment`  
 <span data-ttu-id="7b114-107">Je řetězec znaků, který obsahuje text komentáře.</span><span class="sxs-lookup"><span data-stu-id="7b114-107">Is the character string that contains the text of the comment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b114-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="7b114-108">Example</span></span>  
 <span data-ttu-id="7b114-109">Následující Entity SQL dotaz ukazuje, jak používat komentáře.</span><span class="sxs-lookup"><span data-stu-id="7b114-109">The following Entity SQL query demonstrates how to use comments.</span></span> <span data-ttu-id="7b114-110">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="7b114-110">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="7b114-111">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="7b114-111">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="7b114-112">Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="7b114-112">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="7b114-113">Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="7b114-113">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a><span data-ttu-id="7b114-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7b114-114">See also</span></span>

- [<span data-ttu-id="7b114-115">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="7b114-115">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="7b114-116">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="7b114-116">Entity SQL Reference</span></span>](entity-sql-reference.md)
