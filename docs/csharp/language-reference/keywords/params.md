---
title: klíčové slovo params - C# Reference
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: f462ccc2421fef3ea111d263ec035a701cf04775
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173546"
---
# <a name="params-c-reference"></a><span data-ttu-id="ce534-102">params (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ce534-102">params (C# Reference)</span></span>

<span data-ttu-id="ce534-103">Pomocí klíčového `params` slova můžete zadat [parametr metody,](method-parameters.md) který přebírá proměnný počet argumentů.</span><span class="sxs-lookup"><span data-stu-id="ce534-103">By using the `params` keyword, you can specify a [method parameter](method-parameters.md) that takes a variable number of arguments.</span></span>

<span data-ttu-id="ce534-104">Můžete odeslat seznam argumentů oddělených čárkami typu zadaného v deklaraci parametru nebo pole argumentů zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="ce534-104">You can send a comma-separated list of arguments of the type specified in the parameter declaration or an array of arguments of the specified type.</span></span> <span data-ttu-id="ce534-105">Můžete také odeslat žádné argumenty.</span><span class="sxs-lookup"><span data-stu-id="ce534-105">You also can send no arguments.</span></span> <span data-ttu-id="ce534-106">Pokud neodešlete žádné argumenty, bude délka `params` seznamu nulová.</span><span class="sxs-lookup"><span data-stu-id="ce534-106">If you send no arguments, the length of the `params` list is zero.</span></span>

<span data-ttu-id="ce534-107">Žádné další parametry jsou `params` povoleny po klíčové slovo `params` v deklaraci metody a pouze jedno klíčové slovo je povoleno v deklaraci metody.</span><span class="sxs-lookup"><span data-stu-id="ce534-107">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>

<span data-ttu-id="ce534-108">Deklarovaný `params` typ parametru musí být jednorozměrné pole, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="ce534-108">The declared type of the `params` parameter must be a single-dimensional array, as the following example shows.</span></span> <span data-ttu-id="ce534-109">V opačném případě dojde k chybě kompilátoru [CS0225.](../../misc/cs0225.md)</span><span class="sxs-lookup"><span data-stu-id="ce534-109">Otherwise, a compiler error [CS0225](../../misc/cs0225.md) occurs.</span></span>

## <a name="example"></a><span data-ttu-id="ce534-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce534-110">Example</span></span>

<span data-ttu-id="ce534-111">Následující příklad ukazuje různé způsoby, ve kterém `params` mohou být argumenty odeslány do parametru.</span><span class="sxs-lookup"><span data-stu-id="ce534-111">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="ce534-112">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ce534-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="ce534-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce534-113">See also</span></span>

- [<span data-ttu-id="ce534-114">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ce534-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ce534-115">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ce534-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ce534-116">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="ce534-116">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="ce534-117">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="ce534-117">Method Parameters</span></span>](method-parameters.md)
