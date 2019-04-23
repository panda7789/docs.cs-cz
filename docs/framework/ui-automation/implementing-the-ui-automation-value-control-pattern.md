---
title: Implementace vzoru ovládacích prvků hodnota pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Value
- UI Automation, Value control pattern
- Value control pattern
ms.assetid: b0fcdd87-3add-4345-bca9-e891205e02ba
ms.openlocfilehash: cccaf1afa55d786e43863e094a9745a0a1d00870
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59174951"
---
# <a name="implementing-the-ui-automation-value-control-pattern"></a>Implementace vzoru ovládacích prvků hodnota pro automatizaci uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma popisuje pravidla a zásady pro implementaci <xref:System.Windows.Automation.Provider.IValueProvider>, včetně informací o události a vlastnosti. Odkazy na další odkazy jsou uvedeny na konci tohoto tématu.  
  
 <xref:System.Windows.Automation.ValuePattern> – Vzor ovládacích prvků slouží k podpoře ovládací prvky, které mají vnitřní hodnotu není pokrývání uzlů oblasti a které můžou být vyjádřeny jako řetězec. Tento řetězec lze upravovat, v závislosti na ovládacím prvku a jeho nastavení. Příklady ovládacích prvků, které tento model implementovat, najdete v článku [ovládací prvek vzor mapování pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Pokyny pro implementaci a konvence  
 Při implementaci vzoru ovládacích prvků hodnota, mějte na paměti následující pokyny a konvence:  
  
-   Ovládací prvky jako například <xref:System.Windows.Automation.ControlType.ListItem> a <xref:System.Windows.Automation.ControlType.TreeItem> musí podporovat <xref:System.Windows.Automation.ValuePattern> Pokud hodnota položky upravovat, bez ohledu na aktuální režim úprav ovládacího prvku. Nadřazený ovládací prvek musí také podporovat <xref:System.Windows.Automation.ValuePattern> Pokud podřízené položky se upravovat.  
  
 ![Upravit seznam položek. ](../../../docs/framework/ui-automation/media/uia-valuepattern-editable-listitem.PNG "UIA_ValuePattern_Editable_ListItem")  
Příklad položky upravovat seznam  
  
-   Ovládací prvky pole podporují programový přístup k jejich obsah implementací <xref:System.Windows.Automation.Provider.IValueProvider>. Ale ovládacích prvcích pro úpravy Víceřádkový neimplementují <xref:System.Windows.Automation.Provider.IValueProvider>; místo toho poskytují přístup ke svému obsahu pomocí implementace <xref:System.Windows.Automation.Provider.ITextProvider>.  
  
-   Pokud chcete načíst textový obsah víceřádkové textové pole, musí implementovat ovládací prvek <xref:System.Windows.Automation.Provider.ITextProvider>. Ale <xref:System.Windows.Automation.Provider.ITextProvider> nepodporuje nastavení hodnoty ovládacího prvku.  
  
-   <xref:System.Windows.Automation.Provider.IValueProvider> nepodporuje načtení formátování informace nebo podřetězec hodnoty. Implementace <xref:System.Windows.Automation.Provider.ITextProvider> v těchto scénářích.  
  
-   <xref:System.Windows.Automation.Provider.IValueProvider> musí být implementované ovládací prvky, jako **výběr barvy** ovládacího prvku pro výběr z [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] (ukázáno níže), která podporuje řetězec mapování mezi hodnotu barvy (například "žlutý") a ekvivalentní vnitřní [!INCLUDE[TLA#tla_rgb](../../../includes/tlasharptla-rgb-md.md)]struktury.  
  
 ![Výběr barvy s zvýrazněn žlutou barvou. ](../../../docs/framework/ui-automation/media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Příklad mapování řetězec vzorníku barev  
  
-   Ovládací prvek by měl mít jeho <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> nastavena na `true` a jeho <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> nastavena na `false` předtím, než volání <xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A>.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-ivalueprovider"></a>Požadované členy pro IValueProvider  
 Následující vlastnosti a metody, které jsou požadovány pro implementaci <xref:System.Windows.Automation.Provider.IValueProvider>.  
  
|Požadované členy|Typ člena|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.ValuePattern.ValueProperty>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.ValuePattern.SetValue%2A>|Metoda|Žádný|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Poskytovatelé musí vyvolání následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> – Pokud informace specifické pro národní prostředí je předán do ovládacího prvku v nesprávném formátu například nesprávně naformátovanou datum.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> – Pokud novou hodnotu nelze převést z řetězce na formát ovládacího prvku rozpozná.|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> – Když je proveden pokus o k manipulaci s ovládací prvek, který není povolen.|  
  
## <a name="see-also"></a>Viz také:

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Ukázka ValuePattern vložit Text](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
