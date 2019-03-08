---
title: Mapování vzorů ovládacích prvků pro klienty automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, for UI Automation clients
- UI Automation, clients, control patterns for
ms.assetid: 8b81645b-8be3-4e26-9c98-4fb0fceca06b
ms.openlocfilehash: b98735b111d634584ec019a75d942f39e38cc8c5
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679577"
---
# <a name="control-pattern-mapping-for-ui-automation-clients"></a>Mapování vzorů ovládacích prvků pro klienty automatizace uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
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
|Tlačítko|Žádná|Vyvolání přepínací tlačítko, Rozbalit/sbalit|Žádná|  
|Kalendář|Mřížka tabulky|Výběr, posuňte|Hodnota|  
|Zaškrtávací políčko|Přepnout|Žádná|Žádná|  
|Pole se seznamem|Rozbalit/sbalit|Výběr, hodnota|Posuv|  
|Datová mřížka|Mřížka|Posunout výběr tabulky|Žádná|  
|Datová položka|Položka výběru|Rozbalte sbalit položky mřížky, Posunout položku, tabulky, přepínací tlačítko, hodnota|Žádná|  
|Dokument|Text|Posouvání, hodnota|Žádná|  
|Upravit|Žádná|Textová hodnota rozsahu, hodnota|Žádná|  
|Skupina|Žádná|Rozbalit/sbalit|Žádná|  
|Záhlaví|Žádná|Transformace|Žádná|  
|Položka hlavičky|Žádná|Transformace, vyvolají|Žádná|  
|Hypertextový odkaz|Vyvolat|Hodnota|Žádná|  
|Image|Žádná|Mřížky nebo položky tabulky|Vyvolání, výběr položky|  
|Seznam|Žádná|Mřížka, více zobrazení posuvníku, výběr|Tabulka|  
|Položka seznamu|Položka výběru|Rozbalit/sbalit položky mřížky vyvolání, posuňte se položky, přepnout, hodnota|Žádná|  
|Nabídka|Žádná|Žádný|Žádná|  
|Řádek nabídek|Žádná|Rozbalte sbalit Dock transformace|Žádná|  
|Položka nabídky|Žádná|Rozbalit/sbalit, vyvolají, výběr položky přepínací tlačítko|Žádná|  
|Podokno|Žádná|Ukotvěte. Posouvání, transformace|Okno|  
|Indikátor průběhu|Žádná|Hodnota rozsahu|Žádná|  
|Přepínač|Položka výběru|Žádná|Přepnout|  
|Posuvník|Žádná|Hodnota v rozsahu|Posuv|  
|Oddělovač|Žádná|Žádný|Žádná|  
|Posuvník|Žádná|Rozsah, výběr, hodnota|Žádná|  
|Číselník|Žádná|Rozsah, výběr, hodnota|Žádná|  
|Tlačítko rozdělení|Vyvolání, Rozbalit/sbalit|Žádná|Žádná|  
|Stavový řádek|Žádná|Mřížka|Žádná|  
|Karta|Výběr|Posuv|Žádná|  
|Položka tabulátoru|Položka výběru|Žádná|Vyvolat|  
|Tabulka|Mřížka položky mřížky, tabulky, položka tabulky|Žádná|Žádná|  
|Text|Žádná|Text položky, položka tabulky mřížky|Hodnota|  
|Jezdec|Transformace|Žádná|Žádná|  
|Záhlaví|Žádná|Žádný|Žádná|  
|Panel nástrojů|Žádná|Ukotvit, Rozbalit/sbalit, transformace|Žádná|  
|Popis tlačítka|Žádná|Text okna|Žádná|  
|Strom|Žádná|Posunout výběr|Žádná|  
|Položka stromu|Rozbalit/sbalit|Vyvolání, Posunout položku výběru položek, přepínací tlačítko|Žádná|  
|Okno|Transformace, okno|Ukotvení|Žádná|  
  
> [!NOTE]
>  Pokud typ ovládacího prvku nemá žádné vzory podporovaných ovládacích prvků uvedené, ale má jeden nebo více podmíněně podporováno vzorů ovládacích prvků pro, pak jednu z těchto vzorů ovládacích prvků podmíněné bude podporovat ve všech vícekrát.  
  
## <a name="see-also"></a>Viz také:
- [Přehled automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-overview.md)
