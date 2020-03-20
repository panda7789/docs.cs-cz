---
title: Implementace vzoru ovládacích prvků okno pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
ms.openlocfilehash: dd677ca9f610d463acc7c69f99767bd7b8781589
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180036"
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a>Implementace vzoru ovládacích prvků okno pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma představuje pokyny a <xref:System.Windows.Automation.Provider.IWindowProvider>konvence pro <xref:System.Windows.Automation.WindowPattern> implementaci , včetně informací o vlastnostech, metodách a událostech. Odkazy na další odkazy jsou uvedeny na konci tématu.  
  
 Vzor <xref:System.Windows.Automation.WindowPattern> ovládacího prvku se používá k podpoře ovládacích prvků, které poskytují základní funkce založené na okně v rámci tradiční grafické uživatelské rozhraní (GUI). Příklady ovládacích prvků, které musí implementovat tento vzor ovládacího prvku patří horní úrovně aplikace windows, více dokument rozhraní (MDI) podřízených oken, nastavitelné ovládací prvky rozděleného podokna, modální dialogy a bublina nápovědy.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Prováděcí pokyny a úmluvy  
 Při implementaci vzor ovládacího prvku okno, poznamenejte si následující pokyny a konvence:  
  
- Chcete-li podporovat možnost změnit velikost okna a umístění obrazovky pomocí <xref:System.Windows.Automation.Provider.ITransformProvider> automatizace <xref:System.Windows.Automation.Provider.IWindowProvider>uživatelského rozhraní, musí ovládací prvek implementovat kromě .  
  
- K implementaci <xref:System.Windows.Automation.Provider.IWindowProvider>jsou obvykle vyžadovány ovládací prvky obsahující záhlaví a prvky záhlaví, které umožňují přesunutí, velikost, maximalizaci, minimalizaci nebo zavření ovládacího prvku.  
  
- Ovládací prvky, jako jsou automaticky otevíraná okna s popisky <xref:System.Windows.Automation.Provider.IWindowProvider>a pole se seznamem nebo rozevírací seznam, obvykle neimplementují .  
  
- Okna nápovědy pro bubliny se odzákladních oken základních popisků liší poskytnutím tlačítka Zavřít jako okno.  
  
- Režim celé obrazovky není podporován iWindowProvider, protože je specifické pro konkrétní funkce aplikace a není typické chování okna.  
  
<a name="Required_Members_for_IWindowProvider"></a>
## <a name="required-members-for-iwindowprovider"></a>Požadované členy pro IWindowProvider  
 Následující vlastnosti, metody a události jsou vyžadovány pro rozhraní IWindowProvider.  
  
|Povinný člen|Typ člena|Poznámky|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|Metoda|Žádný|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|Metoda|Žádný|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|Metoda|Žádný|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|Událost|Žádný|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|Událost|Žádný|  
|<xref:System.Windows.Automation.WindowInteractionState>|Událost|Není zaručeno, že bude<xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction>|  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatelé musí vyvolat následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> - Pokud ovládací prvek nepodporuje požadované chování.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> - Pokud parametr není platné číslo.|  
  
## <a name="see-also"></a>Viz také

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
