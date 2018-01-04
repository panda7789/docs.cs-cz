---
title: "Vlastnosti automatizace uživatelského rozhraní pro klienty"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, UI Automation clients
- UI Automation, client properties
ms.assetid: 255905af-0b17-485c-93d4-8a2db2a6524b
caps.latest.revision: "17"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: fdd748da4bb414726e2eae88dcab59cf60259a13
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ui-automation-properties-for-clients"></a>Vlastnosti automatizace uživatelského rozhraní pro klienty
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Tento přehled zavádí vám [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti jako jsou viditelné na automatizace uživatelského rozhraní klientské aplikace.  
  
 Vlastnosti <xref:System.Windows.Automation.AutomationElement> objekty obsahují informace o [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementy, obvykle ovládací prvky. Vlastnosti <xref:System.Windows.Automation.AutomationElement> jsou obecné; je, není specifické pro typ ovládacího prvku. Mnoho z těchto vlastností jsou přístupné <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation> struktura.  
  
 Vzory ovládacích prvků také mít vlastnosti. Vzory ovládacích prvků vlastnosti jsou specifické pro vzoru. Například <xref:System.Windows.Automation.ScrollPattern> má vlastnosti, které umožňují klientskou aplikaci chcete zjistit, jestli je okno vodorovně nebo svisle posouvatelným a jaké jsou aktuální velikosti zobrazení a posuňte pozic. Vzory ovládacích prvků vystavit jejich vlastnosti prostřednictvím strukturou; například <xref:System.Windows.Automation.ScrollPattern.ScrollPatternInformation>.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]vlastnosti jsou jen pro čtení. Nastavení vlastností ovládacího prvku, musíte použít metodu vzoru vhodný ovládací prvek. Například použít <xref:System.Windows.Automation.ScrollPattern.Scroll%2A> ke změně hodnot pozice posouvání okna.  
  
 Pro zlepšení výkonu, hodnoty vlastností ovládacích prvků a vzory ovládacích prvků můžete uložit do mezipaměti, když <xref:System.Windows.Automation.AutomationElement> objekty jsou načteny. Další informace najdete v tématu [ukládání do mezipaměti v klientech automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md).  
  
<a name="Property_IDs"></a>   
## <a name="property-ids"></a>Vlastnost ID  
 Vlastnost [!INCLUDE[TLA#tla_id#plural](../../../includes/tlasharptla-idsharpplural-md.md)] jsou jedinečná a konstantní hodnoty, které jsou zapouzdřené v <xref:System.Windows.Automation.AutomationProperty> objekty. Automatizace uživatelského rozhraní klientské aplikace získat tyto [!INCLUDE[TLA2#tla_id#plural](../../../includes/tla2sharptla-idsharpplural-md.md)] z <xref:System.Windows.Automation.AutomationElement> třídy nebo z příslušné řízení vzor třída <xref:System.Windows.Automation.ScrollPattern>. Zprostředkovatelé automatizace uživatelského rozhraní pro něho z <xref:System.Windows.Automation.AutomationElementIdentifiers> nebo z jednoho z ovládacího prvku vzor identifikátory třídy <xref:System.Windows.Automation.ScrollPatternIdentifiers>.  
  
 Číselný <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> z <xref:System.Windows.Automation.AutomationProperty> zprostředkovatelé používá k určení vlastností, které jsou v dotazován na <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPropertyValue%2A?displayProperty=nameWithType> metoda. Obecně platí, klient aplikace není nutné prozkoumat <xref:System.Windows.Automation.AutomationIdentifier.Id%2A>. <xref:System.Windows.Automation.AutomationIdentifier.ProgrammaticName%2A> Se používá pouze pro účely ladění a diagnostiky.  
  
<a name="Property_Conditions"></a>   
## <a name="property-conditions"></a>Podmínek vlastností  
 Vlastnost [!INCLUDE[TLA2#tla_id#plural](../../../includes/tla2sharptla-idsharpplural-md.md)] se používají při vytváření <xref:System.Windows.Automation.PropertyCondition> objekty použít k vyhledání <xref:System.Windows.Automation.AutomationElement> objekty. Například můžete chtít najít <xref:System.Windows.Automation.AutomationElement> bude název některé nebo všechny ovládací prvky, které jsou povoleny. Každý <xref:System.Windows.Automation.PropertyCondition> Určuje <xref:System.Windows.Automation.AutomationProperty> identifikátor a hodnotu, kterou musí odpovídat vlastnosti.  
  
 Další informace najdete v těchto tématech:  
  
-   <xref:System.Windows.Automation.AutomationElement.FindFirst%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.FindAll%2A>  
  
-   <xref:System.Windows.Automation.TreeWalker.Condition%2A>  
  
<a name="Retrieving_Properties"></a>   
## <a name="retrieving-properties"></a>Načítání vlastností  
 Některé vlastnosti <xref:System.Windows.Automation.AutomationElement> a všechny vlastnosti třídy vzor řízení jsou zveřejněné jako vnořené vlastnosti `Current` nebo `Cached` vlastnost <xref:System.Windows.Automation.AutomationElement> nebo vzor objekt ovládacího prvku.  
  
 Kromě toho žádné <xref:System.Windows.Automation.AutomationElement> nebo vlastnost vzor, včetně vlastnost, která není k dispozici v ovládacího prvku <xref:System.Windows.Automation.AutomationElement.Cached%2A> nebo <xref:System.Windows.Automation.AutomationElement.Current%2A> struktury, můžete načíst pomocí jedné z následujících metod:  
  
-   <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>  
  
 Tyto metody nabízejí mírně lepší výkon a také přístup k plný rozsah vlastností.  
  
 Následující příklad kódu ukazuje dva způsoby načítání vlastnost na <xref:System.Windows.Automation.AutomationElement>.  
  
 [!code-csharp[UIAClient_snip#121](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#121)]
 [!code-vb[UIAClient_snip#121](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#121)]  
  
 Načítání vlastností podporovaných vzorů ovládacích prvků <xref:System.Windows.Automation.AutomationElement>, není potřeba načíst objekt vzor ovládacího prvku. Jednoduše jednu vlastnost identifikátorů vzor předejte do metody.  
  
 Následující příklad kódu ukazuje dva způsoby načítání vlastnost vzor ovládacích prvků.  
  
 [!code-csharp[UIAClient_snip#122](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#122)]
 [!code-vb[UIAClient_snip#122](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#122)]  
  
 `Get` Metody vrací <xref:System.Object>. Aplikace musí před použitím hodnotu přetypovat vrácený objekt, který má správný typ.  
  
<a name="_Default_Property_Values"></a>   
## <a name="default-property-values"></a>Výchozí hodnoty vlastností  
 Pokud zprostředkovatele automatizace uživatelského rozhraní neimplementuje vlastnost, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] systém je možné zadat výchozí hodnotu. Například, pokud zprostředkovatel pro ovládací prvek nepodporuje vlastnost identifikovaný <xref:System.Windows.Automation.AutomationElement.HelpTextProperty>, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vrátí prázdný řetězec. Podobně pokud zprostředkovatel nepodporuje vlastnost identifikovaný <xref:System.Windows.Automation.AutomationElement.IsDockPatternAvailableProperty>, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vrátí `false`.  
  
 Toto chování můžete změnit pomocí <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> a <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> přetížení metody. Pokud zadáte `true` jako druhý parametr [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nevrací výchozí hodnotu, ale místo toho vrátí speciální hodnotu <xref:System.Windows.Automation.AutomationElement.NotSupported>.  
  
 Následující příklad kódu se pokusí načíst vlastnost z elementu, a pokud vlastnost není podporován, je místo toho použít hodnotu definované aplikací.  
  
 [!code-csharp[UIAClient_snip#123](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#123)]
 [!code-vb[UIAClient_snip#123](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#123)]  
  
 Chcete-li zjistit, jaké vlastnosti jsou podporovány elementem, použijte <xref:System.Windows.Automation.AutomationElement.GetSupportedProperties%2A>. Vrátí pole <xref:System.Windows.Automation.AutomationProperty> identifikátory.  
  
<a name="Property_changed_Events"></a>   
## <a name="property-changed-events"></a>Události změny vlastnosti  
 Pokud hodnotu vlastnosti na <xref:System.Windows.Automation.AutomationElement> nebo ovládací prvek vzor změny, událost se vyvolá. Aplikace se mohou přihlásit k takové události voláním <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>, poskytuje řadu <xref:System.Windows.Automation.AutomationProperty> identifikátory jako poslední parametr a zadejte vlastnosti, které vás zajímají.  
  
 V <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>, můžete identifikovat vlastnost, která se změnila kontrolou <xref:System.Windows.Automation.AutomationPropertyChangedEventArgs.Property%2A> členem argumenty událostí. Argumenty také obsahovat staré a nové hodnoty [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnost, která se změnila. Tyto hodnoty jsou typu <xref:System.Object> a musí být přetypovat na typ správné před používá.  
  
<a name="Additional_AutomationElement_Properties"></a>   
## <a name="additional-automationelement-properties"></a>Další AutomationElement vlastnosti  
 Kromě <xref:System.Windows.Automation.AutomationElement.Current%2A> a <xref:System.Windows.Automation.AutomationElement.Cached%2A> struktury vlastnost <xref:System.Windows.Automation.AutomationElement> má následující vlastnosti, které jsou načteny prostřednictvím jednoduché vlastnosti přistupující objekty.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Windows.Automation.AutomationElement.CachedChildren%2A>|Kolekce podřízených <xref:System.Windows.Automation.AutomationElement> objekty, které jsou v mezipaměti.|  
|<xref:System.Windows.Automation.AutomationElement.CachedParent%2A>|<xref:System.Windows.Automation.AutomationElement> Nadřazeného objektu, který je v mezipaměti.|  
|<xref:System.Windows.Automation.AutomationElement.FocusedElement%2A>|(Statické vlastnosti) <xref:System.Windows.Automation.AutomationElement> s zaměření pro vstup.|  
|<xref:System.Windows.Automation.AutomationElement.RootElement%2A>|(Statické vlastnosti) Kořenové <xref:System.Windows.Automation.AutomationElement>.|  
  
## <a name="see-also"></a>Viz také  
 [Práce s mezipamětí u klientů automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)  
 [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)  
 [Přihlášení k odběru událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md)
