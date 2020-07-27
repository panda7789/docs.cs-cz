---
title: Implementace vzoru ovládacích prvků okno pro automatizaci uživatelského rozhraní
description: Přečtěte si pokyny a konvence pro implementaci vzoru ovládacích prvků okna v automatizaci uživatelského rozhraní. Znáte požadované členy pro rozhraní IWindowProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
ms.openlocfilehash: e1d7429f86896947a10b73965caa7d771f54490b
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168182"
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a>Implementace vzoru ovládacích prvků okno pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma obsahuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.IWindowProvider> , včetně informací o <xref:System.Windows.Automation.WindowPattern> vlastnostech, metodách a událostech. Odkazy na další odkazy jsou uvedeny na konci tématu.  
  
 <xref:System.Windows.Automation.WindowPattern>Vzor ovládacího prvku slouží k podpoře ovládacích prvků, které poskytují základní funkce založené na oknech v tradičním grafickém uživatelském rozhraní (GUI). Příklady ovládacích prvků, které musí implementovat tento vzor ovládacích prvků, zahrnují okna aplikace nejvyšší úrovně, podřízená okna rozhraní MDI (Multiple Document Interface), okna, modální dialogová okna a okna nápovědy k bublinám s možností změny velikosti.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Pokyny a konvence implementace  
 Při implementaci vzoru ovládacího prvku okna si všimněte následujících pokynů a konvencí:  
  
- Aby bylo možné podporovat možnost upravit velikost okna a umístění obrazovky pomocí automatizace uživatelského rozhraní, musí ovládací prvek implementovat <xref:System.Windows.Automation.Provider.ITransformProvider> kromě <xref:System.Windows.Automation.Provider.IWindowProvider> .  
  
- Pro implementaci jsou obvykle vyžadovány ovládací prvky, které obsahují záhlaví a prvky záhlaví, které umožňují přesunutí ovládacího prvku, jeho velikost, maximalizaci, minimalizaci nebo zavření <xref:System.Windows.Automation.Provider.IWindowProvider> .  
  
- Ovládací prvky, jako jsou například automaticky otevíraná okna s popisem tlačítka a pole se seznamem nebo nabídky, nejsou obvykle implementovány <xref:System.Windows.Automation.Provider.IWindowProvider> .  
  
- Okna nápovědy k bublinám jsou odlišená od základních popsaných tlačítek pomocí překryvných tlačítek pro tlačítko Zavřít.  
  
- Režim zobrazení na celé obrazovce není podporován IWindowProvider, protože se jedná o konkrétní funkci pro aplikaci a nejedná se o typické chování okna.  
  
<a name="Required_Members_for_IWindowProvider"></a>
## <a name="required-members-for-iwindowprovider"></a>Vyžadovaná členové pro IWindowProvider  
 Pro rozhraní IWindowProvider jsou vyžadovány následující vlastnosti, metody a události.  
  
|Povinný člen|Typ člena|Poznámky|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|Událost|Žádné|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|Událost|Žádné|  
|<xref:System.Windows.Automation.WindowInteractionState>|Událost|Není zaručeno být<xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction>|  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatelé musí vyvolat následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> – Když ovládací prvek nepodporuje požadované chování.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> – Pokud parametr není platným číslem.|  
  
## <a name="see-also"></a>Viz také

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
