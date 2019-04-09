---
title: --(Komentář) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5d9de735-2099-47f1-b7e7-60856f494924
ms.openlocfilehash: 40a0ee8f6bc2cf8fae5779ecb3d103c77dde161b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137173"
---
# <a name="---comment-entity-sql"></a><span data-ttu-id="218fb-102">--(Komentář) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="218fb-102">-- (Comment) (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="218fb-103">dotazy můžou obsahovat komentáře.</span><span class="sxs-lookup"><span data-stu-id="218fb-103">queries can contain comments.</span></span> <span data-ttu-id="218fb-104">Dvě pomlčky (`--`) spusťte řádek komentáře.</span><span class="sxs-lookup"><span data-stu-id="218fb-104">Two dashes (`--`) start a comment line.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="218fb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="218fb-105">Syntax</span></span>  
  
```  
-- text_of_comment  
```  
  
## <a name="arguments"></a><span data-ttu-id="218fb-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="218fb-106">Arguments</span></span>  
 `text_of_comment`  
 <span data-ttu-id="218fb-107">Je řetězec znaků, který obsahuje text komentáře.</span><span class="sxs-lookup"><span data-stu-id="218fb-107">Is the character string that contains the text of the comment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="218fb-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="218fb-108">Example</span></span>  
 <span data-ttu-id="218fb-109">Následující dotaz Entity SQL ukazuje, jak využít komentáře.</span><span class="sxs-lookup"><span data-stu-id="218fb-109">The following Entity SQL query demonstrates how to use comments.</span></span> <span data-ttu-id="218fb-110">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="218fb-110">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="218fb-111">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="218fb-111">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="218fb-112">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="218fb-112">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="218fb-113">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="218fb-113">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a><span data-ttu-id="218fb-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="218fb-114">See also</span></span>

- [<span data-ttu-id="218fb-115">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="218fb-115">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="218fb-116">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="218fb-116">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
