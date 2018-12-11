---
title: Ukázka třídy COM - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
ms.openlocfilehash: b2e9e94f75b048dbe4ce3430c7a590f9be156e1d
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242481"
---
# <a name="example-com-class-c-programming-guide"></a><span data-ttu-id="78a13-102">Ukázka třídy COM (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="78a13-102">Example COM Class (C# Programming Guide)</span></span>
<span data-ttu-id="78a13-103">Následuje příklad třídy, která by vystavit jako objekt modelu COM.</span><span class="sxs-lookup"><span data-stu-id="78a13-103">The following is an example of a class that you would expose as a COM object.</span></span> <span data-ttu-id="78a13-104">Poté, co tento kód byl umístěn v souboru .cs a přidány do projektu, nastavte **zaregistrovat pro interoperabilitu COM** vlastnost **True**.</span><span class="sxs-lookup"><span data-stu-id="78a13-104">After this code has been placed in a .cs file and added to your project, set the **Register for COM Interop** property to **True**.</span></span> <span data-ttu-id="78a13-105">Další informace najdete v tématu [jak: Zaregistrovat pro interoperabilitu COM komponentu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="78a13-105">For more information, see [How to: Register a Component for COM Interop](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).</span></span>
  
 <span data-ttu-id="78a13-106">Vystavení objektů jazyka Visual C# do modelu COM vyžaduje deklarace třídy rozhraní, pokud se vyžaduje rozhraní události a vlastní třídy.</span><span class="sxs-lookup"><span data-stu-id="78a13-106">Exposing Visual C# objects to COM requires declaring a class interface, an events interface if it is required, and the class itself.</span></span> <span data-ttu-id="78a13-107">Členy třídy musí dodržovat tato pravidla být viditelné modelu COM:</span><span class="sxs-lookup"><span data-stu-id="78a13-107">Class members must follow these rules to be visible to COM:</span></span>  
  
-   <span data-ttu-id="78a13-108">Třída musí být veřejné.</span><span class="sxs-lookup"><span data-stu-id="78a13-108">The class must be public.</span></span>  
  
-   <span data-ttu-id="78a13-109">Vlastnosti, metody a události musí být veřejné.</span><span class="sxs-lookup"><span data-stu-id="78a13-109">Properties, methods, and events must be public.</span></span>  
  
-   <span data-ttu-id="78a13-110">Vlastnosti a metody musí být deklarována v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="78a13-110">Properties and methods must be declared on the class interface.</span></span>  
  
-   <span data-ttu-id="78a13-111">Události musí být deklarována v události rozhraní.</span><span class="sxs-lookup"><span data-stu-id="78a13-111">Events must be declared in the event interface.</span></span>  
  
 <span data-ttu-id="78a13-112">Jiné veřejné členy, které nejsou deklarovány v těchto rozhraní ve třídě nesmí být viditelné modelu COM, ale budou viditelné pro ostatní objekty rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="78a13-112">Other public members in the class that are not declared in these interfaces will not be visible to COM, but they will be visible to other .NET Framework objects.</span></span>  
  
 <span data-ttu-id="78a13-113">Vystavit vlastnosti a metody rozhraní COM, musí deklarovat na třídy rozhraní a označte je pomocí `DispId` atribut a je implementovat ve třídě.</span><span class="sxs-lookup"><span data-stu-id="78a13-113">To expose properties and methods to COM, you must declare them on the class interface and mark them with a `DispId` attribute, and implement them in the class.</span></span> <span data-ttu-id="78a13-114">Pořadí, ve kterém jsou členy deklarované v rozhraní je v tom pořadí, používá pro COM vtable.</span><span class="sxs-lookup"><span data-stu-id="78a13-114">The order in which the members are declared in the interface is the order used for the COM vtable.</span></span>  
  
 <span data-ttu-id="78a13-115">K vystavení události z vaší třídy, musí deklarovat v rozhraní události a označit je pomocí `DispId` atribut.</span><span class="sxs-lookup"><span data-stu-id="78a13-115">To expose events from your class, you must declare them on the events interface and mark them with a `DispId` attribute.</span></span> <span data-ttu-id="78a13-116">Třída by neměla implementovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="78a13-116">The class should not implement this interface.</span></span>  
  
 <span data-ttu-id="78a13-117">Třída implementuje rozhraní třídy; To může implementovat více než jedno rozhraní, ale první implementace bude výchozí třída rozhraní.</span><span class="sxs-lookup"><span data-stu-id="78a13-117">The class implements the class interface; it can implement more than one interface, but the first implementation will be the default class interface.</span></span> <span data-ttu-id="78a13-118">Implementace metody a vlastnosti vystavit rozhraní COM tady.</span><span class="sxs-lookup"><span data-stu-id="78a13-118">Implement the methods and properties exposed to COM here.</span></span> <span data-ttu-id="78a13-119">Musí být označena jako veřejná a musí odpovídat deklarace třídy rozhraní.</span><span class="sxs-lookup"><span data-stu-id="78a13-119">They must be marked public and must match the declarations in the class interface.</span></span> <span data-ttu-id="78a13-120">Také deklarujte události vyvolané službou třída tady.</span><span class="sxs-lookup"><span data-stu-id="78a13-120">Also, declare the events raised by the class here.</span></span> <span data-ttu-id="78a13-121">Musí být označena jako veřejná a musí odpovídat deklarace události rozhraní.</span><span class="sxs-lookup"><span data-stu-id="78a13-121">They must be marked public and must match the declarations in the events interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78a13-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="78a13-122">Example</span></span>  
 [!code-csharp[csProgGuideInterop#8](../../../csharp/programming-guide/interop/codesnippet/CSharp/example-com-class_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="78a13-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="78a13-123">See Also</span></span>

- [<span data-ttu-id="78a13-124">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="78a13-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="78a13-125">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="78a13-125">Interoperability</span></span>](../../../csharp/programming-guide/interop/index.md)  
- [<span data-ttu-id="78a13-126">Stránka Sestavení, Návrhář projektu (C#)</span><span class="sxs-lookup"><span data-stu-id="78a13-126">Build Page, Project Designer (C#)</span></span>](/visualstudio/ide/reference/build-page-project-designer-csharp)
