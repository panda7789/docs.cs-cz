---
title: Implementace vzoru ovládacích prvků ukotvení pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, dock
- dock control pattern
- UI Automation, dock control pattern
ms.assetid: ea3d2212-7c8e-4dd7-bf08-73141ca2d4fb
ms.openlocfilehash: 9bc4f80569dc2bab68e3f65c9e99df72df372171
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968906"
---
# <a name="implementing-the-ui-automation-dock-control-pattern"></a>Implementace vzoru ovládacích prvků ukotvení pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 Toto téma obsahuje pokyny a konvence pro <xref:System.Windows.Automation.Provider.IDockProvider>implementaci, včetně informací o vlastnostech. Odkazy na další odkazy jsou uvedeny na konci tématu.  
  
 Vzor <xref:System.Windows.Automation.DockPattern> ovládacího prvku slouží k vystavení vlastností Dock ovládacího prvku v rámci Dock kontejneru. Kontejner Docker je ovládací prvek, který umožňuje uspořádat podřízené prvky vodorovně a svisle vzhledem k sobě. Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků, naleznete v tématu [mapování vzoru ovládacího prvku pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
 ![Dokování kontejneru se dvěma ukotvenými dětmi.](../../../docs/framework/ui-automation/media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")  
Příklad Docker ze sady Visual Studio, kde je okno "Zobrazení tříd" DockPosition. Right a Seznam chyb Window je DockPosition. Bottom  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Pokyny a konvence implementace  
 Při implementaci vzoru ovládacích prvků Docker si všimněte následujících pokynů a konvencí:  
  
- <xref:System.Windows.Automation.Provider.IDockProvider>nevystavuje žádné vlastnosti kontejneru Docker ani žádné vlastnosti ovládacích prvků, které jsou ukotveny v blízkosti aktuálního ovládacího prvku v rámci kontejneru docking.  
  
- Ovládací prvky jsou ukotveny relativně k sobě navzájem na základě jejich aktuálního pořadí z. Čím vyšší je umístění z pořadí vykreslování, tím dále budou umístěny ze zadaného okraje dokovacího kontejneru.  
  
- Pokud se změní velikost dokovacího kontejneru, všechny ukotvené ovládací prvky v kontejneru se přemístí jako vyprázdnění na stejnou hranu, do které byly původně ukotveny. Ukotvené ovládací prvky také změní velikost tak, aby vyplnily jakékoli místo v kontejneru podle toho <xref:System.Windows.Automation.DockPosition>, jak je to ukotveno. Pokud <xref:System.Windows.Automation.DockPosition.Top> je například zadáno, levá a pravá strana ovládacího prvku se rozšíří, aby vyplnila libovolné dostupné místo. Pokud <xref:System.Windows.Automation.DockPosition.Fill> je zadáno, rozšíří se všechny čtyři strany ovládacího prvku tak, aby vyplnily libovolné dostupné místo.  
  
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

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
