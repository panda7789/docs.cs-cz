---
title: Implementace vzoru ovládacích prvků ukotvení pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, dock
- dock control pattern
- UI Automation, dock control pattern
ms.assetid: ea3d2212-7c8e-4dd7-bf08-73141ca2d4fb
ms.openlocfilehash: 1e2084483a34709392b9d3ceab02472c36944132
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435432"
---
# <a name="implementing-the-ui-automation-dock-control-pattern"></a>Implementace vzoru ovládacích prvků ukotvení pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma obsahuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.IDockProvider>, včetně informací o vlastnostech. Odkazy na další odkazy jsou uvedeny na konci tématu.  
  
 Vzor ovládacího prvku <xref:System.Windows.Automation.DockPattern> slouží k vystavení vlastností Dock ovládacího prvku v rámci Dock kontejneru. Kontejner Docker je ovládací prvek, který umožňuje uspořádat podřízené prvky vodorovně a svisle vzhledem k sobě. Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků, naleznete v tématu [mapování vzoru ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).  
  
 ![Dokování kontejneru se dvěma ukotvenými dětmi.](./media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")  
Příklad Docker ze sady Visual Studio, kde je okno "Zobrazení tříd" DockPosition. Right a Seznam chyb Window je DockPosition. Bottom  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Pokyny a konvence implementace  
 Při implementaci vzoru ovládacích prvků Docker si všimněte následujících pokynů a konvencí:  
  
- <xref:System.Windows.Automation.Provider.IDockProvider> nevystavuje žádné vlastnosti kontejneru Docker ani žádné vlastnosti ovládacích prvků, které jsou ukotveny sousedící s aktuálním ovládacím prvkem v rámci kontejneru docking.  
  
- Ovládací prvky jsou ukotveny relativně k sobě navzájem na základě jejich aktuálního pořadí z. Čím vyšší je umístění z pořadí vykreslování, tím dále budou umístěny ze zadaného okraje dokovacího kontejneru.  
  
- Pokud se změní velikost dokovacího kontejneru, všechny ukotvené ovládací prvky v kontejneru se přemístí jako vyprázdnění na stejnou hranu, do které byly původně ukotveny. Ukotvené ovládací prvky také změní velikost tak, aby vyplnily jakékoli místo v kontejneru podle chování při ukotvení jejich <xref:System.Windows.Automation.DockPosition>. Například pokud je zadána <xref:System.Windows.Automation.DockPosition.Top>, levou a pravou stranu ovládacího prvku se rozšíří, aby vyplnila libovolné dostupné místo. Je-li zadán <xref:System.Windows.Automation.DockPosition.Fill>, všechny čtyři strany ovládacího prvku budou rozšířeny, aby vyplnily libovolné dostupné místo.  
  
- V systému s více monitory by měly být ovládací prvky ukotveny k levé nebo pravé straně aktuálního monitorování. Pokud to není možné, měly by být ukotvené na levou stranu levého monitoru nebo na pravé straně monitoru napravo od sebe.  
  
<a name="Required_Members_for_IDockProvider"></a>   
## <a name="required-members-for-idockprovider"></a>Vyžadovaná členové pro IDockProvider  
 Pro implementaci rozhraní IDockProvider jsou vyžadovány následující vlastnosti a metody.  
  
|Vyžadovaná členové|Typ člena|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IDockProvider.DockPosition%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A>|Metoda|Žádné|  
  
 Tento vzor ovládacího prvku nemá žádné přidružené události.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatelé musí vyvolat následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A><br /><br /> – Když ovládací prvek nemůže spustit požadovaný styl ukotvení.|  
  
## <a name="see-also"></a>Viz také:

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
