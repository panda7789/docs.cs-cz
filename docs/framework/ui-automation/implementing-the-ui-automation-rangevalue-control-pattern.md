---
title: Implementace vzoru ovládacích prvků RangeValue pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: 847a8aae3fd0c3d6965c910d19a4cec11cd2a3b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180184"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a>Implementace vzoru ovládacích prvků RangeValue pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma představuje pokyny a <xref:System.Windows.Automation.Provider.IRangeValueProvider>konvence pro implementaci , včetně informací o událostech a vlastnostech. Odkazy na další odkazy jsou uvedeny na konci tématu.  
  
 Vzor <xref:System.Windows.Automation.RangeValuePattern> ovládacího prvku se používá k podpoře ovládacích prvků, které lze nastavit na hodnotu v rozsahu. Příklady ovládacích prvků, které implementují tento vzor ovládacího prvku, naleznete [v tématu Mapování vzorů ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Prováděcí pokyny a úmluvy  
 Při implementaci vzor ovládacího prvku hodnota rozsahu, poznamenejte si následující pokyny a konvence:  
  
- Ovládací prvky umožňují rekalibraci jejich podporovaných vlastností na základě národního prostředí nebo uživatelské předvolby. Příkladem je ovládání teploměru, které lze nastavit tak, aby zobrazovalo teplotu ve Stupních Fahrenheita nebo Celsia.  
  
- Ovládací prvky, které mají nejednoznačné hodnoty rozsahu, například indikátory průběhu nebo posuvníky, by měly mít tyto hodnoty normalizovány.  
  
 ![Indikátor průběhu.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")  
Příklad indikátoru průběhu, kde hodnota je typu Integer a minimální a maximální hodnoty vlastností jsou normalizovány na 0 a 100, v uvedeném pořadí  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>
## <a name="required-members-for-irangevalueprovider"></a>Povinné členy pro iRangeValueProvider  
  
|Povinný člen|Typ člena|Poznámky|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|Metody|Žádný|  
  
 Tento vzor ovládacího prvku nemá žádné přidružené události.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatelé musí vyvolat následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>je volána s hodnotou, <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> která <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>je větší nebo menší než .|  
  
## <a name="see-also"></a>Viz také

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
