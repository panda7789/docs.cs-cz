---
title: klíčové slovo params – C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: dd9699eb50f7dffc7c2f4976a79afbf689ba2470
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660980"
---
# <a name="params-c-reference"></a><span data-ttu-id="4d106-102">params (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="4d106-102">params (C# Reference)</span></span>

<span data-ttu-id="4d106-103">S použitím `params` – klíčové slovo, můžete zadat [parametr metody](method-parameters.md) , která přijímá proměnný počet argumentů.</span><span class="sxs-lookup"><span data-stu-id="4d106-103">By using the `params` keyword, you can specify a [method parameter](method-parameters.md) that takes a variable number of arguments.</span></span>

<span data-ttu-id="4d106-104">Můžete odeslat čárkami oddělený seznam argumentů typ zadaný v deklaraci parametru nebo pole argumentů zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="4d106-104">You can send a comma-separated list of arguments of the type specified in the parameter declaration or an array of arguments of the specified type.</span></span> <span data-ttu-id="4d106-105">Můžete také odeslat žádné argumenty.</span><span class="sxs-lookup"><span data-stu-id="4d106-105">You also can send no arguments.</span></span> <span data-ttu-id="4d106-106">Pokud odešlete bez argumentů, délka `params` seznamu je nula.</span><span class="sxs-lookup"><span data-stu-id="4d106-106">If you send no arguments, the length of the `params` list is zero.</span></span>

<span data-ttu-id="4d106-107">Žádné další parametry nejsou povoleny po `params` – klíčové slovo v deklaraci metody a pouze jeden `params` – klíčové slovo je povolený v deklaraci metody.</span><span class="sxs-lookup"><span data-stu-id="4d106-107">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>

<span data-ttu-id="4d106-108">Deklarovaný typ `params` parametr musí být jednorozměrné pole, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="4d106-108">The declared type of the `params` parameter must be a single-dimensional array, as the following example shows.</span></span> <span data-ttu-id="4d106-109">V opačném případě chybu kompilátoru [CS0225](../../misc/cs0225.md) vyvolá.</span><span class="sxs-lookup"><span data-stu-id="4d106-109">Otherwise, a compiler error [CS0225](../../misc/cs0225.md) occurs.</span></span>

## <a name="example"></a><span data-ttu-id="4d106-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="4d106-110">Example</span></span>

<span data-ttu-id="4d106-111">Následující příklad ukazuje různé způsoby, jimiž lze argumenty odesílat do `params` parametru.</span><span class="sxs-lookup"><span data-stu-id="4d106-111">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)] 

## <a name="c-language-specification"></a><span data-ttu-id="4d106-112">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4d106-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="4d106-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d106-113">See also</span></span>

- [<span data-ttu-id="4d106-114">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4d106-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4d106-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4d106-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4d106-116">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4d106-116">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="4d106-117">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="4d106-117">Method Parameters</span></span>](method-parameters.md)