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
ms.openlocfilehash: d7e0094d0f60aa201ae7229983f3e4b9764d2cbc
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960192"
---
# <a name="params-c-reference"></a><span data-ttu-id="7aad5-102">params (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="7aad5-102">params (C# Reference)</span></span>
<span data-ttu-id="7aad5-103">S použitím `params` – klíčové slovo, můžete zadat [parametr metody](../../../csharp/language-reference/keywords/method-parameters.md) , která přijímá proměnný počet argumentů.</span><span class="sxs-lookup"><span data-stu-id="7aad5-103">By using the `params` keyword, you can specify a [method parameter](../../../csharp/language-reference/keywords/method-parameters.md) that takes a variable number of arguments.</span></span>  
  
 <span data-ttu-id="7aad5-104">Můžete odeslat čárkami oddělený seznam argumentů typ zadaný v deklaraci parametru nebo pole argumentů zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="7aad5-104">You can send a comma-separated list of arguments of the type specified in the parameter declaration or an array of arguments of the specified type.</span></span> <span data-ttu-id="7aad5-105">Můžete také odeslat žádné argumenty.</span><span class="sxs-lookup"><span data-stu-id="7aad5-105">You also can send no arguments.</span></span> <span data-ttu-id="7aad5-106">Pokud odešlete bez argumentů, délka `params` seznamu je nula.</span><span class="sxs-lookup"><span data-stu-id="7aad5-106">If you send no arguments, the length of the `params` list is zero.</span></span>  
  
 <span data-ttu-id="7aad5-107">Žádné další parametry nejsou povoleny po `params` – klíčové slovo v deklaraci metody a pouze jeden `params` – klíčové slovo je povolený v deklaraci metody.</span><span class="sxs-lookup"><span data-stu-id="7aad5-107">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7aad5-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="7aad5-108">Example</span></span>  
 <span data-ttu-id="7aad5-109">Následující příklad ukazuje různé způsoby, jimiž lze argumenty odesílat do `params` parametru.</span><span class="sxs-lookup"><span data-stu-id="7aad5-109">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>  
  
 [!code-csharp[csrefKeywordsMethodParams#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/params_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="7aad5-110">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7aad5-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7aad5-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="7aad5-111">See Also</span></span>  
 [<span data-ttu-id="7aad5-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7aad5-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="7aad5-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="7aad5-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7aad5-114">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7aad5-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="7aad5-115">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="7aad5-115">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)
