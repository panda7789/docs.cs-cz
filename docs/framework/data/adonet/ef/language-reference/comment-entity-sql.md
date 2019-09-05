---
title: --(Komentář) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5d9de735-2099-47f1-b7e7-60856f494924
ms.openlocfilehash: 1ea1929b0e6f965f71fbb015ee6795affb3bce7c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251210"
---
# <a name="---comment-entity-sql"></a><span data-ttu-id="85bae-102">--(Komentář) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="85bae-102">-- (Comment) (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="85bae-103">dotazy můžou obsahovat komentáře.</span><span class="sxs-lookup"><span data-stu-id="85bae-103">queries can contain comments.</span></span> <span data-ttu-id="85bae-104">Dvě pomlčky (`--`) spustí řádek komentáře.</span><span class="sxs-lookup"><span data-stu-id="85bae-104">Two dashes (`--`) start a comment line.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85bae-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85bae-105">Syntax</span></span>  
  
```  
-- text_of_comment  
```  
  
## <a name="arguments"></a><span data-ttu-id="85bae-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="85bae-106">Arguments</span></span>  
 `text_of_comment`  
 <span data-ttu-id="85bae-107">Je řetězec znaků, který obsahuje text komentáře.</span><span class="sxs-lookup"><span data-stu-id="85bae-107">Is the character string that contains the text of the comment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85bae-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="85bae-108">Example</span></span>  
 <span data-ttu-id="85bae-109">Následující Entity SQL dotaz ukazuje, jak používat komentáře.</span><span class="sxs-lookup"><span data-stu-id="85bae-109">The following Entity SQL query demonstrates how to use comments.</span></span> <span data-ttu-id="85bae-110">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="85bae-110">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="85bae-111">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="85bae-111">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="85bae-112">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="85bae-112">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="85bae-113">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="85bae-113">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a><span data-ttu-id="85bae-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85bae-114">See also</span></span>

- [<span data-ttu-id="85bae-115">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="85bae-115">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="85bae-116">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="85bae-116">Entity SQL Reference</span></span>](entity-sql-reference.md)
