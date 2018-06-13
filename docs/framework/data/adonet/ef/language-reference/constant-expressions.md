---
title: Výrazy konstant
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
ms.openlocfilehash: 616f297c261c4309dc0db7a4efe2fcad8cc00966
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32762514"
---
# <a name="constant-expressions"></a><span data-ttu-id="0cce3-102">Výrazy konstant</span><span class="sxs-lookup"><span data-stu-id="0cce3-102">Constant Expressions</span></span>
<span data-ttu-id="0cce3-103">Konstantní výraz se skládá z konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0cce3-103">A constant expression consists of a constant value.</span></span> <span data-ttu-id="0cce3-104">Konstantní hodnoty jsou přímo převést na příkaz konstantní výrazy stromu, bez překladu na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="0cce3-104">Constant values are directly converted to constant command tree expressions, without any translation on the client.</span></span> <span data-ttu-id="0cce3-105">To zahrnuje výrazy, jejichž výsledkem konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0cce3-105">This includes expressions that result in a constant value.</span></span> <span data-ttu-id="0cce3-106">Chování zdroje dat by měl být tedy, že pro všechny výrazy zahrnující konstanty.</span><span class="sxs-lookup"><span data-stu-id="0cce3-106">Therefore, data source behavior should be expected for all expressions involving constants.</span></span> <span data-ttu-id="0cce3-107">To může mít za následek chování, které se liší od chování CLR.</span><span class="sxs-lookup"><span data-stu-id="0cce3-107">This can result in behavior that differs from CLR behavior.</span></span>  
  
 <span data-ttu-id="0cce3-108">Následující příklad ukazuje konstantní výraz, který se vyhodnotí na serveru.</span><span class="sxs-lookup"><span data-stu-id="0cce3-108">The following example shows a constant expression that is evaluated on the server.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]<span data-ttu-id="0cce3-109"> nepodporuje použití třídy uživatele jako konstanta.</span><span class="sxs-lookup"><span data-stu-id="0cce3-109"> does not support using a user class as a constant.</span></span> <span data-ttu-id="0cce3-110">Však odkaz na vlastnost třídy uživatel se považuje za konstantu a budou převést na strom příkaz konstantní výraz a ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="0cce3-110">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cce3-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="0cce3-111">See Also</span></span>  
 [<span data-ttu-id="0cce3-112">Výrazy v dotazech LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="0cce3-112">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
