---
title: "Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], developing using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 236cebc0-bd71-4f18-9fd6-5d0e592375df
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 89be7e347556c8ec34296044f17fbfd4450bc127
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="developing-custom-windows-forms-controls-with-the-net-framework"></a><span data-ttu-id="7ee6b-102">Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7ee6b-102">Developing Custom Windows Forms Controls with the .NET Framework</span></span>
<span data-ttu-id="7ee6b-103">Windows Forms – ovládací prvky jsou opakovaně použitelné součásti, které zapouzdřují uživatelské rozhraní funkce a se používají v aplikacích založených na systému Windows na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="7ee6b-103">Windows Forms controls are reusable components that encapsulate user interface functionality and are used in client-side Windows-based applications.</span></span> <span data-ttu-id="7ee6b-104">Jenom Windows Forms poskytuje mnoho připravené k použití ovládacích prvků, navíc poskytuje infrastrukturu pro vývoj vlastních ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="7ee6b-104">Not only does Windows Forms provide many ready-to-use controls, it also provides the infrastructure for developing your own controls.</span></span> <span data-ttu-id="7ee6b-105">Můžete kombinovat stávající ovládací prvky, rozšířit stávající ovládací prvky nebo vytvořit vlastní ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="7ee6b-105">You can combine existing controls, extend existing controls, or author your own custom controls.</span></span> <span data-ttu-id="7ee6b-106">Tato část obsahuje základní informace a ukázky k rozvoji ovládací prvky Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7ee6b-106">This section provides background information and samples to help you develop Windows Forms controls.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7ee6b-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="7ee6b-107">In This Section</span></span>  
 [<span data-ttu-id="7ee6b-108">Přehled používání ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7ee6b-108">Overview of Using Controls in Windows Forms</span></span>](../../../../docs/framework/winforms/controls/overview-of-using-controls-in-windows-forms.md)  
 <span data-ttu-id="7ee6b-109">Označuje základní prvky používání ovládacích prvků v aplikacích Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7ee6b-109">Highlights the essential elements of using controls in Windows Forms applications.</span></span>  
  
 [<span data-ttu-id="7ee6b-110">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="7ee6b-110">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 <span data-ttu-id="7ee6b-111">Popisuje různé druhy vlastní ovládací prvky můžete vytvořit pomocí <xref:System.Windows.Forms?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7ee6b-111">Describes the different kinds of custom controls you can author with the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span>  
  
 [<span data-ttu-id="7ee6b-112">Základy vývoj ovládacího prvku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7ee6b-112">Windows Forms Control Development Basics</span></span>](../../../../docs/framework/winforms/controls/windows-forms-control-development-basics.md)  
 <span data-ttu-id="7ee6b-113">Popisuje je prvním krokem při vývoji ovládacího prvku Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7ee6b-113">Discusses the first steps in developing a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="7ee6b-114">Vlastnosti v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7ee6b-114">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 <span data-ttu-id="7ee6b-115">Ukazuje, jak přidat do vlastností ovládacích prvků Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7ee6b-115">Shows how to add to properties to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="7ee6b-116">Události v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7ee6b-116">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 <span data-ttu-id="7ee6b-117">Ukazuje, jak zpracovat a definování události v ovládacích prvcích Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7ee6b-117">Shows how to handle and define events in Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="7ee6b-118">Atributy v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7ee6b-118">Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 <span data-ttu-id="7ee6b-119">Popisuje atributy, které můžete provést u vlastnosti nebo jinými členy vlastní ovládací prvky a součásti.</span><span class="sxs-lookup"><span data-stu-id="7ee6b-119">Describes the attributes you can apply to properties or other members of your custom controls and components.</span></span>  
  
 [<span data-ttu-id="7ee6b-120">Vlastní ovládací prvek Malování a vykreslování</span><span class="sxs-lookup"><span data-stu-id="7ee6b-120">Custom Control Painting and Rendering</span></span>](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)  
 <span data-ttu-id="7ee6b-121">Ukazuje, jak přizpůsobit vzhled pro vaše ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="7ee6b-121">Shows how to customize the appearance of your controls.</span></span>  
  
 [<span data-ttu-id="7ee6b-122">Rozložení v systému Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="7ee6b-122">Layout in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/layout-in-windows-forms-controls.md)  
 <span data-ttu-id="7ee6b-123">Ukazuje, jak vytvořit sofistikované rozložení pro ovládací prvky a formuláře.</span><span class="sxs-lookup"><span data-stu-id="7ee6b-123">Shows how to create sophisticated layouts for your controls and forms.</span></span>  
  
 [<span data-ttu-id="7ee6b-124">Více vláken v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7ee6b-124">Multithreading in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/multithreading-in-windows-forms-controls.md)  
 <span data-ttu-id="7ee6b-125">Ukazuje, jak implementovat kontroly, s více vlákny.</span><span class="sxs-lookup"><span data-stu-id="7ee6b-125">Shows how to implement multithreaded controls.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7ee6b-126">Odkaz</span><span class="sxs-lookup"><span data-stu-id="7ee6b-126">Reference</span></span>  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 <span data-ttu-id="7ee6b-127">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="7ee6b-127">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 <span data-ttu-id="7ee6b-128">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="7ee6b-128">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7ee6b-129">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="7ee6b-129">Related Sections</span></span>  
 [<span data-ttu-id="7ee6b-130">Atributy doby návrhu pro součásti</span><span class="sxs-lookup"><span data-stu-id="7ee6b-130">Design-Time Attributes for Components</span></span>](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3)  
 <span data-ttu-id="7ee6b-131">Seznam atributů metadata pro použití komponent a ovládacích prvků tak, aby se zobrazí správně v době návrhu v Návrháři visual.</span><span class="sxs-lookup"><span data-stu-id="7ee6b-131">Lists metadata attributes to apply to components and controls so that they are displayed correctly at design time in visual designers.</span></span>  
  
 [<span data-ttu-id="7ee6b-132">Rozšíření podpory návrhu</span><span class="sxs-lookup"><span data-stu-id="7ee6b-132">Extending Design-Time Support</span></span>](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 <span data-ttu-id="7ee6b-133">Popisuje, jak k implementaci třídy, jako je editory a návrhářů, které podporují návrhu.</span><span class="sxs-lookup"><span data-stu-id="7ee6b-133">Describes how to implement classes such as editors and designers that provide design-time support.</span></span>  
  
 [<span data-ttu-id="7ee6b-134">Postupy: licence komponenty a ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="7ee6b-134">How to: License Components and Controls</span></span>](http://msdn.microsoft.com/library/8e66c1ed-a445-4b26-8185-990b6e2bbd57)  
 <span data-ttu-id="7ee6b-135">Popisuje, jak implementovat licencování v komponenta nebo ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="7ee6b-135">Describes how to implement licensing in your control or component.</span></span>  
  
 <span data-ttu-id="7ee6b-136">Viz také [vývoj ovládacích prvků Windows Forms v době návrhu](http://msdn.microsoft.com/library/w29y3h59\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="7ee6b-136">Also see [Developing Windows Forms Controls at Design Time](http://msdn.microsoft.com/library/w29y3h59\(v=vs.110\)).</span></span>
