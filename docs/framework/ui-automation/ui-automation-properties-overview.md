---
title: Přehled vlastností automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, properties
- properties, UI Automation
ms.assetid: a6c31d7b-b33e-49b3-b5c1-31a345f9b7c8
ms.openlocfilehash: 0468a2f47b9f270e37ad800b83d70c475cbed2c6
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796623"
---
# <a name="ui-automation-properties-overview"></a>Přehled vlastností automatizace uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 Zprostředkovatelé automatizace uživatelského rozhraní zveřejňují vlastnosti u [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elementů. Tyto vlastnosti umožňují klientským aplikacím automatizace uživatelského rozhraní zjišťovat informace o částech [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)], zejména o ovládacích prvcích, včetně statických i dynamických dat.  
  
 V této části najdete obsáhlý přehled [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] vlastností. Konkrétnější informace jsou uvedeny v následujících tématech:  
  
- [Vlastnosti automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)  
  
- [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)  
  
<a name="Property_Identifiers"></a>   
## <a name="property-identifiers"></a>Identifikátory vlastností  
 Každá vlastnost je identifikována číslem a názvem. Názvy vlastností jsou používány pouze pro ladění a diagnostiku. Poskytovatelé používají číselná ID k identifikaci příchozích požadavků na vlastnost. Klientské aplikace však používají <xref:System.Windows.Automation.AutomationProperty>pouze, které zapouzdřují číslo a název pro identifikaci vlastností, které chtějí načíst.  
  
 <xref:System.Windows.Automation.AutomationProperty>objekty reprezentující konkrétní vlastnosti jsou k dispozici jako pole v různých třídách. Z bezpečnostních důvodů poskytovatelé automatizace uživatelského rozhraní získávají tyto objekty ze samostatné sady tříd, které jsou obsaženy v knihovně UIAutomationTypes. dll.  
  
 V následující tabulce jsou vlastnosti třídy, které obsahují <xref:System.Windows.Automation.AutomationProperty>ID.  
  
|Typy vlastností|Klienti získávají ID z|Poskytovatelé získají ID z|  
|-------------------------|--------------------------|----------------------------|  
|Vlastnosti společné pro všechny elementy (viz následující tabulky)|<xref:System.Windows.Automation.AutomationElement>|<xref:System.Windows.Automation.AutomationElementIdentifiers>|  
|Pozice ukotveného okna|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.DockPatternIdentifiers>|  
|Stav prvku, který lze rozbalit a sbalit|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers>|  
|Vlastnosti položky v mřížce|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.GridItemPatternIdentifiers>|  
|Vlastnosti mřížky|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.GridPatternIdentifiers>|  
|Aktuální a podporované zobrazení prvku, který má více zobrazení|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers>|  
|Vlastnosti prvku, který se přesouvá nad určitou škálou hodnot, jako je například posuvník|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.RangeValuePatternIdentifiers>|  
|Vlastnosti okna posouvání|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.ScrollPatternIdentifiers>|  
|Stav a kontejner položky, kterou lze vybrat, jako v seznamu|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers>|  
|Vlastnosti ovládacího prvku, který obsahuje položky výběru|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.SelectionPatternIdentifiers>|  
|Záhlaví sloupců a řádků položky v tabulce|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.TableItemPatternIdentifiers>|  
|Záhlaví sloupců a řádků a orientace tabulky|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.TablePatternIdentifiers>|  
|Stav ovládacího prvku přepínací tlačítko|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.TogglePatternIdentifiers>|  
|Schopnosti prvku, který lze přesunout, otočit nebo změnit jeho velikost|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.TransformPatternIdentifiers>|  
|Hodnoty a možnosti čtení a zápisu prvku, který má hodnotu|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.ValuePatternIdentifiers>|  
|Možnosti a stav okna|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.WindowPatternIdentifiers>|  
  
<a name="Properties_by_Category"></a>   
## <a name="properties-by-category"></a>Vlastnosti podle kategorie  
 Následující tabulky kategorizují vlastnosti, jejichž identifikátory se nacházejí v <xref:System.Windows.Automation.AutomationElement> a. <xref:System.Windows.Automation.AutomationElementIdentifiers> Tyto vlastnosti jsou společné pro všechny ovládací prvky. U všech, ale u některých z nich je pravděpodobně statický po celou dobu životnosti aplikace poskytovatele; Většina dynamických vlastností je přidružená k vzorům ovládacích prvků.  
  
 Sloupec pro **přístup k vlastnostem** uvádí všechny další přistupující objekty pro každou vlastnost, kromě <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> a <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>. Další informace o získání vlastností v klientské aplikaci najdete v tématu [Vlastnosti automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
> [!NOTE]
>  Konkrétní informace o jednotlivých vlastnostech získáte pomocí odkazu ve sloupci **přístup k vlastnostem** .  
  
### <a name="display-characteristics"></a>Vlastnosti zobrazení  
  
|Identifikátor vlastnosti|Přístup k vlastnosti|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>|  
|<xref:System.Windows.Automation.AutomationElement.CultureProperty>|není k dispozici|  
|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsOffscreen%2A>|  
|<xref:System.Windows.Automation.AutomationElement.OrientationProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Orientation%2A>|  
  
### <a name="element-type"></a>Element Type  
  
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
  
### <a name="support-for-patterns"></a>Podpora vzorů  
  
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
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Poskytovatelé by měli v jazyce operačního systému zobrazit následující vlastnosti:  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>  
  
<a name="Properties_and_Events"></a>   
## <a name="properties-and-events"></a>Vlastnosti a události  
 Úzce svázané v rámci s vlastnostmi v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nástroji je koncept událostí změněných vlastností. U dynamických vlastností klientská aplikace potřebuje způsob, jak zjistit, že došlo ke změně hodnoty vlastnosti, aby mohla aktualizovat svou mezipaměť informací nebo reagovat na nové informace jiným způsobem.  
  
 Poskytovatelé vyvolávají události, když se [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] něco změní. Například pokud je zaškrtávací políčko zaškrtnuto nebo vymazáno, událost změněné vlastností je vyvolána implementací vzoru přepínání poskytovatele. Poskytovatelé můžou události vyvolávat selektivně, v závislosti na tom, jestli některý z klientů naslouchá událostem nebo naslouchá konkrétním událostem.  
  
 Ne všechny změny vlastností vyvolávají události; To je zcela až do implementace zprostředkovatele automatizace uživatelského rozhraní pro element. Například standardní poskytovatelé proxy serverů pro seznamy nevyvolávají událost při <xref:System.Windows.Automation.SelectionPattern.SelectionProperty> změnách. V takovém případě musí aplikace naslouchat pro <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>.  
  
 Klienti naslouchají událostem tím, že se přihlásí k odběru. Přihlášení k odběru událostí znamená vytvoření metod delegáta, které mohou zpracovávat události a následně předání metod do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] spolu s konkrétními událostmi, které budou v těchto metodách řešeny. Pro události změněné vlastností musí být klienti implementované <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>.  
  
## <a name="see-also"></a>Viz také:

- [Práce s mezipamětí u klientů automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
- [Vlastnosti automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)
- [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
- [Hledání prvku automatizace uživatelského rozhraní na základě podmínky pro vlastnost](../../../docs/framework/ui-automation/find-a-ui-automation-element-based-on-a-property-condition.md)
- [Vrácení vlastností ze zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/return-properties-from-a-ui-automation-provider.md)
- [Vyvolávání událostí ze zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/raise-events-from-a-ui-automation-provider.md)
