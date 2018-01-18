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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 328284ce07a0361dbfd25b0d765000b497156ff7
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="constant-expressions"></a><span data-ttu-id="4dda8-102">Výrazy konstant</span><span class="sxs-lookup"><span data-stu-id="4dda8-102">Constant Expressions</span></span>
<span data-ttu-id="4dda8-103">Konstantní výraz se skládá z konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4dda8-103">A constant expression consists of a constant value.</span></span> <span data-ttu-id="4dda8-104">Konstantní hodnoty jsou přímo převést na příkaz konstantní výrazy stromu, bez překladu na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="4dda8-104">Constant values are directly converted to constant command tree expressions, without any translation on the client.</span></span> <span data-ttu-id="4dda8-105">To zahrnuje výrazy, jejichž výsledkem konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4dda8-105">This includes expressions that result in a constant value.</span></span> <span data-ttu-id="4dda8-106">Chování zdroje dat by měl být tedy, že pro všechny výrazy zahrnující konstanty.</span><span class="sxs-lookup"><span data-stu-id="4dda8-106">Therefore, data source behavior should be expected for all expressions involving constants.</span></span> <span data-ttu-id="4dda8-107">To může mít za následek chování, které se liší od chování CLR.</span><span class="sxs-lookup"><span data-stu-id="4dda8-107">This can result in behavior that differs from CLR behavior.</span></span>  
  
 <span data-ttu-id="4dda8-108">Následující příklad ukazuje konstantní výraz, který se vyhodnotí na serveru.</span><span class="sxs-lookup"><span data-stu-id="4dda8-108">The following example shows a constant expression that is evaluated on the server.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]<span data-ttu-id="4dda8-109">nepodporuje použití třídy uživatele jako konstanta.</span><span class="sxs-lookup"><span data-stu-id="4dda8-109"> does not support using a user class as a constant.</span></span> <span data-ttu-id="4dda8-110">Však odkaz na vlastnost třídy uživatel se považuje za konstantu a budou převést na strom příkaz konstantní výraz a ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="4dda8-110">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dda8-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="4dda8-111">See Also</span></span>  
 [<span data-ttu-id="4dda8-112">Výrazy v dotazech LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="4dda8-112">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
