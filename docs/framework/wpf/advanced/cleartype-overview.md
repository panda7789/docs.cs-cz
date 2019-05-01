---
title: ClearType – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], ClearType technology
- ClearType [WPF], technology
ms.assetid: 7e2392e0-75dc-463d-a716-908772782431
ms.openlocfilehash: 0127ee4112c4b42a7a55b9233217ea1e02604042
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051339"
---
# <a name="cleartype-overview"></a>ClearType – přehled
Toto téma obsahuje přehled [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] technologie najdete v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  

<a name="overview"></a>   
## <a name="technology-overview"></a>Přehled technologie  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] je software technologie vyvinutá společností [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] , který zlepšuje čitelnost textu na existující monitorů LCD (zobrazí se Liquid Crystal), například Notebook obrazovky, obrazovky v prostředí Pocket PC a monitorování plochý.  [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] funguje díky přístupu do jednotlivých svislé barevné prvky stripe v každý pixel displeje. Před [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)], nejnižší úroveň podrobností, který může zobrazit počítač byl jeden pixel, ale s [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] spuštěná na monitoru LCD, můžeme nyní můžete zobrazit funkce textu malá jako zlomek pixel šířku. Další řešení zvyšuje ostrost malý podrobnosti zobrazení textu, tím se velmi zjednoduší si přečíst dlouhé doby trvání.  
  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] k dispozici v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] je nejnovější generací [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] který má několik vylepšení přes verze nalezená v [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)].  
  
<a name="sub-pixel_positioning"></a>   
## <a name="sub-pixel-positioning"></a>Umístění dílčí pixelů  
 Výrazné zlepšení průběhu předchozí verzi [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] je použití dílčích pixel umístění. Na rozdíl od [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] součástí implementace [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)], [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] součástí [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] umožňuje glyfy ke spuštění v rámci obrazového bodu a nejen začátku hranice pixelu. Z důvodu této další řešení v umístění glyfů je mezery a rozměry glyfy přesné a konzistentní vzhledem k aplikacím.  
  
 Následující dva příklady ukazují, jak glyfy mohou začít na ohraničení dílčí pixel až dílčí pixel umístění se používá. V příkladu na levé straně je vykreslen pomocí předchozí verze [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] renderer, který není využívat umístění dílčí pixelů. V příkladu na pravé straně je vykreslen pomocí nové verze [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] renderer, použití dílčích pixel umístění. Všimněte si, jak každý **e** a **l** pravém obrázku je vykreslen trošku jinak vzhledem k tomu, že každý se spouští v různých dílčí pixelů. Při zobrazení textu v normální velikosti na obrazovce, tento rozdíl není patrné z důvodu vysoký kontrast piktogram image. To je možné pouze z důvodu sofistikované barva filtrování, který je součástí [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)].  
  
 ![Text zobrazený ve dvou verzích ClearType](./media/wcpsdk-mmgraphics-text-cleartype-overview-01.png "wcpsdk_mmgraphics_text_cleartype_overview_01")  
Text zobrazený v dříve a později verzích ClearType  
  
 Následující dva příklady porovnávají výstup z dříve [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] nástroj pro vykreslování s novou verzi [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] zobrazovací jednotky. Umístění subpixel, zobrazí na pravé straně, se výrazně zlepšuje typu na obrazovce, zejména v malých velikostech, kde představuje rozdíl mezi dílčí pixelů a celý pixel podstatnou část piktogram šířku mezery. Všimněte si, že mezery mezi znaky se víc i v druhý obrázek. Kumulativní výhodu, že dílčí pixel umístění do celkového vzhledu obrazovky textu je výrazně vyšší a představuje významný krok ve vývoji [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] technologie.  
  
 ![Text displayed with earlier version of ClearType](./media/wcpsdk-mmgraphics-text-cleartype-overview-02.png "wcpsdk_mmgraphics_text_cleartype_overview_02")  
Text s dříve a novějších verzích ClearType  
  
<a name="y-direction_antialiasing"></a>   
## <a name="y-direction-antialiasing"></a>Vyhlazení směru osy Y  
 Další vylepšení [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] je vyhlazení směru osy y. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] v [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] bez směru osy y vyhlazení poskytuje lepší řešení na osu x, ale ne osy y. Na horní a DNA bez podstruktury křivky ostrých hran zhoršit jeho čitelnost.  
  
 Následující příklad ukazuje účinek s žádné vyhlazení směru osy y. V tomto případě jsou zřejmá ostrých hran na horní a dolní část písmeno.  
  
 ![Text pomocí ostrých hran na bez podstruktury křivky](./media/wcpsdk-mmgraphics-text-cleartype-overview-03.png "wcpsdk_mmgraphics_text_cleartype_overview_03")  
Text pomocí ostrých hran na bez podstruktury křivky  
  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje vyhlazení na úrovni směru osy y vyhlazení jakékoli ostrých hran. To je zvlášť důležité pro zlepšení čitelnosti východoasijské jazyky, kde mají téměř stejné množství vodorovné a svislé bez podstruktury křivky ideografickými znaky.  
  
 Následující příklad ukazuje účinek antialiasingu směru osy y. V takovém případě horní a dolní část písmeno zobrazit smooth křivky.  
  
 ![Text with ClearType y&#45;direction anti&#45;aliasing](./media/wcpsdk-mmgraphics-text-cleartype-overview-04.png "wcpsdk_mmgraphics_text_cleartype_overview_04")  
Text s ClearType směru osy y vyhlazení  
  
<a name="hardware_acceleration"></a>   
## <a name="hardware-acceleration"></a>Hardwarová akcelerace  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] můžete využít výhod hardwarovou akceleraci pro lepší výkon a snížit požadavky na paměť procesoru zatížení a systému. S použitím pixel shaderů a grafické paměti grafické karty [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] poskytuje rychlejší vykreslování textu, zejména pokud se používá animace.  
  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] neupravuje celý systém [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] nastavení. Zakázání [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] v [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] nastaví [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vyhlazení do režimu ve stupních šedi. Kromě toho [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] neprovede žádné změny nastavení [ClearType Tuner PowerToy](https://www.microsoft.com/typography/ClearTypePowerToy.mspx).  
  
 Jeden z [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] rozhodnutí o návrhu architektury, je nezávislé rozložení zajištění lepší podpory pro vyšší rozlišení DPI monitorování, která stále se rozšiřujících rozlišení. Tato akce nemá důsledku [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nenabízí vykreslování textu s aliasem nebo rastrové obrázky v některých východoasijské písma vzhledem k tomu, že jsou oba závislé na rozlišení.  
  
<a name="further_information"></a>   
## <a name="further-information"></a>Další informace  
 [ClearType – informace](https://www.microsoft.com/typography/ClearTypeInfo.mspx)  
  
 [PowerToy ClearType Tuner](https://www.microsoft.com/typography/ClearTypePowerToy.mspx)  
  
## <a name="see-also"></a>Viz také:

- [Nastavení registru ClearType](cleartype-registry-settings.md)
