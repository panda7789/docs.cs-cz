---
title: klíčové slovo params pro pole parametrů - odkaz C#
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
- parameter array
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: 77d7fd19ff57f80f401191027e2fae95026e1966
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738843"
---
# <a name="params-c-reference"></a><span data-ttu-id="cc84e-102">params (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="cc84e-102">params (C# Reference)</span></span>

<span data-ttu-id="cc84e-103">Pomocí klíčového `params` slova můžete zadat [parametr metody,](method-parameters.md) který přebírá proměnný počet argumentů.</span><span class="sxs-lookup"><span data-stu-id="cc84e-103">By using the `params` keyword, you can specify a [method parameter](method-parameters.md) that takes a variable number of arguments.</span></span> <span data-ttu-id="cc84e-104">Typ parametru musí být jednorozměrné pole.</span><span class="sxs-lookup"><span data-stu-id="cc84e-104">The parameter type must be a single-dimensional array.</span></span>

<span data-ttu-id="cc84e-105">Žádné další parametry jsou `params` povoleny po klíčové slovo `params` v deklaraci metody a pouze jedno klíčové slovo je povoleno v deklaraci metody.</span><span class="sxs-lookup"><span data-stu-id="cc84e-105">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>

<span data-ttu-id="cc84e-106">Pokud deklarovaný `params` typ parametru není jednorozměrné pole, dojde k chybě kompilátoru [CS0225.](../../misc/cs0225.md)</span><span class="sxs-lookup"><span data-stu-id="cc84e-106">If the declared type of the `params` parameter is not a single-dimensional array, compiler error [CS0225](../../misc/cs0225.md) occurs.</span></span>

<span data-ttu-id="cc84e-107">Při volání metody s `params` parametrem můžete předat:</span><span class="sxs-lookup"><span data-stu-id="cc84e-107">When you call a method with a `params` parameter, you can pass in:</span></span>

- <span data-ttu-id="cc84e-108">Seznam argumentů oddělených čárkami typu prvků pole.</span><span class="sxs-lookup"><span data-stu-id="cc84e-108">A comma-separated list of arguments of the type of the array elements.</span></span>
- <span data-ttu-id="cc84e-109">Pole argumentů zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="cc84e-109">An array of arguments of the specified type.</span></span>
- <span data-ttu-id="cc84e-110">Žádné argumenty.</span><span class="sxs-lookup"><span data-stu-id="cc84e-110">No arguments.</span></span> <span data-ttu-id="cc84e-111">Pokud neodešlete žádné argumenty, bude délka `params` seznamu nulová.</span><span class="sxs-lookup"><span data-stu-id="cc84e-111">If you send no arguments, the length of the `params` list is zero.</span></span>

## <a name="example"></a><span data-ttu-id="cc84e-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="cc84e-112">Example</span></span>

<span data-ttu-id="cc84e-113">Následující příklad ukazuje různé způsoby, ve kterém `params` mohou být argumenty odeslány do parametru.</span><span class="sxs-lookup"><span data-stu-id="cc84e-113">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="cc84e-114">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cc84e-114">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="cc84e-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="cc84e-115">See also</span></span>

- [<span data-ttu-id="cc84e-116">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cc84e-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="cc84e-117">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cc84e-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="cc84e-118">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="cc84e-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="cc84e-119">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="cc84e-119">Method Parameters</span></span>](method-parameters.md)
