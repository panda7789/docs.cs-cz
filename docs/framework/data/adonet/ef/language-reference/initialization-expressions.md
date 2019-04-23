---
title: Výrazy inicializace
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98daef1f-15d4-483e-985c-d78ea3abe8c8
ms.openlocfilehash: 6f6f27eaecd760e565eeb98a286252981d6df0bb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129139"
---
# <a name="initialization-expressions"></a><span data-ttu-id="1e00f-102">Výrazy inicializace</span><span class="sxs-lookup"><span data-stu-id="1e00f-102">Initialization Expressions</span></span>
<span data-ttu-id="1e00f-103">Výraz inicializace inicializuje nový objekt.</span><span class="sxs-lookup"><span data-stu-id="1e00f-103">An initialization expression initializes a new object.</span></span> <span data-ttu-id="1e00f-104">Většina výrazy inicializace jsou podporované. zahrnuje to nové C# 3.0 a výrazy jazyka Visual Basic 9.0 inicializace.</span><span class="sxs-lookup"><span data-stu-id="1e00f-104">Most initialization expressions are supported, including most new C# 3.0 and Visual Basic 9.0 initialization expressions.</span></span> <span data-ttu-id="1e00f-105">Následující typy lze inicializovat a vrácené LINQ dotazu entity:</span><span class="sxs-lookup"><span data-stu-id="1e00f-105">The following types can be initialized and returned by a LINQ to Entities query:</span></span>  
  
-   <span data-ttu-id="1e00f-106">Kolekce nulu nebo více objektů zadané entity nebo projekce komplexní typy, které jsou definované v konceptuálním modelu.</span><span class="sxs-lookup"><span data-stu-id="1e00f-106">A collection of zero or more typed entity objects or a projection of complex types that are defined in the conceptual model.</span></span>  
  
-   <span data-ttu-id="1e00f-107">Typy CLR nepodporuje [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1e00f-107">CLR types supported by the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span>  
  
-   <span data-ttu-id="1e00f-108">Vložené kolekce.</span><span class="sxs-lookup"><span data-stu-id="1e00f-108">Inline collections.</span></span>  
  
-   <span data-ttu-id="1e00f-109">Anonymní typy.</span><span class="sxs-lookup"><span data-stu-id="1e00f-109">Anonymous types.</span></span>  
  
 <span data-ttu-id="1e00f-110">Inicializace anonymního typu můžete vidět v následujícím příkladu v syntaxi výrazů dotazů:</span><span class="sxs-lookup"><span data-stu-id="1e00f-110">Anonymous type initialization is shown in the following example in query expression syntax:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization)]  
  
 <span data-ttu-id="1e00f-111">Následující příklad v syntaxi dotazů založených na volání metody ukazuje inicializaci anonymního typu:</span><span class="sxs-lookup"><span data-stu-id="1e00f-111">The following example in method-based query syntax shows anonymous type initialization:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization_mq)]  
  
 <span data-ttu-id="1e00f-112">Inicializace uživatelsky definované třídy, je také podporována.</span><span class="sxs-lookup"><span data-stu-id="1e00f-112">User-defined class initialization is also supported.</span></span> <span data-ttu-id="1e00f-113">C# 3.0 a Visual Basic 9.0 inicializace vzor je podporován a předpokládá, že vlastnost getter a setter jsou symetrické.</span><span class="sxs-lookup"><span data-stu-id="1e00f-113">The C# 3.0 and Visual Basic 9.0 initialization pattern is supported and assumes that the property getter and setter are symmetric.</span></span> <span data-ttu-id="1e00f-114">Následující příklad v syntaxe výrazu dotazu ukazuje vlastní třídu během inicializace v dotazu:</span><span class="sxs-lookup"><span data-stu-id="1e00f-114">The following example in query expression syntax shows a custom class being initialized in the query:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myorder)]
 [!code-vb[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myorder)]  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization)]  
  
 <span data-ttu-id="1e00f-115">Následující příklad v syntaxi dotazů založených na volání metody ukazuje vlastní třídu během inicializace v dotazu:</span><span class="sxs-lookup"><span data-stu-id="1e00f-115">The following example in method-based query syntax shows a custom class being initialized in the query:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="1e00f-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1e00f-116">See also</span></span>

- [<span data-ttu-id="1e00f-117">Výrazy v dotazech LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="1e00f-117">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
