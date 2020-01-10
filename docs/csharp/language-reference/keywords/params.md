---
title: klíčové slovo params – C# referenční informace
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: 90d224080f607cbac96514aaf5ac6d67affef9e0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713232"
---
# <a name="params-c-reference"></a><span data-ttu-id="3be75-102">params (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="3be75-102">params (C# Reference)</span></span>

<span data-ttu-id="3be75-103">Pomocí klíčového slova `params` můžete zadat [parametr metody](method-parameters.md) , který přebírá proměnný počet argumentů.</span><span class="sxs-lookup"><span data-stu-id="3be75-103">By using the `params` keyword, you can specify a [method parameter](method-parameters.md) that takes a variable number of arguments.</span></span>

<span data-ttu-id="3be75-104">Můžete odeslat čárkami oddělený seznam argumentů typu určeného v deklaraci parametru nebo pole argumentů zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="3be75-104">You can send a comma-separated list of arguments of the type specified in the parameter declaration or an array of arguments of the specified type.</span></span> <span data-ttu-id="3be75-105">Nemůžete také odesílat žádné argumenty.</span><span class="sxs-lookup"><span data-stu-id="3be75-105">You also can send no arguments.</span></span> <span data-ttu-id="3be75-106">Pokud neodešlete žádné argumenty, délka seznamu `params` je nula.</span><span class="sxs-lookup"><span data-stu-id="3be75-106">If you send no arguments, the length of the `params` list is zero.</span></span>

<span data-ttu-id="3be75-107">V deklaraci metody nejsou povoleny žádné další parametry za klíčovým slovem `params` a v deklaraci metody je povoleno pouze jedno klíčové slovo `params`.</span><span class="sxs-lookup"><span data-stu-id="3be75-107">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>

<span data-ttu-id="3be75-108">Deklarovaný typ parametru `params` musí být jednorozměrné pole, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="3be75-108">The declared type of the `params` parameter must be a single-dimensional array, as the following example shows.</span></span> <span data-ttu-id="3be75-109">V opačném případě dojde k chybě kompilátoru [CS0225](../../misc/cs0225.md) .</span><span class="sxs-lookup"><span data-stu-id="3be75-109">Otherwise, a compiler error [CS0225](../../misc/cs0225.md) occurs.</span></span>

## <a name="example"></a><span data-ttu-id="3be75-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="3be75-110">Example</span></span>

<span data-ttu-id="3be75-111">Následující příklad ukazuje různé způsoby, jak lze do parametru `params` odeslat argumenty.</span><span class="sxs-lookup"><span data-stu-id="3be75-111">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)] 

## <a name="c-language-specification"></a><span data-ttu-id="3be75-112">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3be75-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="3be75-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3be75-113">See also</span></span>

- [<span data-ttu-id="3be75-114">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="3be75-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3be75-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="3be75-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3be75-116">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3be75-116">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="3be75-117">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="3be75-117">Method Parameters</span></span>](method-parameters.md)
