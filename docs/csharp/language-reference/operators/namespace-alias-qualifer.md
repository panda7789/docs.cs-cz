---
title: ':: Operator - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 2e456be075f3487676228244e0119ff46ed9a538
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243475"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="441fc-102">:: – Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="441fc-102">:: Operator (C# Reference)</span></span>
<span data-ttu-id="441fc-103">Kvalifikátor aliasu oboru názvů (`::`) slouží k vyhledání identifikátory.</span><span class="sxs-lookup"><span data-stu-id="441fc-103">The namespace alias qualifier (`::`) is used to look up identifiers.</span></span> <span data-ttu-id="441fc-104">Vždy je umístěný mezi dva identifikátory, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="441fc-104">It is always positioned between two identifiers, as in this example:</span></span>  
  
 [!code-csharp[csRefOperators#27](../../../csharp/language-reference/operators/codesnippet/CSharp/namespace-alias-qualifer_1.cs)]  

<span data-ttu-id="441fc-105">`::` Operátor můžete použít také s *alias direktiva using*:</span><span class="sxs-lookup"><span data-stu-id="441fc-105">The `::` operator can also be used with a *using alias directive*:</span></span>

```csharp
// using Col=System.Collections.Generic;
var numbers = new Col::List<int> { 1, 2, 3 };
```

## <a name="remarks"></a><span data-ttu-id="441fc-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="441fc-106">Remarks</span></span>  
 <span data-ttu-id="441fc-107">Kvalifikátor aliasu oboru názvů může být `global`.</span><span class="sxs-lookup"><span data-stu-id="441fc-107">The namespace alias qualifier can be `global`.</span></span> <span data-ttu-id="441fc-108">Tím se spustí vyhledávání v globálním oboru názvů, ne obor názvů služby alias.</span><span class="sxs-lookup"><span data-stu-id="441fc-108">This invokes a lookup in the global namespace, rather than an aliased namespace.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="441fc-109">Další informace</span><span class="sxs-lookup"><span data-stu-id="441fc-109">For More Information</span></span>  
 <span data-ttu-id="441fc-110">Příklad použití `::` operátoru, najdete v následující části:</span><span class="sxs-lookup"><span data-stu-id="441fc-110">For an example of how to use the `::` operator, see the following section:</span></span>  
  
-   [<span data-ttu-id="441fc-111">Postupy: Použití aliasu globálního Namespace</span><span class="sxs-lookup"><span data-stu-id="441fc-111">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="441fc-112">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="441fc-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="441fc-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="441fc-113">See Also</span></span>

- [<span data-ttu-id="441fc-114">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="441fc-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="441fc-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="441fc-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="441fc-116">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="441fc-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="441fc-117">Klíčová slova oboru názvů</span><span class="sxs-lookup"><span data-stu-id="441fc-117">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
- [<span data-ttu-id="441fc-118">. – operátor</span><span class="sxs-lookup"><span data-stu-id="441fc-118">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)  
- [<span data-ttu-id="441fc-119">extern alias</span><span class="sxs-lookup"><span data-stu-id="441fc-119">extern alias</span></span>](../../../csharp/language-reference/keywords/extern-alias.md)
