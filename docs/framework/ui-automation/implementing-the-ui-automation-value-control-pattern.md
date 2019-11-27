---
title: Implementace vzoru ovládacích prvků hodnota pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Value
- UI Automation, Value control pattern
- Value control pattern
ms.assetid: b0fcdd87-3add-4345-bca9-e891205e02ba
ms.openlocfilehash: c178283b18aaf2c406292d9ab7e12a24c882c102
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447039"
---
# <a name="implementing-the-ui-automation-value-control-pattern"></a>Implementace vzoru ovládacích prvků hodnota pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma obsahuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.IValueProvider>, včetně informací o událostech a vlastnostech. Odkazy na další odkazy jsou uvedeny na konci tématu.  
  
 Vzor ovládacího prvku <xref:System.Windows.Automation.ValuePattern> slouží k podpoře ovládacích prvků, které mají vnitřní hodnotu nepokrývání rozsahu a které mohou být reprezentovány jako řetězec. Tento řetězec může být upravitelný v závislosti na ovládacím prvku a jeho nastavení. Příklady ovládacích prvků, které implementují tento model, najdete v tématu [mapování vzoru ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Pokyny a konvence implementace  
 Při implementaci vzoru ovládacího prvku hodnoty si všimněte následujících pokynů a konvencí:  
  
- Ovládací prvky jako <xref:System.Windows.Automation.ControlType.ListItem> a <xref:System.Windows.Automation.ControlType.TreeItem> musí podporovat <xref:System.Windows.Automation.ValuePattern>, pokud je hodnota kterékoli z položek upravitelná, bez ohledu na aktuální režim úprav ovládacího prvku. Nadřazený ovládací prvek musí také podporovat <xref:System.Windows.Automation.ValuePattern>, pokud jsou podřízené položky editovatelné.  
  
 ![Upravitelná položka seznamu](./media/uia-valuepattern-editable-listitem.PNG "UIA_ValuePattern_Editable_ListItem")  
Příklad položky upravitelného seznamu  
  
- Jednořádkové textové ovládací prvky podporují programový přístup k jejich obsahu implementací <xref:System.Windows.Automation.Provider.IValueProvider>. Nicméně víceřádkové textové ovládací prvky neimplementují <xref:System.Windows.Automation.Provider.IValueProvider>; místo toho poskytují přístup ke svému obsahu implementací <xref:System.Windows.Automation.Provider.ITextProvider>.  
  
- Chcete-li načíst textový obsah víceřádkového ovládacího prvku pro úpravy, ovládací prvek musí implementovat <xref:System.Windows.Automation.Provider.ITextProvider>. <xref:System.Windows.Automation.Provider.ITextProvider> však nepodporuje nastavení hodnoty ovládacího prvku.  
  
- <xref:System.Windows.Automation.Provider.IValueProvider> nepodporuje načítání informací o formátování nebo hodnot podřetězců. Implementujte <xref:System.Windows.Automation.Provider.ITextProvider> v těchto scénářích.  
  
- <xref:System.Windows.Automation.Provider.IValueProvider> musí být implementované ovládacími prvky, jako je výběr výběru **barvy** z aplikace Microsoft Word (viz níže), která podporuje mapování řetězců mezi hodnotou barvy (například "žlutá") a ekvivalentní vnitřní strukturou RGB.  
  
 ![Výběr barvy se žlutým zvýrazněním](./media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Příklad mapování řetězců vzorníku barev  
  
- Ovládací prvek by měl mít <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> nastavenou na `true` a jeho <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> nastaveno na `false` předtím, než povolíte volání <xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A>.  
  
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

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Ukázka vložení textu ValuePattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
