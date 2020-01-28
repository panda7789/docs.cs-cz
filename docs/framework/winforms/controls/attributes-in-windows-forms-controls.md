---
title: Atributy v ovládacích prvcích
ms.date: 03/30/2017
helpviewer_keywords:
- attributes [Windows Forms]
- attributes [Windows Forms], data binding properties
- attributes [Windows Forms], control properties
- attributes [Windows Forms], classes
ms.assetid: 2c5640e9-6c6c-49d7-a5e4-a768f6be7853
ms.openlocfilehash: b32e4f87e953438a3bb11569445a9270e11c7922
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732129"
---
# <a name="attributes-in-windows-forms-controls"></a><span data-ttu-id="634cf-102">Atributy v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="634cf-102">Attributes in Windows Forms Controls</span></span>
<span data-ttu-id="634cf-103">.NET Framework poskytuje celou řadu atributů, které můžete použít pro členy vašich vlastních ovládacích prvků a komponent.</span><span class="sxs-lookup"><span data-stu-id="634cf-103">The .NET Framework provides a variety of attributes you can apply to the members of your custom controls and components.</span></span> <span data-ttu-id="634cf-104">Některé z těchto atributů ovlivňují chování třídy za běhu a jiné ovlivňují chování při návrhu.</span><span class="sxs-lookup"><span data-stu-id="634cf-104">Some of these attributes affect the run-time behavior of a class, and others affect the design-time behavior.</span></span>  
  
