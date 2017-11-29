---
title: "Implementace vzoru ovládacích prvků ScrollItem pro automatizaci uživatelského rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Scroll Item
- UI Automation, Scroll Item control pattern
- Scroll Item control pattern
ms.assetid: 903bab5c-80c1-44d7-bdc2-0a418893b987
caps.latest.revision: "16"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 92c3b4fad775dcd04299e18da126107d8fbb4471
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-scrollitem-control-pattern"></a>Implementace vzoru ovládacích prvků ScrollItem pro automatizaci uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma představuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.IScrollItemProvider>, včetně informací o události, vlastnosti a metody. Na konci tohoto tématu jsou uvedeny odkazy na další odkazy.  
  
 <xref:System.Windows.Automation.ScrollItemPattern> – Vzor ovládacích prvků se používá pro podporu jednotlivých podřízených ovládacích prvků kontejnerů, které implementují <xref:System.Windows.Automation.Provider.IScrollProvider>. Tento vzor ovládacích prvků funguje jako komunikační kanál mezi podřízený ovládací prvek a jeho kontejner, aby bylo zajištěno, že kontejneru můžete měnit aktuálně viditelný obsah (nebo oblast) v rámci jeho zobrazení zobrazíte podřízený ovládací prvek. Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků najdete v tématu [řízení vzor mapování pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Postup implementace a konvence  
 Při implementaci položky posuv – vzor ovládacích prvků, poznamenejte si následující pokyny a konvence:  
  
-   Implementace rozhraní IScrollItemProvider nejsou povinné položky v ovládacím prvku okno nebo plátno. Jako alternativu, ale, že musí vystavit platné umístění pro <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>. To vám umožní automatizace uživatelského rozhraní klientské aplikace používat <xref:System.Windows.Automation.ScrollPattern> řídit vzor metody na kontejneru zobrazíte podřízenou položku.  
  
<a name="Required_Members_for_IScrollItemProvider"></a>   
## <a name="required-members-for-iscrollitemprovider"></a>Požadované členy pro IScrollItemProvider  
 Je vyžadována pro implementaci rozhraní IScrollProvider následující metoda.  
  
|Požadované členy|Typ člena|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider.ScrollIntoView%2A>|– Metoda|Žádné|  
  
 Tento vzor ovládacích prvků nemá žádné přidružené vlastnosti nebo události.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatelé musí throw následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Pokud položku nelze přesunut do zobrazení oblasti:<br /><br /> -   <xref:System.Windows.Automation.ScrollItemPattern.ScrollIntoView%2A>|  
  
## <a name="see-also"></a>Viz také  
 [Přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Vzory ovládacího prvku automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Použití mezipaměti při automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
