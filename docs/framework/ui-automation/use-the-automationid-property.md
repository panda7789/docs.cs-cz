---
title: Používání vlastnosti AutomationID
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AutomationId property
- UI Automation, AutomationId property
- properties, AutomationId
ms.assetid: a24e807b-d7c3-4e93-ac48-80094c4e1c90
ms.openlocfilehash: 1f487e9d686ab82adb40cdc31aad68390fbdff3f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775747"
---
# <a name="use-the-automationid-property"></a>Používání vlastnosti AutomationID
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma obsahuje scénáře a ukázky kódu, které ukazují, jak a kdy <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> je možné najít element v rámci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.  
  
 <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> jednoznačně identifikuje prvku automatizace uživatelského rozhraní z na stejné úrovni. Další informace o identifikátory vlastnosti související s řídit identifikace, naleznete v tématu [přehled vlastností automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
> [!NOTE]
>  <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> nezaručuje jedinečnou identitu v rámci stromu; obvykle potřebuje informace o oboru užitečnost a kontejner. Aplikace může například obsahovat ovládací prvek nabídky s více položek nabídek nejvyšší úrovně, které pak obsahovat více podřízených položek nabídky. Tyto položky nabídky sekundární může identifikovat obecný schématu, jako je například "Item1", "Položka 2" a tak dále, povolení duplicitní identifikátory pro děti napříč položky nabídek nejvyšší úrovně.  
  
## <a name="scenarios"></a>Scénáře  
 Byly zjištěny tři základní scénáře aplikace klienta automatizace uživatelského rozhraní, které vyžadují použití <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> získat přesné a konzistentní výsledky při hledání elementů.  
  
> [!NOTE]
>  <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> podporuje všechny elementy automatizace uživatelského rozhraní v zobrazení ovládacího prvku s výjimkou nejvyšší úrovně aplikace pro windows, odvozený z pohyb mezi elementy automatizace uživatelského rozhraní [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] ovládací prvky, které nemají ID nebo x: Uid a pohyb mezi elementy automatizace uživatelského rozhraní odvozené od [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] ovládací prvky, které není nutné ID ovládacího prvku.  
  
#### <a name="use-a-unique-and-discoverable-automationid-to-locate-a-specific-element-in-the-ui-automation-tree"></a>Použijte jedinečný a dostupnější AutomationID a vyhledejte konkrétní elementu ve stromu automatizace uživatelského rozhraní  
  
- Použijte nástroj, jako [!INCLUDE[TLA#tla_uispy](../../../includes/tlasharptla-uispy-md.md)] do sestavy <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> z [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementu, které vás zajímají. Tuto hodnotu lze pak kopírovat a vložit do klientské aplikace, jako je například testovací skript pro další automatizované testování. Tento přístup snižuje a zjednodušuje kód, který k identifikaci a vyhledání prvek v době běhu.  
  
> [!CAUTION]
>  Obecně platí, pokuste se získat jen přímé podřízené objekty daného <xref:System.Windows.Automation.AutomationElement.RootElement%2A>. Vyhledání potomků může iterovat stovky nebo i tisíce elementů, což může vést k přetečení zásobníku. Pokud se pokoušíte získat konkrétní elementu na nižší úrovni, měli byste začít hledání v okně aplikace nebo z kontejneru na nižší úrovni.  
  
 [!code-csharp[UIAAutomationID_snip#100](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#100)]
 [!code-vb[UIAAutomationID_snip#100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#100)]  
  
#### <a name="use-a-persistent-path-to-return-to-a-previously-identified-automationelement"></a>Vraťte se do dříve zjištěné třída AutomationElement pomocí trvalé cesty  
  
- Klientské aplikace, z skriptů jednoduchý test a robustní záznam a přehrávání nástroje může vyžadovat přístup k prvkům, které nejsou vytvořeny aktuálně, například soubor otevřete dialogové okno nebo položku nabídky a proto neexistuje ve stromu automatizace uživatelského rozhraní. Tyto prvky můžete vytvořit instanci pouze reprodukce, nebo "přehrávání", konkrétní posloupnost akcí uživatelského rozhraní pomocí vlastnosti automatizace uživatelského rozhraní, jako je AutomationID vzorů ovládacích prvků a naslouchacích procesů událostí.
  
 [!code-csharp[UIAAutomationID_snip#UIAWorkerThread](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#uiaworkerthread)]
 [!code-vb[UIAAutomationID_snip#UIAWorkerThread](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#uiaworkerthread)]  
[!code-csharp[UIAAutomationID_snip#Playback](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#playback)]
[!code-vb[UIAAutomationID_snip#Playback](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#playback)]  
  
#### <a name="use-a-relative-path-to-return-to-a-previously-identified-automationelement"></a>Použít relativní cestu k vrácení dříve zjištěné třída AutomationElement  
  
- V některých případech se vzhledem AutomationID je pouze musí být jedinečný mezi na stejné úrovni, může více prvků ve stromu automatizace uživatelského rozhraní mají stejné hodnoty vlastnosti AutomationID. V těchto situacích prvky lze jedinečně identifikovat podle nadřazenou položku a v případě potřeby, výše nadřazených. Například vývojář může poskytnout panel nabídek několik položek nabídky každý s více podřízených položek nabídky, ve kterém jsou podřízené objekty označeny sekvenční AutomationID například "Item1", "Item2 –" a tak dále. Každá položka nabídky může pak být jednoznačně identifikují pomocí jeho AutomationID spolu s AutomationID svého nadřazeného objektu a v případě potřeby jeho výše nadřazených.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>
- [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Hledání prvku automatizace uživatelského rozhraní na základě podmínky pro vlastnost](../../../docs/framework/ui-automation/find-a-ui-automation-element-based-on-a-property-condition.md)
