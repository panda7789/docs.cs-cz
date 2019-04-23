---
title: Výrazy konstant
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
ms.openlocfilehash: 10c74ede8d490bf96a9d0855889669bdc2628b01
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59209200"
---
# <a name="constant-expressions"></a><span data-ttu-id="25e85-102">Výrazy konstant</span><span class="sxs-lookup"><span data-stu-id="25e85-102">Constant Expressions</span></span>
<span data-ttu-id="25e85-103">Konstantní výraz se skládá z konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="25e85-103">A constant expression consists of a constant value.</span></span> <span data-ttu-id="25e85-104">Konstantní hodnoty jsou přímo převést na strom výrazů konstantní příkazový, bez překladu na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="25e85-104">Constant values are directly converted to constant command tree expressions, without any translation on the client.</span></span> <span data-ttu-id="25e85-105">To zahrnuje výrazy, jejichž výsledkem konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="25e85-105">This includes expressions that result in a constant value.</span></span> <span data-ttu-id="25e85-106">Proto by měl očekávat chování zdroje dat pro všechny výrazy zahrnující konstanty.</span><span class="sxs-lookup"><span data-stu-id="25e85-106">Therefore, data source behavior should be expected for all expressions involving constants.</span></span> <span data-ttu-id="25e85-107">Výsledkem může být chování, které se liší od chování modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="25e85-107">This can result in behavior that differs from CLR behavior.</span></span>  
  
 <span data-ttu-id="25e85-108">Následující příklad ukazuje konstantní výraz, který je vyhodnocován na serveru.</span><span class="sxs-lookup"><span data-stu-id="25e85-108">The following example shows a constant expression that is evaluated on the server.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] <span data-ttu-id="25e85-109">nepodporuje použití třídy uživatelů jako konstanta.</span><span class="sxs-lookup"><span data-stu-id="25e85-109">does not support using a user class as a constant.</span></span> <span data-ttu-id="25e85-110">Však odkaz na vlastnost ve třídě uživatele je považován za konstantu a bude převeden na příkaz konstantní výraz stromu a ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="25e85-110">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25e85-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="25e85-111">See also</span></span>

- [<span data-ttu-id="25e85-112">Výrazy v dotazech LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="25e85-112">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
