---
title: "Používání vlastnosti AutomationID"
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
- AutomationId property
- UI Automation, AutomationId property
- properties, AutomationId
ms.assetid: a24e807b-d7c3-4e93-ac48-80094c4e1c90
caps.latest.revision: "21"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: fdd26f335fb2f9b8072103def5b00d91a6740817
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="use-the-automationid-property"></a>Používání vlastnosti AutomationID
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma popisuje scénáře a ukázkový kód, který zobrazí jak a kdy <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> slouží k vyhledání prvek v rámci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.  
  
 <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>jednoznačně identifikuje prvku automatizace uživatelského rozhraní z uzlů na stejné úrovni. Další informace o identifikátory vlastnosti související s řízení identifikace, najdete v části [přehled vlastností automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
> [!NOTE]
>  <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>není zárukou jedinečnou identitu v rámci stromu; obvykle musí kontejneru a oboru informace jsou užitečné. Aplikace může například obsahovat ovládacího prvku nabídka s více položek nabídek nejvyšší úrovně, které obsahovat více podřízených položek nabídky. Tyto položky sekundárním nabídce může být označeno obecné schématu, například "Item1", "Položky 2" a tak dále, což duplicitní identifikátory pro podřízené mezi nabídek na nejvyšší úrovni.  
  
## <a name="scenarios"></a>Scénáře  
 Byly zjištěny tři primární scénáře aplikací klientů automatizace uživatelského rozhraní, které vyžadují použití <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> k dosažení přesnou a konzistentní výsledky při hledání elementů.  
  
> [!NOTE]
>  <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>podporuje všechny elementy automatizace uživatelského rozhraní v zobrazení ovládacího prvku s výjimkou nejvyšší úrovně aplikace windows, elementů automatizace uživatelského rozhraní, které jsou odvozené z [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] ovládacích prvků, které nemají ID nebo x: Uid a elementy automatizace uživatelského rozhraní, které jsou odvozené z [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] , ovládací prvky nemají ID ovládacího prvku.  
  
#### <a name="use-a-unique-and-discoverable-automationid-to-locate-a-specific-element-in-the-ui-automation-tree"></a>Použijte jedinečný a že je zjistitelný AutomationID a vyhledejte konkrétní element ve stromu automatizace uživatelského rozhraní  
  
-   Pomocí některého nástroje, jako například [!INCLUDE[TLA#tla_uispy](../../../includes/tlasharptla-uispy-md.md)] do sestavy <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> z [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementu, které vás zajímají. Tato hodnota může pak zkopírovat a vložit do klientské aplikace jako je například zkušební skript pro následné automatizované testování. Tento přístup snižuje a zjednodušuje kód potřebné k identifikaci a najděte element za běhu.  
  
> [!CAUTION]
>  Obecně platí, že byste měli zkusit získat jen přímé podřízené objekty daného <xref:System.Windows.Automation.AutomationElement.RootElement%2A>. Vyhledejte následníky může iterovat stovky nebo dokonce tisíce elementy, což může způsobit k přetečení zásobníku. Pokud se pokoušíte získat konkrétní element na nižší úrovni, měli byste začít vyhledávání z okna aplikace nebo z kontejneru na nižší úrovni.  
  
 [!code-csharp[UIAAutomationID_snip#100](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#100)]
 [!code-vb[UIAAutomationID_snip#100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#100)]  
  
#### <a name="use-a-persistent-path-to-return-to-a-previously-identified-automationelement"></a>Použijte trvalé cestu se vraťte do dříve zjištěné AutomationElement  
  
-   Klientské aplikace, z jednoduchá testovací skriptů a robustní záznam a přehrávání nástrojů může vyžadovat přístup k elementům, které nejsou instanci aktuálně, například soubor otevřete dialogové okno nebo položku nabídky a proto nejsou k dispozici ve stromu automatizace uživatelského rozhraní. Tyto prvky se dá jenom vytvořit instance reprodukci, nebo "přehrávání", konkrétní posloupnost [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] akce prostřednictvím [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, například AutomationID vzory ovládacích prvků a naslouchacích procesů událostí. V tématu [testování ukázka skriptu generátor](http://msdn.microsoft.com/library/028467fd-2980-4691-9522-0131dcef23a0) pro příklad, který používá [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] ke generování skriptů testovací podle interakce uživatele s [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)].  
  
 [!code-csharp[UIAAutomationID_snip#UIAWorkerThread](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#uiaworkerthread)]
 [!code-vb[UIAAutomationID_snip#UIAWorkerThread](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#uiaworkerthread)]  
[!code-csharp[UIAAutomationID_snip#Playback](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#playback)]
[!code-vb[UIAAutomationID_snip#Playback](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#playback)]  
  
#### <a name="use-a-relative-path-to-return-to-a-previously-identified-automationelement"></a>Použít relativní cestu se vraťte do dříve zjištěné AutomationElement  
  
-   V některých případech vzhledem k tomu, že AutomationID je pouze musí být jedinečný mezi na stejné úrovni, může více elementy ve stromu automatizace uživatelského rozhraní mají stejné hodnoty vlastnosti AutomationID. V těchto situacích elementy lze jedinečně identifikovat podle nadřazený a v případě potřeby nadřazený. Například vývojář může poskytnout řádku nabídek několik položek nabídky každý s více podřízených položek nabídky kde podřízené objekty jsou označeny sekvenční AutomationID je například "Item1", "Item2" a tak dále. Každé položky nabídky může pak jednoznačně identifikovat jeho AutomationID společně s AutomationID nadřazené a v případě potřeby jeho nadřazený.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>  
 [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Hledání prvku automatizace uživatelského rozhraní na základě podmínky pro vlastnost](../../../docs/framework/ui-automation/find-a-ui-automation-element-based-on-a-property-condition.md)
