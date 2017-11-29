---
title: "explicit (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- explicit_CSharpKeyword
- explicit
helpviewer_keywords: explicit keyword [C#]
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2661f46d79b13808bfb169bfbfffc1a17b866b2b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="explicit-c-reference"></a><span data-ttu-id="faef9-102">explicit (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="faef9-102">explicit (C# Reference)</span></span>
<span data-ttu-id="faef9-103">`explicit` – Klíčové slovo deklaruje operátor převodu uživatelem definovaný typ, který musí být volána s přetypování.</span><span class="sxs-lookup"><span data-stu-id="faef9-103">The `explicit` keyword declares a user-defined type conversion operator that must be invoked with a cast.</span></span> <span data-ttu-id="faef9-104">Tento operátor například převede ze třídy s názvem Fahrenheita na třídu s názvem c:</span><span class="sxs-lookup"><span data-stu-id="faef9-104">For example, this operator converts from a class called Fahrenheit to a class called Celsius:</span></span>  
  
 [!code-csharp[csrefKeywordsConversion#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_1.cs)]  
  
 <span data-ttu-id="faef9-105">Tento operátor převodu nelze vyvolat takto:</span><span class="sxs-lookup"><span data-stu-id="faef9-105">This conversion operator can be invoked like this:</span></span>  
  
 [!code-csharp[csrefKeywordsConversion#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_2.cs)]  
  
 <span data-ttu-id="faef9-106">Operátor převodu převede ze zdroje typu na typ cíle.</span><span class="sxs-lookup"><span data-stu-id="faef9-106">The conversion operator converts from a source type to a target type.</span></span> <span data-ttu-id="faef9-107">Typ zdroje poskytuje operátor převodu.</span><span class="sxs-lookup"><span data-stu-id="faef9-107">The source type provides the conversion operator.</span></span> <span data-ttu-id="faef9-108">Na rozdíl od implicitní převod musí být volána operátory explicitního převodu prostřednictvím přetypování.</span><span class="sxs-lookup"><span data-stu-id="faef9-108">Unlike implicit conversion, explicit conversion operators must be invoked by means of a cast.</span></span> <span data-ttu-id="faef9-109">Pokud operaci převodu může způsobit, že výjimky nebo dojít ke ztrátě informací, byste měli označit `explicit`.</span><span class="sxs-lookup"><span data-stu-id="faef9-109">If a conversion operation can cause exceptions or lose information, you should mark it `explicit`.</span></span> <span data-ttu-id="faef9-110">Kompilátor zabrání bezobslužně vyvolání operaci převodu s pravděpodobně nepředpokládaného důsledky.</span><span class="sxs-lookup"><span data-stu-id="faef9-110">This prevents the compiler from silently invoking the conversion operation with possibly unforeseen consequences.</span></span>  
  
 <span data-ttu-id="faef9-111">Vynechání přetypování výsledky v chybě kompilace CS0266.</span><span class="sxs-lookup"><span data-stu-id="faef9-111">Omitting the cast results in compile-time error CS0266.</span></span>  
  
 <span data-ttu-id="faef9-112">Další informace najdete v tématu [použití operátorů převodu](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="faef9-112">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="faef9-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="faef9-113">Example</span></span>  
 <span data-ttu-id="faef9-114">Následující příklad uvádí `Fahrenheit` a `Celsius` třída, z nichž každý obsahuje operátor explicitní převod na jinou třídu.</span><span class="sxs-lookup"><span data-stu-id="faef9-114">The following example provides a `Fahrenheit` and a `Celsius` class, each of which provides an explicit conversion operator to the other class.</span></span>  
  
 [!code-csharp[csrefKeywordsConversion#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="faef9-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="faef9-115">Example</span></span>  
 <span data-ttu-id="faef9-116">V následujícím příkladu definuje struktury, `Digit`, která představuje jednu desítková číslice.</span><span class="sxs-lookup"><span data-stu-id="faef9-116">The following example defines a struct, `Digit`, that represents a single decimal digit.</span></span> <span data-ttu-id="faef9-117">Operátor je definována pro převody z `byte` k `Digit`, ale protože ne všechny bajtů můžete převést na `Digit`, je explicitní převod.</span><span class="sxs-lookup"><span data-stu-id="faef9-117">An operator is defined for conversions from `byte` to `Digit`, but because not all bytes can be converted to a `Digit`, the conversion is explicit.</span></span>  
  
 [!code-csharp[csrefKeywordsConversion#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_4.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="faef9-118">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="faef9-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="faef9-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="faef9-119">See Also</span></span>  
 [<span data-ttu-id="faef9-120">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="faef9-120">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="faef9-121">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="faef9-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="faef9-122">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="faef9-122">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="faef9-123">implicitní</span><span class="sxs-lookup"><span data-stu-id="faef9-123">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)  
 [<span data-ttu-id="faef9-124">operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="faef9-124">operator (C# Reference)</span></span>](../../../csharp/language-reference/keywords/operator.md)  
 [<span data-ttu-id="faef9-125">Postupy: implementace uživatelem definovaných převodů mezi strukturami</span><span class="sxs-lookup"><span data-stu-id="faef9-125">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
 [<span data-ttu-id="faef9-126">Zřetězené uživatelem definované explicitní převody v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="faef9-126">Chained user-defined explicit conversions in C#</span></span>](http://go.microsoft.com/fwlink/?LinkId=112384)
