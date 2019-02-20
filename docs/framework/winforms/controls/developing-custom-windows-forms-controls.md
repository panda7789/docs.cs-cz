---
title: Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], developing using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 236cebc0-bd71-4f18-9fd6-5d0e592375df
ms.openlocfilehash: 427a865bc9550fe489d1a1f22ea4a07b421de1fe
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2019
ms.locfileid: "56442708"
---
# <a name="developing-custom-windows-forms-controls-with-the-net-framework"></a><span data-ttu-id="a7a1a-102">Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a7a1a-102">Developing Custom Windows Forms Controls with the .NET Framework</span></span>
<span data-ttu-id="a7a1a-103">Ovládací prvky Windows Forms jsou opakovaně použitelné komponenty, které zapouzdřují funkce uživatelského rozhraní a se používají v aplikacích založených na Windows na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="a7a1a-103">Windows Forms controls are reusable components that encapsulate user interface functionality and are used in client-side Windows-based applications.</span></span> <span data-ttu-id="a7a1a-104">Nejen Windows Forms poskytuje mnoho ovládacích prvků připravené k použití, navíc poskytuje infrastrukturu pro vývoj vlastních ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="a7a1a-104">Not only does Windows Forms provide many ready-to-use controls, it also provides the infrastructure for developing your own controls.</span></span> <span data-ttu-id="a7a1a-105">Můžete kombinovat existující ovládací prvky, rozšířit existující ovládací prvky nebo vytvořit vlastní ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="a7a1a-105">You can combine existing controls, extend existing controls, or author your own custom controls.</span></span> <span data-ttu-id="a7a1a-106">Tato část obsahuje základní informace a ukázky, které vám pomůžou s vývojem ovládacích prvků Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a7a1a-106">This section provides background information and samples to help you develop Windows Forms controls.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a7a1a-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a7a1a-107">In This Section</span></span>  
 [<span data-ttu-id="a7a1a-108">Přehled používání ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a7a1a-108">Overview of Using Controls in Windows Forms</span></span>](../../../../docs/framework/winforms/controls/overview-of-using-controls-in-windows-forms.md)  
 <span data-ttu-id="a7a1a-109">Popisuje základní prvky pomocí ovládacích prvků v aplikacích Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a7a1a-109">Highlights the essential elements of using controls in Windows Forms applications.</span></span>  
  
 [<span data-ttu-id="a7a1a-110">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="a7a1a-110">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 <span data-ttu-id="a7a1a-111">Popisuje různé druhy můžete vytvořit pomocí vlastních ovládacích prvků <xref:System.Windows.Forms?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a7a1a-111">Describes the different kinds of custom controls you can author with the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span>  
  
 [<span data-ttu-id="a7a1a-112">Základní informace o vývoji ovládacích prvků Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a7a1a-112">Windows Forms Control Development Basics</span></span>](../../../../docs/framework/winforms/controls/windows-forms-control-development-basics.md)  
 <span data-ttu-id="a7a1a-113">Tento článek popisuje první kroky ve vývoji ovládacího prvku Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a7a1a-113">Discusses the first steps in developing a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="a7a1a-114">Vlastnosti v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a7a1a-114">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 <span data-ttu-id="a7a1a-115">Ukazuje, jak přidat do vlastností ovládacích prvků Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a7a1a-115">Shows how to add to properties to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="a7a1a-116">Události v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a7a1a-116">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 <span data-ttu-id="a7a1a-117">Ukazuje, jak zpracovat a definovat události v ovládacích prvcích Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a7a1a-117">Shows how to handle and define events in Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="a7a1a-118">Atributy v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a7a1a-118">Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 <span data-ttu-id="a7a1a-119">Popisuje atributy, které můžete provést u vlastnosti nebo další členové vaší vlastní ovládací prvky a součásti.</span><span class="sxs-lookup"><span data-stu-id="a7a1a-119">Describes the attributes you can apply to properties or other members of your custom controls and components.</span></span>  
  
 [<span data-ttu-id="a7a1a-120">Malování a vykreslování vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="a7a1a-120">Custom Control Painting and Rendering</span></span>](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)  
 <span data-ttu-id="a7a1a-121">Ukazuje, jak přizpůsobit vzhled ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="a7a1a-121">Shows how to customize the appearance of your controls.</span></span>  
  
 [<span data-ttu-id="a7a1a-122">Rozložení v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a7a1a-122">Layout in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/layout-in-windows-forms-controls.md)  
 <span data-ttu-id="a7a1a-123">Ukazuje, jak vytvářet sofistikované rozložení pro ovládací prvky a formuláře.</span><span class="sxs-lookup"><span data-stu-id="a7a1a-123">Shows how to create sophisticated layouts for your controls and forms.</span></span>  
  
 [<span data-ttu-id="a7a1a-124">Multithreading v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a7a1a-124">Multithreading in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/multithreading-in-windows-forms-controls.md)  
 <span data-ttu-id="a7a1a-125">Ukazuje, jak implementovat ovládací prvky s více vlákny.</span><span class="sxs-lookup"><span data-stu-id="a7a1a-125">Shows how to implement multithreaded controls.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a7a1a-126">Odkaz</span><span class="sxs-lookup"><span data-stu-id="a7a1a-126">Reference</span></span>  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 <span data-ttu-id="a7a1a-127">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="a7a1a-127">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 <span data-ttu-id="a7a1a-128">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="a7a1a-128">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a7a1a-129">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="a7a1a-129">Related Sections</span></span>  
 <span data-ttu-id="a7a1a-130">[Atributy doby návrhu pro komponenty](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="a7a1a-130">[Design-Time Attributes for Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))</span></span>  
 <span data-ttu-id="a7a1a-131">Obsahuje seznam atributy metadat použít na komponent a ovládacích prvků tak, aby se správně zobrazí v době návrhu v vizuální návrhářské nástroje.</span><span class="sxs-lookup"><span data-stu-id="a7a1a-131">Lists metadata attributes to apply to components and controls so that they are displayed correctly at design time in visual designers.</span></span>  
  
 <span data-ttu-id="a7a1a-132">[Rozšíření podpory během návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="a7a1a-132">[Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span></span>  
 <span data-ttu-id="a7a1a-133">Popisuje, jak implementovat třídy například editorů a návrhářů, které poskytují podpory během návrhu.</span><span class="sxs-lookup"><span data-stu-id="a7a1a-133">Describes how to implement classes such as editors and designers that provide design-time support.</span></span>  
  
 <span data-ttu-id="a7a1a-134">[Postupy: Licence komponent a ovládacích prvků](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="a7a1a-134">[How to: License Components and Controls](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120))</span></span>  
 <span data-ttu-id="a7a1a-135">Popisuje, jak implementovat licencování ovládacího prvku nebo komponenty.</span><span class="sxs-lookup"><span data-stu-id="a7a1a-135">Describes how to implement licensing in your control or component.</span></span>  
  
 <span data-ttu-id="a7a1a-136">Viz také [vývoj prvky Windows Forms v době návrhu](developing-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="a7a1a-136">Also see [Developing Windows Forms Controls at Design Time](developing-windows-forms-controls-at-design-time.md).</span></span>
