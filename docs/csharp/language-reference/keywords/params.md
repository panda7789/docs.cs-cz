---
description: klíčové slovo params pro pole parametrů – reference jazyka C#
title: klíčové slovo params pro pole parametrů – reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
- parameter array
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: a2726c725508cd297001aaabddeff414704d1115
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134468"
---
# <a name="params-c-reference"></a><span data-ttu-id="b0ae0-103">params (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b0ae0-103">params (C# Reference)</span></span>

<span data-ttu-id="b0ae0-104">Pomocí `params` klíčového slova můžete zadat [parametr metody](method-parameters.md) , který přebírá proměnný počet argumentů.</span><span class="sxs-lookup"><span data-stu-id="b0ae0-104">By using the `params` keyword, you can specify a [method parameter](method-parameters.md) that takes a variable number of arguments.</span></span> <span data-ttu-id="b0ae0-105">Typ parametru musí být jednorozměrné pole.</span><span class="sxs-lookup"><span data-stu-id="b0ae0-105">The parameter type must be a single-dimensional array.</span></span>

<span data-ttu-id="b0ae0-106">V deklaraci metody nejsou povoleny žádné další parametry za `params` klíčovým slovem a `params` v deklaraci metody je povoleno pouze jedno klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="b0ae0-106">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>

<span data-ttu-id="b0ae0-107">Není-li deklarovaný typ `params` parametru jednorozměrné pole, dojde k chybě kompilátoru [CS0225](../../misc/cs0225.md) .</span><span class="sxs-lookup"><span data-stu-id="b0ae0-107">If the declared type of the `params` parameter is not a single-dimensional array, compiler error [CS0225](../../misc/cs0225.md) occurs.</span></span>

<span data-ttu-id="b0ae0-108">Při volání metody s `params` parametrem můžete předat:</span><span class="sxs-lookup"><span data-stu-id="b0ae0-108">When you call a method with a `params` parameter, you can pass in:</span></span>

- <span data-ttu-id="b0ae0-109">Čárkami oddělený seznam argumentů typu prvků pole.</span><span class="sxs-lookup"><span data-stu-id="b0ae0-109">A comma-separated list of arguments of the type of the array elements.</span></span>
- <span data-ttu-id="b0ae0-110">Pole argumentů zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="b0ae0-110">An array of arguments of the specified type.</span></span>
- <span data-ttu-id="b0ae0-111">Žádné argumenty.</span><span class="sxs-lookup"><span data-stu-id="b0ae0-111">No arguments.</span></span> <span data-ttu-id="b0ae0-112">Pokud neodešlete žádné argumenty, délka `params` seznamu je nula.</span><span class="sxs-lookup"><span data-stu-id="b0ae0-112">If you send no arguments, the length of the `params` list is zero.</span></span>

## <a name="example"></a><span data-ttu-id="b0ae0-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0ae0-113">Example</span></span>

<span data-ttu-id="b0ae0-114">Následující příklad ukazuje různé způsoby, jak lze argumenty odeslat do `params` parametru.</span><span class="sxs-lookup"><span data-stu-id="b0ae0-114">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="b0ae0-115">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b0ae0-115">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b0ae0-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="b0ae0-116">See also</span></span>

- [<span data-ttu-id="b0ae0-117">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b0ae0-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b0ae0-118">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="b0ae0-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b0ae0-119">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b0ae0-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b0ae0-120">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="b0ae0-120">Method Parameters</span></span>](method-parameters.md)
