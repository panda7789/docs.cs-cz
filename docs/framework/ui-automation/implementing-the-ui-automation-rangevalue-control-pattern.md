---
title: Implementace vzoru ovládacích prvků RangeValue pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 219f460906d2892ae6cd76d13a2b17378e02b9b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399326"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a>Implementace vzoru ovládacích prvků RangeValue pro automatizaci uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma představuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.IRangeValueProvider>, včetně informací o události a vlastnosti. Na konci tohoto tématu jsou uvedeny odkazy na další odkazy.  
  
 <xref:System.Windows.Automation.RangeValuePattern> – Vzor ovládacích prvků se používá pro podporu ovládací prvky, které lze nastavit na hodnotu v rozsahu. Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků najdete v tématu [řízení vzor mapování pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Postup implementace a konvence  
 Při implementaci hodnotu rozsahu – vzor ovládacích prvků, poznamenejte si následující pokyny a konvence:  
  
-   Ovládací prvky umožňují překalibrování jejich podporovaných vlastností na základě předvoleb národního prostředí nebo uživatele. Příkladem je teploměru ovládací prvek, který lze nastavit pro zobrazení teploty v Fahrenheita nebo c.  
  
-   Ovládací prvky, které mají nejednoznačný rozsah hodnot, například indikátory průběhu nebo posuvníky, by měl mít tyto hodnoty normalized.  
  
 ![Indikátor průběhu. ] (../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")  
Příklad indikátor průběhu, kde hodnota je celé číslo typ a vlastnost minimální a maximální hodnoty jsou normalizovány na 0 a 100,  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>   
## <a name="required-members-for-irangevalueprovider"></a>Požadované členy pro IRangeValueProvider  
  
|Povinný člen|Typ člena|Poznámky|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|Metody|Žádné|  
  
 Tento vzor ovládacích prvků nemá žádné přidružené události.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatelé musí throw následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> je volána s hodnotu, která je větší než <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> nebo menší než <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.|  
  
## <a name="see-also"></a>Viz také  
 [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Použití mezipaměti při automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
