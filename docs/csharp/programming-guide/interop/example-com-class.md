---
title: Příklad průvodce programováním třídy COM – C#
ms.date: 07/20/2015
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
ms.openlocfilehash: 6af85d0314a44acbde0996cecbe6dad82cdcc8db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712075"
---
# <a name="example-com-class-c-programming-guide"></a><span data-ttu-id="37b30-102">Ukázka třídy COM (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="37b30-102">Example COM Class (C# Programming Guide)</span></span>
<span data-ttu-id="37b30-103">Následuje příklad třídy, kterou byste zpřístupnili jako objekt COM.</span><span class="sxs-lookup"><span data-stu-id="37b30-103">The following is an example of a class that you would expose as a COM object.</span></span> <span data-ttu-id="37b30-104">Po umístění tohoto kódu do souboru .cs a přidání do projektu nastavte vlastnost **Register for COM Interop** na **hodnotu True**.</span><span class="sxs-lookup"><span data-stu-id="37b30-104">After this code has been placed in a .cs file and added to your project, set the **Register for COM Interop** property to **True**.</span></span> <span data-ttu-id="37b30-105">Další informace naleznete v [tématu How to: Register a Component for COM Interop](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="37b30-105">For more information, see [How to: Register a Component for COM Interop](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).</span></span>
  
 <span data-ttu-id="37b30-106">Vystavení objektů Visual C# pro com vyžaduje deklarování rozhraní třídy, rozhraní událostí, pokud je požadováno, a samotnou třídu.</span><span class="sxs-lookup"><span data-stu-id="37b30-106">Exposing Visual C# objects to COM requires declaring a class interface, an events interface if it is required, and the class itself.</span></span> <span data-ttu-id="37b30-107">Členové třídy musí dodržovat tato pravidla, aby byla viditelná pro koma:</span><span class="sxs-lookup"><span data-stu-id="37b30-107">Class members must follow these rules to be visible to COM:</span></span>  
  
- <span data-ttu-id="37b30-108">Třída musí být veřejná.</span><span class="sxs-lookup"><span data-stu-id="37b30-108">The class must be public.</span></span>  
  
- <span data-ttu-id="37b30-109">Vlastnosti, metody a události musí být veřejné.</span><span class="sxs-lookup"><span data-stu-id="37b30-109">Properties, methods, and events must be public.</span></span>  
  
- <span data-ttu-id="37b30-110">Vlastnosti a metody musí být deklarovány v rozhraní třídy.</span><span class="sxs-lookup"><span data-stu-id="37b30-110">Properties and methods must be declared on the class interface.</span></span>  
  
- <span data-ttu-id="37b30-111">Události musí být deklarovány v rozhraní události.</span><span class="sxs-lookup"><span data-stu-id="37b30-111">Events must be declared in the event interface.</span></span>  
  
 <span data-ttu-id="37b30-112">Ostatní veřejné členy ve třídě, které nejsou deklarovány v těchto rozhraních nebude viditelné pro COM, ale budou viditelné pro jiné objekty rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="37b30-112">Other public members in the class that are not declared in these interfaces will not be visible to COM, but they will be visible to other .NET Framework objects.</span></span>  
  
 <span data-ttu-id="37b30-113">Chcete-li zpřístupnit vlastnosti a metody com, musíte deklarovat je na rozhraní třídy a označit je atributem `DispId` a implementovat je ve třídě.</span><span class="sxs-lookup"><span data-stu-id="37b30-113">To expose properties and methods to COM, you must declare them on the class interface and mark them with a `DispId` attribute, and implement them in the class.</span></span> <span data-ttu-id="37b30-114">Pořadí, ve kterém jsou členy deklarovány v rozhraní je pořadí používané pro vtable COM.</span><span class="sxs-lookup"><span data-stu-id="37b30-114">The order in which the members are declared in the interface is the order used for the COM vtable.</span></span>  
  
 <span data-ttu-id="37b30-115">Chcete-li vystavit události z vaší třídy, musíte je `DispId` deklarovat na rozhraní událostí a označit je atributem.</span><span class="sxs-lookup"><span data-stu-id="37b30-115">To expose events from your class, you must declare them on the events interface and mark them with a `DispId` attribute.</span></span> <span data-ttu-id="37b30-116">Třída by neměla implementovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="37b30-116">The class should not implement this interface.</span></span>  
  
 <span data-ttu-id="37b30-117">Třída implementuje rozhraní třídy; může implementovat více než jedno rozhraní, ale první implementace bude výchozí rozhraní třídy.</span><span class="sxs-lookup"><span data-stu-id="37b30-117">The class implements the class interface; it can implement more than one interface, but the first implementation will be the default class interface.</span></span> <span data-ttu-id="37b30-118">Implementujte metody a vlastnosti vystavené com zde.</span><span class="sxs-lookup"><span data-stu-id="37b30-118">Implement the methods and properties exposed to COM here.</span></span> <span data-ttu-id="37b30-119">Musí být označeny jako veřejné a musí odpovídat deklaracím v rozhraní třídy.</span><span class="sxs-lookup"><span data-stu-id="37b30-119">They must be marked public and must match the declarations in the class interface.</span></span> <span data-ttu-id="37b30-120">Také deklarovat události vyvolané třídy zde.</span><span class="sxs-lookup"><span data-stu-id="37b30-120">Also, declare the events raised by the class here.</span></span> <span data-ttu-id="37b30-121">Musí být označeny jako veřejné a musí odpovídat deklaracím v rozhraní událostí.</span><span class="sxs-lookup"><span data-stu-id="37b30-121">They must be marked public and must match the declarations in the events interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37b30-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="37b30-122">Example</span></span>  
 [!code-csharp[csProgGuideInterop#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/ExampleCOM.cs#8)]  
  
## <a name="see-also"></a><span data-ttu-id="37b30-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="37b30-123">See also</span></span>

- [<span data-ttu-id="37b30-124">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="37b30-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="37b30-125">Vzájemná funkční spolupráce</span><span class="sxs-lookup"><span data-stu-id="37b30-125">Interoperability</span></span>](./index.md)
- [<span data-ttu-id="37b30-126">Stránka Sestavení, návrhář projektu (C#)</span><span class="sxs-lookup"><span data-stu-id="37b30-126">Build Page, Project Designer (C#)</span></span>](/visualstudio/ide/reference/build-page-project-designer-csharp)
