---
title: params (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: 692c2f61ae99f1c1c8e04a5a1bcad08814d286fe
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2018
ms.locfileid: "42753978"
---
# <a name="params-c-reference"></a><span data-ttu-id="fe1e6-102">params (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="fe1e6-102">params (C# Reference)</span></span>
<span data-ttu-id="fe1e6-103">S použitím `params` – klíčové slovo, můžete zadat [parametr metody](../../../csharp/language-reference/keywords/method-parameters.md) , která přijímá proměnný počet argumentů.</span><span class="sxs-lookup"><span data-stu-id="fe1e6-103">By using the `params` keyword, you can specify a [method parameter](../../../csharp/language-reference/keywords/method-parameters.md) that takes a variable number of arguments.</span></span>  
  
 <span data-ttu-id="fe1e6-104">Můžete odeslat čárkami oddělený seznam argumentů typ zadaný v deklaraci parametru nebo pole argumentů zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="fe1e6-104">You can send a comma-separated list of arguments of the type specified in the parameter declaration or an array of arguments of the specified type.</span></span> <span data-ttu-id="fe1e6-105">Můžete také odeslat žádné argumenty.</span><span class="sxs-lookup"><span data-stu-id="fe1e6-105">You also can send no arguments.</span></span> <span data-ttu-id="fe1e6-106">Pokud odešlete bez argumentů, délka `params` seznamu je nula.</span><span class="sxs-lookup"><span data-stu-id="fe1e6-106">If you send no arguments, the length of the `params` list is zero.</span></span>  
  
 <span data-ttu-id="fe1e6-107">Žádné další parametry nejsou povoleny po `params` – klíčové slovo v deklaraci metody a pouze jeden `params` – klíčové slovo je povolený v deklaraci metody.</span><span class="sxs-lookup"><span data-stu-id="fe1e6-107">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>  
 
 <span data-ttu-id="fe1e6-108">Deklarovaný typ `params` parametr musí být jednorozměrné pole, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="fe1e6-108">The declared type of the `params` parameter must be a single-dimensional array, as the following example shows.</span></span> <span data-ttu-id="fe1e6-109">V opačném případě chybu kompilátoru [CS0225](../../../csharp/misc/cs0225.md) vyvolá.</span><span class="sxs-lookup"><span data-stu-id="fe1e6-109">Otherwise, a compiler error [CS0225](../../../csharp/misc/cs0225.md) occurs.</span></span>
  
## <a name="example"></a><span data-ttu-id="fe1e6-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="fe1e6-110">Example</span></span>  
 <span data-ttu-id="fe1e6-111">Následující příklad ukazuje různé způsoby, jimiž lze argumenty odesílat do `params` parametru.</span><span class="sxs-lookup"><span data-stu-id="fe1e6-111">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>  
  
 [!code-csharp[csrefKeywordsMethodParams#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/params_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="fe1e6-112">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="fe1e6-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fe1e6-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="fe1e6-113">See Also</span></span>  
 [<span data-ttu-id="fe1e6-114">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="fe1e6-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="fe1e6-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="fe1e6-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="fe1e6-116">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="fe1e6-116">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="fe1e6-117">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="fe1e6-117">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)
