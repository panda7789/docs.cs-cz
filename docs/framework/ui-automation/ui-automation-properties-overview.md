---
title: Přehled vlastností automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, properties
- properties, UI Automation
ms.assetid: a6c31d7b-b33e-49b3-b5c1-31a345f9b7c8
ms.openlocfilehash: 8a44fd89017002ae51d9b15a22bac97668d0ff90
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179872"
---
# <a name="ui-automation-properties-overview"></a>Přehled vlastností automatizace uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Zprostředkovatelé automatizace uživatelského rozhraní zveřejňují vlastnosti na [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prvky. Tyto vlastnosti umožňují klientským aplikacím automatizace [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]uživatelského rozhraní zjišťovat informace o částech ovládacích prvků , zejména statických a dynamických dat.  
  
 Tato část poskytuje široký [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] přehled vlastností. Konkrétnější informace jsou uvedeny v následujících tématech:  
  
- [Vlastnosti automatizace uživatelského rozhraní pro klienty](ui-automation-properties-for-clients.md)  
  
- [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru](server-side-ui-automation-provider-implementation.md)  
  
<a name="Property_Identifiers"></a>
## <a name="property-identifiers"></a>Identifikátory vlastností  
 Každá vlastnost je označena číslem a názvem. Názvy vlastností se používají pouze pro ladění a diagnostiku. Zprostředkovatelé používají číselná ID k identifikaci příchozích požadavků na vlastnosti. Klientské aplikace však <xref:System.Windows.Automation.AutomationProperty>používají pouze , který zapouzdřuje číslo a název k identifikaci vlastností, které chtějí načíst.  
  
 <xref:System.Windows.Automation.AutomationProperty>objekty představující určité vlastnosti jsou k dispozici jako pole v různých třídách. Z bezpečnostních důvodů zprostředkovatelé automatizace uživatelského rozhraní získat tyto objekty ze samostatné sady tříd, které jsou obsaženy v Uiautomationtypes.dll.  
  
 Následující tabulka kategorizuje vlastnosti podle tříd, které obsahují <xref:System.Windows.Automation.AutomationProperty>ID.  
  
|Druhy vlastností|Klienti získají ID od|Poskytovatelé získají ID od|  
|-------------------------|--------------------------|----------------------------|  
|Vlastnosti společné pro všechny prvky (viz následující tabulky)|<xref:System.Windows.Automation.AutomationElement>|<xref:System.Windows.Automation.AutomationElementIdentifiers>|  
|Umístění dokovacího okna|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.DockPatternIdentifiers>|  
|Stav prvku, který může rozbalit a sbalit|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers>|  
|Vlastnosti položky v mřížce|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.GridItemPatternIdentifiers>|  
|Vlastnosti mřížky|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.GridPatternIdentifiers>|  
|Aktuální a podporované zobrazení prvku, který má více zobrazení|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers>|  
|Vlastnosti prvku, který se pohybuje v rozsahu hodnot, například posuvník|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.RangeValuePatternIdentifiers>|  
|Vlastnosti rolovacího okna|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.ScrollPatternIdentifiers>|  
|Stav a kontejner položky, kterou lze vybrat, jako v seznamu|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers>|  
|Vlastnosti ovládacího prvku, který obsahuje položky výběru|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.SelectionPatternIdentifiers>|  
|Záhlaví sloupců a řádků položky v tabulce|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.TableItemPatternIdentifiers>|  
|Záhlaví sloupců a řádků a orientace tabulky|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.TablePatternIdentifiers>|  
|Stav přepínacího ovládacího prvku|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.TogglePatternIdentifiers>|  
|Možnosti prvku, který lze přesunout, otočit nebo změnit jejich velikost|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.TransformPatternIdentifiers>|  
|Možnosti hodnoty a čtení a zápisu prvku, který má hodnotu|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.ValuePatternIdentifiers>|  
|Možnosti a stav okna|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.WindowPatternIdentifiers>|  
  
<a name="Properties_by_Category"></a>
## <a name="properties-by-category"></a>Vlastnosti podle kategorie  
 Následující tabulky kategorizují vlastnosti, jejichž ID se nacházejí v <xref:System.Windows.Automation.AutomationElement> a <xref:System.Windows.Automation.AutomationElementIdentifiers>. Tyto vlastnosti jsou společné pro všechny ovládací prvky. Všechny kromě několika z nich jsou pravděpodobně statické po celou dobu životnosti aplikace zprostředkovatele; většina dynamických vlastností je přidružena ke vzorům ovládacího prvku.  
  
 Sloupec **Access vlastností** obsahuje seznam všech dalších přistupujících objektů pro každou vlastnost, kromě <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> a <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>. Další informace o získání vlastností v klientské aplikaci naleznete v [tématu Vlastnosti automatizace uživatelského rozhraní pro klienty](ui-automation-properties-for-clients.md).  
  
