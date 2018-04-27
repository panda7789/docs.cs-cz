---
title: 'Postupy: Vytvoření nové metody pro výčet (Průvodce programováním v C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
caps.latest.revision: 7
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8b05d9f910e8c268fded8cdcc462392a1e80efdb
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a><span data-ttu-id="47a7f-102">Postupy: Vytvoření nové metody pro výčet (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="47a7f-102">How to: Create a New Method for an Enumeration (C# Programming Guide)</span></span>
<span data-ttu-id="47a7f-103">Rozšiřující metody můžete přidat funkce specifické pro konkrétní výčtu typu.</span><span class="sxs-lookup"><span data-stu-id="47a7f-103">You can use extension methods to add functionality specific to a particular enum type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47a7f-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="47a7f-104">Example</span></span>  
 <span data-ttu-id="47a7f-105">V následujícím příkladu `Grades` výčtu představuje možné známky které student mohou zobrazit v třídě.</span><span class="sxs-lookup"><span data-stu-id="47a7f-105">In the following example, the `Grades` enumeration represents the possible letter grades that a student may receive in a class.</span></span> <span data-ttu-id="47a7f-106">Metody rozšíření s názvem `Passing` je přidán do `Grades` zadejte tak, aby každá instance tohoto typu teď "ví" zda představuje úrovni předávání nebo ne.</span><span class="sxs-lookup"><span data-stu-id="47a7f-106">An extension method named `Passing` is added to the `Grades` type so that each instance of that type now "knows" whether it represents a passing grade or not.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-create-a-new-method-for-an-enumeration_1.cs)]  
  
 <span data-ttu-id="47a7f-107">Všimněte si, že `Extensions` třída také obsahuje statické proměnné, která se dynamicky aktualizuje a že návratovou hodnotu metody rozšíření odráží aktuální hodnotu této proměnné.</span><span class="sxs-lookup"><span data-stu-id="47a7f-107">Note that the `Extensions` class also contains a static variable that is updated dynamically and that the return value of the extension method reflects the current value of that variable.</span></span> <span data-ttu-id="47a7f-108">To znamená, že na pozadí jsou rozšiřující metody volána přímo na statické třídy, ve kterém jsou definovány.</span><span class="sxs-lookup"><span data-stu-id="47a7f-108">This demonstrates that, behind the scenes, extension methods are invoked directly on the static class in which they are defined.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="47a7f-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="47a7f-109">Compiling the Code</span></span>  
 <span data-ttu-id="47a7f-110">Pokud chcete spustit tento kód, zkopírujte a vložte jej do Visual C# projektu konzolové aplikace vytvořené v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="47a7f-110">To run this code, copy and paste it into a Visual C# console application project that has been created in Visual Studio.</span></span> <span data-ttu-id="47a7f-111">Ve výchozím nastavení, tento projekt zaměřen na verzi 3.5 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], a obsahuje odkaz na System.Core.dll a `using` direktivy pro System.Linq.</span><span class="sxs-lookup"><span data-stu-id="47a7f-111">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it has a reference to System.Core.dll and a `using` directive for System.Linq.</span></span> <span data-ttu-id="47a7f-112">Pokud z projektu chybí jeden nebo více z těchto požadavků, můžete je přidat ručně.</span><span class="sxs-lookup"><span data-stu-id="47a7f-112">If one or more of these requirements are missing from the project, you can add them manually.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47a7f-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="47a7f-113">See Also</span></span>  
 [<span data-ttu-id="47a7f-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="47a7f-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="47a7f-115">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="47a7f-115">Extension Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
