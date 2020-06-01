---
title: Příklad třídy COM – Průvodce programováním v C#
ms.date: 07/20/2015
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
ms.openlocfilehash: 6051ff91d13a3cb3ca6229d813db34dd6a9f3af6
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241848"
---
# <a name="example-com-class-c-programming-guide"></a><span data-ttu-id="005b1-102">Ukázka třídy COM (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="005b1-102">Example COM Class (C# Programming Guide)</span></span>
<span data-ttu-id="005b1-103">Následuje příklad třídy, kterou byste vystavili jako objekt modelu COM.</span><span class="sxs-lookup"><span data-stu-id="005b1-103">The following is an example of a class that you would expose as a COM object.</span></span> <span data-ttu-id="005b1-104">Po umístění tohoto kódu do souboru. cs a jeho přidání do projektu nastavte vlastnost **Register pro zprostředkovatele komunikace s objekty COM** na **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="005b1-104">After this code has been placed in a .cs file and added to your project, set the **Register for COM Interop** property to **True**.</span></span> <span data-ttu-id="005b1-105">Další informace najdete v tématu [Postup: registrace komponenty pro zprostředkovatele komunikace s objekty COM](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="005b1-105">For more information, see [How to: Register a Component for COM Interop](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).</span></span>
  
 <span data-ttu-id="005b1-106">Vystavení objektů jazyka Visual C# pro model COM vyžaduje deklaraci rozhraní třídy, rozhraní události, pokud je požadováno, a samotnou třídu.</span><span class="sxs-lookup"><span data-stu-id="005b1-106">Exposing Visual C# objects to COM requires declaring a class interface, an events interface if it is required, and the class itself.</span></span> <span data-ttu-id="005b1-107">Členové třídy musí dodržovat tato pravidla, aby je bylo možné zobrazit v modelu COM:</span><span class="sxs-lookup"><span data-stu-id="005b1-107">Class members must follow these rules to be visible to COM:</span></span>  
  
- <span data-ttu-id="005b1-108">Třída musí být veřejná.</span><span class="sxs-lookup"><span data-stu-id="005b1-108">The class must be public.</span></span>  
  
- <span data-ttu-id="005b1-109">Vlastnosti, metody a události musí být veřejné.</span><span class="sxs-lookup"><span data-stu-id="005b1-109">Properties, methods, and events must be public.</span></span>  
  
- <span data-ttu-id="005b1-110">Vlastnosti a metody musí být deklarovány v rozhraní třídy.</span><span class="sxs-lookup"><span data-stu-id="005b1-110">Properties and methods must be declared on the class interface.</span></span>  
  
- <span data-ttu-id="005b1-111">Události musí být deklarovány v rozhraní události.</span><span class="sxs-lookup"><span data-stu-id="005b1-111">Events must be declared in the event interface.</span></span>  
  
 <span data-ttu-id="005b1-112">Ostatní veřejné členy třídy, které nejsou deklarovány v těchto rozhraních, nebudou v modelu COM viditelné, ale budou viditelné pro jiné objekty .NET.</span><span class="sxs-lookup"><span data-stu-id="005b1-112">Other public members in the class that are not declared in these interfaces will not be visible to COM, but they will be visible to other .NET objects.</span></span>  
  
 <span data-ttu-id="005b1-113">Chcete-li vystavit vlastnosti a metody modelu COM, je nutné je deklarovat v rozhraní třídy a označit je `DispId` atributem a implementovat je do třídy.</span><span class="sxs-lookup"><span data-stu-id="005b1-113">To expose properties and methods to COM, you must declare them on the class interface and mark them with a `DispId` attribute, and implement them in the class.</span></span> <span data-ttu-id="005b1-114">Pořadí, ve kterém jsou členy deklarovány v rozhraní, je pořadí použité pro model COM vtable.</span><span class="sxs-lookup"><span data-stu-id="005b1-114">The order in which the members are declared in the interface is the order used for the COM vtable.</span></span>  
  
 <span data-ttu-id="005b1-115">Chcete-li zobrazit události z vaší třídy, je nutné je deklarovat v rozhraní události a označit je `DispId` atributem.</span><span class="sxs-lookup"><span data-stu-id="005b1-115">To expose events from your class, you must declare them on the events interface and mark them with a `DispId` attribute.</span></span> <span data-ttu-id="005b1-116">Třída by neměla implementovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="005b1-116">The class should not implement this interface.</span></span>  
  
 <span data-ttu-id="005b1-117">Třída implementuje rozhraní třídy; může implementovat více než jedno rozhraní, ale první implementace bude výchozím rozhraním třídy.</span><span class="sxs-lookup"><span data-stu-id="005b1-117">The class implements the class interface; it can implement more than one interface, but the first implementation will be the default class interface.</span></span> <span data-ttu-id="005b1-118">Sem Implementujte metody a vlastnosti vystavené objektu COM.</span><span class="sxs-lookup"><span data-stu-id="005b1-118">Implement the methods and properties exposed to COM here.</span></span> <span data-ttu-id="005b1-119">Musí být označeny jako veřejné a musí odpovídat deklaracím v rozhraní třídy.</span><span class="sxs-lookup"><span data-stu-id="005b1-119">They must be marked public and must match the declarations in the class interface.</span></span> <span data-ttu-id="005b1-120">Také deklarovat události vyvolané třídou zde.</span><span class="sxs-lookup"><span data-stu-id="005b1-120">Also, declare the events raised by the class here.</span></span> <span data-ttu-id="005b1-121">Musí být označeny jako veřejné a musí odpovídat deklaracím v rozhraní události.</span><span class="sxs-lookup"><span data-stu-id="005b1-121">They must be marked public and must match the declarations in the events interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="005b1-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="005b1-122">Example</span></span>  
 [!code-csharp[csProgGuideInterop#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/ExampleCOM.cs#8)]  
  
## <a name="see-also"></a><span data-ttu-id="005b1-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="005b1-123">See also</span></span>

- [<span data-ttu-id="005b1-124">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="005b1-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="005b1-125">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="005b1-125">Interoperability</span></span>](./index.md)
- [<span data-ttu-id="005b1-126">Stránka Sestavení, návrhář projektu (C#)</span><span class="sxs-lookup"><span data-stu-id="005b1-126">Build Page, Project Designer (C#)</span></span>](/visualstudio/ide/reference/build-page-project-designer-csharp)
