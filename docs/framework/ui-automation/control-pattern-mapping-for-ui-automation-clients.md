---
title: Mapování vzorů ovládacích prvků pro klienty automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, for UI Automation clients
- UI Automation, clients, control patterns for
ms.assetid: 8b81645b-8be3-4e26-9c98-4fb0fceca06b
ms.openlocfilehash: 689e649343c93d0670c6870098a09f61097f4fb4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180232"
---
# <a name="control-pattern-mapping-for-ui-automation-clients"></a>Mapování vzorů ovládacích prvků pro klienty automatizace uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma obsahuje seznam typů ovládacích prvku a jejich přidružené vzory ovládacího prvku.  
  
 Následující tabulka uspořádá vzory ovládacích prvku do následujících kategorií:  
  
- Podporuje se. Ovládací prvek musí podporovat tento vzor ovládacího prvku.  
  
- Podmíněná podpora. Ovládací prvek může podporovat tento vzor ovládacího prvku v závislosti na stavu ovládacího prvku.  
  
- Není podporováno. Ovládací prvek nepodporuje tento vzor ovládacího prvku; vlastní ovládací prvky mohou podporovat tento vzor ovládacího prvku.  
  
> [!NOTE]
> Některé ovládací prvky mají podmíněnou podporu pro několik vzorů ovládacího prvku v závislosti na funkčnosti ovládacího prvku. Ovládací prvek položky nabídky má například <xref:System.Windows.Automation.ExpandCollapsePattern> <xref:System.Windows.Automation.TogglePattern>podmíněnou <xref:System.Windows.Automation.SelectionItemPattern> <xref:System.Windows.Automation.InvokePattern>podporu pro , , nebo ovládací vzor, v závislosti na jeho funkci v ovládacím prvku nabídky.  
  
<a name="control_mapping_clients"></a>
## <a name="ui-automation-control-patterns-for-clients"></a>Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty  
  
|Typ ovládacího prvku|Podporuje se|Podmíněná podpora|Nepodporuje se|  
|------------------|---------------|-------------------------|-------------------|  
|Tlačítko|Žádný|Vyvolat, přepnout, rozbalit sbalení|Žádný|  
|Kalendář|Mřížka, Tabulka|Výběr, Posun|Hodnota|  
|Políčko|Přepnout|Žádný|Žádný|  
|Pole se seznamem|Rozbalit sbalení|Výběr, Hodnota|Posuv|  
|Datová mřížka|Mřížka|Posunout, Výběr, Tabulka|Žádný|  
|Datová položka|Položka výběru|Rozbalit sbalení, položku mřížky, položku posouvání, tabulku, přepínač, hodnotu|Žádný|  
|Dokument|Text|Posun, hodnota|Žádný|  
|Upravit|Žádný|Text, hodnota rozsahu, hodnota|Žádný|  
|Skupina|Žádný|Rozbalit sbalení|Žádný|  
|Hlavička|Žádný|Transformace|Žádný|  
|Položka hlavičky|Žádný|Transformace, vyvolání|Žádný|  
|Hypertextový odkaz|Invoke|Hodnota|Žádný|  
|Image|Žádný|Položka mřížky, položka tabulky|Vyvolat, položka výběru|  
|Seznam|Žádný|Mřížka, vícenásobné zobrazení, posun, výběr|Table|  
|Položka seznamu|Položka výběru|Rozbalit sbalení, položku mřížky, vyvolat, posouvat položku, přepnout, hodnotu|Žádný|  
|Nabídka|Žádný|Žádný|Žádný|  
|Řádek nabídek|Žádný|Rozbalit sbalení, ukotvit, transformovat|Žádný|  
|Položka nabídky|Žádný|Rozbalit sbalení, vyvolat, položku výběru, přepnout|Žádný|  
|Podokno|Žádný|Dock. Posunout, Transformace|Okno|  
|Indikátor průběhu|Žádný|Hodnota rozsahu, hodnota|Žádný|  
|Přepínač|Položka výběru|Žádný|Přepnout|  
|Posuvník|Žádný|Hodnota v rozsahu|Posuv|  
|Oddělovač|Žádný|Žádný|Žádný|  
|Posuvník|Žádný|Hodnota rozsahu, výběr, hodnota|Žádný|  
|Číselník|Žádný|Hodnota rozsahu, výběr, hodnota|Žádný|  
|Tlačítko rozdělení|Vyvolat, rozbalit sbalení|Žádný|Žádný|  
|Stavový řádek|Žádný|Mřížka|Žádný|  
|Karta|Výběr|Posuv|Žádný|  
|Položka tabulátoru|Položka výběru|Žádný|Invoke|  
|Table|Mřížka, Položka mřížky, Tabulka, Položka tabulky|Žádný|Žádný|  
|Text|Žádný|Položka mřížky, položka tabulky, text|Hodnota|  
|Jezdec|Transformace|Žádný|Žádný|  
|Záhlaví|Žádný|Žádný|Žádný|  
|Panel nástrojů|Žádný|Dock, Rozbalit sbalení, Transformace|Žádný|  
|Tip nástroje|Žádný|Text, Okno|Žádný|  
|Strom|Žádný|Posunout, Výběr|Žádný|  
|Položka stromu|Rozbalit sbalení|Vyvolat, posouvat položku, položku výběru, přepnout|Žádný|  
|Okno|Transformace, Okno|Dock|Žádný|  
  
> [!NOTE]
> Pokud typ ovládacího prvku nemá žádné podporované vzory ovládacího prvku uvedené, ale má jeden nebo více podmíněně podporovaných vzorů ovládacích prvku, pak jeden z těchto vzorů podmíněného ovládacího prvku bude podporována po celou dobu.  
  
## <a name="see-also"></a>Viz také

- [Přehled automatizace uživatelského rozhraní](ui-automation-overview.md)
