---
title: . Operator - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ._CSharpKeyword
helpviewer_keywords:
- member access operator (.) [C#]
- . operator [C#]
- dot operator (.) [C#]
ms.assetid: a1f54b52-b686-4ae5-a48e-a2a9ebd0eb7b
ms.openlocfilehash: a59f69d0349a054c8c2a5b701b8f63df113a6580
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333717"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="c8e06-103">.</span><span class="sxs-lookup"><span data-stu-id="c8e06-103">.</span></span> <span data-ttu-id="c8e06-104">operator (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c8e06-104">operator (C# Reference)</span></span>

<span data-ttu-id="c8e06-105">Tečka – operátor (`.`) se používá pro přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="c8e06-105">The dot operator (`.`) is used for member access.</span></span> <span data-ttu-id="c8e06-106">Operátor tečky Určuje typ nebo obor názvů.</span><span class="sxs-lookup"><span data-stu-id="c8e06-106">The dot operator specifies a member of a type or namespace.</span></span> <span data-ttu-id="c8e06-107">Například operátor tečky slouží k přístupu k určité metody v rámci knihovny tříd rozhraní .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="c8e06-107">For example, the dot operator is used to access specific methods within the .NET Framework class libraries:</span></span>

[!code-csharp[csRefOperators#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#16)]

<span data-ttu-id="c8e06-108">Představte si třeba následující třídy:</span><span class="sxs-lookup"><span data-stu-id="c8e06-108">For example, consider the following class:</span></span>

[!code-csharp[csRefOperators#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#17)]

[!code-csharp[csRefOperators#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#18)]

<span data-ttu-id="c8e06-109">Proměnná `s` se dvěma členy `a` a `b`; pokud ho chcete přistupovat k nim, použijte operátor tečky:</span><span class="sxs-lookup"><span data-stu-id="c8e06-109">The variable `s` has two members, `a` and `b`; to access them, use the dot operator:</span></span>

[!code-csharp[csRefOperators#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#19)]

<span data-ttu-id="c8e06-110">Tečka slouží také k vytvoření kvalifikované názvy, které jsou názvy, které určují obor názvů nebo rozhraní, například, ke kterému patří.</span><span class="sxs-lookup"><span data-stu-id="c8e06-110">The dot is also used to form qualified names, which are names that specify the namespace or interface, for example, to which they belong.</span></span>

[!code-csharp[csRefOperators#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#20)]

<span data-ttu-id="c8e06-111">Using – direktiva provádí některé kvalifikace názvu volitelné:</span><span class="sxs-lookup"><span data-stu-id="c8e06-111">The using directive makes some name qualification optional:</span></span>

[!code-csharp[csRefOperators#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#21)]

<span data-ttu-id="c8e06-112">Ale pokud identifikátor je dvojznačný, musí být kvalifikován:</span><span class="sxs-lookup"><span data-stu-id="c8e06-112">But when an identifier is ambiguous, it must be qualified:</span></span>

[!code-csharp[csRefOperators#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#22)]

## <a name="c-language-specification"></a><span data-ttu-id="c8e06-113">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c8e06-113">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="c8e06-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c8e06-114">See also</span></span>

- [<span data-ttu-id="c8e06-115">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c8e06-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c8e06-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="c8e06-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c8e06-117">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c8e06-117">C# Operators</span></span>](index.md)