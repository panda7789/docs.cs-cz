---
title: Vlastnosti automatizace uživatelského rozhraní pro klienty
description: Přečtěte si přehled vlastností automatizace uživatelského rozhraní, které jsou zpřístupněny klientským aplikacím automatizace uživatelského rozhraní.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, UI Automation clients
- UI Automation, client properties
ms.assetid: 255905af-0b17-485c-93d4-8a2db2a6524b
ms.openlocfilehash: fe78d7da154d79a5f66ee6c190b199065675841f
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163134"
---
# <a name="ui-automation-properties-for-clients"></a>Vlastnosti automatizace uživatelského rozhraní pro klienty
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Tento přehled popisuje [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, které jsou zpřístupněny klientským aplikacím automatizace uživatelského rozhraní.  
  
 Vlastnosti <xref:System.Windows.Automation.AutomationElement> objektů obsahují informace o [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] prvcích, obvykle ovládací prvky. Vlastnosti <xref:System.Windows.Automation.AutomationElement> jsou obecné, to znamená, že nejsou specifické pro typ ovládacího prvku. Mnohé z těchto vlastností jsou zpřístupněny ve <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation> struktuře.  
  
 Vzory ovládacích prvků mají také vlastnosti. Vlastnosti vzorů ovládacích prvků jsou specifické pro vzor. Například <xref:System.Windows.Automation.ScrollPattern> obsahuje vlastnosti, které umožňují klientské aplikaci zjistit, zda je okno svisle nebo vodorovně rolovací a zda jsou aktuální velikosti zobrazení a posunutí umístění. Vzory ovládacích prvků zpřístupňují všechny své vlastnosti prostřednictvím struktury; například <xref:System.Windows.Automation.ScrollPattern.ScrollPatternInformation> .  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]vlastnosti jsou jen pro čtení. Chcete-li nastavit vlastnosti ovládacího prvku, je nutné použít metody příslušného vzoru ovládacího prvku. Například můžete použít <xref:System.Windows.Automation.ScrollPattern.Scroll%2A> ke změně hodnot pozice posuvných oken.  
  
 Aby bylo možné zvýšit výkon, hodnoty vlastností ovládacích prvků a vzorů ovládacích prvků mohou být po načtení objektů uloženy do mezipaměti <xref:System.Windows.Automation.AutomationElement> . Další informace najdete v tématu [ukládání do mezipaměti v klientech automatizace uživatelského rozhraní](caching-in-ui-automation-clients.md).  
  
## <a name="property-ids"></a>ID vlastností  
 Identifikátory vlastností (IDs) jsou jedinečné a konstantní hodnoty, které jsou zapouzdřeny v <xref:System.Windows.Automation.AutomationProperty> objektech. Klientské aplikace automatizace uživatelského rozhraní získávají tato ID z <xref:System.Windows.Automation.AutomationElement> třídy nebo z příslušné třídy vzoru ovládacího prvku, jako je například <xref:System.Windows.Automation.ScrollPattern> . Zprostředkovatelé automatizace uživatelského rozhraní je získají z <xref:System.Windows.Automation.AutomationElementIdentifiers> jedné z tříd identifikátorů vzoru ovládacích prvků, jako je například <xref:System.Windows.Automation.ScrollPatternIdentifiers> .  
  
 Číselná <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> část <xref:System.Windows.Automation.AutomationProperty> je využívána poskytovateli k identifikaci vlastností, které jsou dotazovány v <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPropertyValue%2A?displayProperty=nameWithType> metodě. Obecně klientské aplikace nemusí kontrolovat <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> . <xref:System.Windows.Automation.AutomationIdentifier.ProgrammaticName%2A>Používá se pouze pro účely ladění a diagnostiky.  
  
## <a name="property-conditions"></a>Podmínky vlastnosti  
 ID vlastností se používají při vytváření <xref:System.Windows.Automation.PropertyCondition> objektů používaných k hledání <xref:System.Windows.Automation.AutomationElement> objektů. Například můžete chtít najít <xref:System.Windows.Automation.AutomationElement> , který má určitý název, nebo všechny ovládací prvky, které jsou povoleny. Každý <xref:System.Windows.Automation.PropertyCondition> Určuje <xref:System.Windows.Automation.AutomationProperty> identifikátor a hodnotu, kterou musí vlastnost odpovídat.  
  
 Další informace najdete v následujících referenčních tématech:  
  
- <xref:System.Windows.Automation.AutomationElement.FindFirst%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.FindAll%2A>  
  
- <xref:System.Windows.Automation.TreeWalker.Condition%2A>  
  
