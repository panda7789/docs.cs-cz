---
title: Mapování vzorů ovládacích prvků pro klienty automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, for UI Automation clients
- UI Automation, clients, control patterns for
ms.assetid: 8b81645b-8be3-4e26-9c98-4fb0fceca06b
ms.openlocfilehash: cfd8e5dbe34df7b947646c714a360cf56b0435a4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043864"
---
# <a name="control-pattern-mapping-for-ui-automation-clients"></a>Mapování vzorů ovládacích prvků pro klienty automatizace uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 Toto téma obsahuje seznam typů ovládacích prvků a jejich přidružených vzorů ovládacích prvků.  
  
 V následující tabulce jsou uspořádány vzory ovládacích prvků do následujících kategorií:  
  
- Doložen. Ovládací prvek musí podporovat tento vzor ovládacího prvku.  
  
- Podmíněná podpora. Ovládací prvek může podporovat tento vzor ovládacího prvku v závislosti na stavu ovládacího prvku.  
  
- Není podporováno. Ovládací prvek nepodporuje tento vzor ovládacího prvku; vlastní ovládací prvky můžou tento vzor ovládacích prvků podporovat.  
  
> [!NOTE]
> Některé ovládací prvky mají podmíněnou podporu pro několik vzorů ovládacích prvků v závislosti na funkcích ovládacího prvku. Například ovládací prvek <xref:System.Windows.Automation.InvokePattern>položky nabídky má podmíněnou podporu vzoru, <xref:System.Windows.Automation.ExpandCollapsePattern>, <xref:System.Windows.Automation.TogglePattern>nebo <xref:System.Windows.Automation.SelectionItemPattern> , v závislosti na jeho funkci v ovládacím prvku nabídky.  
  
<a name="control_mapping_clients"></a>   
## <a name="ui-automation-control-patterns-for-clients"></a>Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty  
  
|Typ ovládacího prvku|Podporováno|Podmíněná podpora|Nepodporováno|  
|------------------|---------------|-------------------------|-------------------|  
|Tlačítko|Žádné|Vyvolat, přepínat, rozbalit sbalení|Žádné|  
|Kalendář|Mřížka, tabulka|Výběr, posun|Value|  
|Zaškrtávací políčko|Přepnout|Žádné|Žádné|  
|Pole se seznamem|Rozbalit sbalení|Výběr, hodnota|Posuv|  
|Datová mřížka|Mřížka|Posunutí, výběr, tabulka|Žádné|  
|Datová položka|Položka výběru|Rozbalit sbalení, položku mřížky, posunout položku, tabulka, přepínač, hodnota|Žádné|  
|Dokument|Text|Posunutí, hodnota|Žádné|  
|Upravit|Žádné|Text, hodnota rozsahu, hodnota|Žádné|  
|Skupina|Žádné|Rozbalit sbalení|Žádné|  
|Záhlaví|Žádné|Transformace|Žádné|  
|Položka hlavičky|Žádné|Transformovat, vyvolat|Žádné|  
|Hypertextový odkaz|Vyvolat|Value|Žádné|  
|Image|Žádné|Položka mřížky, položka tabulky|Invoke, výběr položky|  
|Seznam|Žádné|Mřížka, více zobrazení, posun, výběr|Tabulka|  
|Položka seznamu|Položka výběru|Rozbalit sbalení, položku mřížky, vyvolání, posunutí položky, přepínač, hodnota|Žádné|  
|Nabídka|Žádné|Žádný|Žádné|  
|Řádek nabídek|Žádné|Rozbalit sbalit, ukotvit, transformovat|Žádné|  
|Položka nabídky|Žádné|Rozbalit sbalení, vyvolání, výběr položky, přepnout|Žádné|  
|Podokno|Žádné|Vyjměte. Posouvání, transformace|Okno|  
|Indikátor průběhu|Žádné|Hodnota rozsahu, hodnota|Žádné|  
|Přepínač|Položka výběru|Žádné|Přepnout|  
|Posuvník|Žádné|Hodnota v rozsahu|Posuv|  
|Oddělovač|Žádné|Žádný|Žádné|  
|Posuvník|Žádné|Hodnota rozsahu, výběr, hodnota|Žádné|  
|Číselník|Žádné|Hodnota rozsahu, výběr, hodnota|Žádné|  
|Tlačítko rozdělení|Vyvolat, rozbalit sbalit|Žádné|Žádné|  
|Stavový řádek|Žádné|Mřížka|Žádné|  
|Karta|Výběr|Posuv|Žádné|  
|Položka tabulátoru|Položka výběru|Žádné|Vyvolat|  
|Tabulka|Grid, položka mřížky, tabulka, položka tabulky|Žádné|Žádné|  
|Text|Žádné|Položka mřížky, položka tabulky, text|Value|  
|Jezdec|Transformace|Žádné|Žádné|  
|Záhlaví|Žádné|Žádný|Žádné|  
|Panel nástrojů|Žádné|Ukotvit, rozbalit, transformovat|Žádné|  
|Popis nástroje|Žádné|Text, okno|Žádné|  
|Strom|Žádné|Posunutí, výběr|Žádné|  
|Položka stromu|Rozbalit sbalení|Vyvolání, posunutí položky, výběr položky, přepnutí|Žádné|  
|Okno|Transformace, okno|Vyjměte|Žádné|  
  
> [!NOTE]
> Pokud typ ovládacího prvku nemá uvedené žádné podporované vzory ovládacích prvků, ale má jeden nebo více podmíněně podporovaných vzorů ovládacích prvků, pak jeden z těchto vzorů podmíněného řízení bude podporován v každém okamžiku.  
  
## <a name="see-also"></a>Viz také:

- [Přehled automatizace uživatelského rozhraní](ui-automation-overview.md)
