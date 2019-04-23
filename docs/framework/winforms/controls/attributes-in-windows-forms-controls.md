---
title: Atributy v ovládacích prvcích Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- attributes [Windows Forms]
- attributes [Windows Forms], data binding properties
- attributes [Windows Forms], control properties
- attributes [Windows Forms], classes
ms.assetid: 2c5640e9-6c6c-49d7-a5e4-a768f6be7853
ms.openlocfilehash: 9dd4c2aabe1517b66d8e499de3cf2671bb94e0d6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213598"
---
# <a name="attributes-in-windows-forms-controls"></a><span data-ttu-id="b5cf8-102">Atributy v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b5cf8-102">Attributes in Windows Forms Controls</span></span>
<span data-ttu-id="b5cf8-103">Rozhraní .NET Framework poskytuje širokou škálu atributy, které můžete provést u členů vlastní ovládací prvky a součásti.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-103">The .NET Framework provides a variety of attributes you can apply to the members of your custom controls and components.</span></span> <span data-ttu-id="b5cf8-104">Některé z těchto atributů ovlivňují chování za běhu třídy a jiné ovlivňují chování během návrhu.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-104">Some of these attributes affect the run-time behavior of a class, and others affect the design-time behavior.</span></span>  
  
## <a name="attributes-for-control-and-component-properties"></a><span data-ttu-id="b5cf8-105">Atributy pro ovládací prvek a vlastnosti komponent</span><span class="sxs-lookup"><span data-stu-id="b5cf8-105">Attributes for Control and Component Properties</span></span>  
 <span data-ttu-id="b5cf8-106">V následující tabulce jsou uvedeny atributy, že které můžete použít k vlastnosti nebo další členové vaší vlastní ovládací prvky a součásti.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-106">The following table shows the attributes you can apply to properties or other members of your custom controls and components.</span></span> <span data-ttu-id="b5cf8-107">Příklad, který používá mnoho z těchto atributů, naleznete v tématu [jak: Použití atributů v ovládacích prvcích Windows Forms](how-to-apply-attributes-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="b5cf8-107">For an example that uses many of these attributes, see [How to: Apply Attributes in Windows Forms Controls](how-to-apply-attributes-in-windows-forms-controls.md).</span></span>  
  
|<span data-ttu-id="b5cf8-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="b5cf8-108">Attribute</span></span>|<span data-ttu-id="b5cf8-109">Popis</span><span class="sxs-lookup"><span data-stu-id="b5cf8-109">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ComponentModel.AmbientValueAttribute>|<span data-ttu-id="b5cf8-110">Určuje hodnotu pro předání do vlastnosti a způsobit, že vlastnost, která má získat jeho hodnotu z jiného zdroje.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-110">Specifies the value to pass to a property to cause the property to get its value from another source.</span></span> <span data-ttu-id="b5cf8-111">To se označuje jako *podmínek*.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-111">This is known as *ambience*.</span></span>|  
|<xref:System.ComponentModel.BrowsableAttribute>|<span data-ttu-id="b5cf8-112">Určuje, zda vlastnost nebo událost má být zobrazen v **vlastnosti** okna.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-112">Specifies whether a property or event should be displayed in a **Properties** window.</span></span>|  
|<xref:System.ComponentModel.CategoryAttribute>|<span data-ttu-id="b5cf8-113">Určuje název kategorie, ve které chcete seskupit vlastnost nebo událost, když se zobrazí v <xref:System.Windows.Forms.PropertyGrid> ovládacího prvku nastavte na <xref:System.Windows.Forms.PropertySort.Categorized> režimu.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-113">Specifies the name of the category in which to group the property or event when displayed in a <xref:System.Windows.Forms.PropertyGrid> control set to <xref:System.Windows.Forms.PropertySort.Categorized> mode.</span></span>|  
|<xref:System.ComponentModel.DefaultValueAttribute>|<span data-ttu-id="b5cf8-114">Určuje výchozí hodnotu pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-114">Specifies the default value for a property.</span></span>|  
|<xref:System.ComponentModel.DescriptionAttribute>|<span data-ttu-id="b5cf8-115">Určuje popis pro vlastnost nebo událost.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-115">Specifies a description for a property or event.</span></span>|  
|<xref:System.ComponentModel.DisplayNameAttribute>|<span data-ttu-id="b5cf8-116">Určuje zobrazovaný název vlastnosti, události, nebo `public void` metodu, která nepřijímá žádné argumenty.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-116">Specifies the display name for a property, event, or `public void` method that takes no arguments.</span></span>|  
|<xref:System.ComponentModel.EditorAttribute>|<span data-ttu-id="b5cf8-117">Určuje Změna vlastnosti pomocí editoru.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-117">Specifies the editor to use to change a property.</span></span>|  
|<xref:System.ComponentModel.EditorBrowsableAttribute>|<span data-ttu-id="b5cf8-118">Určuje, že vlastnost nebo metoda je zobrazit v editoru.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-118">Specifies that a property or method is viewable in an editor.</span></span>|  
|<xref:System.ComponentModel.Design.HelpKeywordAttribute>|<span data-ttu-id="b5cf8-119">Určuje klíčové slovo kontext pro třídu nebo člen.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-119">Specifies the context keyword for a class or member.</span></span>|  
|<xref:System.ComponentModel.LocalizableAttribute>|<span data-ttu-id="b5cf8-120">Určuje, zda vlastnost musí být lokalizována.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-120">Specifies whether a property should be localized.</span></span>|  
|<xref:System.ComponentModel.PasswordPropertyTextAttribute>|<span data-ttu-id="b5cf8-121">Označuje, že textová reprezentace objektu je skryt znaky, jako je například hvězdičky z obou stran.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-121">Indicates that an object's text representation is obscured by characters such as asterisks.</span></span>|  
|<xref:System.ComponentModel.ReadOnlyAttribute>|<span data-ttu-id="b5cf8-122">Určuje, zda vlastnost nímž je svázán tento atribut je jen pro čtení nebo pro čtení a zápis v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-122">Specifies whether the property this attribute is bound to is read-only or read/write at design time.</span></span>|  
|<xref:System.ComponentModel.RefreshPropertiesAttribute>|<span data-ttu-id="b5cf8-123">Označuje, že by měl při změně hodnoty přidružené vlastnosti aktualizovat mřížku vlastností.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-123">Indicates that the property grid should refresh when the associated property value changes.</span></span>|  
|<xref:System.ComponentModel.TypeConverterAttribute>|<span data-ttu-id="b5cf8-124">Určuje, jaký typ má být použit jako převaděč pro objekt tento atribut je vázán na.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-124">Specifies what type to use as a converter for the object this attribute is bound to.</span></span>|  
  
