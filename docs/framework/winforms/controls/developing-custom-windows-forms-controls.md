---
title: Vývoj vlastních ovládacích prvků
description: Seznamte se s ovládacími prvky Windows Form. Konkrétně se naučíte kombinovat stávající ovládací prvky, roztáhnout existující ovládací prvky a vytvořit vlastní ovládací prvky.
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], developing using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 236cebc0-bd71-4f18-9fd6-5d0e592375df
ms.openlocfilehash: 12013496c9650489fdd7512206317000fc0ec78c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618373"
---
# <a name="developing-custom-windows-forms-controls-with-the-net-framework"></a><span data-ttu-id="bef4e-104">Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bef4e-104">Developing Custom Windows Forms Controls with the .NET Framework</span></span>
<span data-ttu-id="bef4e-105">Ovládací prvky model Windows Forms jsou opakovaně použitelné komponenty, které zapouzdřují funkce uživatelského rozhraní a používají se v aplikacích pro Windows na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="bef4e-105">Windows Forms controls are reusable components that encapsulate user interface functionality and are used in client-side Windows-based applications.</span></span> <span data-ttu-id="bef4e-106">Pouze model Windows Forms poskytuje mnoho ovládacích prvků připravených k použití, poskytuje také infrastrukturu pro vývoj vlastních ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="bef4e-106">Not only does Windows Forms provide many ready-to-use controls, it also provides the infrastructure for developing your own controls.</span></span> <span data-ttu-id="bef4e-107">Můžete zkombinovat existující ovládací prvky, roztáhnout stávající ovládací prvky nebo vytvořit vlastní ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="bef4e-107">You can combine existing controls, extend existing controls, or author your own custom controls.</span></span> <span data-ttu-id="bef4e-108">V této části najdete základní informace a ukázky, které vám pomůžou s vývojem model Windows Formsch ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="bef4e-108">This section provides background information and samples to help you develop Windows Forms controls.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bef4e-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="bef4e-109">In This Section</span></span>  
 [<span data-ttu-id="bef4e-110">Přehled používání ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bef4e-110">Overview of Using Controls in Windows Forms</span></span>](overview-of-using-controls-in-windows-forms.md)  
 <span data-ttu-id="bef4e-111">Zvýrazní základní prvky používání ovládacích prvků v aplikacích model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="bef4e-111">Highlights the essential elements of using controls in Windows Forms applications.</span></span>  
  
 [<span data-ttu-id="bef4e-112">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="bef4e-112">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)  
 <span data-ttu-id="bef4e-113">Popisuje různé druhy vlastních ovládacích prvků, které můžete vytvořit pomocí <xref:System.Windows.Forms?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="bef4e-113">Describes the different kinds of custom controls you can author with the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span>  
  
 [<span data-ttu-id="bef4e-114">Základní informace o vývoji ovládacích prvků Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bef4e-114">Windows Forms Control Development Basics</span></span>](windows-forms-control-development-basics.md)  
 <span data-ttu-id="bef4e-115">Popisuje první kroky při vývoji model Windows Formsho ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="bef4e-115">Discusses the first steps in developing a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="bef4e-116">Vlastnosti v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bef4e-116">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)  
 <span data-ttu-id="bef4e-117">Ukazuje, jak přidat do vlastností model Windows Forms ovládacími prvky.</span><span class="sxs-lookup"><span data-stu-id="bef4e-117">Shows how to add to properties to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="bef4e-118">Události v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bef4e-118">Events in Windows Forms Controls</span></span>](events-in-windows-forms-controls.md)  
 <span data-ttu-id="bef4e-119">Ukazuje, jak zpracovávat a definovat události v ovládacích prvcích model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="bef4e-119">Shows how to handle and define events in Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="bef4e-120">Atributy v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bef4e-120">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)  
 <span data-ttu-id="bef4e-121">Popisuje atributy, které lze použít pro vlastnosti nebo jiné členy vašich vlastních ovládacích prvků a komponent.</span><span class="sxs-lookup"><span data-stu-id="bef4e-121">Describes the attributes you can apply to properties or other members of your custom controls and components.</span></span>  
  
 [<span data-ttu-id="bef4e-122">Malování a vykreslování vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="bef4e-122">Custom Control Painting and Rendering</span></span>](custom-control-painting-and-rendering.md)  
 <span data-ttu-id="bef4e-123">Ukazuje, jak přizpůsobit vzhled ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="bef4e-123">Shows how to customize the appearance of your controls.</span></span>  
  
 [<span data-ttu-id="bef4e-124">Rozložení v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bef4e-124">Layout in Windows Forms Controls</span></span>](layout-in-windows-forms-controls.md)  
 <span data-ttu-id="bef4e-125">Ukazuje, jak vytvořit sofistikovaná rozložení pro ovládací prvky a formuláře.</span><span class="sxs-lookup"><span data-stu-id="bef4e-125">Shows how to create sophisticated layouts for your controls and forms.</span></span>  
  
 [<span data-ttu-id="bef4e-126">Multithreading v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bef4e-126">Multithreading in Windows Forms Controls</span></span>](multithreading-in-windows-forms-controls.md)  
 <span data-ttu-id="bef4e-127">Ukazuje, jak implementovat ovládací prvky s více vlákny.</span><span class="sxs-lookup"><span data-stu-id="bef4e-127">Shows how to implement multithreaded controls.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="bef4e-128">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="bef4e-128">Reference</span></span>  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 <span data-ttu-id="bef4e-129">Popisuje tuto třídu a má odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="bef4e-129">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 <span data-ttu-id="bef4e-130">Popisuje tuto třídu a má odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="bef4e-130">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bef4e-131">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="bef4e-131">Related Sections</span></span>  
 <span data-ttu-id="bef4e-132">[Atributy pro dobu návrhu pro součásti](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="bef4e-132">[Design-Time Attributes for Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))</span></span>  
 <span data-ttu-id="bef4e-133">Seznam atributů metadat, které se mají použít u komponent a ovládacích prvků tak, aby se v době návrhu v vizuálních návrhářích zobrazovaly správně.</span><span class="sxs-lookup"><span data-stu-id="bef4e-133">Lists metadata attributes to apply to components and controls so that they are displayed correctly at design time in visual designers.</span></span>  
  
 <span data-ttu-id="bef4e-134">[Rozšíření podpory během návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="bef4e-134">[Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span></span>  
 <span data-ttu-id="bef4e-135">Popisuje, jak implementovat třídy, jako jsou editory a návrháři, které poskytují podporu při návrhu.</span><span class="sxs-lookup"><span data-stu-id="bef4e-135">Describes how to implement classes such as editors and designers that provide design-time support.</span></span>  
  
 <span data-ttu-id="bef4e-136">[Postupy: Licencování komponent a ovládacích prvků](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="bef4e-136">[How to: License Components and Controls](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120))</span></span>  
 <span data-ttu-id="bef4e-137">Popisuje, jak implementovat licencování ve vašem ovládacím prvku nebo komponentě.</span><span class="sxs-lookup"><span data-stu-id="bef4e-137">Describes how to implement licensing in your control or component.</span></span>  
  
 <span data-ttu-id="bef4e-138">Viz také [vývoj model Windows Formsch ovládacích prvků v době návrhu](developing-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="bef4e-138">Also see [Developing Windows Forms Controls at Design Time](developing-windows-forms-controls-at-design-time.md).</span></span>
