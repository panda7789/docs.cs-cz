---
title: Přehled vlastností automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, properties
- properties, UI Automation
ms.assetid: a6c31d7b-b33e-49b3-b5c1-31a345f9b7c8
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 3707196cf833577e65dbd1879f2762ec4336abc2
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47073512"
---
# <a name="ui-automation-properties-overview"></a>Přehled vlastností automatizace uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Vystavení zprostředkovatele automatizace uživatelského rozhraní vlastností na [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elementy. Tyto vlastnosti umožňují automatizace uživatelského rozhraní klientských aplikací získat informace o části [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)], zejména ovládací prvky, včetně statickými a dynamickými daty.  
  
 Tato část poskytuje komplexní přehled [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] vlastnosti. Podrobnější informace jsou uvedeny v následujících tématech:  
  
-   [Vlastnosti automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)  
  
-   [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)  
  
<a name="Property_Identifiers"></a>   
## <a name="property-identifiers"></a>Vlastnost identifikátory  
 Každé vlastnosti je identifikován číslo a název. Názvy vlastností se používají pouze pro ladění a Diagnostika. Poskytovatelé číselné [!INCLUDE[TLA2#tla_id#plural](../../../includes/tla2sharptla-idsharpplural-md.md)] k identifikaci příchozí žádosti vlastnost. Klientské aplikace, ale pouze pomocí <xref:System.Windows.Automation.AutomationProperty>, který zapouzdřuje číslo a název, identifikovat vlastnosti chtějí získat.  
  
 <xref:System.Windows.Automation.AutomationProperty> objektů představujících určité vlastnosti jsou k dispozici jako pole v různých tříd. Z bezpečnostních důvodů se zprostředkovateli automatizace uživatelského rozhraní od samostatnou sadu tříd, které jsou obsaženy v Uiautomationtypes.dll získat tyto objekty.  
  
 Následující tabulka rozděluje vlastnosti v rámci tříd, které obsahují <xref:System.Windows.Automation.AutomationProperty> [!INCLUDE[TLA2#tla_id#plural](../../../includes/tla2sharptla-idsharpplural-md.md)].  
  
|Typy vlastností|Klienti získat ID z|Poskytovatelé získat ID z|  
|-------------------------|--------------------------|----------------------------|  
|Vlastnosti společné pro všechny elementy (viz následující tabulky)|<xref:System.Windows.Automation.AutomationElement>|<xref:System.Windows.Automation.AutomationElementIdentifiers>|  
|Umístění okno ukotvení|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.DockPatternIdentifiers>|  
|Stav elementu, který můžete rozbalit nebo sbalit|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers>|  
|Vlastnosti položky v mřížce|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.GridItemPatternIdentifiers>|  
|Vlastnosti tabulky|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.GridPatternIdentifiers>|  
|Aktuální a podporované zobrazení elementu, který má více zobrazení|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers>|  
|Vlastnosti elementu, který přesouvá napříč celou škálou hodnot, například ovládací prvek posuvník|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.RangeValuePatternIdentifiers>|  
|Vlastnosti umožňující posouvání okna|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.ScrollPatternIdentifiers>|  
|Stav a kontejner položky, kterou lze vybrat, stejně jako v seznamu|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers>|  
|Vlastnosti ovládacího prvku, který obsahuje výběr položky|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.SelectionPatternIdentifiers>|  
|Záhlaví řádků a sloupců položky v tabulce|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.TableItemPatternIdentifiers>|  
|Záhlaví řádků a sloupců a orientaci tabulky.|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.TablePatternIdentifiers>|  
|Stav ovládacího prvku přepínací tlačítko|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.TogglePatternIdentifiers>|  
|Možnosti elementu, který je možné přesunout, otočit, nebo se změněnou velikostí|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.TransformPatternIdentifiers>|  
|Možnosti hodnot a r/w elementu, který má hodnotu|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.ValuePatternIdentifiers>|  
|Možnosti a stav okna.|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.WindowPatternIdentifiers>|  
  
<a name="Properties_by_Category"></a>   
## <a name="properties-by-category"></a>Vlastnosti podle kategorie  
 V následujících tabulkách kategorizace vlastnosti jejíž [!INCLUDE[TLA2#tla_id#plural](../../../includes/tla2sharptla-idsharpplural-md.md)] se nacházejí v <xref:System.Windows.Automation.AutomationElement> a <xref:System.Windows.Automation.AutomationElementIdentifiers>. Tyto vlastnosti jsou společné pro všechny ovládací prvky. Vše kromě několik z nich můžou mít statické během životního cyklu aplikace zprostředkovatele. Většina dynamických vlastností jsou spojeny s vzorů ovládacích prvků.  
  
 **Přístup k vlastnostem** sloupec uvádí všechny přistupující objekty pro každou vlastnost kromě <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> a <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>. Další informace o získání vlastnosti v klientské aplikaci najdete v tématu [vlastnosti automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
> [!NOTE]
>  Konkrétní informace o jednotlivých vlastnostech odkazu v **přístup k vlastnostem** sloupce.  
  
### <a name="display-characteristics"></a>Vlastnosti zobrazení  
  
|Identifikátor vlastnosti|Přístup k vlastnosti|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>|  
|<xref:System.Windows.Automation.AutomationElement.CultureProperty>|není k dispozici|  
|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsOffscreen%2A>|  
|<xref:System.Windows.Automation.AutomationElement.OrientationProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Orientation%2A>|  
  
### <a name="element-type"></a>Typ elementu  
  
|Identifikátor vlastnosti|Přístup k vlastnosti|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsContentElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsControlElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LocalizedControlType%2A>|  
  
### <a name="identification"></a>Identifikace  
  
|Identifikátor vlastnosti|Přístup k vlastnosti|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClassNameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ClassName%2A>|  
|<xref:System.Windows.Automation.AutomationElement.FrameworkIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.FrameworkId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LabeledByProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LabeledBy%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ProcessIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ProcessId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.RuntimeIdProperty>|<xref:System.Windows.Automation.AutomationElement.GetRuntimeId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NativeWindowHandleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.NativeWindowHandle%2A>|  
  
### <a name="interaction"></a>Interakce  
  
|Identifikátor vlastnosti|Přístup k vlastnosti|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AcceleratorKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AccessKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>|<xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>|  
|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HasKeyboardFocus%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsEnabled%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsKeyboardFocusable%2A>|  
  
### <a name="support-for-patterns"></a>Podpora pro vzory  
  
|Identifikátor vlastnosti|Přístup k vlastnosti|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.IsDockPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsExpandCollapsePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsGridItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsGridPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsInvokePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsMultipleViewPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsRangeValuePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsScrollItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsScrollPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsSelectionItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsSelectionPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTableItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTablePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTogglePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTransformPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsValuePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsWindowPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
  
### <a name="miscellaneous"></a>Různé  
  
|Identifikátor vlastnosti|Přístup k vlastnosti|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.IsRequiredForFormProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsRequiredForForm%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsPassword%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemStatusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemStatus%2A>|  
  
<a name="Localization"></a>   
## <a name="localization"></a>Lokalizace  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] poskytovatelé by se měl prokázat následující vlastnosti v jazyce operačního systému:  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>  
  
<a name="Properties_and_Events"></a>   
## <a name="properties-and-events"></a>Vlastnosti a události.  
 Úzce souvisí se pomocí vlastnosti v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] je Princip události změny vlastnosti. Pro dynamické vlastnosti klientská aplikace potřebuje způsob, jak zjistit, že hodnoty vlastnosti došlo ke změně, aby mohli aktualizovat své mezipaměti informace nebo reagovat na nové informace jiným způsobem.  
  
 Poskytovatelé vyvolat události, když se něco v [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] změny. Například pokud zaškrtávací políčko zaškrtnuto nebo Ne, je vyvolána událost změny vlastnosti poskytovatele implementací vzorku přepínací tlačítko. Poskytovatelé může vyvolat události selektivně, v závislosti na tom, jestli jsou všichni klienti naslouchání událostem, nebo naslouchá určité události.  
  
 Ne všechny změny vlastností vyvolat události; který je zcela v kompetenci implementace zprostředkovatele automatizace uživatelského rozhraní pro element. Například standardní proxy zprostředkovatelé pro pole se seznamem nevyvolávejte událost při <xref:System.Windows.Automation.SelectionPattern.SelectionProperty> změny. V tomto případě aplikace místo toho musí naslouchat <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>.  
  
 Klienti naslouchat událostem se přihlásíte k jejich odběru. Přihlášení k odběru událostí znamená, že vytváření metod delegáta, které může zpracovávat události a následné předání metod na [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] spolu s konkrétní události, které se budou řešit v těchto metod. Události změny vlastnosti zejména, klienti musí implementovat <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>.  
  
## <a name="see-also"></a>Viz také  
 [Práce s mezipamětí u klientů automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)  
 [Vlastnosti automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)  
 [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)  
 [Hledání prvku automatizace uživatelského rozhraní na základě podmínky pro vlastnost](../../../docs/framework/ui-automation/find-a-ui-automation-element-based-on-a-property-condition.md)  
 [Vrácení vlastností ze zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/return-properties-from-a-ui-automation-provider.md)  
 [Vyvolávání událostí ze zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/raise-events-from-a-ui-automation-provider.md)
