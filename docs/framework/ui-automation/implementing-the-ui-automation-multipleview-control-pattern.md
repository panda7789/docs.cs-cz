---
title: Implementace vzoru ovládacích prvků MultipleView pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
ms.openlocfilehash: 9decb617e30a340d3e73e911f7848110de5599e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180160"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a>Implementace vzoru ovládacích prvků MultipleView pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma představuje pokyny a <xref:System.Windows.Automation.Provider.IMultipleViewProvider>konvence pro implementaci , včetně informací o událostech a vlastnostech. Odkazy na další odkazy jsou uvedeny na konci tématu.  
  
 Vzor <xref:System.Windows.Automation.MultipleViewPattern> ovládacího prvku se používá k podpoře ovládacích prvků, které poskytují a jsou schopny přepínat mezi více reprezentace stejné sady informací nebo podřízené ovládací prvky.  
  
 Příklady ovládacích prvků, které mohou představovat více zobrazení, zahrnují zobrazení seznamu (které může zobrazovat jeho obsah jako miniatury, dlaždice, ikony nebo podrobnosti), grafy aplikace Microsoft Excel (výsečový, spojnicový, pruhový, hodnota buňky se vzorcem), dokumenty aplikace Microsoft Word (normální, rozložení webu, tisk rozložení, rozložení pro čtení, osnovu), kalendáře aplikace Microsoft Outlook (rok, měsíc, týden, den) a vzhledy programu Microsoft Windows Media Player. Podporovaná zobrazení jsou určena vývojářem ovládacího prvku a jsou specifická pro každý ovládací prvek.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Prováděcí pokyny a úmluvy  
 Při implementaci vzor ovládacího prvku více zobrazení, poznamenejte si následující pokyny a konvence:  
  
- <xref:System.Windows.Automation.Provider.IMultipleViewProvider>by měla být také implementována na kontejneru, který spravuje aktuální zobrazení, pokud se liší od ovládacího prvku, který poskytuje aktuální zobrazení. Průzkumník Windows například obsahuje ovládací prvek List pro aktuální obsah složky, zatímco zobrazení ovládacího prvku je spravováno z aplikace Průzkumník windows.  
  
- Ovládací prvek, který je schopen seřadit jeho obsah není považován za podporu více zobrazení.  
  
- Kolekce zobrazení musí být identické napříč instancemi.  
  
- Názvy zobrazení musí být vhodné pro použití v aplikacích Převod textu na řeč, Braillově písmu a dalších aplikacích čitelných pro člověka.  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>
## <a name="required-members-for-imultipleviewprovider"></a>Požadované členy pro iMultipleViewProvider  
 Následující vlastnosti a metody jsou vyžadovány pro implementaci IMultipleViewProvider.  
  
|Požadované členy|Typ člena|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|Metoda|Žádný|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|Metoda|Žádný|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|Metoda|Žádný|  
  
 Neexistují žádné události spojené s tímto vzorem ovládacího prvku.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatel musí vyvolat následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|Při <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> volání <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> buď nebo je volána s parametrem, který není členem kolekce podporovaných zobrazení.|  
  
## <a name="see-also"></a>Viz také

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
