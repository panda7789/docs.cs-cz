---
title: Atributy v ovládacích prvcích Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- attributes [Windows Forms]
- attributes [Windows Forms], data binding properties
- attributes [Windows Forms], control properties
- attributes [Windows Forms], classes
ms.assetid: 2c5640e9-6c6c-49d7-a5e4-a768f6be7853
ms.openlocfilehash: e06836e53a69394ad899bedc8e545dbff9b9c29d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="attributes-in-windows-forms-controls"></a>Atributy v ovládacích prvcích Windows Forms
Rozhraní .NET Framework poskytuje celou řadu atributy, které můžete použít pro členy vlastní ovládací prvky a součásti. Některé z těchto atributů ovlivnit chování běhové třídy a jiné ovlivňují chování návrhu.  
  
## <a name="attributes-for-control-and-component-properties"></a>Atributy pro řízení a vlastnosti komponenty  
 V následující tabulce jsou uvedeny atributy, že které můžete použít k vlastnosti nebo jinými členy vlastní ovládací prvky a součásti. Příklad, který používá některé z těchto atributů, naleznete v části [postupy: použití atributů v ovládacích prvcích Windows Forms](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).  
  
|Atribut|Popis|  
|---------------|-----------------|  
|<xref:System.ComponentModel.AmbientValueAttribute>|Určuje hodnotu, která mají být předána do vlastnosti a způsobit, že vlastnost k získání svou hodnotu z jiného zdroje. To se označuje jako *podmínek, za*.|  
|<xref:System.ComponentModel.BrowsableAttribute>|Určuje, zda vlastnost nebo událost má být zobrazena v **vlastnosti** okno.|  
|<xref:System.ComponentModel.CategoryAttribute>|Určuje název kategorie, ve které chcete seskupit vlastnost nebo událost, pokud se zobrazí v <xref:System.Windows.Forms.PropertyGrid> řízení nastavené na <xref:System.Windows.Forms.PropertySort.Categorized> režimu.|  
|<xref:System.ComponentModel.DefaultValueAttribute>|Určuje výchozí hodnotu pro vlastnost.|  
|<xref:System.ComponentModel.DescriptionAttribute>|Určuje popis vlastnosti nebo události.|  
|<xref:System.ComponentModel.DisplayNameAttribute>|Určuje zobrazovaný název vlastnosti, události, nebo `public``void` metody, které nepřijímá žádné argumenty.|  
|<xref:System.ComponentModel.EditorAttribute>|Určuje editoru použít ke změně vlastností.|  
|<xref:System.ComponentModel.EditorBrowsableAttribute>|Určuje, že vlastnosti nebo metody je zobrazitelný v editoru.|  
|<xref:System.ComponentModel.Design.HelpKeywordAttribute>|Určuje klíčové slovo kontext pro třídu nebo člena.|  
|<xref:System.ComponentModel.LocalizableAttribute>|Určuje, zda by měl být lokalizovaný vlastnost.|  
|<xref:System.ComponentModel.PasswordPropertyTextAttribute>|Označuje, že je po znaky, jako jsou hvězdičky skryt reprezentace objektu.|  
|<xref:System.ComponentModel.ReadOnlyAttribute>|Určuje, zda vlastnost, kterou tento atribut je svázán je jen pro čtení nebo zápisu v době návrhu.|  
|<xref:System.ComponentModel.RefreshPropertiesAttribute>|Určuje, zda by měl při změně hodnoty přidružené vlastnosti obnovte mřížku vlastností.|  
|<xref:System.ComponentModel.TypeConverterAttribute>|Určuje, jaký typ, který chcete použít jako převaděč pro objekt tento atribut je vázán k.|  
  
## <a name="attributes-for-data-binding-properties"></a>Atributy pro vlastnosti datové vazby  
 V následující tabulce jsou uvedeny atributy, že které můžete použít k určení, jak se vaše vlastní ovládací prvky a součásti komunikovat s datová vazba.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|<xref:System.ComponentModel.BindableAttribute>|Určuje, zda vlastnost se obvykle používá pro vazbu.|  
|<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|Určuje zdroj dat a vlastnosti člena dat pro součást.|  
|<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|Určuje výchozí vlastnost vazby pro součást.|  
|<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|Určuje zdroj dat a vlastnosti člena dat pro součást.|  
|<xref:System.ComponentModel.AttributeProviderAttribute>|Umožňuje atribut přesměrování.|  
  
## <a name="attributes-for-classes"></a>Atributy pro třídy  
 V následující tabulce jsou uvedeny atributy, že které můžete použít k určení chování vlastní ovládací prvky a součásti v době návrhu.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|<xref:System.ComponentModel.DefaultEventAttribute>|Určuje výchozí událost pro komponentu.|  
|<xref:System.ComponentModel.DefaultPropertyAttribute>|Určuje výchozí vlastnost pro komponentu.|  
|<xref:System.ComponentModel.DesignerAttribute>|Určuje třídu použít k implementaci návrhu služby pro součást.|  
|<xref:System.ComponentModel.DesignerCategoryAttribute>|Určuje, že návrháře pro třídu patří do určité kategorie.|  
|<xref:System.ComponentModel.ToolboxItemAttribute>|Představuje atribut položka panelu nástrojů.|  
|<xref:System.ComponentModel.ToolboxItemFilterAttribute>|Určuje řetězec filtru a typ filtru pro položka panelu nástrojů.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Attribute>  
 [Postupy: Použití atributů v ovládacích prvcích Windows Forms](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)  
 [Rozšíření podpory návrhu](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 [Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
