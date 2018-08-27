---
title: ':: – operátor (Referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 480ed224d1994dac926dfc78d59e227c8d1e8f36
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42934992"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="522bf-102">:: – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="522bf-102">:: Operator (C# Reference)</span></span>
<span data-ttu-id="522bf-103">Kvalifikátor aliasu oboru názvů (`::`) slouží k vyhledání identifikátory.</span><span class="sxs-lookup"><span data-stu-id="522bf-103">The namespace alias qualifier (`::`) is used to look up identifiers.</span></span> <span data-ttu-id="522bf-104">Vždy je umístěný mezi dva identifikátory, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="522bf-104">It is always positioned between two identifiers, as in this example:</span></span>  
  
 [!code-csharp[csRefOperators#27](../../../csharp/language-reference/operators/codesnippet/CSharp/namespace-alias-qualifer_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="522bf-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="522bf-105">Remarks</span></span>  
 <span data-ttu-id="522bf-106">Kvalifikátor aliasu oboru názvů může být `global`.</span><span class="sxs-lookup"><span data-stu-id="522bf-106">The namespace alias qualifier can be `global`.</span></span> <span data-ttu-id="522bf-107">Tím se spustí vyhledávání v globálním oboru názvů, ne obor názvů služby alias.</span><span class="sxs-lookup"><span data-stu-id="522bf-107">This invokes a lookup in the global namespace, rather than an aliased namespace.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="522bf-108">Další informace</span><span class="sxs-lookup"><span data-stu-id="522bf-108">For More Information</span></span>  
 <span data-ttu-id="522bf-109">Příklad použití `::` operátoru, najdete v následující části:</span><span class="sxs-lookup"><span data-stu-id="522bf-109">For an example of how to use the `::` operator, see the following section:</span></span>  
  
-   [<span data-ttu-id="522bf-110">Postupy: Použití aliasu globálního oboru názvů</span><span class="sxs-lookup"><span data-stu-id="522bf-110">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="522bf-111">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="522bf-111">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="522bf-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="522bf-112">See Also</span></span>

- [<span data-ttu-id="522bf-113">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="522bf-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="522bf-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="522bf-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="522bf-115">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="522bf-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="522bf-116">Klíčová slova oboru názvů</span><span class="sxs-lookup"><span data-stu-id="522bf-116">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
- [<span data-ttu-id="522bf-117">. – operátor</span><span class="sxs-lookup"><span data-stu-id="522bf-117">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)  
- [<span data-ttu-id="522bf-118">extern alias</span><span class="sxs-lookup"><span data-stu-id="522bf-118">extern alias</span></span>](../../../csharp/language-reference/keywords/extern-alias.md)
