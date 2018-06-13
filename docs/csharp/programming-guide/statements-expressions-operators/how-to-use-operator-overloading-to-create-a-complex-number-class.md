---
title: 'Postupy: Použití přetížení operátoru pro vytvoření třídy reprezentující komplexní čísla (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- complex numbers [C#]
- classes [C#], operator overloading
- operator overloading [C#], complex numbers
- operator overloading [C#], using to create classes
- operators [C#], overloading to create a complex number class
ms.assetid: c9b8d982-5112-413f-bae3-b42ae3248ddf
ms.openlocfilehash: d746355dac1b99690a5a94c829bd35598c6c8be8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33328861"
---
# <a name="how-to-use-operator-overloading-to-create-a-complex-number-class-c-programming-guide"></a><span data-ttu-id="834a5-102">Postupy: Použití přetížení operátoru pro vytvoření třídy reprezentující komplexní čísla (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="834a5-102">How to: Use Operator Overloading to Create a Complex Number Class (C# Programming Guide)</span></span>
<span data-ttu-id="834a5-103">Tento příklad ukazuje, jak můžete použít přetížení operátoru pro vytvoření třídy reprezentující komplexní čísla `Complex` , který definuje komplexní přidání.</span><span class="sxs-lookup"><span data-stu-id="834a5-103">This example shows how you can use operator overloading to create a complex number class `Complex` that defines complex addition.</span></span> <span data-ttu-id="834a5-104">Program zobrazí imaginary a části reálná čísla a přidání dojít k použití přepsání `ToString` metoda.</span><span class="sxs-lookup"><span data-stu-id="834a5-104">The program displays the imaginary and the real parts of the numbers and the addition result using an override of the `ToString` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="834a5-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="834a5-105">Example</span></span>  
 [!code-csharp[csProgGuideStatements#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-operator-overloading-to-create-a-complex-number-class_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="834a5-106">Viz také</span><span class="sxs-lookup"><span data-stu-id="834a5-106">See Also</span></span>  
 [<span data-ttu-id="834a5-107">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="834a5-107">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="834a5-108">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="834a5-108">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="834a5-109">Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="834a5-109">operator (C# Reference)</span></span>](../../../csharp/language-reference/keywords/operator.md)  
 [<span data-ttu-id="834a5-110">Proč se přetížené operátory vždy v C#?</span><span class="sxs-lookup"><span data-stu-id="834a5-110">Why are overloaded operators always static in C#?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/05/14/why-are-overloaded-operators-always-static-in-c/)
