---
title: Mapování vzorů ovládacích prvků pro klienty automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, for UI Automation clients
- UI Automation, clients, control patterns for
ms.assetid: 8b81645b-8be3-4e26-9c98-4fb0fceca06b
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 02244043d802029364c7a725940f03ecdd21f573
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864654"
---
# <a name="control-pattern-mapping-for-ui-automation-clients"></a>Mapování vzorů ovládacích prvků pro klienty automatizace uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma uvádí typy ovládacích prvků a jejich přidružený ovládací prvek vzorce.  
  
 V následující tabulce slouží k uspořádání vzorů ovládacích prvků do následujících kategorií:  
  
-   Podporované. Ovládací prvek musí podporovat tento – vzor ovládacích prvků.  
  
-   Podmíněné podpory. Ovládací prvek může podporovat tento – vzor ovládacích prvků v závislosti na stavu ovládacího prvku.  
  
-   Není podporováno. Ovládací prvek nepodporuje tento – vzor ovládacích prvků; vlastní ovládací prvky mohou podporovat tento – vzor ovládacích prvků.  
  
> [!NOTE]
>  Některé ovládací prvky mají podmíněné podporu pro několik vzorů ovládacích prvků v závislosti na funkce ovládací prvek. Například má podmíněné podporu pro ovládací prvek položky nabídky <xref:System.Windows.Automation.InvokePattern>, <xref:System.Windows.Automation.ExpandCollapsePattern>, <xref:System.Windows.Automation.TogglePattern>, nebo <xref:System.Windows.Automation.SelectionItemPattern> – vzor ovládacích prvků, v závislosti na jeho funkce v ovládacím prvku nabídky.  
  
<a name="control_mapping_clients"></a>   
## <a name="ui-automation-control-patterns-for-clients"></a>Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty  
  
|Typ ovládacího prvku|Podporováno|Podpora podmíněného|Nepodporováno|  
|------------------|---------------|-------------------------|-------------------|  
|Tlačítko|Žádné|Vyvolání přepínací tlačítko, Rozbalit/sbalit|Žádné|  
|Kalendář|Mřížka tabulky|Výběr, posuňte|Hodnota|  
|Zaškrtávací políčko|Přepnout|Žádné|Žádné|  
|Pole se seznamem|Rozbalit/sbalit|Výběr, hodnota|Posuv|  
|Datová mřížka|Mřížka|Posunout výběr tabulky|Žádné|  
|Datová položka|Položka výběru|Rozbalte sbalit položky mřížky, Posunout položku, tabulky, přepínací tlačítko, hodnota|Žádné|  
|Dokument|Text|Posouvání, hodnota|Žádné|  
|Upravit|Žádné|Textová hodnota rozsahu, hodnota|Žádné|  
|Skupina|Žádné|Rozbalit/sbalit|Žádné|  
|Záhlaví|Žádné|Transformace|Žádné|  
|Položka hlavičky|Žádné|Transformace, vyvolají|Žádné|  
|Hypertextový odkaz|Vyvolat|Hodnota|Žádné|  
|Image|Žádné|Mřížky nebo položky tabulky|Vyvolání, výběr položky|  
|Seznam|Žádné|Mřížka, více zobrazení posuvníku, výběr|Tabulka|  
|Položka seznamu|Položka výběru|Rozbalit/sbalit položky mřížky vyvolání, posuňte se položky, přepnout, hodnota|Žádné|  
|Nabídka|Žádné|Žádné|Žádné|  
|Řádek nabídek|Žádné|Rozbalte sbalit Dock transformace|Žádné|  
|Položka nabídky|Žádné|Rozbalit/sbalit, vyvolají, výběr položky přepínací tlačítko|Žádné|  
|Podokno|Žádné|Ukotvěte. Posouvání, transformace|Okno|  
|Indikátor průběhu|Žádné|Hodnota rozsahu|Žádné|  
|Přepínač|Položka výběru|Žádné|Přepnout|  
|Posuvník|Žádné|Hodnota v rozsahu|Posuv|  
|Oddělovač|Žádné|Žádné|Žádné|  
|Posuvník|Žádné|Rozsah, výběr, hodnota|Žádné|  
|Číselník|Žádné|Rozsah, výběr, hodnota|Žádné|  
|Tlačítko rozdělení|Vyvolání, Rozbalit/sbalit|Žádné|Žádné|  
|Stavový řádek|Žádné|Mřížka|Žádné|  
|Tabulátor|Výběr|Posuv|Žádné|  
|Položka tabulátoru|Položka výběru|Žádné|Vyvolat|  
|Tabulka|Mřížka položky mřížky, tabulky, položka tabulky|Žádné|Žádné|  
|Text|Žádné|Text položky, položka tabulky mřížky|Hodnota|  
|Jezdec|Transformace|Žádné|Žádné|  
|Záhlaví|Žádné|Žádné|Žádné|  
|Panel nástrojů|Žádné|Ukotvit, Rozbalit/sbalit, transformace|Žádné|  
|Popis tlačítka|Žádné|Text okna|Žádné|  
|Strom|Žádné|Posunout výběr|Žádné|  
|Položka stromu|Rozbalit/sbalit|Vyvolání, Posunout položku výběru položek, přepínací tlačítko|Žádné|  
|Okno|Transformace, okno|Ukotvení|Žádné|  
  
> [!NOTE]
>  Pokud typ ovládacího prvku nemá žádné vzory podporovaných ovládacích prvků uvedené, ale má jeden nebo více podmíněně podporováno vzorů ovládacích prvků pro, pak jednu z těchto vzorů ovládacích prvků podmíněné bude podporovat ve všech vícekrát.  
  
## <a name="see-also"></a>Viz také  
 [Přehled automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-overview.md)
