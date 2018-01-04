---
title: "Mapování vzorů ovládacích prvků pro klienty automatizace uživatelského rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, for UI Automation clients
- UI Automation, clients, control patterns for
ms.assetid: 8b81645b-8be3-4e26-9c98-4fb0fceca06b
caps.latest.revision: "18"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 6a5f9d115c601775cc4f5b1c61d71d739f7a405b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="control-pattern-mapping-for-ui-automation-clients"></a>Mapování vzorů ovládacích prvků pro klienty automatizace uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma uvádí typy ovládacích prvků a jejich vzory přidružených ovládacích prvků.  
  
 V následující tabulce slouží k uspořádání vzory ovládacích prvků do následujících kategorií:  
  
-   Podporováno. Ovládací prvek musí podporovat tento vzor ovládacích prvků.  
  
-   Podpora podmíněného. Ovládací prvek může podporovat tento vzor ovládacích prvků v závislosti na stavu ovládacího prvku.  
  
-   Není podporováno. Ovládací prvek nepodporuje tento – vzor ovládacích prvků; vlastní ovládací prvky může podporovat tento vzor ovládacích prvků.  
  
> [!NOTE]
>  Některé ovládací prvky mít podmíněného podporu pro několik vzorů ovládacích prvků v závislosti na funkci ovládacího prvku. Například ovládací prvek položky nabídky má podmíněného podpora <xref:System.Windows.Automation.InvokePattern>, <xref:System.Windows.Automation.ExpandCollapsePattern>, <xref:System.Windows.Automation.TogglePattern>, nebo <xref:System.Windows.Automation.SelectionItemPattern> – vzor ovládacích prvků, v závislosti na jeho funkce v ovládacím prvku nabídky.  
  
<a name="control_mapping_clients"></a>   
## <a name="ui-automation-control-patterns-for-clients"></a>Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty  
  
|– Typ ovládacího prvku|Podporováno|Podpora podmíněného|Nepodporováno|  
|------------------|---------------|-------------------------|-------------------|  
|Tlačítko|Žádné|Vyvolání přepnutí, rozbalte položku sbalit|Žádné|  
|Kalendář|Mřížky, tabulka|Výběr, posuňte|Hodnota|  
|Zaškrtávací políčko|Přepnout|Žádné|Žádné|  
|Pole se seznamem|Rozbalte položku sbalit|Výběr, hodnota|Posuv|  
|Datová mřížka|Mřížka|Posuv, výběr, tabulka|Žádné|  
|Datová položka|Položka výběru|Rozbalte položku sbalit, položky v mřížce, Scroll položky, tabulku, přepínač, hodnota|Žádné|  
|Dokument|Text|Posuv, hodnota|Žádné|  
|Upravit|Žádné|Hodnota text, hodnotu rozsahu|Žádné|  
|Skupina|Žádné|Rozbalte položku sbalit|Žádné|  
|Záhlaví|Žádné|Transformace|Žádné|  
|Položka hlavičky|Žádné|Transformace, vyvolání|Žádné|  
|Hypertextový odkaz|Vyvolat|Hodnota|Žádné|  
|Image|Žádné|Položky v mřížce, položka tabulky|Vyvolání, výběr položky|  
|Seznam|Žádné|Posuv mřížky, více zobrazení, výběr|Tabulka|  
|Položky seznamu|Položka výběru|Rozbalte položku sbalit, položky v mřížce, vyvolání, posuňte se položky, přepněte, hodnota|Žádné|  
|Nabídka|Žádné|Žádné|Žádné|  
|Řádek nabídek|Žádné|Rozbalte položku sbalit, ukotvení, transformace|Žádné|  
|Položka nabídky|Žádné|Rozbalte sbalit, vyvolání, položka výběru přepnutí|Žádné|  
|Podokno|Žádné|Ukotvení. Posuňte, transformace|Okno|  
|Indikátor průběhu|Žádné|Hodnotu rozsahu, hodnota|Žádné|  
|Přepínač|Položka výběru|Žádné|Přepnout|  
|Posuvník|Žádné|Hodnota v rozsahu|Posuv|  
|Oddělovač|Žádné|Žádné|Žádné|  
|Posuvník|Žádné|Hodnota, výběr, hodnota rozsahu|Žádné|  
|Číselník|Žádné|Hodnota, výběr, hodnota rozsahu|Žádné|  
|Tlačítko rozdělení|Vyvolání, rozbalte položku sbalit|Žádné|Žádné|  
|Stavový řádek|Žádné|Mřížka|Žádné|  
|Tabulátor|Výběr|Posuv|Žádné|  
|Položka tabulátoru|Položka výběru|Žádné|Vyvolat|  
|Tabulka|Mřížky, položky v mřížce, tabulce, tabulka položek|Žádné|Žádné|  
|Text|Žádné|Text položky, položka tabulky mřížky|Hodnota|  
|Jezdec|Transformace|Žádné|Žádné|  
|Záhlaví|Žádné|Žádné|Žádné|  
|Panel nástrojů|Žádné|Ukotvení, rozbalte položku sbalit, transformace|Žádné|  
|Popis tlačítka|Žádné|Text, okno|Žádné|  
|Strom|Žádné|Posun výběru|Žádné|  
|Položka stromu|Rozbalte položku sbalit|Vyvolání, posuňte položky, položka výběru, přepínač|Žádné|  
|Okno|Transformace, okno|Ukotvení|Žádné|  
  
> [!NOTE]
>  Pokud typ ovládacího prvku nemá žádné podporované řízení vzorce uvedené, ale má jeden nebo více podmíněně podporovaných vzorů ovládacích prvků, potom jeden z těchto vzory podmíněného ovládacích prvků budou podporovány ve všech případech.  
  
## <a name="see-also"></a>Viz také  
 [Přehled automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-overview.md)
