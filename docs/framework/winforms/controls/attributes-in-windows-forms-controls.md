---
title: Atributy v ovládacích prvcích Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- attributes [Windows Forms]
- attributes [Windows Forms], data binding properties
- attributes [Windows Forms], control properties
- attributes [Windows Forms], classes
ms.assetid: 2c5640e9-6c6c-49d7-a5e4-a768f6be7853
ms.openlocfilehash: 8e845df7eb83f01adb2086025cf47e7fdc896ba6
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724398"
---
# <a name="attributes-in-windows-forms-controls"></a>Atributy v ovládacích prvcích Windows Forms
Rozhraní .NET Framework poskytuje širokou škálu atributy, které můžete provést u členů vlastní ovládací prvky a součásti. Některé z těchto atributů ovlivňují chování za běhu třídy a jiné ovlivňují chování během návrhu.  
  
## <a name="attributes-for-control-and-component-properties"></a>Atributy pro ovládací prvek a vlastnosti komponent  
 V následující tabulce jsou uvedeny atributy, že které můžete použít k vlastnosti nebo další členové vaší vlastní ovládací prvky a součásti. Příklad, který používá mnoho z těchto atributů, naleznete v tématu [jak: Použití atributů v ovládacích prvcích Windows Forms](how-to-apply-attributes-in-windows-forms-controls.md).  
  
|Atribut|Popis|  
|---------------|-----------------|  
|<xref:System.ComponentModel.AmbientValueAttribute>|Určuje hodnotu pro předání do vlastnosti a způsobit, že vlastnost, která má získat jeho hodnotu z jiného zdroje. To se označuje jako *podmínek*.|  
|<xref:System.ComponentModel.BrowsableAttribute>|Určuje, zda vlastnost nebo událost má být zobrazen v **vlastnosti** okna.|  
|<xref:System.ComponentModel.CategoryAttribute>|Určuje název kategorie, ve které chcete seskupit vlastnost nebo událost, když se zobrazí v <xref:System.Windows.Forms.PropertyGrid> ovládacího prvku nastavte na <xref:System.Windows.Forms.PropertySort.Categorized> režimu.|  
|<xref:System.ComponentModel.DefaultValueAttribute>|Určuje výchozí hodnotu pro vlastnost.|  
|<xref:System.ComponentModel.DescriptionAttribute>|Určuje popis pro vlastnost nebo událost.|  
|<xref:System.ComponentModel.DisplayNameAttribute>|Určuje zobrazovaný název vlastnosti, události, nebo `public void` metodu, která nepřijímá žádné argumenty.|  
|<xref:System.ComponentModel.EditorAttribute>|Určuje Změna vlastnosti pomocí editoru.|  
|<xref:System.ComponentModel.EditorBrowsableAttribute>|Určuje, že vlastnost nebo metoda je zobrazit v editoru.|  
|<xref:System.ComponentModel.Design.HelpKeywordAttribute>|Určuje klíčové slovo kontext pro třídu nebo člen.|  
|<xref:System.ComponentModel.LocalizableAttribute>|Určuje, zda vlastnost musí být lokalizována.|  
|<xref:System.ComponentModel.PasswordPropertyTextAttribute>|Označuje, že textová reprezentace objektu je skryt znaky, jako je například hvězdičky z obou stran.|  
|<xref:System.ComponentModel.ReadOnlyAttribute>|Určuje, zda vlastnost nímž je svázán tento atribut je jen pro čtení nebo pro čtení a zápis v době návrhu.|  
|<xref:System.ComponentModel.RefreshPropertiesAttribute>|Označuje, že by měl při změně hodnoty přidružené vlastnosti aktualizovat mřížku vlastností.|  
|<xref:System.ComponentModel.TypeConverterAttribute>|Určuje, jaký typ má být použit jako převaděč pro objekt tento atribut je vázán na.|  
  
## <a name="attributes-for-data-binding-properties"></a>Atributy pro datové vazby vlastnosti  
 V následující tabulce jsou uvedeny atributy, že které můžete použít k určení, jak vlastní ovládací prvky a součásti interakci s datovou vazbu.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|<xref:System.ComponentModel.BindableAttribute>|Určuje, zda vlastnost se obvykle používá pro vazbu.|  
|<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|Určuje zdroj dat a dat člena vlastnosti pro komponentu.|  
|<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|Určuje výchozí vlastnost vazby pro komponentu.|  
|<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|Určuje zdroj dat a dat člena vlastnosti pro komponentu.|  
|<xref:System.ComponentModel.AttributeProviderAttribute>|Atribut umožňuje přesměrování.|  
  
## <a name="attributes-for-classes"></a>Atributy třídy  
 V následující tabulce jsou uvedeny atributy, že které můžete použít k určení chování vlastní ovládací prvky a součásti v době návrhu.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|<xref:System.ComponentModel.DefaultEventAttribute>|Určuje výchozí událost pro komponentu.|  
|<xref:System.ComponentModel.DefaultPropertyAttribute>|Určuje výchozí vlastnost pro komponentu.|  
|<xref:System.ComponentModel.DesignerAttribute>|Určuje třídu použít k implementaci služby v době návrhu pro komponenty.|  
|<xref:System.ComponentModel.DesignerCategoryAttribute>|Určuje, že návrhář pro třídu patří do určité kategorie.|  
|<xref:System.ComponentModel.ToolboxItemAttribute>|Představuje atribut položky panelu nástrojů.|  
|<xref:System.ComponentModel.ToolboxItemFilterAttribute>|Určuje řetězec filtru a typ filtru určený pro položku sady nástrojů.|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Attribute>
- [Postupy: Použití atributů v ovládacích prvcích Windows Forms](how-to-apply-attributes-in-windows-forms-controls.md)
- [Rozšíření podpory během návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))
- [Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework](developing-custom-windows-forms-controls.md)
