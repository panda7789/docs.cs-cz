---
title: Implementace vzoru ovládacích prvků okno pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
ms.openlocfilehash: 4f11f82b628ac020cbda70d65adf7813291c60a6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168035"
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a>Implementace vzoru ovládacích prvků okno pro automatizaci uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma popisuje pravidla a zásady pro implementaci <xref:System.Windows.Automation.Provider.IWindowProvider>, včetně informací o <xref:System.Windows.Automation.WindowPattern> vlastnosti, metody a události. Odkazy na další odkazy jsou uvedeny na konci tohoto tématu.  
  
 <xref:System.Windows.Automation.WindowPattern> – Vzor ovládacích prvků slouží k podpoře ovládací prvky, které poskytuje základní funkce založené na oknech v rámci tradičního [!INCLUDE[TLA#tla_gui](../../../includes/tlasharptla-gui-md.md)]. Příklady ovládacích prvků, které musí implementovat toto – vzor ovládacích prvků nejvyšší úrovně aplikace pro windows, [!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)] podřízených oken, ovládací prvky umožňující změnu velikosti rozdělení podokně, modální dialogová okna a bubliny pomáhají systému windows.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Pokyny pro implementaci a konvence  
 Při implementaci vzoru ovládacích prvků okno, poznamenejte si následující pokyny a konvence:  
  
-   Chcete-li podporují možnost změnit velikost obě okna a obrazovky pozice použitím automatizace uživatelského rozhraní, musí implementovat ovládací prvek <xref:System.Windows.Automation.Provider.ITransformProvider> kromě <xref:System.Windows.Automation.Provider.IWindowProvider>.  
  
-   Ovládací prvky, které obsahují záhlaví a prvky název panelu, které povolte stažení ovládacího prvku přesune, velikost, maximalizované, minimalizovat nebo uzavřel jsou zpravidla vyžadovány k implementaci <xref:System.Windows.Automation.Provider.IWindowProvider>.  
  
-   Ovládací prvky, jako je například automaticky otevíraná okna popisu tlačítka a pole se seznamem pole nebo nabídky rozevíracích neimplementují obvykle <xref:System.Windows.Automation.Provider.IWindowProvider>.  
  
-   Bublině nápovědy systému windows jsou rozlišené ze základní popis automaticky otevíraná okna tak, že zřídíte jako okno zavřít.  
  
-   Režim celé obrazovky není podporována IWindowProvider je specifické pro funkce k aplikaci a není chování typické okna.  
  
<a name="Required_Members_for_IWindowProvider"></a>   
## <a name="required-members-for-iwindowprovider"></a>Požadované členy pro IWindowProvider  
 Následující vlastnosti, metody a události jsou požadovány pro IWindowProvider rozhraní.  
  
|Povinný člen|Typ člena|Poznámky|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|Metoda|Žádný|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|Metoda|Žádný|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|Metoda|Žádný|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|Událost|Žádný|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|Událost|Žádné|  
|<xref:System.Windows.Automation.WindowInteractionState>|Událost|Není zaručeno, že bude <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction>|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Poskytovatelé musí vyvolání následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> – Když ovládací prvek nepodporuje požadované chování.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> -Pokud parametr není platné číslo.|  
  
## <a name="see-also"></a>Viz také:

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
