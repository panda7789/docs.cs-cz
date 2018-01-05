---
title: "Inicializace výrazy"
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
ms.assetid: 98daef1f-15d4-483e-985c-d78ea3abe8c8
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f04d487f032bb8a5f36f3bd7d77ee3e7be480e27
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="initialization-expressions"></a><span data-ttu-id="5da30-102">Inicializace výrazy</span><span class="sxs-lookup"><span data-stu-id="5da30-102">Initialization Expressions</span></span>
<span data-ttu-id="5da30-103">Výraz inicializace inicializuje nový objekt.</span><span class="sxs-lookup"><span data-stu-id="5da30-103">An initialization expression initializes a new object.</span></span> <span data-ttu-id="5da30-104">Většina inicializace výrazy jsou podporovány, včetně většina nových C# 3.0 a Visual Basic 9.0 inicializace výrazů.</span><span class="sxs-lookup"><span data-stu-id="5da30-104">Most initialization expressions are supported, including most new C# 3.0 and Visual Basic 9.0 initialization expressions.</span></span> <span data-ttu-id="5da30-105">Následující typy můžete inicializovat a vrácený LINQ entity dotazu:</span><span class="sxs-lookup"><span data-stu-id="5da30-105">The following types can be initialized and returned by a LINQ to Entities query:</span></span>  
  
-   <span data-ttu-id="5da30-106">Kolekce nula nebo více objektů zadané entity nebo projekci komplexních typů, které jsou definované v konceptuálním modelu.</span><span class="sxs-lookup"><span data-stu-id="5da30-106">A collection of zero or more typed entity objects or a projection of complex types that are defined in the conceptual model.</span></span>  
  
-   <span data-ttu-id="5da30-107">Typy CLR nepodporuje [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5da30-107">CLR types supported by the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span>  
  
-   <span data-ttu-id="5da30-108">Vložené kolekce.</span><span class="sxs-lookup"><span data-stu-id="5da30-108">Inline collections.</span></span>  
  
-   <span data-ttu-id="5da30-109">Anonymní typy.</span><span class="sxs-lookup"><span data-stu-id="5da30-109">Anonymous types.</span></span>  
  
 <span data-ttu-id="5da30-110">Inicializace anonymní typ je znázorněno v následujícím příkladu v syntaxe výrazu dotazu:</span><span class="sxs-lookup"><span data-stu-id="5da30-110">Anonymous type initialization is shown in the following example in query expression syntax:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization)]  
  
 <span data-ttu-id="5da30-111">Následující příklad v syntaxi dotazu na základě metod ukazuje inicializace anonymní typ:</span><span class="sxs-lookup"><span data-stu-id="5da30-111">The following example in method-based query syntax shows anonymous type initialization:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization_mq)]  
  
 <span data-ttu-id="5da30-112">Inicializace uživatelsky definované třídy, je také podporována.</span><span class="sxs-lookup"><span data-stu-id="5da30-112">User-defined class initialization is also supported.</span></span> <span data-ttu-id="5da30-113">Inicializace vzor C# 3.0 a Visual Basic 9.0 je podporována a předpokládá, že se symetrické vlastnost getter a setter.</span><span class="sxs-lookup"><span data-stu-id="5da30-113">The C# 3.0 and Visual Basic 9.0 initialization pattern is supported and assumes that the property getter and setter are symmetric.</span></span> <span data-ttu-id="5da30-114">Následující příklad v syntaxe výrazu dotazu ukazuje vlastní třídu inicializován v dotazu:</span><span class="sxs-lookup"><span data-stu-id="5da30-114">The following example in query expression syntax shows a custom class being initialized in the query:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myorder)]
 [!code-vb[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myorder)]  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization)]  
  
 <span data-ttu-id="5da30-115">V syntaxi dotazu na základě metod následující příklad ukazuje třídu vlastní inicializaci v dotazu:</span><span class="sxs-lookup"><span data-stu-id="5da30-115">The following example in method-based query syntax shows a custom class being initialized in the query:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="5da30-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="5da30-116">See Also</span></span>  
 [<span data-ttu-id="5da30-117">Výrazy v dotazech LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="5da30-117">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
