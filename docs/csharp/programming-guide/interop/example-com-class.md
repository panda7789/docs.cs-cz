---
title: "Ukázka třídy COM (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 01b0a5b857171a1354a7dd6b518a7e151073ca32
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="example-com-class-c-programming-guide"></a><span data-ttu-id="cf92d-102">Ukázka třídy COM (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="cf92d-102">Example COM Class (C# Programming Guide)</span></span>
<span data-ttu-id="cf92d-103">Následuje příklad třídu, která by vystavit jako objekt COM.</span><span class="sxs-lookup"><span data-stu-id="cf92d-103">The following is an example of a class that you would expose as a COM object.</span></span> <span data-ttu-id="cf92d-104">Po tento kód je umístěn v souboru .cs a přidat do projektu, nastavte **zaregistrovat zprostředkovatel komunikace s objekty COM** vlastnost **True**.</span><span class="sxs-lookup"><span data-stu-id="cf92d-104">After this code has been placed in a .cs file and added to your project, set the **Register for COM Interop** property to **True**.</span></span> <span data-ttu-id="cf92d-105">Další informace najdete v tématu [NIB: postupy: zaregistrovat součásti zprostředkovatel komunikace s objekty COM](http://msdn.microsoft.com/library/4de7d474-56e8-4027-994d-d47ca4725c5e).</span><span class="sxs-lookup"><span data-stu-id="cf92d-105">For more information, see [NIB: How to: Register a Component for COM Interop](http://msdn.microsoft.com/library/4de7d474-56e8-4027-994d-d47ca4725c5e).</span></span>  
  
 <span data-ttu-id="cf92d-106">Vystavení objektů jazyka Visual C# do modelu COM vyžaduje deklarování třídy rozhraní, rozhraní události v případě potřeby a vlastní třídy.</span><span class="sxs-lookup"><span data-stu-id="cf92d-106">Exposing Visual C# objects to COM requires declaring a class interface, an events interface if it is required, and the class itself.</span></span> <span data-ttu-id="cf92d-107">Členy třídy nutné postupovat podle těchto pravidel být viditelné modelu COM:</span><span class="sxs-lookup"><span data-stu-id="cf92d-107">Class members must follow these rules to be visible to COM:</span></span>  
  
-   <span data-ttu-id="cf92d-108">Třída musí být veřejné.</span><span class="sxs-lookup"><span data-stu-id="cf92d-108">The class must be public.</span></span>  
  
-   <span data-ttu-id="cf92d-109">Vlastnosti, metod a události musí být veřejné.</span><span class="sxs-lookup"><span data-stu-id="cf92d-109">Properties, methods, and events must be public.</span></span>  
  
-   <span data-ttu-id="cf92d-110">Vlastnosti a metody musí být deklarován v rozhraní třídy.</span><span class="sxs-lookup"><span data-stu-id="cf92d-110">Properties and methods must be declared on the class interface.</span></span>  
  
-   <span data-ttu-id="cf92d-111">Události musí být deklarován události rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cf92d-111">Events must be declared in the event interface.</span></span>  
  
 <span data-ttu-id="cf92d-112">Jiné veřejné členy ve třídě, které nejsou deklarované v těchto rozhraní se nezobrazí COM, ale nebudou se viditelné pro jiné objekty rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cf92d-112">Other public members in the class that are not declared in these interfaces will not be visible to COM, but they will be visible to other .NET Framework objects.</span></span>  
  
 <span data-ttu-id="cf92d-113">Která zveřejňuje vlastnosti a metody do modelu COM, musí deklarovat je v rozhraní třídy a označit je s `DispId` atribut a jejich implementaci ve třídě.</span><span class="sxs-lookup"><span data-stu-id="cf92d-113">To expose properties and methods to COM, you must declare them on the class interface and mark them with a `DispId` attribute, and implement them in the class.</span></span> <span data-ttu-id="cf92d-114">Pořadí, ve které jsou deklarované členy v rozhraní je v pořadí, použít pro COM vtable.</span><span class="sxs-lookup"><span data-stu-id="cf92d-114">The order in which the members are declared in the interface is the order used for the COM vtable.</span></span>  
  
 <span data-ttu-id="cf92d-115">Ke zveřejnění události z vaší třídy, musí deklarovat je v rozhraní události a označit je pomocí `DispId` atribut.</span><span class="sxs-lookup"><span data-stu-id="cf92d-115">To expose events from your class, you must declare them on the events interface and mark them with a `DispId` attribute.</span></span> <span data-ttu-id="cf92d-116">Třída nesmí toto rozhraní implementovat.</span><span class="sxs-lookup"><span data-stu-id="cf92d-116">The class should not implement this interface.</span></span>  
  
 <span data-ttu-id="cf92d-117">Třída implementuje rozhraní třídy; ho můžete implementovat více než jedno rozhraní, ale bude první implementace rozhraní výchozí třídy.</span><span class="sxs-lookup"><span data-stu-id="cf92d-117">The class implements the class interface; it can implement more than one interface, but the first implementation will be the default class interface.</span></span> <span data-ttu-id="cf92d-118">Implementace metody a vlastnosti vystaven objektům modelu COM v tomto poli.</span><span class="sxs-lookup"><span data-stu-id="cf92d-118">Implement the methods and properties exposed to COM here.</span></span> <span data-ttu-id="cf92d-119">Tyto musí být označen a deklarace v rozhraní třídy se musí shodovat.</span><span class="sxs-lookup"><span data-stu-id="cf92d-119">They must be marked public and must match the declarations in the class interface.</span></span> <span data-ttu-id="cf92d-120">Události vyvolané třídou zde také deklarujte.</span><span class="sxs-lookup"><span data-stu-id="cf92d-120">Also, declare the events raised by the class here.</span></span> <span data-ttu-id="cf92d-121">Tyto musí být označen a deklarace v rozhraní události se musí shodovat.</span><span class="sxs-lookup"><span data-stu-id="cf92d-121">They must be marked public and must match the declarations in the events interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf92d-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="cf92d-122">Example</span></span>  
 [!code-csharp[csProgGuideInterop#8](../../../csharp/programming-guide/interop/codesnippet/CSharp/example-com-class_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="cf92d-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="cf92d-123">See Also</span></span>  
 [<span data-ttu-id="cf92d-124">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="cf92d-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="cf92d-125">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="cf92d-125">Interoperability</span></span>](../../../csharp/programming-guide/interop/index.md)  
 [<span data-ttu-id="cf92d-126">Stránka Sestavení, Návrhář projektu (C#)</span><span class="sxs-lookup"><span data-stu-id="cf92d-126">Build Page, Project Designer (C#)</span></span>](/visualstudio/ide/reference/build-page-project-designer-csharp)
