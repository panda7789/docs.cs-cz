---
title: Vlastnosti ovládacích prvků
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], properties overview (using code)
- controls [Windows Forms], properties
- properties [Windows Forms]
ms.assetid: 2785279b-fb57-4937-8f6b-2050e475db6f
ms.openlocfilehash: 82bfab15cef4946661a37d2d88fbe1b797f3d816
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741177"
---
# <a name="properties-in-windows-forms-controls"></a><span data-ttu-id="f2d40-102">Vlastnosti v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f2d40-102">Properties in Windows Forms Controls</span></span>
<span data-ttu-id="f2d40-103">Ovládací prvek model Windows Forms zdědí mnoho vlastností <xref:System.Windows.Forms.Control?displayProperty=nameWithType>základní třídy.</span><span class="sxs-lookup"><span data-stu-id="f2d40-103">A Windows Forms control inherits many properties form the base class <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f2d40-104">Mezi tyto vlastnosti patří například <xref:System.Windows.Forms.Control.Font%2A>, <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Bounds%2A>, <xref:System.Windows.Forms.Control.ClientRectangle%2A>, <xref:System.Windows.Forms.Control.DisplayRectangle%2A>, <xref:System.Windows.Forms.Control.Enabled%2A>, <xref:System.Windows.Forms.Control.Focused%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, <xref:System.Windows.Forms.Control.Visible%2A>, <xref:System.Windows.Forms.Control.AutoSize%2A>a mnoho dalších.</span><span class="sxs-lookup"><span data-stu-id="f2d40-104">These include properties such as <xref:System.Windows.Forms.Control.Font%2A>, <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Bounds%2A>, <xref:System.Windows.Forms.Control.ClientRectangle%2A>, <xref:System.Windows.Forms.Control.DisplayRectangle%2A>, <xref:System.Windows.Forms.Control.Enabled%2A>, <xref:System.Windows.Forms.Control.Focused%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, <xref:System.Windows.Forms.Control.Visible%2A>, <xref:System.Windows.Forms.Control.AutoSize%2A>, and many others.</span></span> <span data-ttu-id="f2d40-105">Podrobnosti o děděných vlastnostech naleznete v tématu <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f2d40-105">For details about inherited properties, see <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="f2d40-106">Můžete přepsat děděné vlastnosti v ovládacím prvku a také definovat nové vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f2d40-106">You can override inherited properties in your control as well as define new properties.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f2d40-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f2d40-107">In This Section</span></span>  
 [<span data-ttu-id="f2d40-108">Definování vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f2d40-108">Defining a Property</span></span>](defining-a-property-in-windows-forms-controls.md)  
 <span data-ttu-id="f2d40-109">Ukazuje, jak implementovat vlastnost pro vlastní ovládací prvek nebo komponentu a ukazuje, jak integrovat vlastnost do návrhového prostředí.</span><span class="sxs-lookup"><span data-stu-id="f2d40-109">Shows how to implement a property for a custom control or component and shows how to integrate the property into the design environment.</span></span>  
  
 [<span data-ttu-id="f2d40-110">Definování výchozích hodnot pomocí metod ShouldSerialize a Reset</span><span class="sxs-lookup"><span data-stu-id="f2d40-110">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>](defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 <span data-ttu-id="f2d40-111">Ukazuje, jak definovat výchozí hodnoty vlastností pro vlastní ovládací prvek nebo komponentu.</span><span class="sxs-lookup"><span data-stu-id="f2d40-111">Shows how to define default property values for a custom control or component.</span></span>  
  
 [<span data-ttu-id="f2d40-112">Události změny vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f2d40-112">Property-Changed Events</span></span>](property-changed-events.md)  
 <span data-ttu-id="f2d40-113">Popisuje, jak povolit oznámení o změně vlastností při změně hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f2d40-113">Describes how to enable property-change notifications when a property value changes.</span></span>  
  
 [<span data-ttu-id="f2d40-114">Postupy: Vystavení vlastností základních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="f2d40-114">How to: Expose Properties of Constituent Controls</span></span>](how-to-expose-properties-of-constituent-controls.md)  
 <span data-ttu-id="f2d40-115">Ukazuje, jak vystavit vlastnosti ovládacích prvků prvku ve vlastním složeném ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="f2d40-115">Shows how to expose properties of constituent controls in a custom composite control.</span></span>  
  
 [<span data-ttu-id="f2d40-116">Implementace metody ve vlastních ovládacích prvcích</span><span class="sxs-lookup"><span data-stu-id="f2d40-116">Method Implementation in Custom Controls</span></span>](method-implementation-in-custom-controls.md)  
 <span data-ttu-id="f2d40-117">Popisuje, jak implementovat metody ve vlastních ovládacích prvcích a komponentách.</span><span class="sxs-lookup"><span data-stu-id="f2d40-117">Describes how to implement methods in custom controls and components.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f2d40-118">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="f2d40-118">Reference</span></span>  
 <xref:System.Windows.Forms.UserControl>  
 <span data-ttu-id="f2d40-119">Dokumentuje základní třídu pro implementaci složených ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="f2d40-119">Documents the base class for implementing composite controls.</span></span>  
  
 <xref:System.ComponentModel.TypeConverterAttribute>  
 <span data-ttu-id="f2d40-120">Dokumentuje atribut určující <xref:System.ComponentModel.TypeConverter>, který se má použít pro typ vlastní vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f2d40-120">Documents the attribute that specifies the <xref:System.ComponentModel.TypeConverter> to use for a custom property type.</span></span>  
  
 <xref:System.ComponentModel.EditorAttribute>  
 <span data-ttu-id="f2d40-121">Dokumentuje atribut určující <xref:System.Drawing.Design.UITypeEditor>, který se má použít pro vlastní vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f2d40-121">Documents the attribute that specifies the <xref:System.Drawing.Design.UITypeEditor> to use for a custom property.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f2d40-122">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="f2d40-122">Related Sections</span></span>  
 [<span data-ttu-id="f2d40-123">Atributy v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f2d40-123">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)  
 <span data-ttu-id="f2d40-124">Popisuje atributy, které lze použít pro vlastnosti nebo jiné členy vašich vlastních ovládacích prvků a komponent.</span><span class="sxs-lookup"><span data-stu-id="f2d40-124">Describes the attributes you can apply to properties or other members of your custom controls and components.</span></span>  
  
 <span data-ttu-id="f2d40-125">[Atributy pro dobu návrhu pro součásti](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="f2d40-125">[Design-Time Attributes for Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))</span></span>  
 <span data-ttu-id="f2d40-126">Seznam atributů metadat, které se mají použít u komponent a ovládacích prvků tak, aby se v době návrhu v vizuálních návrhářích zobrazovaly správně.</span><span class="sxs-lookup"><span data-stu-id="f2d40-126">Lists metadata attributes to apply to components and controls so that they are displayed correctly at design time in visual designers.</span></span>  
  
 <span data-ttu-id="f2d40-127">[Rozšíření podpory pro dobu návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="f2d40-127">[Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span></span>  
 <span data-ttu-id="f2d40-128">Popisuje, jak implementovat třídy, jako jsou editory a návrháři, které poskytují podporu při návrhu.</span><span class="sxs-lookup"><span data-stu-id="f2d40-128">Describes how to implement classes such as editors and designers that provide design-time support.</span></span>
