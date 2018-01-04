---
title: "Implementace vzoru ovládacích prvků transformace pro automatizaci uživatelského rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Transform
- Transform control pattern
- UI Automation, Transform control pattern
ms.assetid: 5f49d843-5845-4800-9d9c-56ce0d146844
caps.latest.revision: "14"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 629428f2f5e30d0b7dee07f270fcf5bacaeb5f30
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-the-ui-automation-transform-control-pattern"></a>Implementace vzoru ovládacích prvků transformace pro automatizaci uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma představuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.ITransformProvider>, včetně informací o události, vlastnosti a metody. Na konci tohoto tématu jsou uvedeny odkazy na další odkazy.  
  
 <xref:System.Windows.Automation.TransformPattern> – Vzor ovládacích prvků se používá pro podporu ovládacích prvků, které můžete přesunout, po změně velikosti nebo otáčet v dvojrozměrném prostoru. Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků najdete v tématu [řízení vzor mapování pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Postup implementace a konvence  
 Když implementace vzoru ovládacích prvků transformace, poznamenejte si následující pokyny a konvence:  
  
-   Podpora pro tento vzor ovládacích prvků není omezeno pouze na objekty na ploše. Tento vzor ovládacích prvků musí také podporovat podřízené objekty daného objektu kontejneru Pokud podřízených objektů můžete přesunout, po změně velikosti nebo otáčet volně uvnitř kontejneru.  
  
-   Objekt nelze přesunout, po změně velikosti nebo otáčet tak, aby jeho výsledná umístění obrazovky by být zcela mimo souřadnice svého kontejneru a proto nejsou přístupné na klávesnici nebo myš (například když okno nejvyšší úrovně je přesunut mimo obrazovku a nebo podřízený objekt je přesunut mimo hranice kontejneru zobrazení). V těchto případech je umístěna do objektu co nejblíže souřadnice požadovaný obrazovky nejdříve s horní a levé souřadnice přepsána uvnitř kontejneru.  
  
-   Pro systémy s více monitorování Pokud je přesunout objekt, změněnou nebo otočený zcela mimo souřadnice kombinované plochy obrazovky, objekt je umístěn na primárním monitoru co nejblíže požadovaný souřadnice míře.  
  
-   Všechny parametry a hodnoty vlastností jsou absolutní a nezávislé na národním prostředí.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-itransformprovider"></a>Požadované členy pro ITransformProvider  
 Následující vlastnosti a metody jsou požadovány pro implementaci <xref:System.Windows.Automation.Provider.ITransformProvider>.  
  
|Požadované členy|Typ člena|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanMove%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanResize%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanRotate%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A>|Metoda|Žádné|  
  
 Tento vzor ovládacích prvků nemá žádné přidružené události.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatelé musí throw následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A><br /><br /> -Pokud <xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> je false.|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A><br /><br /> -Pokud <xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> je false.|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A><br /><br /> -Pokud <xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> je false.|  
  
## <a name="see-also"></a>Viz také  
 [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Použití mezipaměti při automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
