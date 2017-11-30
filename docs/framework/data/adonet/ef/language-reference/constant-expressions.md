---
title: "Výrazy konstant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 759805b2970aa760e4bce882789efbc947303573
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="constant-expressions"></a><span data-ttu-id="bb986-102">Výrazy konstant</span><span class="sxs-lookup"><span data-stu-id="bb986-102">Constant Expressions</span></span>
<span data-ttu-id="bb986-103">Konstantní výraz se skládá z konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bb986-103">A constant expression consists of a constant value.</span></span> <span data-ttu-id="bb986-104">Konstantní hodnoty jsou přímo převést na příkaz konstantní výrazy stromu, bez překladu na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="bb986-104">Constant values are directly converted to constant command tree expressions, without any translation on the client.</span></span> <span data-ttu-id="bb986-105">To zahrnuje výrazy, jejichž výsledkem konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bb986-105">This includes expressions that result in a constant value.</span></span> <span data-ttu-id="bb986-106">Chování zdroje dat by měl být tedy, že pro všechny výrazy zahrnující konstanty.</span><span class="sxs-lookup"><span data-stu-id="bb986-106">Therefore, data source behavior should be expected for all expressions involving constants.</span></span> <span data-ttu-id="bb986-107">To může mít za následek chování, které se liší od chování CLR.</span><span class="sxs-lookup"><span data-stu-id="bb986-107">This can result in behavior that differs from CLR behavior.</span></span>  
  
 <span data-ttu-id="bb986-108">Následující příklad ukazuje konstantní výraz, který se vyhodnotí na serveru.</span><span class="sxs-lookup"><span data-stu-id="bb986-108">The following example shows a constant expression that is evaluated on the server.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]<span data-ttu-id="bb986-109">nepodporuje použití třídy uživatele jako konstanta.</span><span class="sxs-lookup"><span data-stu-id="bb986-109"> does not support using a user class as a constant.</span></span> <span data-ttu-id="bb986-110">Však odkaz na vlastnost třídy uživatel se považuje za konstantu a budou převést na strom příkaz konstantní výraz a ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="bb986-110">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb986-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="bb986-111">See Also</span></span>  
 [<span data-ttu-id="bb986-112">Výrazy v technologii LINQ to Entities dotazy</span><span class="sxs-lookup"><span data-stu-id="bb986-112">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
