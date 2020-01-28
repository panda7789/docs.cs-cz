---
title: Vývoj vlastních ovládacích prvků
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], developing using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 236cebc0-bd71-4f18-9fd6-5d0e592375df
ms.openlocfilehash: 9dbc1c4530b3a0f4e579ca67c7ae88c1685222ea
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745995"
---
# <a name="developing-custom-windows-forms-controls-with-the-net-framework"></a><span data-ttu-id="9d582-102">Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9d582-102">Developing Custom Windows Forms Controls with the .NET Framework</span></span>
<span data-ttu-id="9d582-103">Ovládací prvky model Windows Forms jsou opakovaně použitelné komponenty, které zapouzdřují funkce uživatelského rozhraní a používají se v aplikacích pro Windows na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="9d582-103">Windows Forms controls are reusable components that encapsulate user interface functionality and are used in client-side Windows-based applications.</span></span> <span data-ttu-id="9d582-104">Pouze model Windows Forms poskytuje mnoho ovládacích prvků připravených k použití, poskytuje také infrastrukturu pro vývoj vlastních ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="9d582-104">Not only does Windows Forms provide many ready-to-use controls, it also provides the infrastructure for developing your own controls.</span></span> <span data-ttu-id="9d582-105">Můžete zkombinovat existující ovládací prvky, roztáhnout stávající ovládací prvky nebo vytvořit vlastní ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="9d582-105">You can combine existing controls, extend existing controls, or author your own custom controls.</span></span> <span data-ttu-id="9d582-106">V této části najdete základní informace a ukázky, které vám pomůžou s vývojem model Windows Formsch ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="9d582-106">This section provides background information and samples to help you develop Windows Forms controls.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9d582-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="9d582-107">In This Section</span></span>  
 [<span data-ttu-id="9d582-108">Přehled používání ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9d582-108">Overview of Using Controls in Windows Forms</span></span>](overview-of-using-controls-in-windows-forms.md)  
 <span data-ttu-id="9d582-109">Zvýrazní základní prvky používání ovládacích prvků v aplikacích model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="9d582-109">Highlights the essential elements of using controls in Windows Forms applications.</span></span>  
  
 [<span data-ttu-id="9d582-110">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="9d582-110">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)  
 <span data-ttu-id="9d582-111">Popisuje různé druhy vlastních ovládacích prvků, které můžete vytvořit pomocí oboru názvů <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9d582-111">Describes the different kinds of custom controls you can author with the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span>  
  
 [<span data-ttu-id="9d582-112">Základní informace o vývoji ovládacích prvků Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9d582-112">Windows Forms Control Development Basics</span></span>](windows-forms-control-development-basics.md)  
 <span data-ttu-id="9d582-113">Popisuje první kroky při vývoji model Windows Formsho ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9d582-113">Discusses the first steps in developing a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="9d582-114">Vlastnosti v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9d582-114">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)  
 <span data-ttu-id="9d582-115">Ukazuje, jak přidat do vlastností model Windows Forms ovládacími prvky.</span><span class="sxs-lookup"><span data-stu-id="9d582-115">Shows how to add to properties to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="9d582-116">Události v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9d582-116">Events in Windows Forms Controls</span></span>](events-in-windows-forms-controls.md)  
 <span data-ttu-id="9d582-117">Ukazuje, jak zpracovávat a definovat události v ovládacích prvcích model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="9d582-117">Shows how to handle and define events in Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="9d582-118">Atributy v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9d582-118">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)  
 <span data-ttu-id="9d582-119">Popisuje atributy, které lze použít pro vlastnosti nebo jiné členy vašich vlastních ovládacích prvků a komponent.</span><span class="sxs-lookup"><span data-stu-id="9d582-119">Describes the attributes you can apply to properties or other members of your custom controls and components.</span></span>  
  
 [<span data-ttu-id="9d582-120">Malování a vykreslování vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="9d582-120">Custom Control Painting and Rendering</span></span>](custom-control-painting-and-rendering.md)  
 <span data-ttu-id="9d582-121">Ukazuje, jak přizpůsobit vzhled ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="9d582-121">Shows how to customize the appearance of your controls.</span></span>  
  
 [<span data-ttu-id="9d582-122">Rozložení v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9d582-122">Layout in Windows Forms Controls</span></span>](layout-in-windows-forms-controls.md)  
 <span data-ttu-id="9d582-123">Ukazuje, jak vytvořit sofistikovaná rozložení pro ovládací prvky a formuláře.</span><span class="sxs-lookup"><span data-stu-id="9d582-123">Shows how to create sophisticated layouts for your controls and forms.</span></span>  
  
 [<span data-ttu-id="9d582-124">Multithreading v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9d582-124">Multithreading in Windows Forms Controls</span></span>](multithreading-in-windows-forms-controls.md)  
 <span data-ttu-id="9d582-125">Ukazuje, jak implementovat ovládací prvky s více vlákny.</span><span class="sxs-lookup"><span data-stu-id="9d582-125">Shows how to implement multithreaded controls.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9d582-126">Odkaz</span><span class="sxs-lookup"><span data-stu-id="9d582-126">Reference</span></span>  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 <span data-ttu-id="9d582-127">Popisuje tuto třídu a má odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="9d582-127">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 <span data-ttu-id="9d582-128">Popisuje tuto třídu a má odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="9d582-128">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9d582-129">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="9d582-129">Related Sections</span></span>  
 <span data-ttu-id="9d582-130">[Atributy pro dobu návrhu pro součásti](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="9d582-130">[Design-Time Attributes for Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))</span></span>  
 <span data-ttu-id="9d582-131">Seznam atributů metadat, které se mají použít u komponent a ovládacích prvků tak, aby se v době návrhu v vizuálních návrhářích zobrazovaly správně.</span><span class="sxs-lookup"><span data-stu-id="9d582-131">Lists metadata attributes to apply to components and controls so that they are displayed correctly at design time in visual designers.</span></span>  
  
 <span data-ttu-id="9d582-132">[Rozšíření podpory pro dobu návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="9d582-132">[Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span></span>  
 <span data-ttu-id="9d582-133">Popisuje, jak implementovat třídy, jako jsou editory a návrháři, které poskytují podporu při návrhu.</span><span class="sxs-lookup"><span data-stu-id="9d582-133">Describes how to implement classes such as editors and designers that provide design-time support.</span></span>  
  
 <span data-ttu-id="9d582-134">[Postupy: licenční komponenty a ovládací prvky](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="9d582-134">[How to: License Components and Controls](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120))</span></span>  
 <span data-ttu-id="9d582-135">Popisuje, jak implementovat licencování ve vašem ovládacím prvku nebo komponentě.</span><span class="sxs-lookup"><span data-stu-id="9d582-135">Describes how to implement licensing in your control or component.</span></span>  
  
 <span data-ttu-id="9d582-136">Viz také [vývoj model Windows Formsch ovládacích prvků v době návrhu](developing-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="9d582-136">Also see [Developing Windows Forms Controls at Design Time](developing-windows-forms-controls-at-design-time.md).</span></span>
