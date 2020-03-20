---
title: Implementace vzoru ovládacích prvků ukotvení pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, dock
- dock control pattern
- UI Automation, dock control pattern
ms.assetid: ea3d2212-7c8e-4dd7-bf08-73141ca2d4fb
ms.openlocfilehash: b1213791609245209fa37e3cdcb0876c963bfeb0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180210"
---
# <a name="implementing-the-ui-automation-dock-control-pattern"></a>Implementace vzoru ovládacích prvků ukotvení pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma představuje pokyny a <xref:System.Windows.Automation.Provider.IDockProvider>konvence pro implementaci , včetně informací o vlastnostech. Odkazy na další odkazy jsou uvedeny na konci tématu.  
  
 Vzor <xref:System.Windows.Automation.DockPattern> ovládacího prvku se používá k vystavení vlastností ukotvení ovládacího prvku v dokovacím kontejneru. Dokovací kontejner je ovládací prvek, který umožňuje uspořádat podřízené prvky vodorovně a svisle, vzhledem k sobě navzájem. Příklady ovládacích prvků, které implementují tento vzor ovládacího prvku, naleznete [v tématu Mapování vzorů ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).  
  
 ![Dokovací kontejner se dvěma ukotvenými dětmi.](./media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")  
Příklad ukotvení z visual studia, kde je okno "Zobrazení třídy" DockPosition.Right a "Error List" Okno je DockPosition.Bottom  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Prováděcí pokyny a úmluvy  
 Při implementaci vzoru ovládacího prvku Dock si poznamenejte následující pokyny a konvence:  
  
- <xref:System.Windows.Automation.Provider.IDockProvider>nezveřejňuje žádné vlastnosti dokovacího kontejneru nebo žádné vlastnosti ovládacích prvků, které jsou ukotveny vedle aktuálního ovládacího prvku v dokovacím kontejneru.  
  
- Ovládací prvky jsou ukotveny vzhledem k sobě navzájem na základě jejich aktuální pořadí vykreslovací; čím vyšší je umístění pořadí vykreslování, tím dále jsou umístěny od zadaného okraje dokovacího kontejneru.  
  
- Pokud dojde kontejner uskutečnění velikost, všechny ukotvené ovládací prvky v rámci kontejneru bude přemístit vyprázdnění na stejný okraj, ke kterému byly původně ukotveny. Ukotvené ovládací prvky také změní velikost tak, aby vyplnily libovolné <xref:System.Windows.Automation.DockPosition>místo v kontejneru podle dokovacího chování jejich . Například pokud <xref:System.Windows.Automation.DockPosition.Top> je zadán, levé a pravé strany ovládacího prvku se rozbalí vyplnit všechny dostupné místo. Pokud <xref:System.Windows.Automation.DockPosition.Fill> je zadán, všechny čtyři strany ovládacího prvku se rozbalí tak, aby vyplnily libovolné dostupné místo.  
  
- V systému s více monitory by ovládací prvky měly ukotvit na levé nebo pravé straně aktuálního monitoru. Pokud to není možné, měly by ukotvit na levé straně monitoru nejvíce vlevo nebo na pravé straně monitoru nejvíce vpravo.  
  
<a name="Required_Members_for_IDockProvider"></a>
## <a name="required-members-for-idockprovider"></a>Požadované členy pro IDockProvider  
 Následující vlastnosti a metody jsou vyžadovány pro implementaci rozhraní IDockProvider.  
  
|Požadované členy|Typ člena|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IDockProvider.DockPosition%2A>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A>|Metoda|Žádný|  
  
 Tento vzor ovládacího prvku nemá žádné přidružené události.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatelé musí vyvolat následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A><br /><br /> - Pokud ovládací prvek není schopen provést požadovaný styl doku.|  
  
## <a name="see-also"></a>Viz také

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