## <a name="attributes-for-data-binding-properties"></a><span data-ttu-id="b5cf8-125">Atributy pro datové vazby vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b5cf8-125">Attributes for Data Binding Properties</span></span>  
 <span data-ttu-id="b5cf8-126">V následující tabulce jsou uvedeny atributy, že které můžete použít k určení, jak vlastní ovládací prvky a součásti interakci s datovou vazbu.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-126">The following table shows the attributes you can apply to specify how your custom controls and components interact with data binding.</span></span>  
  
|<span data-ttu-id="b5cf8-127">Atribut</span><span class="sxs-lookup"><span data-stu-id="b5cf8-127">Attribute</span></span>|<span data-ttu-id="b5cf8-128">Popis</span><span class="sxs-lookup"><span data-stu-id="b5cf8-128">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ComponentModel.BindableAttribute>|<span data-ttu-id="b5cf8-129">Určuje, zda vlastnost se obvykle používá pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-129">Specifies whether a property is typically used for binding.</span></span>|  
|<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|<span data-ttu-id="b5cf8-130">Určuje zdroj dat a dat člena vlastnosti pro komponentu.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-130">Specifies the data source and data member properties for a component.</span></span>|  
|<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|<span data-ttu-id="b5cf8-131">Určuje výchozí vlastnost vazby pro komponentu.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-131">Specifies the default binding property for a component.</span></span>|  
|<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|<span data-ttu-id="b5cf8-132">Určuje zdroj dat a dat člena vlastnosti pro komponentu.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-132">Specifies the data source and data member properties for a component.</span></span>|  
|<xref:System.ComponentModel.AttributeProviderAttribute>|<span data-ttu-id="b5cf8-133">Atribut umožňuje přesměrování.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-133">Enables attribute redirection.</span></span>|  
  
## <a name="attributes-for-classes"></a><span data-ttu-id="b5cf8-134">Atributy třídy</span><span class="sxs-lookup"><span data-stu-id="b5cf8-134">Attributes for Classes</span></span>  
 <span data-ttu-id="b5cf8-135">V následující tabulce jsou uvedeny atributy, že které můžete použít k určení chování vlastní ovládací prvky a součásti v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-135">The following table shows the attributes you can apply to specify the behavior of your custom controls and components at design time.</span></span>  
  
|<span data-ttu-id="b5cf8-136">Atribut</span><span class="sxs-lookup"><span data-stu-id="b5cf8-136">Attribute</span></span>|<span data-ttu-id="b5cf8-137">Popis</span><span class="sxs-lookup"><span data-stu-id="b5cf8-137">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ComponentModel.DefaultEventAttribute>|<span data-ttu-id="b5cf8-138">Určuje výchozí událost pro komponentu.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-138">Specifies the default event for a component.</span></span>|  
|<xref:System.ComponentModel.DefaultPropertyAttribute>|<span data-ttu-id="b5cf8-139">Určuje výchozí vlastnost pro komponentu.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-139">Specifies the default property for a component.</span></span>|  
|<xref:System.ComponentModel.DesignerAttribute>|<span data-ttu-id="b5cf8-140">Určuje třídu použít k implementaci služby v době návrhu pro komponenty.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-140">Specifies the class used to implement design-time services for a component.</span></span>|  
|<xref:System.ComponentModel.DesignerCategoryAttribute>|<span data-ttu-id="b5cf8-141">Určuje, že návrhář pro třídu patří do určité kategorie.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-141">Specifies that the designer for a class belongs to a certain category.</span></span>|  
|<xref:System.ComponentModel.ToolboxItemAttribute>|<span data-ttu-id="b5cf8-142">Představuje atribut položky panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-142">Represents an attribute of a toolbox item.</span></span>|  
|<xref:System.ComponentModel.ToolboxItemFilterAttribute>|<span data-ttu-id="b5cf8-143">Určuje řetězec filtru a typ filtru určený pro položku sady nástrojů.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-143">Specifies the filter string and filter type to use for a Toolbox item.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b5cf8-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b5cf8-144">See also</span></span>

- <xref:System.Attribute>
- [<span data-ttu-id="b5cf8-145">Postupy: Použití atributů v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b5cf8-145">How to: Apply Attributes in Windows Forms Controls</span></span>](how-to-apply-attributes-in-windows-forms-controls.md)
- <span data-ttu-id="b5cf8-146">[Rozšíření podpory během návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="b5cf8-146">[Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span></span>
- [<span data-ttu-id="b5cf8-147">Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b5cf8-147">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
