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
ms.openlocfilehash: 6f02a4825206da0dd4949083cc54f555a8ae40b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914446"
---
# <a name="ui-automation-properties-for-clients"></a>Vlastnosti automatizace uživatelského rozhraní pro klienty
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 Tento přehled popisuje [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, které jsou zpřístupněny klientským aplikacím automatizace uživatelského rozhraní.  
  
 Vlastnosti objektů obsahují informace o [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] prvcích, obvykle ovládací prvky. <xref:System.Windows.Automation.AutomationElement> Vlastnosti <xref:System.Windows.Automation.AutomationElement> jsou obecné, to znamená, že nejsou specifické pro typ ovládacího prvku. Mnohé z těchto vlastností jsou zpřístupněny ve <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation> struktuře.  
  
 Vzory ovládacích prvků mají také vlastnosti. Vlastnosti vzorů ovládacích prvků jsou specifické pro vzor. Například <xref:System.Windows.Automation.ScrollPattern> obsahuje vlastnosti, které umožňují klientské aplikaci zjistit, zda je okno svisle nebo vodorovně rolovací a zda jsou aktuální velikosti zobrazení a posunutí umístění. Vzory ovládacích prvků zpřístupňují všechny své vlastnosti prostřednictvím struktury; například <xref:System.Windows.Automation.ScrollPattern.ScrollPatternInformation>.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]vlastnosti jsou jen pro čtení. Chcete-li nastavit vlastnosti ovládacího prvku, je nutné použít metody příslušného vzoru ovládacího prvku. Například můžete použít <xref:System.Windows.Automation.ScrollPattern.Scroll%2A> ke změně hodnot pozice posuvných oken.  
  
 Aby bylo možné zvýšit výkon, hodnoty vlastností ovládacích prvků a vzorů ovládacích prvků <xref:System.Windows.Automation.AutomationElement> mohou být po načtení objektů uloženy do mezipaměti. Další informace najdete v tématu [ukládání do mezipaměti v klientech automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md).  
  
## <a name="property-ids"></a>ID vlastností  
 Identifikátory vlastností (IDS) jsou jedinečné a konstantní hodnoty, které jsou zapouzdřeny <xref:System.Windows.Automation.AutomationProperty> v objektech. Klientské aplikace automatizace uživatelského rozhraní získávají tato ID z <xref:System.Windows.Automation.AutomationElement> třídy nebo z příslušné třídy vzoru ovládacího prvku, <xref:System.Windows.Automation.ScrollPattern>jako je například. Zprostředkovatelé automatizace uživatelského rozhraní je <xref:System.Windows.Automation.AutomationElementIdentifiers> získají z jedné z tříd identifikátorů vzoru ovládacích prvků, <xref:System.Windows.Automation.ScrollPatternIdentifiers>jako je například.  
  
 Číselná <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPropertyValue%2A?displayProperty=nameWithType> část je využívána poskytovateli k identifikaci vlastností, které jsou dotazovány v metodě. <xref:System.Windows.Automation.AutomationProperty> Obecně klientské aplikace nemusí kontrolovat <xref:System.Windows.Automation.AutomationIdentifier.Id%2A>. Používá <xref:System.Windows.Automation.AutomationIdentifier.ProgrammaticName%2A> se pouze pro účely ladění a diagnostiky.  
  
## <a name="property-conditions"></a>Podmínky vlastnosti  
 ID vlastností se používají při vytváření <xref:System.Windows.Automation.PropertyCondition> objektů používaných k hledání <xref:System.Windows.Automation.AutomationElement> objektů. Například můžete chtít najít <xref:System.Windows.Automation.AutomationElement> , který má určitý název, nebo všechny ovládací prvky, které jsou povoleny. <xref:System.Windows.Automation.PropertyCondition> Každý<xref:System.Windows.Automation.AutomationProperty> Určuje identifikátor a hodnotu, kterou musí vlastnost odpovídat.  
  
 Další informace najdete v následujících referenčních tématech:  
  
- <xref:System.Windows.Automation.AutomationElement.FindFirst%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.FindAll%2A>  
  
- <xref:System.Windows.Automation.TreeWalker.Condition%2A>  
  
