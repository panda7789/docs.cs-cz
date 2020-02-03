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
# <a name="attributes-in-windows-forms-controls"></a>Atributy v ovládacích prvcích Windows Forms
.NET Framework poskytuje celou řadu atributů, které můžete použít pro členy vašich vlastních ovládacích prvků a komponent. Některé z těchto atributů ovlivňují chování třídy za běhu a jiné ovlivňují chování při návrhu.  
  
## <a name="attributes-for-control-and-component-properties"></a>Atributy ovládacího prvku a vlastností komponenty  
 V následující tabulce jsou uvedeny atributy, které lze použít pro vlastnosti nebo jiné členy vlastních ovládacích prvků a komponent. Příklad, který používá mnoho z těchto atributů, naleznete v tématu [How to: Apply Attributes in model Windows Forms Controls](how-to-apply-attributes-in-windows-forms-controls.md).  
  
|Atribut|Popis|  
|---------------|-----------------|  
|<xref:System.ComponentModel.AmbientValueAttribute>|Určuje hodnotu, která má být předána vlastnosti, která způsobí, že vlastnost získá hodnotu z jiného zdroje. To se označuje jako *Ambience*.|  
|<xref:System.ComponentModel.BrowsableAttribute>|Určuje, zda se má vlastnost nebo událost zobrazit v okně **vlastnosti** .|  
|<xref:System.ComponentModel.CategoryAttribute>|Určuje název kategorie, ve které se má seskupit vlastnost nebo událost, když se zobrazí v ovládacím prvku <xref:System.Windows.Forms.PropertyGrid> nastaveném na režim <xref:System.Windows.Forms.PropertySort.Categorized>.|  
|<xref:System.ComponentModel.DefaultValueAttribute>|Určuje výchozí hodnotu pro vlastnost.|  
|<xref:System.ComponentModel.DescriptionAttribute>|Určuje popis vlastnosti nebo události.|  
|<xref:System.ComponentModel.DisplayNameAttribute>|Určuje zobrazovaný název pro metodu vlastnosti, události nebo `public void`, která nepřijímá žádné argumenty.|  
|<xref:System.ComponentModel.EditorAttribute>|Určuje editor, který se má použít ke změně vlastnosti.|  
|<xref:System.ComponentModel.EditorBrowsableAttribute>|Určuje, že vlastnost nebo metoda je možné zobrazit v editoru.|  
|<xref:System.ComponentModel.Design.HelpKeywordAttribute>|Určuje klíčové slovo kontextu pro třídu nebo člena.|  
|<xref:System.ComponentModel.LocalizableAttribute>|Určuje, zda má být vlastnost lokalizována.|  
|<xref:System.ComponentModel.PasswordPropertyTextAttribute>|Označuje, že reprezentace textu objektu je skryta znaky, jako jsou hvězdičky.|  
|<xref:System.ComponentModel.ReadOnlyAttribute>|Určuje, zda vlastnost, ke které je tento atribut vázán, je určena jen pro čtení, nebo čtení a zápis v době návrhu.|  
|<xref:System.ComponentModel.RefreshPropertiesAttribute>|Označuje, že se má při změně hodnoty přidružené vlastnosti aktualizovat Mřížka vlastností.|  
|<xref:System.ComponentModel.TypeConverterAttribute>|Určuje typ, který se použije jako převaděč pro objekt, ke kterému je tento atribut vázán.|  
  
## <a name="attributes-for-data-binding-properties"></a>Atributy pro vlastnosti datové vazby  
 V následující tabulce jsou uvedeny atributy, které můžete použít, chcete-li určit, jak vlastní ovládací prvky a komponenty pracují s datovou vazbou.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|<xref:System.ComponentModel.BindableAttribute>|Určuje, zda je vlastnost obvykle použita pro vazbu.|  
|<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|Určuje zdroj dat a vlastnosti datového člena pro komponentu.|  
|<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|Určuje výchozí vlastnost vazby pro komponentu.|  
|<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|Určuje zdroj dat a vlastnosti datového člena pro komponentu.|  
|<xref:System.ComponentModel.AttributeProviderAttribute>|Povolí přesměrování atributu.|  
  
## <a name="attributes-for-classes"></a>Atributy pro třídy  
 V následující tabulce jsou uvedeny atributy, které lze použít pro určení chování vlastních ovládacích prvků a komponent v době návrhu.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|<xref:System.ComponentModel.DefaultEventAttribute>|Určuje výchozí událost pro komponentu.|  
|<xref:System.ComponentModel.DefaultPropertyAttribute>|Určuje výchozí vlastnost pro komponentu.|  
|<xref:System.ComponentModel.DesignerAttribute>|Určuje třídu, která se používá k implementaci služeb doby návrhu pro komponentu.|  
|<xref:System.ComponentModel.DesignerCategoryAttribute>|Určuje, že Návrhář pro třídu patří do určité kategorie.|  
|<xref:System.ComponentModel.ToolboxItemAttribute>|Představuje atribut položky sady nástrojů.|  
|<xref:System.ComponentModel.ToolboxItemFilterAttribute>|Určuje řetězec filtru a typ filtru, který se má použít pro položku panelu nástrojů.|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Attribute>
- [Postupy: Použití atributů v ovládacích prvcích Windows Forms](how-to-apply-attributes-in-windows-forms-controls.md)
- [Rozšíření podpory pro dobu návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))
- [Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework](developing-custom-windows-forms-controls.md)
