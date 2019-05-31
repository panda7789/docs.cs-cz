---
title: ':: – operátor - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 0b456ed3ce9965ef389d8ce40167afa4ac33da18
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422521"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="bc964-102">:: – operátor (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="bc964-102">:: operator (C# Reference)</span></span>

<span data-ttu-id="bc964-103">Kvalifikátor aliasu oboru názvů (`::`) slouží k vyhledání identifikátory.</span><span class="sxs-lookup"><span data-stu-id="bc964-103">The namespace alias qualifier (`::`) is used to look up identifiers.</span></span> <span data-ttu-id="bc964-104">Vždy je umístěný mezi dva identifikátory, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="bc964-104">It is always positioned between two identifiers, as in this example:</span></span>

[!code-csharp[csRefOperators#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#27)]

<span data-ttu-id="bc964-105">`::` Operátor můžete použít také s *alias direktiva using*:</span><span class="sxs-lookup"><span data-stu-id="bc964-105">The `::` operator can also be used with a *using alias directive*:</span></span>

```csharp
// using Col=System.Collections.Generic;
var numbers = new Col::List<int> { 1, 2, 3 };
```

## <a name="remarks"></a><span data-ttu-id="bc964-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bc964-106">Remarks</span></span>

<span data-ttu-id="bc964-107">Kvalifikátor aliasu oboru názvů může být `global`.</span><span class="sxs-lookup"><span data-stu-id="bc964-107">The namespace alias qualifier can be `global`.</span></span> <span data-ttu-id="bc964-108">Tím se spustí vyhledávání v globálním oboru názvů, ne obor názvů služby alias.</span><span class="sxs-lookup"><span data-stu-id="bc964-108">This invokes a lookup in the global namespace, rather than an aliased namespace.</span></span>

## <a name="for-more-information"></a><span data-ttu-id="bc964-109">Další informace</span><span class="sxs-lookup"><span data-stu-id="bc964-109">For more information</span></span>

<span data-ttu-id="bc964-110">Příklad použití `::` operátoru, najdete v následující části:</span><span class="sxs-lookup"><span data-stu-id="bc964-110">For an example of how to use the `::` operator, see the following section:</span></span>

- [<span data-ttu-id="bc964-111">Postupy: Použití aliasu globálního Namespace</span><span class="sxs-lookup"><span data-stu-id="bc964-111">How to: Use the Global Namespace Alias</span></span>](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)

## <a name="c-language-specification"></a><span data-ttu-id="bc964-112">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bc964-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="bc964-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bc964-113">See also</span></span>

- [<span data-ttu-id="bc964-114">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bc964-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="bc964-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="bc964-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="bc964-116">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bc964-116">C# operators</span></span>](index.md)
- [<span data-ttu-id="bc964-117">. – operátor</span><span class="sxs-lookup"><span data-stu-id="bc964-117">. operator</span></span>](member-access-operators.md#member-access-operator-)
- [<span data-ttu-id="bc964-118">extern alias</span><span class="sxs-lookup"><span data-stu-id="bc964-118">extern alias</span></span>](../keywords/extern-alias.md)
