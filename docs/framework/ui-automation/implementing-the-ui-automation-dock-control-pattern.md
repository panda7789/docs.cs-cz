---
title: Implementace vzoru ovládacích prvků ukotvení pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, dock
- dock control pattern
- UI Automation, dock control pattern
ms.assetid: ea3d2212-7c8e-4dd7-bf08-73141ca2d4fb
ms.openlocfilehash: 32ee58833b83e2a3356b6c1598abd207364e6ec1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609930"
---
# <a name="implementing-the-ui-automation-dock-control-pattern"></a>Implementace vzoru ovládacích prvků ukotvení pro automatizaci uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma popisuje pravidla a zásady pro implementaci <xref:System.Windows.Automation.Provider.IDockProvider>, včetně informací o vlastnostech. Odkazy na další odkazy jsou uvedeny na konci tohoto tématu.  
  
 <xref:System.Windows.Automation.DockPattern> – Vzor ovládacích prvků se používá k vystavení vlastnosti dock ovládacího prvku kontejneru ukotvení. Ukotvení kontejner je prvek, který umožňuje uspořádat podřízené prvky vodorovně a svisle, relativně vůči sobě navzájem. Příklady ovládacích prvků, které tento ovládací prvek model implementovat, najdete v článku [ovládací prvek vzor mapování pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
 ![Ukotvení s dvěma dětmi ukotvených kontejneru. ](../../../docs/framework/ui-automation/media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")  
Ukotvení příklad ze sady Visual Studio, ve kterém je okno "Zobrazení tříd" DockPosition.Right a okna "Seznam chyb" je DockPosition.Bottom  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Pokyny pro implementaci a konvence  
 Při implementaci vzoru ovládacích prvků ukotvení, mějte na paměti následující pokyny a konvence:  
  
- <xref:System.Windows.Automation.Provider.IDockProvider> nevystavuje žádné vlastnosti kontejneru dokovací ani žádné vlastnosti ovládacích prvků, které jsou ukotveny vedle aktuální ovládací prvek v rámci kontejneru ukotvení.  
  
- Ovládací prvky jsou ukotveny relativně vůči sobě navzájem podle jejich aktuálního pořadí vykreslování; vyšší jejich pořadí z umístění, dál vystavili z zadaný okraj kontejneru ukotvení.  
  
- Pokud je velikost kontejneru ukotvení, všechny ukotvených ovládacích prvků v kontejneru přemístí vyprázdnění stejné hrany, které byly původně ukotven. Ukotvených ovládacích prvků se taky změnit velikost, tak, aby vyplnil libovolné místo v kontejneru podle dokovací chování jejich <xref:System.Windows.Automation.DockPosition>. Například pokud <xref:System.Windows.Automation.DockPosition.Top> není zadána, levé a pravé straně ovládacího prvku se rozbalí a k dispozici prostor. Pokud <xref:System.Windows.Automation.DockPosition.Fill> není zadána, všechny čtyři strany ovládacího prvku se rozbalí a k dispozici prostor.  
  
- V systému s více monitorů by měl ovládacích prvků ukotvení do levé nebo pravé straně aktuálního monitoru. Pokud to není možné, jsou by měl ukotvení na levé straně úplně vlevo monitorování nebo pravé straně úplně vpravo monitorování.  
  
<a name="Required_Members_for_IDockProvider"></a>   
## <a name="required-members-for-idockprovider"></a>Požadované členy pro IDockProvider  
 Následující vlastnosti a metody jsou požadovány pro implementaci rozhraní IDockProvider.  
  
|Požadované členy|Typ člena|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IDockProvider.DockPosition%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A>|Metoda|Žádné|  
  
 Tento model ovládací prvek nemá žádné přidružené události.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Poskytovatelé musí vyvolání následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A><br /><br /> – Když není moci být prováděny dock požadovaný styl ovládacího prvku.|  
  
## <a name="see-also"></a>Viz také:

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
