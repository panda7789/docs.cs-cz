---
title: Implementace vzoru ovládacích prvků hodnota pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Value
- UI Automation, Value control pattern
- Value control pattern
ms.assetid: b0fcdd87-3add-4345-bca9-e891205e02ba
ms.openlocfilehash: eb77f26bbe3546a3f90804c3648f8547fb6abad0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180094"
---
# <a name="implementing-the-ui-automation-value-control-pattern"></a>Implementace vzoru ovládacích prvků hodnota pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma představuje pokyny a <xref:System.Windows.Automation.Provider.IValueProvider>konvence pro implementaci , včetně informací o událostech a vlastnostech. Odkazy na další odkazy jsou uvedeny na konci tématu.  
  
 Vzor <xref:System.Windows.Automation.ValuePattern> ovládacího prvku se používá k podpoře ovládacích prvků, které mají vnitřní hodnotu, která nezahrnuje oblast a které mohou být reprezentovány jako řetězec. Tento řetězec lze upravit, v závislosti na ovládacím prvku a jeho nastavení. Příklady ovládacích prvků, které implementují tento vzor, naleznete [v tématu Mapování vzorů ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Prováděcí pokyny a úmluvy  
 Při implementaci vzor řízení hodnoty, poznamenejte si následující pokyny a konvence:  
  
- Ovládací prvky, jako <xref:System.Windows.Automation.ControlType.ListItem> je a <xref:System.Windows.Automation.ControlType.TreeItem> musí podporovat, <xref:System.Windows.Automation.ValuePattern> pokud je hodnota některé z položek upravitelná, bez ohledu na aktuální režim úprav ovládacího prvku. Nadřazený <xref:System.Windows.Automation.ValuePattern> ovládací prvek musí také podporovat, pokud podřízené položky jsou upravitelné.  
  
 ![Upravitelná položka seznamu.](./media/uia-valuepattern-editable-listitem.PNG "UIA_ValuePattern_Editable_ListItem")  
Příklad upravitelné položky seznamu  
  
- Jednořádkové ovládací prvky úprav podporují programový <xref:System.Windows.Automation.Provider.IValueProvider>přístup k jejich obsahu implementací . Víceřádkové ovládací prvky úprav <xref:System.Windows.Automation.Provider.IValueProvider>však neimplementují ; místo toho poskytují přístup ke <xref:System.Windows.Automation.Provider.ITextProvider>svému obsahu implementací .  
  
- Chcete-li načíst textový obsah víceřádkového ovládacího <xref:System.Windows.Automation.Provider.ITextProvider>prvku pro úpravy, musí ovládací prvek implementovat . Však <xref:System.Windows.Automation.Provider.ITextProvider> nepodporuje nastavení hodnoty ovládacího prvku.  
  
- <xref:System.Windows.Automation.Provider.IValueProvider>nepodporuje načítání informací o formátování nebo hodnot podřetězců. Implementujte <xref:System.Windows.Automation.Provider.ITextProvider> v těchto scénářích.  
  
- <xref:System.Windows.Automation.Provider.IValueProvider>musí být implementována ovládacími prvky, jako je například ovládací prvek **výběru barvy** z aplikace Microsoft Word (znázorněno níže), který podporuje mapování řetězců mezi hodnotou barvy (například "žlutá") a ekvivalentní vnitřní strukturou RGB.  
  
 ![Výběr barvy se zvýrazněnou žlutou barvou](./media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Příklad mapování řetězce políčka barev  
  
- Ovládací prvek by <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> měl `true` mít <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> nastavena na a jeho nastavit `false` před povolením volání <xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A>.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>
## <a name="required-members-for-ivalueprovider"></a>Povinné členy pro IValueProvider  
 Následující vlastnosti a metody jsou <xref:System.Windows.Automation.Provider.IValueProvider>vyžadovány pro implementaci .  
  
|Požadované členy|Typ člena|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.ValuePattern.ValueProperty>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.ValuePattern.SetValue%2A>|Metoda|Žádný|  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatelé musí vyvolat následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> - Pokud jsou informace specifické pro národní prostředí předány ovládacímu prvku v nesprávném formátu, například nesprávně formátované datum.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> - Pokud nelze novou hodnotu převést z řetězce do formátu, který ovládací prvek rozpozná.|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> - Při pokusu o manipulaci s ovládacím prvkem, který není povolen.|  
  
## <a name="see-also"></a>Viz také

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Ukázka textu vložení vzoru valuePattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