## <a name="attributes-for-control-and-component-properties"></a><span data-ttu-id="634cf-105">Atributy ovládacího prvku a vlastností komponenty</span><span class="sxs-lookup"><span data-stu-id="634cf-105">Attributes for Control and Component Properties</span></span>  
 <span data-ttu-id="634cf-106">V následující tabulce jsou uvedeny atributy, které lze použít pro vlastnosti nebo jiné členy vlastních ovládacích prvků a komponent.</span><span class="sxs-lookup"><span data-stu-id="634cf-106">The following table shows the attributes you can apply to properties or other members of your custom controls and components.</span></span> <span data-ttu-id="634cf-107">Příklad, který používá mnoho z těchto atributů, naleznete v tématu [How to: Apply Attributes in model Windows Forms Controls](how-to-apply-attributes-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="634cf-107">For an example that uses many of these attributes, see [How to: Apply Attributes in Windows Forms Controls](how-to-apply-attributes-in-windows-forms-controls.md).</span></span>  
  
|<span data-ttu-id="634cf-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="634cf-108">Attribute</span></span>|<span data-ttu-id="634cf-109">Popis</span><span class="sxs-lookup"><span data-stu-id="634cf-109">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ComponentModel.AmbientValueAttribute>|<span data-ttu-id="634cf-110">Určuje hodnotu, která má být předána vlastnosti, která způsobí, že vlastnost získá hodnotu z jiného zdroje.</span><span class="sxs-lookup"><span data-stu-id="634cf-110">Specifies the value to pass to a property to cause the property to get its value from another source.</span></span> <span data-ttu-id="634cf-111">To se označuje jako *Ambience*.</span><span class="sxs-lookup"><span data-stu-id="634cf-111">This is known as *ambience*.</span></span>|  
|<xref:System.ComponentModel.BrowsableAttribute>|<span data-ttu-id="634cf-112">Určuje, zda se má vlastnost nebo událost zobrazit v okně **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="634cf-112">Specifies whether a property or event should be displayed in a **Properties** window.</span></span>|  
|<xref:System.ComponentModel.CategoryAttribute>|<span data-ttu-id="634cf-113">Určuje název kategorie, ve které se má seskupit vlastnost nebo událost, když se zobrazí v ovládacím prvku <xref:System.Windows.Forms.PropertyGrid> nastaveném na režim <xref:System.Windows.Forms.PropertySort.Categorized>.</span><span class="sxs-lookup"><span data-stu-id="634cf-113">Specifies the name of the category in which to group the property or event when displayed in a <xref:System.Windows.Forms.PropertyGrid> control set to <xref:System.Windows.Forms.PropertySort.Categorized> mode.</span></span>|  
|<xref:System.ComponentModel.DefaultValueAttribute>|<span data-ttu-id="634cf-114">Určuje výchozí hodnotu pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="634cf-114">Specifies the default value for a property.</span></span>|  
|<xref:System.ComponentModel.DescriptionAttribute>|<span data-ttu-id="634cf-115">Určuje popis vlastnosti nebo události.</span><span class="sxs-lookup"><span data-stu-id="634cf-115">Specifies a description for a property or event.</span></span>|  
|<xref:System.ComponentModel.DisplayNameAttribute>|<span data-ttu-id="634cf-116">Určuje zobrazovaný název pro metodu vlastnosti, události nebo `public void`, která nepřijímá žádné argumenty.</span><span class="sxs-lookup"><span data-stu-id="634cf-116">Specifies the display name for a property, event, or `public void` method that takes no arguments.</span></span>|  
|<xref:System.ComponentModel.EditorAttribute>|<span data-ttu-id="634cf-117">Určuje editor, který se má použít ke změně vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="634cf-117">Specifies the editor to use to change a property.</span></span>|  
|<xref:System.ComponentModel.EditorBrowsableAttribute>|<span data-ttu-id="634cf-118">Určuje, že vlastnost nebo metoda je možné zobrazit v editoru.</span><span class="sxs-lookup"><span data-stu-id="634cf-118">Specifies that a property or method is viewable in an editor.</span></span>|  
|<xref:System.ComponentModel.Design.HelpKeywordAttribute>|<span data-ttu-id="634cf-119">Určuje klíčové slovo kontextu pro třídu nebo člena.</span><span class="sxs-lookup"><span data-stu-id="634cf-119">Specifies the context keyword for a class or member.</span></span>|  
|<xref:System.ComponentModel.LocalizableAttribute>|<span data-ttu-id="634cf-120">Určuje, zda má být vlastnost lokalizována.</span><span class="sxs-lookup"><span data-stu-id="634cf-120">Specifies whether a property should be localized.</span></span>|  
|<xref:System.ComponentModel.PasswordPropertyTextAttribute>|<span data-ttu-id="634cf-121">Označuje, že reprezentace textu objektu je skryta znaky, jako jsou hvězdičky.</span><span class="sxs-lookup"><span data-stu-id="634cf-121">Indicates that an object's text representation is obscured by characters such as asterisks.</span></span>|  
|<xref:System.ComponentModel.ReadOnlyAttribute>|<span data-ttu-id="634cf-122">Určuje, zda vlastnost, ke které je tento atribut vázán, je určena jen pro čtení, nebo čtení a zápis v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="634cf-122">Specifies whether the property this attribute is bound to is read-only or read/write at design time.</span></span>|  
|<xref:System.ComponentModel.RefreshPropertiesAttribute>|<span data-ttu-id="634cf-123">Označuje, že se má při změně hodnoty přidružené vlastnosti aktualizovat Mřížka vlastností.</span><span class="sxs-lookup"><span data-stu-id="634cf-123">Indicates that the property grid should refresh when the associated property value changes.</span></span>|  
|<xref:System.ComponentModel.TypeConverterAttribute>|<span data-ttu-id="634cf-124">Určuje typ, který se použije jako převaděč pro objekt, ke kterému je tento atribut vázán.</span><span class="sxs-lookup"><span data-stu-id="634cf-124">Specifies what type to use as a converter for the object this attribute is bound to.</span></span>|  
  
## <a name="attributes-for-data-binding-properties"></a><span data-ttu-id="634cf-125">Atributy pro vlastnosti datové vazby</span><span class="sxs-lookup"><span data-stu-id="634cf-125">Attributes for Data Binding Properties</span></span>  
 <span data-ttu-id="634cf-126">V následující tabulce jsou uvedeny atributy, které můžete použít, chcete-li určit, jak vlastní ovládací prvky a komponenty pracují s datovou vazbou.</span><span class="sxs-lookup"><span data-stu-id="634cf-126">The following table shows the attributes you can apply to specify how your custom controls and components interact with data binding.</span></span>  
  
|<span data-ttu-id="634cf-127">Atribut</span><span class="sxs-lookup"><span data-stu-id="634cf-127">Attribute</span></span>|<span data-ttu-id="634cf-128">Popis</span><span class="sxs-lookup"><span data-stu-id="634cf-128">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ComponentModel.BindableAttribute>|<span data-ttu-id="634cf-129">Určuje, zda je vlastnost obvykle použita pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="634cf-129">Specifies whether a property is typically used for binding.</span></span>|  
|<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|<span data-ttu-id="634cf-130">Určuje zdroj dat a vlastnosti datového člena pro komponentu.</span><span class="sxs-lookup"><span data-stu-id="634cf-130">Specifies the data source and data member properties for a component.</span></span>|  
|<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|<span data-ttu-id="634cf-131">Určuje výchozí vlastnost vazby pro komponentu.</span><span class="sxs-lookup"><span data-stu-id="634cf-131">Specifies the default binding property for a component.</span></span>|  
|<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|<span data-ttu-id="634cf-132">Určuje zdroj dat a vlastnosti datového člena pro komponentu.</span><span class="sxs-lookup"><span data-stu-id="634cf-132">Specifies the data source and data member properties for a component.</span></span>|  
|<xref:System.ComponentModel.AttributeProviderAttribute>|<span data-ttu-id="634cf-133">Povolí přesměrování atributu.</span><span class="sxs-lookup"><span data-stu-id="634cf-133">Enables attribute redirection.</span></span>|  
  
## <a name="attributes-for-classes"></a><span data-ttu-id="634cf-134">Atributy pro třídy</span><span class="sxs-lookup"><span data-stu-id="634cf-134">Attributes for Classes</span></span>  
 <span data-ttu-id="634cf-135">V následující tabulce jsou uvedeny atributy, které lze použít pro určení chování vlastních ovládacích prvků a komponent v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="634cf-135">The following table shows the attributes you can apply to specify the behavior of your custom controls and components at design time.</span></span>  
  
|<span data-ttu-id="634cf-136">Atribut</span><span class="sxs-lookup"><span data-stu-id="634cf-136">Attribute</span></span>|<span data-ttu-id="634cf-137">Popis</span><span class="sxs-lookup"><span data-stu-id="634cf-137">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ComponentModel.DefaultEventAttribute>|<span data-ttu-id="634cf-138">Určuje výchozí událost pro komponentu.</span><span class="sxs-lookup"><span data-stu-id="634cf-138">Specifies the default event for a component.</span></span>|  
|<xref:System.ComponentModel.DefaultPropertyAttribute>|<span data-ttu-id="634cf-139">Určuje výchozí vlastnost pro komponentu.</span><span class="sxs-lookup"><span data-stu-id="634cf-139">Specifies the default property for a component.</span></span>|  
|<xref:System.ComponentModel.DesignerAttribute>|<span data-ttu-id="634cf-140">Určuje třídu, která se používá k implementaci služeb doby návrhu pro komponentu.</span><span class="sxs-lookup"><span data-stu-id="634cf-140">Specifies the class used to implement design-time services for a component.</span></span>|  
|<xref:System.ComponentModel.DesignerCategoryAttribute>|<span data-ttu-id="634cf-141">Určuje, že Návrhář pro třídu patří do určité kategorie.</span><span class="sxs-lookup"><span data-stu-id="634cf-141">Specifies that the designer for a class belongs to a certain category.</span></span>|  
|<xref:System.ComponentModel.ToolboxItemAttribute>|<span data-ttu-id="634cf-142">Představuje atribut položky sady nástrojů.</span><span class="sxs-lookup"><span data-stu-id="634cf-142">Represents an attribute of a toolbox item.</span></span>|  
|<xref:System.ComponentModel.ToolboxItemFilterAttribute>|<span data-ttu-id="634cf-143">Určuje řetězec filtru a typ filtru, který se má použít pro položku panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="634cf-143">Specifies the filter string and filter type to use for a Toolbox item.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="634cf-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="634cf-144">See also</span></span>

- <xref:System.Attribute>
- [<span data-ttu-id="634cf-145">Postupy: Použití atributů v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="634cf-145">How to: Apply Attributes in Windows Forms Controls</span></span>](how-to-apply-attributes-in-windows-forms-controls.md)
- <span data-ttu-id="634cf-146">[Rozšíření podpory pro dobu návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="634cf-146">[Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span></span>
- [<span data-ttu-id="634cf-147">Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="634cf-147">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
