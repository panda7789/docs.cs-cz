---
title: Implementace vzoru ovládacích prvků přepínání pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- Toggle control pattern
- control patterns, Toggle
- UI Automation, Toggle control pattern
ms.assetid: 3cfe875f-b0c0-413d-9703-5f14e6a1a30e
ms.openlocfilehash: 5f64842d31d46af3d648b9b570d1cfb210e2910a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180065"
---
# <a name="implementing-the-ui-automation-toggle-control-pattern"></a>Implementace vzoru ovládacích prvků přepínání pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma představuje pokyny a <xref:System.Windows.Automation.Provider.IToggleProvider>konvence pro implementaci , včetně informací o metodách a vlastnostech. Odkazy na další odkazy jsou uvedeny na konci tématu.  
  
 Vzor <xref:System.Windows.Automation.TogglePattern> ovládacího prvku se používá k podpoře ovládacích prvků, které lze cykonoběh přes sadu stavů a udržovat stav po nastavení. Příklady ovládacích prvků, které implementují tento vzor ovládacího prvku, naleznete [v tématu Mapování vzorů ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Prováděcí pokyny a úmluvy  
 Při implementaci přepnout ovládací prvek vzor, poznamenejte si následující pokyny a konvence:  
  
- Ovládací prvky, které při aktivaci neudržují stav, například tlačítka, tlačítka panelu nástrojů a hypertextové odkazy, musí být implementovány. <xref:System.Windows.Automation.Provider.IInvokeProvider>  
  
- Ovládací prvek musí <xref:System.Windows.Automation.ToggleState> cykinožní <xref:System.Windows.Automation.ToggleState.Off> cyklus v <xref:System.Windows.Automation.ToggleState.Indeterminate>následujícím pořadí: <xref:System.Windows.Automation.ToggleState.On>a, pokud je podporován, .  
  
- <xref:System.Windows.Automation.TogglePattern>neposkytuje SetState(newState) metoda z důvodu problémů obklopujících přímé nastavení tri-state CheckBox bez cyklické prostřednictvím jeho příslušné <xref:System.Windows.Automation.ToggleState> pořadí.  
  
- Ovládací prvek RadioButton <xref:System.Windows.Automation.Provider.IToggleProvider>se neimplementuje , protože není schopen cykinovat přes své platné stavy.  
  
<a name="Required_Members_for_IToggleProvider"></a>
## <a name="required-members-for-itoggleprovider"></a>Povinné členy pro IToggleProvider  
 Následující vlastnosti a metody jsou <xref:System.Windows.Automation.Provider.IToggleProvider>vyžadovány pro implementaci .  
  
|Povinný člen|Typ člena|Poznámky|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|Metoda|Žádný|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|Vlastnost|Žádný|  
  
 Tento vzor ovládacího prvku nemá žádné přidružené události.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Výjimky  
 Tento vzor ovládacího prvku nemá žádné přidružené výjimky.  
  
## <a name="see-also"></a>Viz také

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Zjištění stavu přepnutí zaškrtávacího políčka pomocí automatizace uživatelského rozhraní](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
