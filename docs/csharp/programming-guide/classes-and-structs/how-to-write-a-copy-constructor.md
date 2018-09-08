---
title: 'Postupy: Zápis kopírovacího konstruktoru (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: d6ecfc3659dcf533db0f4e7b67fdffd620a584fd
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44182003"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="924a3-102">Postupy: Zápis kopírovacího konstruktoru (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="924a3-102">How to: Write a Copy Constructor (C# Programming Guide)</span></span>
<span data-ttu-id="924a3-103">C# neposkytuje konstruktor kopírování pro objekty, ale můžete jej napsat sami.</span><span class="sxs-lookup"><span data-stu-id="924a3-103">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="924a3-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="924a3-104">Example</span></span>  
 <span data-ttu-id="924a3-105">V následujícím příkladu `Person` [třídy](../../../csharp/language-reference/keywords/class.md) definuje kopírovacího konstruktora představujícího společně s argumentem instanci `Person`.</span><span class="sxs-lookup"><span data-stu-id="924a3-105">In the following example, the `Person`[class](../../../csharp/language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="924a3-106">Hodnoty vlastností argumentu jsou přiřazeny novým vlastnostem nové instance `Person`.</span><span class="sxs-lookup"><span data-stu-id="924a3-106">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="924a3-107">Kód obsahuje alternativní kopírovací konstruktor, který odešle `Name` a `Age` vlastnosti instance, kterou chcete zkopírovat do konstruktoru instance třídy.</span><span class="sxs-lookup"><span data-stu-id="924a3-107">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[csProgGuideObjects#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-write-a-copy-constructor_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="924a3-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="924a3-108">See Also</span></span>

- <xref:System.ICloneable>  
- [<span data-ttu-id="924a3-109">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="924a3-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="924a3-110">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="924a3-110">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [<span data-ttu-id="924a3-111">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="924a3-111">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
- [<span data-ttu-id="924a3-112">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="924a3-112">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