## <a name="retrieving-properties"></a>Načítání vlastností  
 Některé vlastnosti <xref:System.Windows.Automation.AutomationElement> a všechny vlastnosti třídy vzoru ovládacího prvku jsou zpřístupněny jako vnořené vlastnosti `Current` `Cached` objektu nebo <xref:System.Windows.Automation.AutomationElement> vzoru ovládacího prvku nebo.  
  
 Kromě toho se <xref:System.Windows.Automation.AutomationElement> dá načíst jakákoli vlastnost vzoru ovládacího prvku nebo, včetně vlastnosti, která není k dispozici ve <xref:System.Windows.Automation.AutomationElement.Cached%2A> <xref:System.Windows.Automation.AutomationElement.Current%2A> struktuře nebo, pomocí jedné z následujících metod:  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>  
  
 Tyto metody nabízejí poněkud lepší výkon a také přístup k celé škále vlastností.  
  
 Následující příklad kódu ukazuje dva způsoby načítání vlastnosti v <xref:System.Windows.Automation.AutomationElement> .  
  
 [!code-csharp[UIAClient_snip#121](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#121)]
 [!code-vb[UIAClient_snip#121](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#121)]  
  
 Chcete-li načíst vlastnosti vzorů ovládacích prvků <xref:System.Windows.Automation.AutomationElement> , které jsou podporovány nástrojem, není nutné načíst objekt vzoru ovládacího prvku. Jednoduše do metody předejte jeden z identifikátorů vlastnosti vzoru.  
  
 Následující příklad kódu ukazuje dva způsoby, jak načíst vlastnost pro vzor ovládacího prvku.  
  
 [!code-csharp[UIAClient_snip#122](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#122)]
 [!code-vb[UIAClient_snip#122](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#122)]  
  
 `Get`Metody vrací <xref:System.Object> . Aplikace musí přetypování vráceného objektu na správný typ před použitím hodnoty.  
  
## <a name="default-property-values"></a>Výchozí hodnoty vlastností  
 Pokud zprostředkovatel automatizace uživatelského rozhraní neimplementuje vlastnost, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] systém bude moci dodat výchozí hodnotu. Například pokud poskytovatel pro ovládací prvek nepodporuje vlastnost identifikovanou pomocí <xref:System.Windows.Automation.AutomationElement.HelpTextProperty> , [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vrátí prázdný řetězec. Podobně, pokud zprostředkovatel nepodporuje vlastnost identifikovanou pomocí <xref:System.Windows.Automation.AutomationElement.IsDockPatternAvailableProperty> , [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vrátí `false` .  
  
 Toto chování lze změnit pomocí <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> přetížení metody a. Když zadáte `true` jako druhý parametr, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nevrátí výchozí hodnotu, ale místo toho vrátí speciální hodnotu <xref:System.Windows.Automation.AutomationElement.NotSupported> .  
  
 Následující příklad kódu se pokusí načíst vlastnost z prvku a pokud vlastnost není podporována, je místo toho použita hodnota definovaná aplikací.  
  
 [!code-csharp[UIAClient_snip#123](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#123)]
 [!code-vb[UIAClient_snip#123](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#123)]  
  
 Chcete-li zjistit, jaké vlastnosti jsou podporovány prvkem, použijte <xref:System.Windows.Automation.AutomationElement.GetSupportedProperties%2A> . Vrátí pole <xref:System.Windows.Automation.AutomationProperty> identifikátorů.  
  
## <a name="property-changed-events"></a>Události změněné vlastností  
 Když se změní hodnota vlastnosti ve <xref:System.Windows.Automation.AutomationElement> vzoru ovládacího prvku nebo, vyvolá se událost. Aplikace se může přihlásit k odběru takových událostí voláním, zadáním <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> pole <xref:System.Windows.Automation.AutomationProperty> identifikátorů jako posledního parametru, aby bylo možné určit vlastnosti zájmu.  
  
 V rozhraní <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler> můžete identifikovat vlastnost, která se změnila kontrolou <xref:System.Windows.Automation.AutomationPropertyChangedEventArgs.Property%2A> člena argumentů události. Argumenty obsahují také starou a novou hodnotu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, která se změnila. Tyto hodnoty jsou typu <xref:System.Object> a před použitím musí být přetypování na správný typ.  
  
## <a name="additional-automationelement-properties"></a>Další vlastnosti třída AutomationElement neobsahuje  
 Kromě <xref:System.Windows.Automation.AutomationElement.Current%2A> <xref:System.Windows.Automation.AutomationElement.Cached%2A> struktur vlastností a <xref:System.Windows.Automation.AutomationElement> má následující vlastnosti, které jsou načteny prostřednictvím přístupových objektů jednoduchých vlastností.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Windows.Automation.AutomationElement.CachedChildren%2A>|Kolekce podřízených <xref:System.Windows.Automation.AutomationElement> objektů, které jsou v mezipaměti.|  
|<xref:System.Windows.Automation.AutomationElement.CachedParent%2A>|<xref:System.Windows.Automation.AutomationElement>Nadřazený objekt, který je v mezipaměti.|  
|<xref:System.Windows.Automation.AutomationElement.FocusedElement%2A>|(Statická vlastnost) <xref:System.Windows.Automation.AutomationElement>, Který má vstupní fokus.|  
|<xref:System.Windows.Automation.AutomationElement.RootElement%2A>|(Statická vlastnost) Kořenová složka <xref:System.Windows.Automation.AutomationElement> .|  
  
## <a name="see-also"></a>Viz také

- [Práce s mezipamětí u klientů automatizace uživatelského rozhraní](caching-in-ui-automation-clients.md)
- [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru](server-side-ui-automation-provider-implementation.md)
- [Přihlášení k odběru událostí automatizace uživatelského rozhraní](subscribe-to-ui-automation-events.md)