## <a name="retrieving-properties"></a>Načítání vlastností  
 Některé vlastnosti <xref:System.Windows.Automation.AutomationElement> a všechny vlastnosti třídy vzoru ovládacího prvku jsou zpřístupněny jako vnořené vlastnosti `Current` objektu nebo `Cached` <xref:System.Windows.Automation.AutomationElement> vzoru ovládacího prvku nebo.  
  
 Kromě toho se dá <xref:System.Windows.Automation.AutomationElement> načíst jakákoli vlastnost vzoru ovládacího prvku nebo, včetně vlastnosti, která není k <xref:System.Windows.Automation.AutomationElement.Cached%2A> dispozici ve struktuře nebo <xref:System.Windows.Automation.AutomationElement.Current%2A> , pomocí jedné z následujících metod:  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>  
  
 Tyto metody nabízejí poněkud lepší výkon a také přístup k celé škále vlastností.  
  
 Následující příklad kódu ukazuje dva způsoby načítání vlastnosti v <xref:System.Windows.Automation.AutomationElement>.  
  
 [!code-csharp[UIAClient_snip#121](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#121)]
 [!code-vb[UIAClient_snip#121](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#121)]  
  
 Chcete-li načíst vlastnosti vzorů ovládacích prvků <xref:System.Windows.Automation.AutomationElement>, které jsou podporovány nástrojem, není nutné načíst objekt vzoru ovládacího prvku. Jednoduše do metody předejte jeden z identifikátorů vlastnosti vzoru.  
  
 Následující příklad kódu ukazuje dva způsoby, jak načíst vlastnost pro vzor ovládacího prvku.  
  
 [!code-csharp[UIAClient_snip#122](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#122)]
 [!code-vb[UIAClient_snip#122](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#122)]  
  
 `Get` Metody<xref:System.Object>vrací. Aplikace musí přetypování vráceného objektu na správný typ před použitím hodnoty.  
  
## <a name="default-property-values"></a>Výchozí hodnoty vlastností  
 Pokud zprostředkovatel automatizace uživatelského rozhraní neimplementuje vlastnost, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] systém bude moci dodat výchozí hodnotu. Například pokud poskytovatel pro ovládací prvek nepodporuje vlastnost identifikovanou pomocí <xref:System.Windows.Automation.AutomationElement.HelpTextProperty>, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vrátí prázdný řetězec. Podobně, pokud zprostředkovatel nepodporuje vlastnost identifikovanou pomocí <xref:System.Windows.Automation.AutomationElement.IsDockPatternAvailableProperty>, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vrátí `false`.  
  
 Toto chování lze změnit pomocí <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> přetížení metody a. <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> Když zadáte `true` jako druhý parametr, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nevrátí výchozí hodnotu, ale místo toho vrátí speciální hodnotu <xref:System.Windows.Automation.AutomationElement.NotSupported>.  
  
 Následující příklad kódu se pokusí načíst vlastnost z prvku a pokud vlastnost není podporována, je místo toho použita hodnota definovaná aplikací.  
  
 [!code-csharp[UIAClient_snip#123](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#123)]
 [!code-vb[UIAClient_snip#123](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#123)]  
  
 Chcete-li zjistit, jaké vlastnosti jsou podporovány prvkem, <xref:System.Windows.Automation.AutomationElement.GetSupportedProperties%2A>použijte. Vrátí pole <xref:System.Windows.Automation.AutomationProperty> identifikátorů.  
  
## <a name="property-changed-events"></a>Události změněné vlastností  
 Když se změní hodnota vlastnosti ve <xref:System.Windows.Automation.AutomationElement> vzoru ovládacího prvku nebo, vyvolá se událost. Aplikace se může přihlásit k odběru takových událostí voláním <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>, zadáním <xref:System.Windows.Automation.AutomationProperty> pole identifikátorů jako posledního parametru, aby bylo možné určit vlastnosti zájmu.  
  
 V rozhraní <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>můžete identifikovat vlastnost, která se změnila <xref:System.Windows.Automation.AutomationPropertyChangedEventArgs.Property%2A> kontrolou člena argumentů události. Argumenty obsahují také starou a novou hodnotu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, která se změnila. Tyto hodnoty jsou typu <xref:System.Object> a před použitím musí být přetypování na správný typ.  
  
## <a name="additional-automationelement-properties"></a>Další vlastnosti třída AutomationElement neobsahuje  
 Kromě <xref:System.Windows.Automation.AutomationElement.Current%2A> <xref:System.Windows.Automation.AutomationElement.Cached%2A> struktur<xref:System.Windows.Automation.AutomationElement> vlastností a má následující vlastnosti, které jsou načteny prostřednictvím přístupových objektů jednoduchých vlastností.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Windows.Automation.AutomationElement.CachedChildren%2A>|Kolekce podřízených <xref:System.Windows.Automation.AutomationElement> objektů, které jsou v mezipaměti.|  
|<xref:System.Windows.Automation.AutomationElement.CachedParent%2A>|<xref:System.Windows.Automation.AutomationElement> Nadřazený objekt, který je v mezipaměti.|  
|<xref:System.Windows.Automation.AutomationElement.FocusedElement%2A>|(Statická vlastnost) <xref:System.Windows.Automation.AutomationElement> , Který má vstupní fokus.|  
|<xref:System.Windows.Automation.AutomationElement.RootElement%2A>|(Statická vlastnost) Kořenová <xref:System.Windows.Automation.AutomationElement>složka.|  
  
## <a name="see-also"></a>Viz také:

- [Práce s mezipamětí u klientů automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
- [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
- [Přihlášení k odběru událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md)
