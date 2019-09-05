---
title: Implementace vzoru ovládacích prvků hodnota pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Value
- UI Automation, Value control pattern
- Value control pattern
ms.assetid: b0fcdd87-3add-4345-bca9-e891205e02ba
ms.openlocfilehash: 4af35b3ad1277723d4102b3aeac48748588ef8bf
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70244008"
---
# <a name="implementing-the-ui-automation-value-control-pattern"></a>Implementace vzoru ovládacích prvků hodnota pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 Toto téma obsahuje pokyny a konvence pro <xref:System.Windows.Automation.Provider.IValueProvider>implementaci, včetně informací o událostech a vlastnostech. Odkazy na další odkazy jsou uvedeny na konci tématu.  
  
 Vzor <xref:System.Windows.Automation.ValuePattern> ovládacího prvku se používá pro podporu ovládacích prvků, které mají vnitřní hodnotu, která není pokrývá rozsah a která může být reprezentována jako řetězec. Tento řetězec může být upravitelný v závislosti na ovládacím prvku a jeho nastavení. Příklady ovládacích prvků, které implementují tento model, najdete v tématu [mapování vzoru ovládacího prvku pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Pokyny a konvence implementace  
 Při implementaci vzoru ovládacího prvku hodnoty si všimněte následujících pokynů a konvencí:  
  
- Ovládací prvky jako <xref:System.Windows.Automation.ControlType.TreeItem> <xref:System.Windows.Automation.ValuePattern> a musí podporovat, pokud je hodnota kterékoli z položek upravitelná bez ohledu na aktuální režim úprav ovládacího prvku. <xref:System.Windows.Automation.ControlType.ListItem> Nadřazený ovládací prvek musí podporovat <xref:System.Windows.Automation.ValuePattern> i v případě, že jsou podřízené položky editovatelné.  
  
 ![Upravitelná položka seznamu](../../../docs/framework/ui-automation/media/uia-valuepattern-editable-listitem.PNG "UIA_ValuePattern_Editable_ListItem")  
Příklad položky upravitelného seznamu  
  
- Jednořádkové textové ovládací prvky podporují programový přístup ke svému obsahu implementací <xref:System.Windows.Automation.Provider.IValueProvider>. Nicméně víceřádkové textové ovládací prvky neimplementují <xref:System.Windows.Automation.Provider.IValueProvider>; namísto toho poskytují přístup ke svému obsahu implementací. <xref:System.Windows.Automation.Provider.ITextProvider>  
  
- Chcete-li načíst textový obsah víceřádkového ovládacího prvku pro úpravy, musí být ovládací prvek <xref:System.Windows.Automation.Provider.ITextProvider>implementován. <xref:System.Windows.Automation.Provider.ITextProvider> Nicméně nepodporuje nastavení hodnoty ovládacího prvku.  
  
- <xref:System.Windows.Automation.Provider.IValueProvider>nepodporuje načítání informací o formátování nebo hodnot podřetězců. Implementujte <xref:System.Windows.Automation.Provider.ITextProvider> v těchto scénářích.  
  
- <xref:System.Windows.Automation.Provider.IValueProvider>musí být implementována ovládacími prvky, jako je ovládací prvek výběru [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] výběru barvy z (zobrazeno níže), který podporuje mapování řetězců mezi hodnotou barvy (například "žlutá") a ekvivalentní vnitřní strukturou RGB.  
  
 ![Výběr barvy se žlutým zvýrazněním](../../../docs/framework/ui-automation/media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Příklad mapování řetězců vzorníku barev  
  
- Aby bylo možné povolit volání <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> `true` `false` <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> ,musímítovládacíprveknastavennaa<xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A>jeho sadu na.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-ivalueprovider"></a>Vyžadovaná členové pro IValueProvider  
 Pro implementaci <xref:System.Windows.Automation.Provider.IValueProvider>jsou vyžadovány následující vlastnosti a metody.  
  
|Vyžadovaná členové|Typ člena|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.ValuePattern.ValueProperty>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.ValuePattern.SetValue%2A>|Metoda|Žádné|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatelé musí vyvolat následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> – Pokud jsou informace specifické pro národní prostředí předány ovládacímu prvku v nesprávném formátu, jako je například nesprávně naformátované datum.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> – Pokud novou hodnotu nelze převést z řetězce na formát, který ovládací prvek rozpozná.|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> – Když se provede pokus o manipulaci s ovládacím prvkem, který není povolený.|  
  
## <a name="see-also"></a>Viz také:

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Ukázka vložení textu ValuePattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
