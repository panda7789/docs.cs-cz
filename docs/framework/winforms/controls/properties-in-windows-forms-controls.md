---
title: Vlastnosti v ovládacích prvcích Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], properties overview (using code)
- controls [Windows Forms], properties
- properties [Windows Forms]
ms.assetid: 2785279b-fb57-4937-8f6b-2050e475db6f
ms.openlocfilehash: 37db3f16a17acc7f3a6e594bd284ba368801e70a
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45609814"
---
# <a name="properties-in-windows-forms-controls"></a><span data-ttu-id="aa2ac-102">Vlastnosti v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="aa2ac-102">Properties in Windows Forms Controls</span></span>
<span data-ttu-id="aa2ac-103">Ovládací prvek Windows Forms dědí mnoho vlastností formuláře základní třídy <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="aa2ac-103">A Windows Forms control inherits many properties form the base class <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="aa2ac-104">Tyto vlastnosti patří například <xref:System.Windows.Forms.Control.Font%2A>, <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Bounds%2A>, <xref:System.Windows.Forms.Control.ClientRectangle%2A>, <xref:System.Windows.Forms.Control.DisplayRectangle%2A>, <xref:System.Windows.Forms.Control.Enabled%2A>, <xref:System.Windows.Forms.Control.Focused%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, <xref:System.Windows.Forms.Control.Visible%2A>, <xref:System.Windows.Forms.Control.AutoSize%2A>a mnoha dalších.</span><span class="sxs-lookup"><span data-stu-id="aa2ac-104">These include properties such as <xref:System.Windows.Forms.Control.Font%2A>, <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Bounds%2A>, <xref:System.Windows.Forms.Control.ClientRectangle%2A>, <xref:System.Windows.Forms.Control.DisplayRectangle%2A>, <xref:System.Windows.Forms.Control.Enabled%2A>, <xref:System.Windows.Forms.Control.Focused%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, <xref:System.Windows.Forms.Control.Visible%2A>, <xref:System.Windows.Forms.Control.AutoSize%2A>, and many others.</span></span> <span data-ttu-id="aa2ac-105">Podrobnosti o zděděné vlastnosti najdete v tématu <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="aa2ac-105">For details about inherited properties, see <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="aa2ac-106">Můžete lze přepsat zděděné vlastnosti v ovládacím prvku také definovat nové vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="aa2ac-106">You can override inherited properties in your control as well as define new properties.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="aa2ac-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="aa2ac-107">In This Section</span></span>  
 [<span data-ttu-id="aa2ac-108">Definování vlastnosti</span><span class="sxs-lookup"><span data-stu-id="aa2ac-108">Defining a Property</span></span>](../../../../docs/framework/winforms/controls/defining-a-property-in-windows-forms-controls.md)  
 <span data-ttu-id="aa2ac-109">Ukazuje, jak implementovat vlastnost vlastního ovládacího prvku nebo komponenty a ukazuje, jak integrovat vlastnost do vývojového prostředí.</span><span class="sxs-lookup"><span data-stu-id="aa2ac-109">Shows how to implement a property for a custom control or component and shows how to integrate the property into the design environment.</span></span>  
  
 [<span data-ttu-id="aa2ac-110">Definování výchozích hodnot pomocí metod ShouldSerialize a Reset</span><span class="sxs-lookup"><span data-stu-id="aa2ac-110">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>](../../../../docs/framework/winforms/controls/defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 <span data-ttu-id="aa2ac-111">Ukazuje, jak definovat výchozí hodnoty vlastností pro vlastní ovládací prvek nebo komponenty.</span><span class="sxs-lookup"><span data-stu-id="aa2ac-111">Shows how to define default property values for a custom control or component.</span></span>  
  
 [<span data-ttu-id="aa2ac-112">Události změny vlastnosti</span><span class="sxs-lookup"><span data-stu-id="aa2ac-112">Property-Changed Events</span></span>](../../../../docs/framework/winforms/controls/property-changed-events.md)  
 <span data-ttu-id="aa2ac-113">Popisuje, jak povolit změnu vlastnosti oznámení při změně hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="aa2ac-113">Describes how to enable property-change notifications when a property value changes.</span></span>  
  
 [<span data-ttu-id="aa2ac-114">Postupy: Vystavení vlastností základních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="aa2ac-114">How to: Expose Properties of Constituent Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md)  
 <span data-ttu-id="aa2ac-115">Ukazuje, jak vystavení vlastností základních ovládacích prvků ve vlastní složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="aa2ac-115">Shows how to expose properties of constituent controls in a custom composite control.</span></span>  
  
 [<span data-ttu-id="aa2ac-116">Implementace metody ve vlastních ovládacích prvcích</span><span class="sxs-lookup"><span data-stu-id="aa2ac-116">Method Implementation in Custom Controls</span></span>](../../../../docs/framework/winforms/controls/method-implementation-in-custom-controls.md)  
 <span data-ttu-id="aa2ac-117">Popisuje, jak implementovat metody ve vlastních ovládacích prvků a komponent.</span><span class="sxs-lookup"><span data-stu-id="aa2ac-117">Describes how to implement methods in custom controls and components.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="aa2ac-118">Odkaz</span><span class="sxs-lookup"><span data-stu-id="aa2ac-118">Reference</span></span>  
 <xref:System.Windows.Forms.UserControl>  
 <span data-ttu-id="aa2ac-119">Dokumenty základní třídu pro implementaci složených ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="aa2ac-119">Documents the base class for implementing composite controls.</span></span>  
  
 <xref:System.ComponentModel.TypeConverterAttribute>  
 <span data-ttu-id="aa2ac-120">Atribut, který určuje dokumenty <xref:System.ComponentModel.TypeConverter> pro vlastní vlastnost typu.</span><span class="sxs-lookup"><span data-stu-id="aa2ac-120">Documents the attribute that specifies the <xref:System.ComponentModel.TypeConverter> to use for a custom property type.</span></span>  
  
 <xref:System.ComponentModel.EditorAttribute>  
 <span data-ttu-id="aa2ac-121">Dokumenty atributu, který určuje, <xref:System.Drawing.Design.UITypeEditor> chcete použít pro vlastní vlastnost.</span><span class="sxs-lookup"><span data-stu-id="aa2ac-121">Documents the attribute that specifies the <xref:System.Drawing.Design.UITypeEditor> to use for a custom property.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="aa2ac-122">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="aa2ac-122">Related Sections</span></span>  
 [<span data-ttu-id="aa2ac-123">Atributy v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="aa2ac-123">Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 <span data-ttu-id="aa2ac-124">Popisuje atributy, které můžete provést u vlastnosti nebo další členové vaší vlastní ovládací prvky a součásti.</span><span class="sxs-lookup"><span data-stu-id="aa2ac-124">Describes the attributes you can apply to properties or other members of your custom controls and components.</span></span>  
  
 [<span data-ttu-id="aa2ac-125">Atributy doby návrhu pro komponenty</span><span class="sxs-lookup"><span data-stu-id="aa2ac-125">Design-Time Attributes for Components</span></span>](https://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3)  
 <span data-ttu-id="aa2ac-126">Obsahuje seznam atributy metadat použít na komponent a ovládacích prvků tak, aby se správně zobrazí v době návrhu v vizuální návrhářské nástroje.</span><span class="sxs-lookup"><span data-stu-id="aa2ac-126">Lists metadata attributes to apply to components and controls so that they are displayed correctly at design time in visual designers.</span></span>  
  
 [<span data-ttu-id="aa2ac-127">Rozšíření podpory během návrhu</span><span class="sxs-lookup"><span data-stu-id="aa2ac-127">Extending Design-Time Support</span></span>](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 <span data-ttu-id="aa2ac-128">Popisuje, jak implementovat třídy například editorů a návrhářů, které poskytují podpory během návrhu.</span><span class="sxs-lookup"><span data-stu-id="aa2ac-128">Describes how to implement classes such as editors and designers that provide design-time support.</span></span>
