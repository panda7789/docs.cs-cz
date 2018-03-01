---
title: ":: – operátor (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6b4f1683e1250ed745e15ced88203ca942c75ff8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="f98dd-102">:: – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="f98dd-102">:: Operator (C# Reference)</span></span>
<span data-ttu-id="f98dd-103">Kvalifikátor alias oboru názvů (`::`) se používá k vyhledání identifikátory.</span><span class="sxs-lookup"><span data-stu-id="f98dd-103">The namespace alias qualifier (`::`) is used to look up identifiers.</span></span> <span data-ttu-id="f98dd-104">Vždy je umístěný mezi dva identifikátory, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f98dd-104">It is always positioned between two identifiers, as in this example:</span></span>  
  
 [!code-csharp[csRefOperators#27](../../../csharp/language-reference/operators/codesnippet/CSharp/namespace-alias-qualifer_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="f98dd-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f98dd-105">Remarks</span></span>  
 <span data-ttu-id="f98dd-106">Kvalifikátor alias oboru názvů lze `global`.</span><span class="sxs-lookup"><span data-stu-id="f98dd-106">The namespace alias qualifier can be `global`.</span></span> <span data-ttu-id="f98dd-107">Tím se spustí vyhledávání v globálním oboru názvů, nikoli na obor názvů alias.</span><span class="sxs-lookup"><span data-stu-id="f98dd-107">This invokes a lookup in the global namespace, rather than an aliased namespace.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="f98dd-108">Další informace</span><span class="sxs-lookup"><span data-stu-id="f98dd-108">For More Information</span></span>  
 <span data-ttu-id="f98dd-109">Příklad použití `::` operátor, najdete v následující části:</span><span class="sxs-lookup"><span data-stu-id="f98dd-109">For an example of how to use the `::` operator, see the following section:</span></span>  
  
-   [<span data-ttu-id="f98dd-110">Postupy: použití aliasu globálního Namespace</span><span class="sxs-lookup"><span data-stu-id="f98dd-110">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="f98dd-111">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f98dd-111">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f98dd-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="f98dd-112">See Also</span></span>  
 [<span data-ttu-id="f98dd-113">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f98dd-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f98dd-114">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="f98dd-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f98dd-115">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f98dd-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="f98dd-116">Namespace klíčová slova</span><span class="sxs-lookup"><span data-stu-id="f98dd-116">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="f98dd-117">. Operátor</span><span class="sxs-lookup"><span data-stu-id="f98dd-117">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)  
 [<span data-ttu-id="f98dd-118">externí alias</span><span class="sxs-lookup"><span data-stu-id="f98dd-118">extern alias</span></span>](../../../csharp/language-reference/keywords/extern-alias.md)
