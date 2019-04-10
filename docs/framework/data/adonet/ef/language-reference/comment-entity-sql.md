---
title: --(Komentář) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5d9de735-2099-47f1-b7e7-60856f494924
ms.openlocfilehash: c10b17931c6024e2a9e947083747435d8aa54fa2
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59339512"
---
# <a name="---comment-entity-sql"></a><span data-ttu-id="7730f-102">--(Komentář) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="7730f-102">-- (Comment) (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="7730f-103">dotazy můžou obsahovat komentáře.</span><span class="sxs-lookup"><span data-stu-id="7730f-103">queries can contain comments.</span></span> <span data-ttu-id="7730f-104">Dvě pomlčky (`--`) spusťte řádek komentáře.</span><span class="sxs-lookup"><span data-stu-id="7730f-104">Two dashes (`--`) start a comment line.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7730f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7730f-105">Syntax</span></span>  
  
```  
-- text_of_comment  
```  
  
## <a name="arguments"></a><span data-ttu-id="7730f-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="7730f-106">Arguments</span></span>  
 `text_of_comment`  
 <span data-ttu-id="7730f-107">Je řetězec znaků, který obsahuje text komentáře.</span><span class="sxs-lookup"><span data-stu-id="7730f-107">Is the character string that contains the text of the comment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7730f-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="7730f-108">Example</span></span>  
 <span data-ttu-id="7730f-109">Následující dotaz Entity SQL ukazuje, jak využít komentáře.</span><span class="sxs-lookup"><span data-stu-id="7730f-109">The following Entity SQL query demonstrates how to use comments.</span></span> <span data-ttu-id="7730f-110">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="7730f-110">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="7730f-111">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="7730f-111">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="7730f-112">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="7730f-112">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="7730f-113">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="7730f-113">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a><span data-ttu-id="7730f-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7730f-114">See also</span></span>

- [<span data-ttu-id="7730f-115">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="7730f-115">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="7730f-116">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="7730f-116">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
