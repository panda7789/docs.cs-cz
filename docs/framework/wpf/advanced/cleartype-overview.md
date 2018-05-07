---
title: ClearType – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], ClearType technology
- ClearType [WPF], technology
ms.assetid: 7e2392e0-75dc-463d-a716-908772782431
ms.openlocfilehash: 1d434fa913d077d72f0f889dc69eccc8a9ed0e9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cleartype-overview"></a>ClearType – přehled
Toto téma obsahuje přehled [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] technologie v nalezen [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
  
<a name="overview"></a>   
## <a name="technology-overview"></a>Přehled technologie  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] je technologie softwaru vyvinuté [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] která zlepšuje čitelnost textu na existující monitorů LCD (zobrazí se Crystal kapaliny), například přenosný počítač obrazovky, Pocket PC obrazovky a ploché monitory.  [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] funguje díky přístupu k elementů stripe jednotlivých svislé barev v každé pixelů displeje. Před [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)], nejnižší úroveň podrobností, která může zobrazovat počítač byl jednoho pixelů, ale s [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] spuštěna na monitoru LCD, můžete, zobrazuje se teď funkce textu malá jako zlomek pixel šířku. Navíc řešení zvyšuje ostrost jen nepatrnou podrobnosti zobrazení textu, výrazně usnadňují čtení přes dlouhé doby trvání.  
  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] k dispozici v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] je nejnovější generace [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] který má několik vylepšení přes nalezená verze v [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)].  
  
<a name="sub-pixel_positioning"></a>   
## <a name="sub-pixel-positioning"></a>Umístění dílčí pixelů  
 Přináší značné vylepšení v předchozí verzi [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] je použití umístění dílčí pixelů. Na rozdíl od [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] implementace najít v [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)], [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] najít v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] umožňuje glyfů spustit v rámci pixelů a ne jenom hranice začátku obrazového bodu. Z důvodu toto navíc řešení v umístění glyfů je mezer a proporce glyfy přesnější a konzistentní.  
  
 Následující dva příklady ukazují, jak může glyfů začít na ohraničení dílčí pixelů až dílčí pixelů umístění se používá. V příkladu na levé straně je vykreslen pomocí starší verze produktu [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] zobrazovací jednotky, které využívají není umístění dílčí pixelů. V příkladu na pravé straně je vykreslen pomocí nové verze [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] zobrazovací jednotky, pomocí umístění dílčí pixelů. Všimněte si, jak se každý **e** a **l** v pravém bitové kopie je vykreslen trochu jinak vzhledem k tomu, že každý se spouští v různých dílčí pixelů. Při zobrazení textu v jeho normální velikost na obrazovce, tento rozdíl není patrné z důvodu vysoký kontrast glyfy bitové kopie. To je možné pouze z důvodu sofistikované barva filtrování, která je obsažena v [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)].  
  
 ![Text, zobrazí se dvě verze ClearType](../../../../docs/framework/wpf/advanced/media/wcpsdk-mmgraphics-text-cleartype-overview-01.png "wcpsdk_mmgraphics_text_cleartype_overview_01")  
Text zobrazovaný s ClearType starší a novější verze  
  
 Následující dva příklady porovnat výstup z dříve [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] zobrazovací jednotky k nové verzi [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] zobrazovací jednotky. Umístění subpixel, zobrazí na pravé straně výrazně zlepšuje mezery typu na obrazovce, zejména u malých velikostí, kde představuje rozdíl mezi dílčí pixelů a celý pixelů podstatnou část šířka glyfů. Všimněte si, že mezery mezi znaky je více i v druhé bitové kopie. Kumulativní výhodou dílčí pixelů umístění celkového vzhledu obrazovky textu je výrazně zvýšit a představuje významné vývoj v [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] technologie.  
  
 ![Text zobrazovaný starší verzí ClearType](../../../../docs/framework/wpf/advanced/media/wcpsdk-mmgraphics-text-cleartype-overview-02.png "wcpsdk_mmgraphics_text_cleartype_overview_02")  
Text s ClearType starší a novější verze  
  
<a name="y-direction_antialiasing"></a>   
## <a name="y-direction-antialiasing"></a>Vyhlazení směru osy Y  
 Jiné zkvalitňování [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] je vyhlazení směru osy y. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] v [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] bez směru osy y vyhlazení poskytuje lepší řešení na ose x, ale není osy y. Na tolní počítače a dolním okraji bez podstruktury křivek vícenásobná okrajů snižují jeho čitelnost.  
  
 Následující příklad ukazuje účinek použití vyhlazení žádné směru osy y. V tomto případě jsou zřejmá vícenásobná okrajů na horní a dolní část písmeno.  
  
 ![Text s vícenásobná okraje na bez podstruktury křivek](../../../../docs/framework/wpf/advanced/media/wcpsdk-mmgraphics-text-cleartype-overview-03.png "wcpsdk_mmgraphics_text_cleartype_overview_03")  
Text s vícenásobná okraje na bez podstruktury křivek  
  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje vyhlazení na úrovni směru osy y vyhlazování se žádné vícenásobná okraje. To je obzvláště důležité pro zlepšení čitelnosti asijské jazyky, které mají ideografickými znaky skoro stejné množství vodorovného a svislého bez podstruktury křivek.  
  
 Následující příklad ukazuje účinek antialiasingu směru osy y. V takovém případě horní a dolní část písmeno zobrazit smooth křivky.  
  
 ![Text ClearType y&#45;směr anti&#45;aliasy](../../../../docs/framework/wpf/advanced/media/wcpsdk-mmgraphics-text-cleartype-overview-04.png "wcpsdk_mmgraphics_text_cleartype_overview_04")  
Text s ClearType směru osy y vyhlazení  
  
<a name="hardware_acceleration"></a>   
## <a name="hardware-acceleration"></a>Hardwarová akcelerace  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] můžete využít výhod hardwarovou akceleraci pro lepší výkon a snížit požadavky na zatížení a systému paměť procesoru. Pomocí shadery pixelů a grafické paměti grafické karty, [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] poskytuje rychlejší vykreslování textu, zvláště pokud použita animace.  
  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nedojde ke změně celého systému [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] nastavení. Zakázání [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] v [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] nastaví [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vyhlazení ve stupních šedi režimu. Kromě toho [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] neprovede žádné změny nastavení [ClearType aplikace ladění PowerToy](http://www.microsoft.com/typography/ClearTypePowerToy.mspx).  
  
 Jeden z [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] rozhodnutí o návrhu architektury je nezávislé rozložení lepší podpory vyšší rozlišení DPI monitorování, která stále se rozšiřujících rozlišení. Tato akce nemá na důsledek [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nejsou podporovány vykreslování textu alias nebo rastrových obrázků v některé východoasijských písem vzhledem k tomu, že jsou oba závislé na rozlišení.  
  
<a name="further_information"></a>   
## <a name="further-information"></a>Další informace  
 [Informace o ClearType](http://www.microsoft.com/typography/ClearTypeInfo.mspx)  
  
 [PowerToy aplikace ClearType ladění](http://www.microsoft.com/typography/ClearTypePowerToy.mspx)  
  
## <a name="see-also"></a>Viz také  
 [Nastavení registru ClearType](../../../../docs/framework/wpf/advanced/cleartype-registry-settings.md)