> [!NOTE]
> Konkrétní informace o jednotlivých vlastnostech získáte odkazem ve **sloupci Access vlastností.**  
  
### <a name="display-characteristics"></a>Charakteristiky zobrazení  
  
|Identifikátor vlastnosti|Přístup k vlastnostem|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>|  
|<xref:System.Windows.Automation.AutomationElement.CultureProperty>|neuvedeno|  
|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsOffscreen%2A>|  
|<xref:System.Windows.Automation.AutomationElement.OrientationProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Orientation%2A>|  
  
### <a name="element-type"></a>Typ prvku  
  
|Identifikátor vlastnosti|Přístup k vlastnostem|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsContentElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsControlElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LocalizedControlType%2A>|  
  
### <a name="identification"></a>Identifikace  
  
|Identifikátor vlastnosti|Přístup k vlastnostem|  
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
  
|Identifikátor vlastnosti|Přístup k vlastnostem|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AcceleratorKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AccessKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>|<xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>|  
|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HasKeyboardFocus%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsEnabled%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsKeyboardFocusable%2A>|  
  
### <a name="support-for-patterns"></a>Podpora pro vzory  
  
|Identifikátor vlastnosti|Přístup k vlastnostem|  
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
  
|Identifikátor vlastnosti|Přístup k vlastnostem|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.IsRequiredForFormProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsRequiredForForm%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsPassword%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemStatusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemStatus%2A>|  
  
<a name="Localization"></a>
## <a name="localization"></a>Lokalizace  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]poskytovatelé by měli v jazyce operačního systému prezentovat následující vlastnosti:  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>  
  
<a name="Properties_and_Events"></a>
## <a name="properties-and-events"></a>Vlastnosti a události  
 Úzce souvisí s [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnostmi v je koncept události změněné vlastnostmi. Pro dynamické vlastnosti klientská aplikace potřebuje způsob, jak zjistit, že hodnota vlastnosti se změnila, tak, aby mohla aktualizovat svou mezipaměť informací nebo reagovat na nové informace jiným způsobem.  
  
 Zprostředkovatelé vyvolat události, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] když něco v změny. Pokud je například zaškrtnuto nebo zaškrtnuto políčko, je událost změněná vlastností vyvolána implementací vzoru Přepnout zprostředkovatelem. Zprostředkovatelé mohou vyvolat události selektivně, v závislosti na tom, zda všichni klienti jsou naslouchání události nebo naslouchání pro konkrétní události.  
  
 Ne všechny změny vlastností vyvolávají události; to je zcela až do implementace zprostředkovatele automatizace uživatelského rozhraní pro prvek. Například standardní zprostředkovatelé proxy pro seznamy nevyvolávají <xref:System.Windows.Automation.SelectionPattern.SelectionProperty> událost při změnách. V tomto případě aplikace místo toho <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>musí naslouchat .  
  
 Klienti poslouchají události tím, že se k nim přihlásí. Přihlášení k odběru událostí znamená vytvoření metody delegáta, které mohou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zpracovávat události a pak předávání metod spolu s konkrétní události, které budou řešeny v těchto metodách. Pro události změněné vlastnostmi zejména <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>klienti musí implementovat .  
  
## <a name="see-also"></a>Viz také

- [Práce s mezipamětí u klientů automatizace uživatelského rozhraní](caching-in-ui-automation-clients.md)
- [Vlastnosti automatizace uživatelského rozhraní pro klienty](ui-automation-properties-for-clients.md)
- [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru](server-side-ui-automation-provider-implementation.md)
- [Hledání prvku automatizace uživatelského rozhraní na základě podmínky pro vlastnost](find-a-ui-automation-element-based-on-a-property-condition.md)
- [Vrácení vlastností ze zprostředkovatele automatizace uživatelského rozhraní](return-properties-from-a-ui-automation-provider.md)
- [Vyvolávání událostí ze zprostředkovatele automatizace uživatelského rozhraní](raise-events-from-a-ui-automation-provider.md)
