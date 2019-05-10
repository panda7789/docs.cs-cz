---
title: Mapování vzorů ovládacích prvků pro klienty automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, for UI Automation clients
- UI Automation, clients, control patterns for
ms.assetid: 8b81645b-8be3-4e26-9c98-4fb0fceca06b
ms.openlocfilehash: 78274e2a5597291adcdafccf759b826f54a264ea
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647203"
---
# <a name="control-pattern-mapping-for-ui-automation-clients"></a>Mapování vzorů ovládacích prvků pro klienty automatizace uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma uvádí typy ovládacích prvků a jejich přidružený ovládací prvek vzorce.  
  
 V následující tabulce slouží k uspořádání vzorů ovládacích prvků do následujících kategorií:  
  
- Podporované. Ovládací prvek musí podporovat tento – vzor ovládacích prvků.  
  
- Podmíněné podpory. Ovládací prvek může podporovat tento – vzor ovládacích prvků v závislosti na stavu ovládacího prvku.  
  
- Není podporováno. Ovládací prvek nepodporuje tento – vzor ovládacích prvků; vlastní ovládací prvky mohou podporovat tento – vzor ovládacích prvků.  
  
> [!NOTE]
>  Některé ovládací prvky mají podmíněné podporu pro několik vzorů ovládacích prvků v závislosti na funkce ovládací prvek. Například má podmíněné podporu pro ovládací prvek položky nabídky <xref:System.Windows.Automation.InvokePattern>, <xref:System.Windows.Automation.ExpandCollapsePattern>, <xref:System.Windows.Automation.TogglePattern>, nebo <xref:System.Windows.Automation.SelectionItemPattern> – vzor ovládacích prvků, v závislosti na jeho funkce v ovládacím prvku nabídky.  
  
<a name="control_mapping_clients"></a>   
## <a name="ui-automation-control-patterns-for-clients"></a>Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty  
  
|Typ ovládacího prvku|Podporováno|Podpora podmíněného|Nepodporováno|  
|------------------|---------------|-------------------------|-------------------|  
|Tlačítko|Žádné|Vyvolání přepínací tlačítko, Rozbalit/sbalit|Žádný|  
|Kalendář|Mřížka tabulky|Výběr, posuňte|Hodnota|  
|Zaškrtávací políčko|Přepnout|Žádné|Žádné|  
|Pole se seznamem|Rozbalit/sbalit|Výběr, hodnota|Posuv|  
|Datová mřížka|Mřížka|Posunout výběr tabulky|Žádné|  
|Datová položka|Položka výběru|Rozbalte sbalit položky mřížky, Posunout položku, tabulky, přepínací tlačítko, hodnota|Žádné|  
|Dokument|Text|Posouvání, hodnota|Žádné|  
|Upravit|Žádný|Textová hodnota rozsahu, hodnota|Žádné|  
|Skupina|Žádný|Rozbalit/sbalit|Žádný|  
|Záhlaví|Žádné|Transformace|Žádný|  
|Položka hlavičky|Žádný|Transformace, vyvolají|Žádný|  
|Hypertextový odkaz|Vyvolat|Value|Žádné|  
|Image|Žádné|Mřížky nebo položky tabulky|Vyvolání, výběr položky|  
|Seznam|Žádný|Mřížka, více zobrazení posuvníku, výběr|Tabulka|  
|Položka seznamu|Položka výběru|Rozbalit/sbalit položky mřížky vyvolání, posuňte se položky, přepnout, hodnota|Žádné|  
|Nabídka|Žádné|Žádný|Žádný|  
|Řádek nabídek|Žádný|Rozbalte sbalit Dock transformace|Žádné|  
|Položka nabídky|Žádné|Rozbalit/sbalit, vyvolají, výběr položky přepínací tlačítko|Žádné|  
|Podokno|Žádný|Ukotvěte. Posouvání, transformace|Okno|  
|Indikátor průběhu|Žádný|Hodnota rozsahu|Žádné|  
|Přepínač|Položka výběru|Žádný|Přepnout|  
|Posuvník|Žádné|Hodnota v rozsahu|Posuv|  
|Oddělovač|Žádné|Žádný|Žádné|  
|Posuvník|Žádné|Rozsah, výběr, hodnota|Žádné|  
|Číselník|Žádný|Rozsah, výběr, hodnota|Žádné|  
|Tlačítko rozdělení|Vyvolání, Rozbalit/sbalit|Žádné|Žádný|  
|Stavový řádek|Žádné|Mřížka|Žádný|  
|Karta|Výběr|Posuv|Žádný|  
|Položka tabulátoru|Položka výběru|Žádné|Vyvolat|  
|Tabulka|Mřížka položky mřížky, tabulky, položka tabulky|Žádné|Žádný|  
|Text|Žádné|Text položky, položka tabulky mřížky|Value|  
|Jezdec|Transformace|Žádné|Žádné|  
|Záhlaví|Žádný|Žádný|Žádný|  
|Panel nástrojů|Žádné|Ukotvit, Rozbalit/sbalit, transformace|Žádný|  
|Popis tlačítka|Žádné|Text okna|Žádné|  
|Strom|Žádný|Posunout výběr|Žádné|  
|Položka stromu|Rozbalit/sbalit|Vyvolání, Posunout položku výběru položek, přepínací tlačítko|Žádné|  
|Okno|Transformace, okno|Ukotvení|Žádné|  
  
> [!NOTE]
>  Pokud typ ovládacího prvku nemá žádné vzory podporovaných ovládacích prvků uvedené, ale má jeden nebo více podmíněně podporováno vzorů ovládacích prvků pro, pak jednu z těchto vzorů ovládacích prvků podmíněné bude podporovat ve všech vícekrát.  
  
## <a name="see-also"></a>Viz také:

- [Přehled automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-overview.md)
