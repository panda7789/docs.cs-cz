---
title: Vlastnosti automatizace uživatelského rozhraní pro klienty
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, UI Automation clients
- UI Automation, client properties
ms.assetid: 255905af-0b17-485c-93d4-8a2db2a6524b
ms.openlocfilehash: 3ef1e7c6e21f30c5bdea096003f192c38059ab2e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441358"
---
# <a name="ui-automation-properties-for-clients"></a>Vlastnosti automatizace uživatelského rozhraní pro klienty
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Tento přehled představuje [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastností, které jsou zpřístupněny klientským aplikacím automatizace uživatelského rozhraní.  
  
 Vlastnosti objektů <xref:System.Windows.Automation.AutomationElement> obsahují informace o [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] prvky, obvykle ovládací prvky. Vlastnosti <xref:System.Windows.Automation.AutomationElement> jsou obecné; To znamená, že není specifické pro typ ovládacího prvku. Mnohé z těchto vlastností jsou zpřístupněny ve struktuře <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation>.  
  
 Vzory ovládacích prvků mají také vlastnosti. Vlastnosti vzorů ovládacích prvků jsou specifické pro vzor. Například <xref:System.Windows.Automation.ScrollPattern> obsahuje vlastnosti, které umožňují klientské aplikaci zjistit, zda je okno svisle nebo vodorovně rolovací a jaké jsou aktuální velikosti zobrazení a posunutí umístění. Vzory ovládacích prvků zpřístupňují všechny své vlastnosti prostřednictvím struktury; například <xref:System.Windows.Automation.ScrollPattern.ScrollPatternInformation>.  
  
 vlastnosti [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jsou jen pro čtení. Chcete-li nastavit vlastnosti ovládacího prvku, je nutné použít metody příslušného vzoru ovládacího prvku. Můžete například použít <xref:System.Windows.Automation.ScrollPattern.Scroll%2A> ke změně hodnot pozice posuvných oken.  
  
 Aby bylo možné zvýšit výkon, hodnoty vlastností ovládacích prvků a vzorů ovládacích prvků mohou být uloženy do mezipaměti při načítání <xref:System.Windows.Automation.AutomationElement> objektů. Další informace najdete v tématu [ukládání do mezipaměti v klientech automatizace uživatelského rozhraní](caching-in-ui-automation-clients.md).  
  
## <a name="property-ids"></a>ID vlastností  
 Identifikátory vlastností (IDs) jsou jedinečné a konstantní hodnoty, které jsou zapouzdřeny v <xref:System.Windows.Automation.AutomationProperty> objekty. Klientské aplikace automatizace uživatelského rozhraní získávají tato ID z třídy <xref:System.Windows.Automation.AutomationElement> nebo z příslušné třídy vzoru ovládacího prvku, jako je například <xref:System.Windows.Automation.ScrollPattern>. Zprostředkovatelé automatizace uživatelského rozhraní je získají z <xref:System.Windows.Automation.AutomationElementIdentifiers> nebo z jedné z tříd identifikátorů vzoru ovládacího prvku, jako je například <xref:System.Windows.Automation.ScrollPatternIdentifiers>.  
  
 Číselná <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> <xref:System.Windows.Automation.AutomationProperty> je využívána poskytovateli k identifikaci vlastností, které jsou dotazovány v metodě <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPropertyValue%2A?displayProperty=nameWithType>. Obecně klientské aplikace nemusí kontrolovat <xref:System.Windows.Automation.AutomationIdentifier.Id%2A>. <xref:System.Windows.Automation.AutomationIdentifier.ProgrammaticName%2A> se používá pouze pro účely ladění a diagnostiky.  
  
## <a name="property-conditions"></a>Podmínky vlastnosti  
 ID vlastností se používají při vytváření <xref:System.Windows.Automation.PropertyCondition> objektů používaných k hledání objektů <xref:System.Windows.Automation.AutomationElement>. Například můžete chtít najít <xref:System.Windows.Automation.AutomationElement>, který má určitý název, nebo všechny ovládací prvky, které jsou povoleny. Každý <xref:System.Windows.Automation.PropertyCondition> Určuje identifikátor <xref:System.Windows.Automation.AutomationProperty> a hodnotu, kterou musí vlastnost odpovídat.  
  
 Další informace najdete v následujících referenčních tématech:  
  
- <xref:System.Windows.Automation.AutomationElement.FindFirst%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.FindAll%2A>  
  
- <xref:System.Windows.Automation.TreeWalker.Condition%2A>  
  
## <a name="retrieving-properties"></a>Načítání vlastností  
 Některé vlastnosti <xref:System.Windows.Automation.AutomationElement> a všechny vlastnosti třídy vzoru ovládacího prvku jsou zpřístupněny jako vnořené vlastnosti vlastnosti `Current` nebo `Cached` objektu <xref:System.Windows.Automation.AutomationElement> nebo objektu vzoru ovládacího prvku.  
  
 Kromě toho je možné načíst libovolné <xref:System.Windows.Automation.AutomationElement> nebo vlastnost vzoru ovládacího prvku, včetně vlastnosti, která není k dispozici ve struktuře <xref:System.Windows.Automation.AutomationElement.Cached%2A> nebo <xref:System.Windows.Automation.AutomationElement.Current%2A>, pomocí jedné z následujících metod:  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>  
  
 Tyto metody nabízejí poněkud lepší výkon a také přístup k celé škále vlastností.  
  
 Následující příklad kódu ukazuje dva způsoby načítání vlastnosti v <xref:System.Windows.Automation.AutomationElement>.  
  
 [!code-csharp[UIAClient_snip#121](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#121)]
 [!code-vb[UIAClient_snip#121](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#121)]  
  
 Chcete-li načíst vlastnosti vzorů ovládacích prvků, které jsou podporovány <xref:System.Windows.Automation.AutomationElement>, není nutné načíst objekt vzoru ovládacího prvku. Jednoduše do metody předejte jeden z identifikátorů vlastnosti vzoru.  
  
 Následující příklad kódu ukazuje dva způsoby, jak načíst vlastnost pro vzor ovládacího prvku.  
  
 [!code-csharp[UIAClient_snip#122](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#122)]
 [!code-vb[UIAClient_snip#122](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#122)]  
  
 Metody `Get` vrací <xref:System.Object>. Aplikace musí přetypování vráceného objektu na správný typ před použitím hodnoty.  
  
## <a name="default-property-values"></a>Výchozí hodnoty vlastností  
 Pokud zprostředkovatel automatizace uživatelského rozhraní neimplementuje vlastnost, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] systém bude moci dodat výchozí hodnotu. Například pokud poskytovatel pro ovládací prvek nepodporuje vlastnost identifikovanou <xref:System.Windows.Automation.AutomationElement.HelpTextProperty>, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vrátí prázdný řetězec. Podobně pokud poskytovatel nepodporuje vlastnost identifikovanou <xref:System.Windows.Automation.AutomationElement.IsDockPatternAvailableProperty>, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vrátí `false`.  
  
 Toto chování lze změnit pomocí přetížení metod <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> a <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType>. Když jako druhý parametr určíte `true`, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nevrátí výchozí hodnotu, ale místo toho vrátí <xref:System.Windows.Automation.AutomationElement.NotSupported>speciální hodnotu.  
  
 Následující příklad kódu se pokusí načíst vlastnost z prvku a pokud vlastnost není podporována, je místo toho použita hodnota definovaná aplikací.  
  
 [!code-csharp[UIAClient_snip#123](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#123)]
 [!code-vb[UIAClient_snip#123](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#123)]  
  
 Chcete-li zjistit, jaké vlastnosti jsou podporovány prvkem, použijte <xref:System.Windows.Automation.AutomationElement.GetSupportedProperties%2A>. Vrátí pole identifikátorů <xref:System.Windows.Automation.AutomationProperty>.  
  
## <a name="property-changed-events"></a>Události změněné vlastností  
 Když se změní hodnota vlastnosti u <xref:System.Windows.Automation.AutomationElement> nebo vzoru ovládacího prvku, vyvolá se událost. Aplikace se může přihlásit k odběru takových událostí voláním <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>a zadáním pole identifikátorů <xref:System.Windows.Automation.AutomationProperty> jako posledního parametru, aby bylo možné určit vlastnosti zájmu.  
  
 V <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>můžete určit vlastnost, která se změnila, zkontrolováním <xref:System.Windows.Automation.AutomationPropertyChangedEventArgs.Property%2A> člena argumentů události. Argumenty obsahují také starou a novou hodnotu vlastnosti [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], která se změnila. Tyto hodnoty jsou typu <xref:System.Object> a před použitím musí být přetypování na správný typ.  
  
## <a name="additional-automationelement-properties"></a>Další vlastnosti třída AutomationElement neobsahuje  
 Kromě struktur vlastností <xref:System.Windows.Automation.AutomationElement.Current%2A> a <xref:System.Windows.Automation.AutomationElement.Cached%2A> má <xref:System.Windows.Automation.AutomationElement> následující vlastnosti, které jsou načteny prostřednictvím přístupových objektů jednoduchých vlastností.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Windows.Automation.AutomationElement.CachedChildren%2A>|Kolekce podřízených objektů <xref:System.Windows.Automation.AutomationElement>, které jsou v mezipaměti.|  
|<xref:System.Windows.Automation.AutomationElement.CachedParent%2A>|Nadřazený objekt <xref:System.Windows.Automation.AutomationElement>, který je v mezipaměti.|  
|<xref:System.Windows.Automation.AutomationElement.FocusedElement%2A>|(Statická vlastnost) <xref:System.Windows.Automation.AutomationElement>, která má fokus vstupu.|  
|<xref:System.Windows.Automation.AutomationElement.RootElement%2A>|(Statická vlastnost) Kořenový <xref:System.Windows.Automation.AutomationElement>.|  
  
## <a name="see-also"></a>Viz také:

- [Práce s mezipamětí u klientů automatizace uživatelského rozhraní](caching-in-ui-automation-clients.md)
- [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru](server-side-ui-automation-provider-implementation.md)
- [Přihlášení k odběru událostí automatizace uživatelského rozhraní](subscribe-to-ui-automation-events.md)
