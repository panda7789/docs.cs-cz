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
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: c1ab9a9eeae6de29fc838e263225050ec4122f2d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43505638"
---
# <a name="ui-automation-properties-for-clients"></a>Vlastnosti automatizace uživatelského rozhraní pro klienty
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Tento přehled je představen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti jako jsou vystaveny pro automatizaci uživatelského rozhraní klientské aplikace.  
  
 Vlastnosti na <xref:System.Windows.Automation.AutomationElement> objekty obsahují informace o [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] prvky, obvykle ovládacích prvků. Vlastnosti <xref:System.Windows.Automation.AutomationElement> jsou obecné; který je, není specifická pro typ ovládacího prvku. Mnohé z těchto vlastností jsou přístupné <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation> struktury.  
  
 Vzory ovládacích prvků mají také vlastnosti. Vlastnosti vzorů ovládacích prvků jsou specifické pro vzor. Například <xref:System.Windows.Automation.ScrollPattern> má vlastnosti, které umožňují klientská aplikace ke zjištění, zda je vodorovně nebo svisle posuvného okna a jaké jsou aktuální velikosti zobrazení a pozice posuvníku. Vzory ovládacích prvků zveřejnit své vlastnosti strukturou; například <xref:System.Windows.Automation.ScrollPattern.ScrollPatternInformation>.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti jsou jen pro čtení. Pokud chcete nastavit vlastnosti ovládacího prvku, musíte použít metody vzor odpovídající ovládací prvek. Například použít <xref:System.Windows.Automation.ScrollPattern.Scroll%2A> Chcete-li změnit hodnoty pozice okna posouvání.  
  
 Ke zlepšení výkonu, hodnoty vlastností ovládacích prvků a vzorů ovládacích prvků můžete uložit do mezipaměti při <xref:System.Windows.Automation.AutomationElement> objekty jsou načteny. Další informace najdete v tématu [práce s mezipamětí u klientů automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md).  
  
