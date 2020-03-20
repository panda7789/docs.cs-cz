---
title: ClearType – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], ClearType technology
- ClearType [WPF], technology
ms.assetid: 7e2392e0-75dc-463d-a716-908772782431
ms.openlocfilehash: b76c0cb04e5de498374cbf28c8813fe5c95d41ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186155"
---
# <a name="cleartype-overview"></a>ClearType – přehled
Toto téma obsahuje přehled technologie Microsoft ClearType, která se nachází v rozhraní [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  

<a name="overview"></a>
## <a name="technology-overview"></a>Přehled technologií  
 ClearType je softwarová technologie vyvinutá společností Microsoft, která zlepšuje čitelnost textu na stávajících LCD (displeje z tekutých krystalů), jako jsou obrazovky notebooků, obrazovky kapesních počítačů a ploché monitory.  Funkce ClearType funguje tak, že přistupuje k jednotlivým prvkům svislého barevného proužku v každém pixelu obrazovky LCD. Před ClearType, nejmenší úroveň detailů, které počítač mohl zobrazit byl jeden pixel, ale s ClearType běží na monitoru LCD, můžeme nyní zobrazit funkce textu tak malý jako zlomek pixelu na šířku. Dodatečné rozlišení zvyšuje ostrost drobných detailů v textovém displeji, takže je mnohem snazší číst po dlouhou dobu.  
  
 ClearType k [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] dispozici v je nejnovější generace ClearType, který má několik vylepšení oproti verzi nalézt v Microsoft Windows Graphics Device Interface (GDI).  
  
<a name="sub-pixel_positioning"></a>
## <a name="sub-pixel-positioning"></a>Polohování subpixelů  
 Významné zlepšení oproti předchozí verzi ClearType je použití sub-pixel umístění. Na rozdíl od implementace ClearType nalezené v GDI umožňuje technologie ClearType nalezená v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikaci umožňuje glyfům začínat uvnitř obrazového bodu, a nikoli pouze počáteční hranici obrazového bodu. Z důvodu tohoto dodatečného rozlišení v umístění glyfů jsou mezery a proporce glyfů přesnější a konzistentní.  
  
 Následující dva příklady ukazují, jak mohou glyfy začínat na libovolné hranici subpixelů při použití umístění subpixelů. Příklad vlevo je vykreslen pomocí dřívější verze vykreslovače ClearType, která nepoužívala umístění subpixelů. Příklad vpravo je vykreslen pomocí nové verze vykreslovače ClearType pomocí umístění sub-pixel. Všimněte si, jak každý **e** a **l** v pravém obrázku je vykreslen mírně odlišně, protože každý začíná na jiném sub-pixel. Při zobrazení textu v normální velikosti na obrazovce není tento rozdíl zpomeněn z důvodu vysokého kontrastu obrazu glyfu. To je možné pouze díky sofistikovanému filtrování barev, které je součástí programu ClearType.  
  
 ![Text zobrazený se dvěma verzemi programu ClearType](./media/wcpsdk-mmgraphics-text-cleartype-overview-01.png "wcpsdk_mmgraphics_text_cleartype_overview_01")  
Text zobrazený v dřívějších a novějších verzích programu ClearType  
  
 Následující dva příklady porovnávají výstup z dřívějšího vykreslovače ClearType s novou verzí vykreslovače ClearType. Umístění subpixelu zobrazené vpravo výrazně zlepšuje mezery textu na obrazovce, zejména v malých velikostech, kde rozdíl mezi subpixelem a celým obrazovým bodem představuje významný podíl šířky glyfu. Všimněte si, že mezery mezi písmeny je rovnoměrnější v druhém obrázku. Kumulativní přínos umístění subpixelů k celkovému vzhledu obrazovky textu je výrazně zvýšen a představuje významný vývoj v technologii ClearType.  
  
 ![Text zobrazený v dřívější verzi programu ClearType](./media/wcpsdk-mmgraphics-text-cleartype-overview-02.png "wcpsdk_mmgraphics_text_cleartype_overview_02")  
Text s dřívějšími a novějšími verzemi programu ClearType  
  
<a name="y-direction_antialiasing"></a>
## <a name="y-direction-antialiasing"></a>Vymýšce ve směru Y  
 Dalším vylepšením cleartype je [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vyhlazení směru y. ClearType v GDI bez vyhlazení směru y poskytuje lepší rozlišení na ose x, ale ne na ose y. Na vrcholcích a dně mělkých křivek zubaté hrany snižují jeho čitelnost.  
  
 Následující příklad ukazuje účinek nemají y-směr vyhlazení. V tomto případě jsou zřejmé zubaté okraje v horní a dolní části písmene.  
  
 ![Text s zubatými okraji na mělkých křivách](./media/wcpsdk-mmgraphics-text-cleartype-overview-03.png "wcpsdk_mmgraphics_text_cleartype_overview_03")  
Text s zubatými okraji na mělkých křivách  
  
 ClearType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] in poskytuje vyhlazení na úrovni směru y, aby vyhladila všechny zubaté hrany. To je obzvláště důležité pro zlepšení čitelnosti východoasijských jazyků, kde ideografy mají téměř stejné množství horizontálních a vertikálních mělkých křivek.  
  
 Následující příklad ukazuje účinek vyznavačů směru y. V tomto případě horní a dolní část dopisu zobrazí hladkou křivku.  
  
 ![Text s&#45;směr ClearType proti&#45;aliasů](./media/wcpsdk-mmgraphics-text-cleartype-overview-04.png "wcpsdk_mmgraphics_text_cleartype_overview_04")  
Text s vyhlazením ve směru y příkazu ClearType  
  
<a name="hardware_acceleration"></a>
## <a name="hardware-acceleration"></a>Hardwarová akcelerace  
 Program ClearType in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] může využít hardwarovou akceleraci pro lepší výkon a snížení zatížení procesoru a požadavků na systémovou paměť. Pomocí shaderů pixelů a grafické paměti grafické karty poskytuje funkce ClearType rychlejší vykreslování textu, zejména při použití animace.  
  
 Program ClearType in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nezmění nastavení programu ClearType pro celý systém. Zakázáním programu ClearType v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] systému Windows nastavíte vyhlazení do režimu stupňů šedi. Kromě toho Aplikace [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ClearType in nemění nastavení [zařízení ClearType Tuner PowerToy](https://www.microsoft.com/typography/ClearTypePowerToy.mspx).  
  
 Jedním z [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] rozhodnutí o architektonickém návrhu je mít rozlišení nezávislé rozložení lépe podporovat vyšší rozlišení DPI monitory, které jsou stále rozšířenější. To má za [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] následek nepodporuje vykreslování aliased textu nebo rastrové obrázky v některých východoasijských písem, protože jsou oba rozlišení závislé.  
  
<a name="further_information"></a>
## <a name="further-information"></a>Další informace  
 [Informace o typu ClearType](https://www.microsoft.com/typography/ClearTypeInfo.mspx)  
  
 [ClearType Tuner PowerToy](https://www.microsoft.com/typography/ClearTypePowerToy.mspx)  
  
## <a name="see-also"></a>Viz také

- [Nastavení registru ClearType](cleartype-registry-settings.md)
