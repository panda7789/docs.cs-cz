---
title: "Vlastnosti v ovládacích prvcích Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], properties overview (using code)
- controls [Windows Forms], properties
- properties [Windows Forms]
ms.assetid: 2785279b-fb57-4937-8f6b-2050e475db6f
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8d645a321319bf54ca0cc4f142c343420eb1f30e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="properties-in-windows-forms-controls"></a><span data-ttu-id="e86ea-102">Vlastnosti v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e86ea-102">Properties in Windows Forms Controls</span></span>
<span data-ttu-id="e86ea-103">Ovládacího prvku Windows Forms základní třídy dědí mnoho vlastností formuláře <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e86ea-103">A Windows Forms control inherits many properties form the base class <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e86ea-104">Patří mezi ně vlastnosti, jako <xref:System.Windows.Forms.Control.Font%2A>, <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Bounds%2A>, <xref:System.Windows.Forms.Control.ClientRectangle%2A>, <xref:System.Windows.Forms.Control.DisplayRectangle%2A>, <xref:System.Windows.Forms.Control.Enabled%2A>, <xref:System.Windows.Forms.Control.Focused%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, <xref:System.Windows.Forms.Control.Visible%2A>, <xref:System.Windows.Forms.Control.AutoSize%2A>a mnohé další.</span><span class="sxs-lookup"><span data-stu-id="e86ea-104">These include properties such as <xref:System.Windows.Forms.Control.Font%2A>, <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Bounds%2A>, <xref:System.Windows.Forms.Control.ClientRectangle%2A>, <xref:System.Windows.Forms.Control.DisplayRectangle%2A>, <xref:System.Windows.Forms.Control.Enabled%2A>, <xref:System.Windows.Forms.Control.Focused%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, <xref:System.Windows.Forms.Control.Visible%2A>, <xref:System.Windows.Forms.Control.AutoSize%2A>, and many others.</span></span> <span data-ttu-id="e86ea-105">Podrobnosti o zděděné vlastnosti najdete v tématu <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e86ea-105">For details about inherited properties, see <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="e86ea-106">Vám může potlačení zděděné vlastnosti v vlastního ovládacího prvku, stejně jako definovat nové vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e86ea-106">You can override inherited properties in your control as well as define new properties.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e86ea-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="e86ea-107">In This Section</span></span>  
 [<span data-ttu-id="e86ea-108">Definování vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e86ea-108">Defining a Property</span></span>](../../../../docs/framework/winforms/controls/defining-a-property-in-windows-forms-controls.md)  
 <span data-ttu-id="e86ea-109">Ukazuje, jak implementovat vlastnost pro vlastní ovládací prvek nebo součást a ukazuje, jak integrovat vlastnost do prostředí návrhu.</span><span class="sxs-lookup"><span data-stu-id="e86ea-109">Shows how to implement a property for a custom control or component and shows how to integrate the property into the design environment.</span></span>  
  
 [<span data-ttu-id="e86ea-110">Definování výchozích hodnot pomocí metod ShouldSerialize a Reset</span><span class="sxs-lookup"><span data-stu-id="e86ea-110">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>](../../../../docs/framework/winforms/controls/defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 <span data-ttu-id="e86ea-111">Ukazuje, jak definovat výchozí hodnoty vlastností pro vlastní ovládací prvek nebo součást.</span><span class="sxs-lookup"><span data-stu-id="e86ea-111">Shows how to define default property values for a custom control or component.</span></span>  
  
 [<span data-ttu-id="e86ea-112">Události změny vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e86ea-112">Property-Changed Events</span></span>](../../../../docs/framework/winforms/controls/property-changed-events.md)  
 <span data-ttu-id="e86ea-113">Popisuje, jak povolit změnu vlastnosti oznámení při změně hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e86ea-113">Describes how to enable property-change notifications when a property value changes.</span></span>  
  
 [<span data-ttu-id="e86ea-114">Postupy: Vystavení vlastností základních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="e86ea-114">How to: Expose Properties of Constituent Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md)  
 <span data-ttu-id="e86ea-115">Ukazuje, jak vystavení vlastností základních ovládacích prvků v vlastní složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e86ea-115">Shows how to expose properties of constituent controls in a custom composite control.</span></span>  
  
 [<span data-ttu-id="e86ea-116">Implementace metody ve vlastních ovládacích prvcích</span><span class="sxs-lookup"><span data-stu-id="e86ea-116">Method Implementation in Custom Controls</span></span>](../../../../docs/framework/winforms/controls/method-implementation-in-custom-controls.md)  
 <span data-ttu-id="e86ea-117">Popisuje, jak implementovat metody ve vlastních ovládacích prvků a komponent.</span><span class="sxs-lookup"><span data-stu-id="e86ea-117">Describes how to implement methods in custom controls and components.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e86ea-118">Odkaz</span><span class="sxs-lookup"><span data-stu-id="e86ea-118">Reference</span></span>  
 <xref:System.Windows.Forms.UserControl>  
 <span data-ttu-id="e86ea-119">Dokumenty základní třídu pro implementaci složených ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="e86ea-119">Documents the base class for implementing composite controls.</span></span>  
  
 <xref:System.ComponentModel.TypeConverterAttribute>  
 <span data-ttu-id="e86ea-120">Dokumenty atribut, který určuje <xref:System.ComponentModel.TypeConverter> pro typ vlastní vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e86ea-120">Documents the attribute that specifies the <xref:System.ComponentModel.TypeConverter> to use for a custom property type.</span></span>  
  
 <xref:System.ComponentModel.EditorAttribute>  
 <span data-ttu-id="e86ea-121">Atribut, který určuje dokumentů <xref:System.Drawing.Design.UITypeEditor> pro vlastní vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e86ea-121">Documents the attribute that specifies the <xref:System.Drawing.Design.UITypeEditor> to use for a custom property.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e86ea-122">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="e86ea-122">Related Sections</span></span>  
 [<span data-ttu-id="e86ea-123">Atributy v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e86ea-123">Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 <span data-ttu-id="e86ea-124">Popisuje atributy, které můžete provést u vlastnosti nebo jinými členy vlastní ovládací prvky a součásti.</span><span class="sxs-lookup"><span data-stu-id="e86ea-124">Describes the attributes you can apply to properties or other members of your custom controls and components.</span></span>  
  
 [<span data-ttu-id="e86ea-125">Atributy doby návrhu pro součásti</span><span class="sxs-lookup"><span data-stu-id="e86ea-125">Design-Time Attributes for Components</span></span>](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3)  
 <span data-ttu-id="e86ea-126">Seznam atributů metadata pro použití komponent a ovládacích prvků tak, aby se zobrazí správně v době návrhu v Návrháři visual.</span><span class="sxs-lookup"><span data-stu-id="e86ea-126">Lists metadata attributes to apply to components and controls so that they are displayed correctly at design time in visual designers.</span></span>  
  
 [<span data-ttu-id="e86ea-127">Rozšíření podpory návrhu</span><span class="sxs-lookup"><span data-stu-id="e86ea-127">Extending Design-Time Support</span></span>](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 <span data-ttu-id="e86ea-128">Popisuje, jak k implementaci třídy, jako je editory a návrhářů, které podporují návrhu.</span><span class="sxs-lookup"><span data-stu-id="e86ea-128">Describes how to implement classes such as editors and designers that provide design-time support.</span></span>
