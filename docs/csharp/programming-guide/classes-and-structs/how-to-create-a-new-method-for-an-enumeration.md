---
title: 'Postupy: Vytvoření nové metody pro výčet - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 411606b6d86f8781be0cb2db19474d563c09a610
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725126"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a><span data-ttu-id="02028-102">Postupy: Vytvoření nové metody pro výčet (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="02028-102">How to: Create a New Method for an Enumeration (C# Programming Guide)</span></span>
<span data-ttu-id="02028-103">Rozšiřující metody slouží k přidání funkce specifické pro typ konkrétní výčtu.</span><span class="sxs-lookup"><span data-stu-id="02028-103">You can use extension methods to add functionality specific to a particular enum type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02028-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="02028-104">Example</span></span>  
 <span data-ttu-id="02028-105">V následujícím příkladu `Grades` výčet představuje možné písmeno tříd, které student může zobrazit ve třídě.</span><span class="sxs-lookup"><span data-stu-id="02028-105">In the following example, the `Grades` enumeration represents the possible letter grades that a student may receive in a class.</span></span> <span data-ttu-id="02028-106">Rozšiřující metody s názvem `Passing` se přidá do `Grades` tak, aby každá instance daného typu nyní "ví", zda představuje na podnikové úrovni předávání nebo ne.</span><span class="sxs-lookup"><span data-stu-id="02028-106">An extension method named `Passing` is added to the `Grades` type so that each instance of that type now "knows" whether it represents a passing grade or not.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-create-a-new-method-for-an-enumeration_1.cs)]  
  
 <span data-ttu-id="02028-107">Všimněte si, `Extensions` třída také obsahuje statickou proměnnou, která se dynamicky aktualizuje a že návratová hodnota metody rozšíření odpovídá aktuální hodnotě proměnné.</span><span class="sxs-lookup"><span data-stu-id="02028-107">Note that the `Extensions` class also contains a static variable that is updated dynamically and that the return value of the extension method reflects the current value of that variable.</span></span> <span data-ttu-id="02028-108">Tento příklad ukazuje, že na pozadí jsou rozšiřující metody vyvolány přímo u statické třídy, ve kterém jsou definovány.</span><span class="sxs-lookup"><span data-stu-id="02028-108">This demonstrates that, behind the scenes, extension methods are invoked directly on the static class in which they are defined.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="02028-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="02028-109">Compiling the Code</span></span>  
 <span data-ttu-id="02028-110">Tento kód spustit, zkopírujte a vložte ho do jazyka Visual C# projekt konzolové aplikace, který nebyl vytvořen v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="02028-110">To run this code, copy and paste it into a Visual C# console application project that has been created in Visual Studio.</span></span> <span data-ttu-id="02028-111">Ve výchozím nastavení, tento projekt zaměřen na verzi 3.5 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], a obsahuje odkaz na System.Core.dll a `using` směrnice pro System.Linq.</span><span class="sxs-lookup"><span data-stu-id="02028-111">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it has a reference to System.Core.dll and a `using` directive for System.Linq.</span></span> <span data-ttu-id="02028-112">Pokud z projektu chybí jeden nebo více z těchto požadavků, můžete je přidat ručně.</span><span class="sxs-lookup"><span data-stu-id="02028-112">If one or more of these requirements are missing from the project, you can add them manually.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02028-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="02028-113">See also</span></span>

- [<span data-ttu-id="02028-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="02028-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="02028-115">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="02028-115">Extension Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
