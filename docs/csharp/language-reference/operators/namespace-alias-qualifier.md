---
title: ':: operator- C# reference'
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
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631134"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="40e65-102">:: – operátorC# (Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="40e65-102">:: operator (C# reference)</span></span>

<span data-ttu-id="40e65-103">Kvalifikátor aliasu oboru názvů (`::`) se používá k vyhledání identifikátorů.</span><span class="sxs-lookup"><span data-stu-id="40e65-103">The namespace alias qualifier (`::`) is used to look up identifiers.</span></span> <span data-ttu-id="40e65-104">Je vždy umístěn mezi dvěma identifikátory, jako v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="40e65-104">It is always positioned between two identifiers, as in this example:</span></span>

[!code-csharp[csRefOperators#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#27)]

<span data-ttu-id="40e65-105">Operátor lze také použít s *direktivou using alias:* `::`</span><span class="sxs-lookup"><span data-stu-id="40e65-105">The `::` operator can also be used with a *using alias directive*:</span></span>

```csharp
// using Col=System.Collections.Generic;
var numbers = new Col::List<int> { 1, 2, 3 };
```

## <a name="remarks"></a><span data-ttu-id="40e65-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="40e65-106">Remarks</span></span>

<span data-ttu-id="40e65-107">Kvalifikátor aliasu oboru názvů může být `global`.</span><span class="sxs-lookup"><span data-stu-id="40e65-107">The namespace alias qualifier can be `global`.</span></span> <span data-ttu-id="40e65-108">Tím se vyvolá vyhledávání v globálním oboru názvů, nikoli obor názvů s aliasem.</span><span class="sxs-lookup"><span data-stu-id="40e65-108">This invokes a lookup in the global namespace, rather than an aliased namespace.</span></span>

## <a name="for-more-information"></a><span data-ttu-id="40e65-109">Další informace</span><span class="sxs-lookup"><span data-stu-id="40e65-109">For more information</span></span>

<span data-ttu-id="40e65-110">Příklad použití `::` operátoru naleznete v následující části:</span><span class="sxs-lookup"><span data-stu-id="40e65-110">For an example of how to use the `::` operator, see the following section:</span></span>

- [<span data-ttu-id="40e65-111">Postupy: Použití aliasu globálního oboru názvů</span><span class="sxs-lookup"><span data-stu-id="40e65-111">How to: Use the Global Namespace Alias</span></span>](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)

## <a name="c-language-specification"></a><span data-ttu-id="40e65-112">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="40e65-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="40e65-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="40e65-113">See also</span></span>

- [<span data-ttu-id="40e65-114">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="40e65-114">C# reference</span></span>](../index.md)
- [<span data-ttu-id="40e65-115">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="40e65-115">C# operators</span></span>](index.md)
- [<span data-ttu-id="40e65-116">. podnikatel</span><span class="sxs-lookup"><span data-stu-id="40e65-116">. operator</span></span>](member-access-operators.md#member-access-operator-)
- [<span data-ttu-id="40e65-117">extern alias</span><span class="sxs-lookup"><span data-stu-id="40e65-117">extern alias</span></span>](../keywords/extern-alias.md)
