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
ms.openlocfilehash: c494e8dbb18f44ce5520b21800a21d3feb03da59
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025071"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="5f45e-102">:: – operátor (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="5f45e-102">:: operator (C# reference)</span></span>

<span data-ttu-id="5f45e-103">Kvalifikátor aliasu oboru názvů (`::`) slouží k vyhledání identifikátory.</span><span class="sxs-lookup"><span data-stu-id="5f45e-103">The namespace alias qualifier (`::`) is used to look up identifiers.</span></span> <span data-ttu-id="5f45e-104">Vždy je umístěný mezi dva identifikátory, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="5f45e-104">It is always positioned between two identifiers, as in this example:</span></span>

[!code-csharp[csRefOperators#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#27)]

<span data-ttu-id="5f45e-105">`::` Operátor můžete použít také s *alias direktiva using*:</span><span class="sxs-lookup"><span data-stu-id="5f45e-105">The `::` operator can also be used with a *using alias directive*:</span></span>

```csharp
// using Col=System.Collections.Generic;
var numbers = new Col::List<int> { 1, 2, 3 };
```

## <a name="remarks"></a><span data-ttu-id="5f45e-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5f45e-106">Remarks</span></span>

<span data-ttu-id="5f45e-107">Kvalifikátor aliasu oboru názvů může být `global`.</span><span class="sxs-lookup"><span data-stu-id="5f45e-107">The namespace alias qualifier can be `global`.</span></span> <span data-ttu-id="5f45e-108">Tím se spustí vyhledávání v globálním oboru názvů, ne obor názvů služby alias.</span><span class="sxs-lookup"><span data-stu-id="5f45e-108">This invokes a lookup in the global namespace, rather than an aliased namespace.</span></span>

## <a name="for-more-information"></a><span data-ttu-id="5f45e-109">Další informace</span><span class="sxs-lookup"><span data-stu-id="5f45e-109">For more information</span></span>

<span data-ttu-id="5f45e-110">Příklad použití `::` operátoru, najdete v následující části:</span><span class="sxs-lookup"><span data-stu-id="5f45e-110">For an example of how to use the `::` operator, see the following section:</span></span>

- [<span data-ttu-id="5f45e-111">Postupy: Použití aliasu globálního Namespace</span><span class="sxs-lookup"><span data-stu-id="5f45e-111">How to: Use the Global Namespace Alias</span></span>](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)

## <a name="c-language-specification"></a><span data-ttu-id="5f45e-112">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5f45e-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="5f45e-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5f45e-113">See also</span></span>

- [<span data-ttu-id="5f45e-114">C#referenční dokumentace</span><span class="sxs-lookup"><span data-stu-id="5f45e-114">C# reference</span></span>](../index.md)
- [<span data-ttu-id="5f45e-115">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5f45e-115">C# operators</span></span>](index.md)
- [<span data-ttu-id="5f45e-116">. – operátor</span><span class="sxs-lookup"><span data-stu-id="5f45e-116">. operator</span></span>](member-access-operators.md#member-access-operator-)
- [<span data-ttu-id="5f45e-117">extern alias</span><span class="sxs-lookup"><span data-stu-id="5f45e-117">extern alias</span></span>](../keywords/extern-alias.md)