<a name="Property_IDs"></a>   
## <a name="property-ids"></a>Vlastnost ID  
 Vlastnost [!INCLUDE[TLA#tla_id#plural](../../../includes/tlasharptla-idsharpplural-md.md)] jsou jedinečné, konstantní hodnoty, které jsou zapouzdřeny v <xref:System.Windows.Automation.AutomationProperty> objekty. Automatizace uživatelského rozhraní klientských aplikací získat tyto [!INCLUDE[TLA2#tla_id#plural](../../../includes/tla2sharptla-idsharpplural-md.md)] z <xref:System.Windows.Automation.AutomationElement> třídy nebo z příslušné řídit vzor třídy <xref:System.Windows.Automation.ScrollPattern>. Získání zprostředkovatelů automatizace uživatelského rozhraní je z <xref:System.Windows.Automation.AutomationElementIdentifiers> nebo z jednoho ovládacího prvku vzorku identifikátory tříd <xref:System.Windows.Automation.ScrollPatternIdentifiers>.  
  
 Číselné <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> z <xref:System.Windows.Automation.AutomationProperty> poskytovatelé používá k identifikaci vlastnosti, které jsou v dotazován na <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPropertyValue%2A?displayProperty=nameWithType> metody. Obecně platí, není nutné prozkoumat klientské aplikace <xref:System.Windows.Automation.AutomationIdentifier.Id%2A>. <xref:System.Windows.Automation.AutomationIdentifier.ProgrammaticName%2A> Se používá pouze pro účely ladění a diagnostiku.  
  
<a name="Property_Conditions"></a>   
## <a name="property-conditions"></a>Vlastnosti podmínky  
 Vlastnost [!INCLUDE[TLA2#tla_id#plural](../../../includes/tla2sharptla-idsharpplural-md.md)] se používají při konstrukci <xref:System.Windows.Automation.PropertyCondition> objekty používané k vyhledání <xref:System.Windows.Automation.AutomationElement> objekty. Například možná budete chtít najít <xref:System.Windows.Automation.AutomationElement> nemá určitým názvem a všechny ovládací prvky, které jsou povoleny. Každý <xref:System.Windows.Automation.PropertyCondition> Určuje <xref:System.Windows.Automation.AutomationProperty> identifikátor a hodnotu, která musí odpovídat vlastnosti.  
  
 Další informace najdete v tématu v těchto tématech:  
  
-   <xref:System.Windows.Automation.AutomationElement.FindFirst%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.FindAll%2A>  
  
-   <xref:System.Windows.Automation.TreeWalker.Condition%2A>  
  
<a name="Retrieving_Properties"></a>   
## <a name="retrieving-properties"></a>Načítání vlastností  
 Některé vlastnosti <xref:System.Windows.Automation.AutomationElement> a všechny vlastnosti třídy vzor ovládacího prvku jsou vystaveny jako vnořené vlastnosti `Current` nebo `Cached` vlastnost <xref:System.Windows.Automation.AutomationElement> nebo vzor objekt ovládacího prvku.  
  
 Kromě toho všechny <xref:System.Windows.Automation.AutomationElement> nebo vlastnost vzor, včetně vlastnost, která není k dispozici v ovládacího prvku <xref:System.Windows.Automation.AutomationElement.Cached%2A> nebo <xref:System.Windows.Automation.AutomationElement.Current%2A> strukturu, je možné načíst pomocí jedné z následujících metod:  
  
-   <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>  
  
 Tyto metody nabízejí o trochu lepší výkon a také přístup k široké spektrum vlastnosti.  
  
 Následující příklad kódu ukazuje dva způsoby načítání vlastnosti na <xref:System.Windows.Automation.AutomationElement>.  
  
 [!code-csharp[UIAClient_snip#121](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#121)]
 [!code-vb[UIAClient_snip#121](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#121)]  
  
 Načíst vlastnosti podporovaných vzorů ovládacích prvků <xref:System.Windows.Automation.AutomationElement>, není potřeba načíst objekt ovládacího prvku modelu. Jeden z identifikátorů vlastnost model jednoduše předejte metodě.  
  
 Následující příklad kódu ukazuje dva způsoby načítání vlastnost na vzor ovládacích prvků.  
  
 [!code-csharp[UIAClient_snip#122](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#122)]
 [!code-vb[UIAClient_snip#122](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#122)]  
  
 `Get` Metody vrátit <xref:System.Object>. Aplikaci musíte přetypovat vrácený objekt na správný typ. před pomocí hodnoty.  
  
<a name="_Default_Property_Values"></a>   
## <a name="default-property-values"></a>Výchozí hodnoty vlastností  
 Pokud zprostředkovatele automatizace uživatelského rozhraní neimplementuje vlastnost, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] systém je možné zadat výchozí hodnotu. Například, pokud zprostředkovatel pro ovládací prvek nepodporuje vlastnost identifikovaný <xref:System.Windows.Automation.AutomationElement.HelpTextProperty>, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vrátí prázdný řetězec. Podobně pokud zprostředkovatel nepodporuje vlastnost identifikovaný <xref:System.Windows.Automation.AutomationElement.IsDockPatternAvailableProperty>, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vrátí `false`.  
  
 Toto chování můžete změnit pomocí <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> a <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> přetížení metody. Pokud zadáte `true` jako druhý parametr [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nevrací výchozí hodnotu, ale místo toho vrátí zvláštní hodnota <xref:System.Windows.Automation.AutomationElement.NotSupported>.  
  
 Následující příklad kódu se pokusí načíst z elementu vlastnosti, a pokud vlastnost není podporována, se místo toho používá hodnotu definovaného aplikací.  
  
 [!code-csharp[UIAClient_snip#123](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#123)]
 [!code-vb[UIAClient_snip#123](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#123)]  
  
 Chcete-li zjistit, které vlastnosti jsou podporovány elementu, použijte <xref:System.Windows.Automation.AutomationElement.GetSupportedProperties%2A>. Vrátí pole <xref:System.Windows.Automation.AutomationProperty> identifikátory.  
  
<a name="Property_changed_Events"></a>   
## <a name="property-changed-events"></a>Události změny vlastnosti  
 Pokud hodnotu vlastnosti na <xref:System.Windows.Automation.AutomationElement> nebo ovládací prvek vzor změny událost je vyvolána. Aplikace může přihlásit k odběru těchto událostí voláním <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>, poskytuje celou řadu <xref:System.Windows.Automation.AutomationProperty> identifikátory jako poslední parametr, aby bylo možné určit vlastnosti, které vás zajímají.  
  
 V <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>, můžete určit, které se změnily tak, že zkontrolujete vlastnost <xref:System.Windows.Automation.AutomationPropertyChangedEventArgs.Property%2A> členem argumenty události. Argumenty také obsahovat staré a nové hodnoty [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnost, která se změnila. Tyto hodnoty jsou typu <xref:System.Object> a musí být přetypovat na správný typ před použitím.  
  
<a name="Additional_AutomationElement_Properties"></a>   
## <a name="additional-automationelement-properties"></a>Třída AutomationElement další vlastnosti  
 Kromě <xref:System.Windows.Automation.AutomationElement.Current%2A> a <xref:System.Windows.Automation.AutomationElement.Cached%2A> vlastnost struktury <xref:System.Windows.Automation.AutomationElement> má následující vlastnosti, které jsou načteny prostřednictvím přístupových objektů pro jednoduchou vlastnost.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Windows.Automation.AutomationElement.CachedChildren%2A>|Kolekce podřízených <xref:System.Windows.Automation.AutomationElement> objekty, které jsou v mezipaměti.|  
|<xref:System.Windows.Automation.AutomationElement.CachedParent%2A>|<xref:System.Windows.Automation.AutomationElement> Nadřazený objekt, který je v mezipaměti.|  
|<xref:System.Windows.Automation.AutomationElement.FocusedElement%2A>|(Statická vlastnost) <xref:System.Windows.Automation.AutomationElement> , Který má vstupní fokus.|  
|<xref:System.Windows.Automation.AutomationElement.RootElement%2A>|(Statická vlastnost) Kořen <xref:System.Windows.Automation.AutomationElement>.|  
  
## <a name="see-also"></a>Viz také  
 [Práce s mezipamětí u klientů automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)  
 [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)  
 [Přihlášení k odběru událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md)
