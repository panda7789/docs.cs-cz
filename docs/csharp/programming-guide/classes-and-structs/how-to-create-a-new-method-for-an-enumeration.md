---
title: Postup vytvoření nové metody pro výčet – Průvodce programováním v C#
description: Naučte se používat rozšiřující metody pro přidání funkce do výčtu v jazyce C#. Tento příklad ukazuje metodu rozšíření s názvem předání pro výčet s názvem třídy.
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 6c01a73476e98e8344a7a8dc35a5fd80384fc7a2
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864485"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a><span data-ttu-id="19876-104">Postup vytvoření nové metody pro výčet (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="19876-104">How to create a new method for an enumeration (C# Programming Guide)</span></span>
<span data-ttu-id="19876-105">Metody rozšíření lze použít k přidání funkcí specifických pro konkrétní typ výčtu.</span><span class="sxs-lookup"><span data-stu-id="19876-105">You can use extension methods to add functionality specific to a particular enum type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19876-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="19876-106">Example</span></span>  
 <span data-ttu-id="19876-107">V následujícím příkladu `Grades` výčet představuje možné známky, které může student získat ve třídě.</span><span class="sxs-lookup"><span data-stu-id="19876-107">In the following example, the `Grades` enumeration represents the possible letter grades that a student may receive in a class.</span></span> <span data-ttu-id="19876-108">Rozšiřující metoda s názvem `Passing` je přidána do `Grades` typu tak, že každá instance daného typu teď "ví", zda představuje třídu předání nebo ne.</span><span class="sxs-lookup"><span data-stu-id="19876-108">An extension method named `Passing` is added to the `Grades` type so that each instance of that type now "knows" whether it represents a passing grade or not.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 <span data-ttu-id="19876-109">Všimněte si, že `Extensions` Třída také obsahuje statickou proměnnou, která je dynamicky aktualizována a že návratová hodnota metody rozšíření odráží aktuální hodnotu této proměnné.</span><span class="sxs-lookup"><span data-stu-id="19876-109">Note that the `Extensions` class also contains a static variable that is updated dynamically and that the return value of the extension method reflects the current value of that variable.</span></span> <span data-ttu-id="19876-110">To ukazuje, že na pozadí jsou metody rozšíření vyvolány přímo na statickou třídu, ve které jsou definovány.</span><span class="sxs-lookup"><span data-stu-id="19876-110">This demonstrates that, behind the scenes, extension methods are invoked directly on the static class in which they are defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19876-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="19876-111">See also</span></span>

- [<span data-ttu-id="19876-112">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="19876-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="19876-113">Metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="19876-113">Extension Methods</span></span>](./extension-methods.md)
