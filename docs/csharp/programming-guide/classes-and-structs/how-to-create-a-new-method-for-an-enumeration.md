---
title: 'Postupy: Vytvoření nové metody pro výčet - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 2ca388d19c0e4e1b098076caa5baa0a83cc0dd4c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65585875"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a><span data-ttu-id="a1e52-102">Postupy: Vytvoření nové metody pro výčet (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="a1e52-102">How to: Create a New Method for an Enumeration (C# Programming Guide)</span></span>
<span data-ttu-id="a1e52-103">Rozšiřující metody slouží k přidání funkce specifické pro typ konkrétní výčtu.</span><span class="sxs-lookup"><span data-stu-id="a1e52-103">You can use extension methods to add functionality specific to a particular enum type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1e52-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="a1e52-104">Example</span></span>  
 <span data-ttu-id="a1e52-105">V následujícím příkladu `Grades` výčet představuje možné písmeno tříd, které student může zobrazit ve třídě.</span><span class="sxs-lookup"><span data-stu-id="a1e52-105">In the following example, the `Grades` enumeration represents the possible letter grades that a student may receive in a class.</span></span> <span data-ttu-id="a1e52-106">Rozšiřující metody s názvem `Passing` se přidá do `Grades` tak, aby každá instance daného typu nyní "ví", zda představuje na podnikové úrovni předávání nebo ne.</span><span class="sxs-lookup"><span data-stu-id="a1e52-106">An extension method named `Passing` is added to the `Grades` type so that each instance of that type now "knows" whether it represents a passing grade or not.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 <span data-ttu-id="a1e52-107">Všimněte si, `Extensions` třída také obsahuje statickou proměnnou, která se dynamicky aktualizuje a že návratová hodnota metody rozšíření odpovídá aktuální hodnotě proměnné.</span><span class="sxs-lookup"><span data-stu-id="a1e52-107">Note that the `Extensions` class also contains a static variable that is updated dynamically and that the return value of the extension method reflects the current value of that variable.</span></span> <span data-ttu-id="a1e52-108">Tento příklad ukazuje, že na pozadí jsou rozšiřující metody vyvolány přímo u statické třídy, ve kterém jsou definovány.</span><span class="sxs-lookup"><span data-stu-id="a1e52-108">This demonstrates that, behind the scenes, extension methods are invoked directly on the static class in which they are defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1e52-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a1e52-109">See also</span></span>

- [<span data-ttu-id="a1e52-110">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="a1e52-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="a1e52-111">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="a1e52-111">Extension Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
