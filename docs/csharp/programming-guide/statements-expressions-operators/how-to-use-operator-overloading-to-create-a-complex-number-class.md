---
title: "Postupy: Použití přetížení operátoru pro vytvoření třídy reprezentující komplexní čísla (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- complex numbers [C#]
- classes [C#], operator overloading
- operator overloading [C#], complex numbers
- operator overloading [C#], using to create classes
- operators [C#], overloading to create a complex number class
ms.assetid: c9b8d982-5112-413f-bae3-b42ae3248ddf
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2053684a9b20c3ec8f4d8ac275832516b3f2c265
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-operator-overloading-to-create-a-complex-number-class-c-programming-guide"></a><span data-ttu-id="a8361-102">Postupy: Použití přetížení operátoru pro vytvoření třídy reprezentující komplexní čísla (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="a8361-102">How to: Use Operator Overloading to Create a Complex Number Class (C# Programming Guide)</span></span>
<span data-ttu-id="a8361-103">Tento příklad ukazuje, jak můžete použít přetížení operátoru pro vytvoření třídy reprezentující komplexní čísla `Complex` , který definuje komplexní přidání.</span><span class="sxs-lookup"><span data-stu-id="a8361-103">This example shows how you can use operator overloading to create a complex number class `Complex` that defines complex addition.</span></span> <span data-ttu-id="a8361-104">Program zobrazí imaginary a části reálná čísla a přidání dojít k použití přepsání `ToString` metoda.</span><span class="sxs-lookup"><span data-stu-id="a8361-104">The program displays the imaginary and the real parts of the numbers and the addition result using an override of the `ToString` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8361-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="a8361-105">Example</span></span>  
 [!code-csharp[csProgGuideStatements#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-operator-overloading-to-create-a-complex-number-class_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="a8361-106">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8361-106">See Also</span></span>  
 [<span data-ttu-id="a8361-107">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="a8361-107">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a8361-108">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a8361-108">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="a8361-109">operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="a8361-109">operator (C# Reference)</span></span>](../../../csharp/language-reference/keywords/operator.md)  
 [<span data-ttu-id="a8361-110">Proč se přetížené operátory vždy v C#?</span><span class="sxs-lookup"><span data-stu-id="a8361-110">Why are overloaded operators always static in C#?</span></span>](http://go.microsoft.com/fwlink/?LinkId=112383)
