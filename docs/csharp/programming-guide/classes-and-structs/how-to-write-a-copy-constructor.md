---
title: "Postupy: Zápis kopírovacího konstruktoru (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f15d8fabc49cbff5515b78a7d2fb6f9e49d0704e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="38258-102">Postupy: Zápis kopírovacího konstruktoru (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="38258-102">How to: Write a Copy Constructor (C# Programming Guide)</span></span>
<span data-ttu-id="38258-103">C# neposkytuje kopírovacího konstruktoru pro objekty, ale můžete napsat vlastní.</span><span class="sxs-lookup"><span data-stu-id="38258-103">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38258-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="38258-104">Example</span></span>  
 <span data-ttu-id="38258-105">V následujícím příkladu `Person` [třída](../../../csharp/language-reference/keywords/class.md) definuje kopie konstruktor, který přijímá, jako její argument instanci `Person`.</span><span class="sxs-lookup"><span data-stu-id="38258-105">In the following example, the `Person`[class](../../../csharp/language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="38258-106">Hodnoty vlastnosti argumentu přiřazené k vlastnosti novou instanci třídy `Person`.</span><span class="sxs-lookup"><span data-stu-id="38258-106">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="38258-107">Kód obsahuje alternativní kopírovací konstruktor, který odesílá `Name` a `Age` vlastnosti instance, kterou chcete zkopírovat do konstruktoru instance třídy.</span><span class="sxs-lookup"><span data-stu-id="38258-107">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[csProgGuideObjects#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-write-a-copy-constructor_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="38258-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="38258-108">See Also</span></span>  
 <xref:System.ICloneable>  
 [<span data-ttu-id="38258-109">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="38258-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="38258-110">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="38258-110">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="38258-111">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="38258-111">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [<span data-ttu-id="38258-112">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="38258-112">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
