---
title: Implementace vzoru ovládacích prvků hodnota pro automatizaci uživatelského rozhraní
description: Přečtěte si pokyny a konvence pro implementaci vzoru řízení hodnoty v automatizaci uživatelského rozhraní. Znáte požadované členy pro rozhraní IValueProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Value
- UI Automation, Value control pattern
- Value control pattern
ms.assetid: b0fcdd87-3add-4345-bca9-e891205e02ba
ms.openlocfilehash: a15c0b50996e2c0dfdc937bc9565d5f9ba20c992
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168200"
---
# <a name="implementing-the-ui-automation-value-control-pattern"></a>Implementace vzoru ovládacích prvků hodnota pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma obsahuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.IValueProvider> , včetně informací o událostech a vlastnostech. Odkazy na další odkazy jsou uvedeny na konci tématu.  
  
 <xref:System.Windows.Automation.ValuePattern>Vzor ovládacího prvku se používá pro podporu ovládacích prvků, které mají vnitřní hodnotu, která není pokrývá rozsah a která může být reprezentována jako řetězec. Tento řetězec může být upravitelný v závislosti na ovládacím prvku a jeho nastavení. Příklady ovládacích prvků, které implementují tento model, najdete v tématu [mapování vzoru ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Pokyny a konvence implementace  
 Při implementaci vzoru ovládacího prvku hodnoty si všimněte následujících pokynů a konvencí:  
  
- Ovládací prvky jako <xref:System.Windows.Automation.ControlType.ListItem> a <xref:System.Windows.Automation.ControlType.TreeItem> musí podporovat <xref:System.Windows.Automation.ValuePattern> , pokud je hodnota kterékoli z položek upravitelná bez ohledu na aktuální režim úprav ovládacího prvku. Nadřazený ovládací prvek musí podporovat i <xref:System.Windows.Automation.ValuePattern> v případě, že jsou podřízené položky editovatelné.  
  
 ![Upravitelná položka seznamu](./media/uia-valuepattern-editable-listitem.PNG "UIA_ValuePattern_Editable_ListItem")  
Příklad položky upravitelného seznamu  
  
- Jednořádkové textové ovládací prvky podporují programový přístup ke svému obsahu implementací <xref:System.Windows.Automation.Provider.IValueProvider> . Nicméně víceřádkové textové ovládací prvky neimplementují <xref:System.Windows.Automation.Provider.IValueProvider> ; namísto toho poskytují přístup ke svému obsahu implementací <xref:System.Windows.Automation.Provider.ITextProvider> .  
  
- Chcete-li načíst textový obsah víceřádkového ovládacího prvku pro úpravy, musí být ovládací prvek implementován <xref:System.Windows.Automation.Provider.ITextProvider> . Nicméně nepodporuje <xref:System.Windows.Automation.Provider.ITextProvider> Nastavení hodnoty ovládacího prvku.  
  
- <xref:System.Windows.Automation.Provider.IValueProvider>nepodporuje načítání informací o formátování nebo hodnot podřetězců. Implementujte <xref:System.Windows.Automation.Provider.ITextProvider> v těchto scénářích.  
  
- <xref:System.Windows.Automation.Provider.IValueProvider>musí být implementována ovládacími prvky, jako je výběr výběru **barvy** z aplikace Microsoft Word (viz níže), která podporuje mapování řetězců mezi hodnotou barvy (například "žlutá") a ekvivalentní vnitřní strukturou RGB.  
  
 ![Výběr barvy se žlutým zvýrazněním](./media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Příklad mapování řetězců vzorníku barev  
  
- Aby bylo možné povolit volání, musí mít ovládací prvek <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> nastaven na `true` a jeho <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> sadu na `false` <xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A> .  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>
## <a name="required-members-for-ivalueprovider"></a>Vyžadovaná členové pro IValueProvider  
 Pro implementaci jsou vyžadovány následující vlastnosti a metody <xref:System.Windows.Automation.Provider.IValueProvider> .  
  
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
  
## <a name="see-also"></a>Viz také

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Ukázka vložení textu ValuePattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
