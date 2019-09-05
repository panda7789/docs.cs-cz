---
title: Výrazy inicializace
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98daef1f-15d4-483e-985c-d78ea3abe8c8
ms.openlocfilehash: 109be8ef2bf41326fcab5896ecdc359859683345
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250674"
---
# <a name="initialization-expressions"></a><span data-ttu-id="ed352-102">Výrazy inicializace</span><span class="sxs-lookup"><span data-stu-id="ed352-102">Initialization Expressions</span></span>
<span data-ttu-id="ed352-103">Inicializační výraz inicializuje nový objekt.</span><span class="sxs-lookup"><span data-stu-id="ed352-103">An initialization expression initializes a new object.</span></span> <span data-ttu-id="ed352-104">Většina inicializačních výrazů je podporovaná, včetně C# většiny nových Visual Basicch inicializačních výrazů 3,0 a 9,0.</span><span class="sxs-lookup"><span data-stu-id="ed352-104">Most initialization expressions are supported, including most new C# 3.0 and Visual Basic 9.0 initialization expressions.</span></span> <span data-ttu-id="ed352-105">Následující typy lze inicializovat a vracet LINQ to Entitiesm dotazem:</span><span class="sxs-lookup"><span data-stu-id="ed352-105">The following types can be initialized and returned by a LINQ to Entities query:</span></span>  
  
- <span data-ttu-id="ed352-106">Kolekce nula nebo více typových objektů entit nebo projekce komplexních typů, které jsou definovány v koncepčním modelu.</span><span class="sxs-lookup"><span data-stu-id="ed352-106">A collection of zero or more typed entity objects or a projection of complex types that are defined in the conceptual model.</span></span>  
  
- <span data-ttu-id="ed352-107">Typy CLR podporované [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ed352-107">CLR types supported by the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span>  
  
- <span data-ttu-id="ed352-108">Vložené kolekce.</span><span class="sxs-lookup"><span data-stu-id="ed352-108">Inline collections.</span></span>  
  
- <span data-ttu-id="ed352-109">Anonymní typy.</span><span class="sxs-lookup"><span data-stu-id="ed352-109">Anonymous types.</span></span>  
  
 <span data-ttu-id="ed352-110">V následujícím příkladu se v syntaxi výrazu dotazu zobrazuje příklad inicializace anonymního typu:</span><span class="sxs-lookup"><span data-stu-id="ed352-110">Anonymous type initialization is shown in the following example in query expression syntax:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization)]  
  
 <span data-ttu-id="ed352-111">Následující příklad v syntaxi dotazu založeného na metodách ukazuje inicializaci anonymního typu:</span><span class="sxs-lookup"><span data-stu-id="ed352-111">The following example in method-based query syntax shows anonymous type initialization:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization_mq)]  
  
 <span data-ttu-id="ed352-112">Podporuje se i uživatelsky definovaná inicializace třídy.</span><span class="sxs-lookup"><span data-stu-id="ed352-112">User-defined class initialization is also supported.</span></span> <span data-ttu-id="ed352-113">Inicializační C# vzor 3,0 a Visual Basic 9,0 je podporován a předpokládá, že metoda getter a setter vlastnosti je symetrická.</span><span class="sxs-lookup"><span data-stu-id="ed352-113">The C# 3.0 and Visual Basic 9.0 initialization pattern is supported and assumes that the property getter and setter are symmetric.</span></span> <span data-ttu-id="ed352-114">Následující příklad v syntaxi výrazu dotazu ukazuje vlastní třídu, která je inicializována v dotazu:</span><span class="sxs-lookup"><span data-stu-id="ed352-114">The following example in query expression syntax shows a custom class being initialized in the query:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myorder)]
 [!code-vb[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myorder)]  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization)]  
  
 <span data-ttu-id="ed352-115">Následující příklad syntaxe dotazu založeného na metodách zobrazuje vlastní třídu, která je inicializována v dotazu:</span><span class="sxs-lookup"><span data-stu-id="ed352-115">The following example in method-based query syntax shows a custom class being initialized in the query:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="ed352-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ed352-116">See also</span></span>

- [<span data-ttu-id="ed352-117">Výrazy v dotazech LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="ed352-117">Expressions in LINQ to Entities Queries</span></span>](expressions-in-linq-to-entities-queries.md)
