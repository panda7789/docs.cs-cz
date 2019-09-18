---
title: Implementace vzoru ovládacích prvků RangeValue pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: 57986fa28a7a1bb7f70409b332147ff5b9615ec0
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043412"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a>Implementace vzoru ovládacích prvků RangeValue pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 Toto téma obsahuje pokyny a konvence pro <xref:System.Windows.Automation.Provider.IRangeValueProvider>implementaci, včetně informací o událostech a vlastnostech. Odkazy na další odkazy jsou uvedeny na konci tématu.  
  
 Vzor <xref:System.Windows.Automation.RangeValuePattern> ovládacího prvku slouží k podpoře ovládacích prvků, které lze nastavit na hodnotu v rozsahu. Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků, naleznete v tématu [mapování vzoru ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Pokyny a konvence implementace  
 Při implementaci vzoru ovládacího prvku hodnota rozsahu si všimněte následujících pokynů a konvencí:  
  
- Ovládací prvky umožňují rekalibraci podporovaných vlastností v závislosti na národním prostředí nebo uživatelské preference. Příkladem je ovládací prvek teploměr, který lze nastavit tak, aby zobrazoval teplotu ve stupních Fahrenheita nebo Celsia.  
  
- Ovládací prvky, které mají dvojznačné hodnoty rozsahu, například indikátory průběhu nebo posuvníky, by měly mít tyto hodnoty normalizovány.  
  
 Indikátor ![průběhu](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")  
Příklad indikátoru průběhu, kde hodnota je typu Integer a minimální a maximální hodnoty vlastností jsou normalizovány na 0 a 100, v uvedeném pořadí.  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>   
## <a name="required-members-for-irangevalueprovider"></a>Vyžadovaná členové pro IRangeValueProvider  
  
|Povinný člen|Typ člena|Poznámky|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|Metody|Žádné|  
  
 Tento vzor ovládacího prvku nemá žádné přidružené události.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatelé musí vyvolat následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>je volána s hodnotou, která je buď větší než <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> nebo menší než <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.|  
  
## <a name="see-also"></a>Viz také:

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
