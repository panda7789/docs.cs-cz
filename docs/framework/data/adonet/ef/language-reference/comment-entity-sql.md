---
title: --(Komentář) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5d9de735-2099-47f1-b7e7-60856f494924
ms.openlocfilehash: c10b17931c6024e2a9e947083747435d8aa54fa2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61605987"
---
# <a name="---comment-entity-sql"></a><span data-ttu-id="0749e-102">--(Komentář) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0749e-102">-- (Comment) (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="0749e-103">dotazy můžou obsahovat komentáře.</span><span class="sxs-lookup"><span data-stu-id="0749e-103">queries can contain comments.</span></span> <span data-ttu-id="0749e-104">Dvě pomlčky (`--`) spusťte řádek komentáře.</span><span class="sxs-lookup"><span data-stu-id="0749e-104">Two dashes (`--`) start a comment line.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0749e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0749e-105">Syntax</span></span>  
  
```  
-- text_of_comment  
```  
  
## <a name="arguments"></a><span data-ttu-id="0749e-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="0749e-106">Arguments</span></span>  
 `text_of_comment`  
 <span data-ttu-id="0749e-107">Je řetězec znaků, který obsahuje text komentáře.</span><span class="sxs-lookup"><span data-stu-id="0749e-107">Is the character string that contains the text of the comment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0749e-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="0749e-108">Example</span></span>  
 <span data-ttu-id="0749e-109">Následující dotaz Entity SQL ukazuje, jak využít komentáře.</span><span class="sxs-lookup"><span data-stu-id="0749e-109">The following Entity SQL query demonstrates how to use comments.</span></span> <span data-ttu-id="0749e-110">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="0749e-110">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0749e-111">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="0749e-111">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="0749e-112">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="0749e-112">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="0749e-113">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="0749e-113">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a><span data-ttu-id="0749e-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0749e-114">See also</span></span>

- [<span data-ttu-id="0749e-115">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="0749e-115">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="0749e-116">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="0749e-116">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
