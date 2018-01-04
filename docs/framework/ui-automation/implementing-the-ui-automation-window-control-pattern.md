---
title: "Implementace vzoru ovládacích prvků okno pro automatizaci uživatelského rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
caps.latest.revision: "21"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 3f1b44184f1a241943d9fa9d60a62a703dbaf0d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a>Implementace vzoru ovládacích prvků okno pro automatizaci uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma představuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.IWindowProvider>, včetně informací o <xref:System.Windows.Automation.WindowPattern> vlastnosti, metod a události. Na konci tohoto tématu jsou uvedeny odkazy na další odkazy.  
  
 <xref:System.Windows.Automation.WindowPattern> – Vzor ovládacích prvků se používá pro podporu ovládacích prvků, které poskytují základní funkce se systémem Windows v rámci tradiční [!INCLUDE[TLA#tla_gui](../../../includes/tlasharptla-gui-md.md)]. Příklady ovládacích prvků, které musí implementovat toto – vzor ovládacích prvků windows nejvyšší úrovně aplikace [!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)] podřízená okna, ovládací prvky umožňující změnu velikosti rozdělení podokně, modálních dialogových oken a bublinách pomohou systému windows.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Postup implementace a konvence  
 Když implementace vzoru ovládacích prvků okno, poznamenejte si následující pokyny a konvence:  
  
-   Pro podporu možnost Upravit velikost obě okna a obrazovky pozice pomocí automatizace uživatelského rozhraní, musí implementovat ovládacího prvku <xref:System.Windows.Automation.Provider.ITransformProvider> kromě <xref:System.Windows.Automation.Provider.IWindowProvider>.  
  
-   Ovládací prvky, které obsahují záhlaví a název panelu elementy, které povolte ovládacího prvku se přesune, po změně velikosti, Maximalizovaný, rychle minimalizovat nebo uzavřen se obvykle vyžadují k implementaci <xref:System.Windows.Automation.Provider.IWindowProvider>.  
  
-   Ovládací prvky, jako je například automaticky otevíraná okna popisek a pole se seznamem pole nebo nabídky rozevírací seznamy neimplementují obvykle <xref:System.Windows.Automation.Provider.IWindowProvider>.  
  
-   Bublině nápovědy systému windows jsou rozlišené ze základní popis automaticky otevíraná okna pomocí poskytování tlačítko Zavřít okno podobné.  
  
-   Režim celé obrazovky není podporována IWindowProvider je specifické pro funkce k aplikaci a není chování typické okno.  
  
<a name="Required_Members_for_IWindowProvider"></a>   
## <a name="required-members-for-iwindowprovider"></a>Požadované členy pro IWindowProvider  
 Následující vlastnosti, metod a události jsou požadovány pro rozhraní IWindowProvider.  
  
|Povinný člen|Typ člena|Poznámky|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|Událost|Žádné|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|Událost|Žádné|  
|<xref:System.Windows.Automation.WindowInteractionState>|Událost|Není zaručena bezpečnost pro přístup<xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction>|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatelé musí throw následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> – Když ovládacího prvku nepodporuje požadované chování.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> – Když parametru není platné číslo.|  
  
## <a name="see-also"></a>Viz také  
 [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Použití mezipaměti při automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
