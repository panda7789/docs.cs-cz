---
title: "Implementace vzoru ovládacích prvků ukotvení pro automatizaci uživatelského rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, dock
- dock control pattern
- UI Automation, dock control pattern
ms.assetid: ea3d2212-7c8e-4dd7-bf08-73141ca2d4fb
caps.latest.revision: "23"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 136d4ec56cf0c78aac03d1b3f44a18cd268d3bc9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-the-ui-automation-dock-control-pattern"></a>Implementace vzoru ovládacích prvků ukotvení pro automatizaci uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma představuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.IDockProvider>, včetně informací o vlastnostech. Na konci tohoto tématu jsou uvedeny odkazy na další odkazy.  
  
 <xref:System.Windows.Automation.DockPattern> – Vzor ovládacích prvků se používá k vystavení vlastností ukotvení ovládacího prvku do kontejneru, ukotvení. Ukotvení kontejner je ovládací prvek, který umožňuje uspořádat podřízené elementy vodorovně a svisle, relativně k sobě navzájem. Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků najdete v tématu [řízení vzor mapování pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
 ![Ukotvení kontejner s dvěma ukotveného podřízené objekty. ] (../../../docs/framework/ui-automation/media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")  
Ukotvení příklad ze sady Visual Studio, kde je okno "Zobrazení tříd" DockPosition.Right a v okně "Seznam chyb" je DockPosition.Bottom  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Postup implementace a konvence  
 Když implementace vzoru ovládacích prvků ukotvení, poznamenejte si následující pokyny a konvence:  
  
-   <xref:System.Windows.Automation.Provider.IDockProvider>nevystavuje žádné vlastnosti ukotvení kontejneru nebo vlastnosti ovládacích prvků, které jsou ukotven přiléhající k aktuální ovládací prvek v rámci kontejneru ukotvení.  
  
-   Ovládací prvky jsou ukotven relativně k sobě navzájem podle jejich aktuálního pořadí z-order; vyšší jejich pořadí z-order umístění dále jsou umístěny z zadaný okraj ukotvení kontejneru.  
  
-   Pokud se změnila velikost ukotvení kontejneru, všechny ukotvených ovládacích prvků v kontejneru přemístí vyprázdnit na stejnou hranici, do které byly původně ukotven. Ukotvených ovládacích prvků bude taky změnit velikost, aby vyplnilo veškeré místo v kontejneru podle ukotvení chování jejich <xref:System.Windows.Automation.DockPosition>. Například pokud <xref:System.Windows.Automation.DockPosition.Top> není zadaný, aby vyplnilo veškeré dostupné místo bude rozšiřovat levé a pravé straně ovládacího prvku. Pokud <xref:System.Windows.Automation.DockPosition.Fill> není zadaný, aby vyplnilo veškeré dostupné místo se rozbalí všechny čtyři strany ovládacího prvku.  
  
-   V několika monitorování systému by měl ovládacích prvků ukotvení levé nebo pravé straně aktuálního monitorování. Pokud tento způsob není možný, že by měl ukotvení na levé straně krajní levé monitorování nebo pravé straně úplně vpravo monitorování.  
  
<a name="Required_Members_for_IDockProvider"></a>   
## <a name="required-members-for-idockprovider"></a>Požadované členy pro IDockProvider  
 Následující vlastnosti a metody jsou požadovány pro implementaci rozhraní IDockProvider.  
  
|Požadované členy|Typ člena|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IDockProvider.DockPosition%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A>|Metoda|Žádné|  
  
 Tento vzor ovládacích prvků nemá žádné přidružené události.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatelé musí throw následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A><br /><br /> – Když není provést styl ukotvení požadovaný ovládací prvek.|  
  
## <a name="see-also"></a>Viz také  
 [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Použití mezipaměti při automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
