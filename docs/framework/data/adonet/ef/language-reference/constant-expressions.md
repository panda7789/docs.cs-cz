---
title: Výrazy konstant
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
ms.openlocfilehash: b31cd881f1307ec734c026d3c873d7a650e19a20
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251135"
---
# <a name="constant-expressions"></a><span data-ttu-id="d5422-102">Výrazy konstant</span><span class="sxs-lookup"><span data-stu-id="d5422-102">Constant Expressions</span></span>
<span data-ttu-id="d5422-103">Konstantní výraz se skládá z konstantní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d5422-103">A constant expression consists of a constant value.</span></span> <span data-ttu-id="d5422-104">Konstantní hodnoty jsou přímo převedeny na konstantní výrazy stromu příkazů bez jakéhokoli překladu na klienta.</span><span class="sxs-lookup"><span data-stu-id="d5422-104">Constant values are directly converted to constant command tree expressions, without any translation on the client.</span></span> <span data-ttu-id="d5422-105">To zahrnuje výrazy, které mají za následek konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d5422-105">This includes expressions that result in a constant value.</span></span> <span data-ttu-id="d5422-106">Proto by mělo být očekávané chování zdroje dat pro všechny výrazy, které obsahují konstanty.</span><span class="sxs-lookup"><span data-stu-id="d5422-106">Therefore, data source behavior should be expected for all expressions involving constants.</span></span> <span data-ttu-id="d5422-107">To může mít za následek chování, které se liší od chování CLR.</span><span class="sxs-lookup"><span data-stu-id="d5422-107">This can result in behavior that differs from CLR behavior.</span></span>  
  
 <span data-ttu-id="d5422-108">Následující příklad ukazuje konstantní výraz, který je vyhodnocen na serveru.</span><span class="sxs-lookup"><span data-stu-id="d5422-108">The following example shows a constant expression that is evaluated on the server.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 <span data-ttu-id="d5422-109">LINQ to Entities nepodporuje použití třídy uživatele jako konstanty.</span><span class="sxs-lookup"><span data-stu-id="d5422-109">LINQ to Entities does not support using a user class as a constant.</span></span> <span data-ttu-id="d5422-110">Odkaz na vlastnost třídy uživatele se však považuje za konstantu a bude převeden na výraz konstantního stromu příkazů a proveden ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="d5422-110">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5422-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d5422-111">See also</span></span>

- [<span data-ttu-id="d5422-112">Výrazy v dotazech LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="d5422-112">Expressions in LINQ to Entities Queries</span></span>](expressions-in-linq-to-entities-queries.md)
