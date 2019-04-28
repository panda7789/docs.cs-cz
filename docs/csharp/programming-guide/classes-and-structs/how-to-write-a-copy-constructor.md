---
title: 'Postupy: Zápis kopírovacího konstruktoru - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: 169bdfc53d0c30ffc14e5a9525920679a94fbf23
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651776"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="3ee27-102">Postupy: Zápis kopírovacího konstruktoru (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="3ee27-102">How to: Write a Copy Constructor (C# Programming Guide)</span></span>
<span data-ttu-id="3ee27-103">C# neposkytuje konstruktor kopírování pro objekty, ale můžete jej napsat sami.</span><span class="sxs-lookup"><span data-stu-id="3ee27-103">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ee27-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="3ee27-104">Example</span></span>  
 <span data-ttu-id="3ee27-105">V následujícím příkladu `Person` [třídy](../../../csharp/language-reference/keywords/class.md) definuje kopírovacího konstruktora představujícího společně s argumentem instanci `Person`.</span><span class="sxs-lookup"><span data-stu-id="3ee27-105">In the following example, the `Person`[class](../../../csharp/language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="3ee27-106">Hodnoty vlastností argumentu jsou přiřazeny novým vlastnostem nové instance `Person`.</span><span class="sxs-lookup"><span data-stu-id="3ee27-106">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="3ee27-107">Kód obsahuje alternativní kopírovací konstruktor, který odešle `Name` a `Age` vlastnosti instance, kterou chcete zkopírovat do konstruktoru instance třídy.</span><span class="sxs-lookup"><span data-stu-id="3ee27-107">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a><span data-ttu-id="3ee27-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3ee27-108">See also</span></span>

- <xref:System.ICloneable>
- [<span data-ttu-id="3ee27-109">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="3ee27-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="3ee27-110">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="3ee27-110">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="3ee27-111">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="3ee27-111">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [<span data-ttu-id="3ee27-112">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="3ee27-112">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
