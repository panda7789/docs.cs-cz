---
title: "Atributy v ovládacích prvcích Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- attributes [Windows Forms]
- attributes [Windows Forms], data binding properties
- attributes [Windows Forms], control properties
- attributes [Windows Forms], classes
ms.assetid: 2c5640e9-6c6c-49d7-a5e4-a768f6be7853
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 13aad22dca249147e3037bcef6da755c264021db
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="attributes-in-windows-forms-controls"></a><span data-ttu-id="f095f-102">Atributy v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f095f-102">Attributes in Windows Forms Controls</span></span>
<span data-ttu-id="f095f-103">Rozhraní .NET Framework poskytuje celou řadu atributy, které můžete použít pro členy vlastní ovládací prvky a součásti.</span><span class="sxs-lookup"><span data-stu-id="f095f-103">The .NET Framework provides a variety of attributes you can apply to the members of your custom controls and components.</span></span> <span data-ttu-id="f095f-104">Některé z těchto atributů ovlivnit chování běhové třídy a jiné ovlivňují chování návrhu.</span><span class="sxs-lookup"><span data-stu-id="f095f-104">Some of these attributes affect the run-time behavior of a class, and others affect the design-time behavior.</span></span>  
  
## <a name="attributes-for-control-and-component-properties"></a><span data-ttu-id="f095f-105">Atributy pro řízení a vlastnosti komponenty</span><span class="sxs-lookup"><span data-stu-id="f095f-105">Attributes for Control and Component Properties</span></span>  
 <span data-ttu-id="f095f-106">V následující tabulce jsou uvedeny atributy, že které můžete použít k vlastnosti nebo jinými členy vlastní ovládací prvky a součásti.</span><span class="sxs-lookup"><span data-stu-id="f095f-106">The following table shows the attributes you can apply to properties or other members of your custom controls and components.</span></span> <span data-ttu-id="f095f-107">Příklad, který používá některé z těchto atributů, naleznete v části [postupy: použití atributů v ovládacích prvcích Windows Forms](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="f095f-107">For an example that uses many of these attributes, see [How to: Apply Attributes in Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).</span></span>  
  
|<span data-ttu-id="f095f-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="f095f-108">Attribute</span></span>|<span data-ttu-id="f095f-109">Popis</span><span class="sxs-lookup"><span data-stu-id="f095f-109">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ComponentModel.AmbientValueAttribute>|<span data-ttu-id="f095f-110">Určuje hodnotu, která mají být předána do vlastnosti a způsobit, že vlastnost k získání svou hodnotu z jiného zdroje.</span><span class="sxs-lookup"><span data-stu-id="f095f-110">Specifies the value to pass to a property to cause the property to get its value from another source.</span></span> <span data-ttu-id="f095f-111">To se označuje jako *podmínek, za*.</span><span class="sxs-lookup"><span data-stu-id="f095f-111">This is known as *ambience*.</span></span>|  
|<xref:System.ComponentModel.BrowsableAttribute>|<span data-ttu-id="f095f-112">Určuje, zda vlastnost nebo událost má být zobrazena v **vlastnosti** okno.</span><span class="sxs-lookup"><span data-stu-id="f095f-112">Specifies whether a property or event should be displayed in a **Properties** window.</span></span>|  
|<xref:System.ComponentModel.CategoryAttribute>|<span data-ttu-id="f095f-113">Určuje název kategorie, ve které chcete seskupit vlastnost nebo událost, pokud se zobrazí v <xref:System.Windows.Forms.PropertyGrid> řízení nastavené na <xref:System.Windows.Forms.PropertySort.Categorized> režimu.</span><span class="sxs-lookup"><span data-stu-id="f095f-113">Specifies the name of the category in which to group the property or event when displayed in a <xref:System.Windows.Forms.PropertyGrid> control set to <xref:System.Windows.Forms.PropertySort.Categorized> mode.</span></span>|  
|<xref:System.ComponentModel.DefaultValueAttribute>|<span data-ttu-id="f095f-114">Určuje výchozí hodnotu pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f095f-114">Specifies the default value for a property.</span></span>|  
|<xref:System.ComponentModel.DescriptionAttribute>|<span data-ttu-id="f095f-115">Určuje popis vlastnosti nebo události.</span><span class="sxs-lookup"><span data-stu-id="f095f-115">Specifies a description for a property or event.</span></span>|  
|<xref:System.ComponentModel.DisplayNameAttribute>|<span data-ttu-id="f095f-116">Určuje zobrazovaný název vlastnosti, události, nebo `public``void` metody, které nepřijímá žádné argumenty.</span><span class="sxs-lookup"><span data-stu-id="f095f-116">Specifies the display name for a property, event, or `public``void` method that takes no arguments.</span></span>|  
|<xref:System.ComponentModel.EditorAttribute>|<span data-ttu-id="f095f-117">Určuje editoru použít ke změně vlastností.</span><span class="sxs-lookup"><span data-stu-id="f095f-117">Specifies the editor to use to change a property.</span></span>|  
|<xref:System.ComponentModel.EditorBrowsableAttribute>|<span data-ttu-id="f095f-118">Určuje, že vlastnosti nebo metody je zobrazitelný v editoru.</span><span class="sxs-lookup"><span data-stu-id="f095f-118">Specifies that a property or method is viewable in an editor.</span></span>|  
|<xref:System.ComponentModel.Design.HelpKeywordAttribute>|<span data-ttu-id="f095f-119">Určuje klíčové slovo kontext pro třídu nebo člena.</span><span class="sxs-lookup"><span data-stu-id="f095f-119">Specifies the context keyword for a class or member.</span></span>|  
|<xref:System.ComponentModel.LocalizableAttribute>|<span data-ttu-id="f095f-120">Určuje, zda by měl být lokalizovaný vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f095f-120">Specifies whether a property should be localized.</span></span>|  
|<xref:System.ComponentModel.PasswordPropertyTextAttribute>|<span data-ttu-id="f095f-121">Označuje, že je po znaky, jako jsou hvězdičky skryt reprezentace objektu.</span><span class="sxs-lookup"><span data-stu-id="f095f-121">Indicates that an object's text representation is obscured by characters such as asterisks.</span></span>|  
|<xref:System.ComponentModel.ReadOnlyAttribute>|<span data-ttu-id="f095f-122">Určuje, zda vlastnost, kterou tento atribut je svázán je jen pro čtení nebo zápisu v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="f095f-122">Specifies whether the property this attribute is bound to is read-only or read/write at design time.</span></span>|  
|<xref:System.ComponentModel.RefreshPropertiesAttribute>|<span data-ttu-id="f095f-123">Určuje, zda by měl při změně hodnoty přidružené vlastnosti obnovte mřížku vlastností.</span><span class="sxs-lookup"><span data-stu-id="f095f-123">Indicates that the property grid should refresh when the associated property value changes.</span></span>|  
|<xref:System.ComponentModel.TypeConverterAttribute>|<span data-ttu-id="f095f-124">Určuje, jaký typ, který chcete použít jako převaděč pro objekt tento atribut je vázán k.</span><span class="sxs-lookup"><span data-stu-id="f095f-124">Specifies what type to use as a converter for the object this attribute is bound to.</span></span>|  
  
## <a name="attributes-for-data-binding-properties"></a><span data-ttu-id="f095f-125">Atributy pro vlastnosti datové vazby</span><span class="sxs-lookup"><span data-stu-id="f095f-125">Attributes for Data Binding Properties</span></span>  
 <span data-ttu-id="f095f-126">V následující tabulce jsou uvedeny atributy, že které můžete použít k určení, jak se vaše vlastní ovládací prvky a součásti komunikovat s datová vazba.</span><span class="sxs-lookup"><span data-stu-id="f095f-126">The following table shows the attributes you can apply to specify how your custom controls and components interact with data binding.</span></span>  
  
|<span data-ttu-id="f095f-127">Atribut</span><span class="sxs-lookup"><span data-stu-id="f095f-127">Attribute</span></span>|<span data-ttu-id="f095f-128">Popis</span><span class="sxs-lookup"><span data-stu-id="f095f-128">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ComponentModel.BindableAttribute>|<span data-ttu-id="f095f-129">Určuje, zda vlastnost se obvykle používá pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="f095f-129">Specifies whether a property is typically used for binding.</span></span>|  
|<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|<span data-ttu-id="f095f-130">Určuje zdroj dat a vlastnosti člena dat pro součást.</span><span class="sxs-lookup"><span data-stu-id="f095f-130">Specifies the data source and data member properties for a component.</span></span>|  
|<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|<span data-ttu-id="f095f-131">Určuje výchozí vlastnost vazby pro součást.</span><span class="sxs-lookup"><span data-stu-id="f095f-131">Specifies the default binding property for a component.</span></span>|  
|<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|<span data-ttu-id="f095f-132">Určuje zdroj dat a vlastnosti člena dat pro součást.</span><span class="sxs-lookup"><span data-stu-id="f095f-132">Specifies the data source and data member properties for a component.</span></span>|  
|<xref:System.ComponentModel.AttributeProviderAttribute>|<span data-ttu-id="f095f-133">Umožňuje atribut přesměrování.</span><span class="sxs-lookup"><span data-stu-id="f095f-133">Enables attribute redirection.</span></span>|  
  
## <a name="attributes-for-classes"></a><span data-ttu-id="f095f-134">Atributy pro třídy</span><span class="sxs-lookup"><span data-stu-id="f095f-134">Attributes for Classes</span></span>  
 <span data-ttu-id="f095f-135">V následující tabulce jsou uvedeny atributy, že které můžete použít k určení chování vlastní ovládací prvky a součásti v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="f095f-135">The following table shows the attributes you can apply to specify the behavior of your custom controls and components at design time.</span></span>  
  
|<span data-ttu-id="f095f-136">Atribut</span><span class="sxs-lookup"><span data-stu-id="f095f-136">Attribute</span></span>|<span data-ttu-id="f095f-137">Popis</span><span class="sxs-lookup"><span data-stu-id="f095f-137">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ComponentModel.DefaultEventAttribute>|<span data-ttu-id="f095f-138">Určuje výchozí událost pro komponentu.</span><span class="sxs-lookup"><span data-stu-id="f095f-138">Specifies the default event for a component.</span></span>|  
|<xref:System.ComponentModel.DefaultPropertyAttribute>|<span data-ttu-id="f095f-139">Určuje výchozí vlastnost pro komponentu.</span><span class="sxs-lookup"><span data-stu-id="f095f-139">Specifies the default property for a component.</span></span>|  
|<xref:System.ComponentModel.DesignerAttribute>|<span data-ttu-id="f095f-140">Určuje třídu použít k implementaci návrhu služby pro součást.</span><span class="sxs-lookup"><span data-stu-id="f095f-140">Specifies the class used to implement design-time services for a component.</span></span>|  
|<xref:System.ComponentModel.DesignerCategoryAttribute>|<span data-ttu-id="f095f-141">Určuje, že návrháře pro třídu patří do určité kategorie.</span><span class="sxs-lookup"><span data-stu-id="f095f-141">Specifies that the designer for a class belongs to a certain category.</span></span>|  
|<xref:System.ComponentModel.ToolboxItemAttribute>|<span data-ttu-id="f095f-142">Představuje atribut položka panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="f095f-142">Represents an attribute of a toolbox item.</span></span>|  
|<xref:System.ComponentModel.ToolboxItemFilterAttribute>|<span data-ttu-id="f095f-143">Určuje řetězec filtru a typ filtru pro položka panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="f095f-143">Specifies the filter string and filter type to use for a Toolbox item.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f095f-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="f095f-144">See Also</span></span>  
 <xref:System.Attribute>  
 [<span data-ttu-id="f095f-145">Postupy: Použití atributů v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f095f-145">How to: Apply Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)  
 [<span data-ttu-id="f095f-146">Rozšíření podpory návrhu</span><span class="sxs-lookup"><span data-stu-id="f095f-146">Extending Design-Time Support</span></span>](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 [<span data-ttu-id="f095f-147">Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f095f-147">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
