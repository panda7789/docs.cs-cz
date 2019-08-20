---
title: 'Postupy: Vytvoření nové metody pro průvodce C# programováním výčtu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 99a2005e1a64fa214776145a903341fb162f0633
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597044"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a><span data-ttu-id="b15d1-102">Postupy: Vytvoření nové metody pro výčet (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="b15d1-102">How to: Create a New Method for an Enumeration (C# Programming Guide)</span></span>
<span data-ttu-id="b15d1-103">Metody rozšíření lze použít k přidání funkcí specifických pro konkrétní typ výčtu.</span><span class="sxs-lookup"><span data-stu-id="b15d1-103">You can use extension methods to add functionality specific to a particular enum type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b15d1-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="b15d1-104">Example</span></span>  
 <span data-ttu-id="b15d1-105">V následujícím příkladu `Grades` výčet představuje možné známky, které může student získat ve třídě.</span><span class="sxs-lookup"><span data-stu-id="b15d1-105">In the following example, the `Grades` enumeration represents the possible letter grades that a student may receive in a class.</span></span> <span data-ttu-id="b15d1-106">Rozšiřující metoda s názvem `Passing` je přidána `Grades` do typu tak, že každá instance daného typu teď "ví", zda představuje třídu předání nebo ne.</span><span class="sxs-lookup"><span data-stu-id="b15d1-106">An extension method named `Passing` is added to the `Grades` type so that each instance of that type now "knows" whether it represents a passing grade or not.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 <span data-ttu-id="b15d1-107">Všimněte si, `Extensions` že třída také obsahuje statickou proměnnou, která je dynamicky aktualizována a že návratová hodnota metody rozšíření odráží aktuální hodnotu této proměnné.</span><span class="sxs-lookup"><span data-stu-id="b15d1-107">Note that the `Extensions` class also contains a static variable that is updated dynamically and that the return value of the extension method reflects the current value of that variable.</span></span> <span data-ttu-id="b15d1-108">To ukazuje, že na pozadí jsou metody rozšíření vyvolány přímo na statickou třídu, ve které jsou definovány.</span><span class="sxs-lookup"><span data-stu-id="b15d1-108">This demonstrates that, behind the scenes, extension methods are invoked directly on the static class in which they are defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b15d1-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b15d1-109">See also</span></span>

- [<span data-ttu-id="b15d1-110">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b15d1-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b15d1-111">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="b15d1-111">Extension Methods</span></span>](./extension-methods.md)
