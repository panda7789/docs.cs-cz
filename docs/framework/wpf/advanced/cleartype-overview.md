---
title: ClearType – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], ClearType technology
- ClearType [WPF], technology
ms.assetid: 7e2392e0-75dc-463d-a716-908772782431
ms.openlocfilehash: 405d06a8da8ec5c428c1565bcd08236de0f1fa88
ms.sourcegitcommit: 3eeea78f52ca771087a6736c23f74600cc662658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/31/2019
ms.locfileid: "68672049"
---
# <a name="cleartype-overview"></a>ClearType – přehled
Toto téma poskytuje přehled technologie Microsoft ClearType, kterou najdete v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]tématu.  

<a name="overview"></a>   
## <a name="technology-overview"></a>Přehled technologie  
 ClearType je softwarová technologie vyvinutá [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] nástrojem, která vylepšuje čitelnost textu v existujících LCDS (Liquid Crystal displeje), jako jsou obrazovky přenosné počítače, obrazovky Pocket PC a monitorované ploché panely.  Technologie ClearType funguje tak, že přistupuje k jednotlivým prvkům svislého barevného pruhu v každém pixelu obrazovky LCD. Před technologií ClearType teď může být nejmenší úroveň podrobností, kterou by byl počítač zobrazený, jeden pixel, ale u technologie ClearType běžící na monitoru LCD teď můžeme zobrazovat funkce textu jako malého podílu v šířce pixelů. Další řešení zvyšuje ostrost drobných podrobností v zobrazení textu, což usnadňuje čtení dlouhých dob trvání.  
  
 Technologie ClearType dostupná v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nástroji je nejnovější generace technologie ClearType, která má několik vylepšení verze v Microsoft Windows GDI (GDI).  
  
<a name="sub-pixel_positioning"></a>   
## <a name="sub-pixel-positioning"></a>Umístění dílčích pixelů  
 Výrazným vylepšením oproti předchozí verzi technologie ClearType je použití umístění s dílčími pixely. Na rozdíl od implementace technologie ClearType nalezené v rozhraní GDI umožňuje technologie [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ClearType nalezená v v obrazovém obrazci, nikoli pouze počáteční hranici pixelu. Vzhledem k tomuto dodatečnému rozlišení v glyfech umístění jsou mezery a poměry glyfů přesnější a konzistentní.  
  
 Následující dva příklady ukazují, jak se glyfy můžou začínat na libovolné hranici dílčích pixelů při použití umístění v pixelech. Příklad na levé straně se vykreslí pomocí starší verze zobrazovací jednotky ClearType, která nevyužívá umístění dílčích pixelů. Příklad na pravé straně se vykreslí pomocí nové verze zobrazovací jednotky ClearType s použitím umístění dílčích pixelů. Všimněte si, jak se jednotlivé **e** a **l** v pravé imagi vykreslují mírně odlišně, protože každá začíná na jiném dílčím pixelu. Při prohlížení textu na obrazovce na normální velikosti není tento rozdíl znatelný kvůli vysokému kontrastu obrázku glyfu. To je možné jenom v důsledku sofistikovaného filtrování barev, které je součástí technologie ClearType.  
  
 ![Text zobrazený se dvěma verzemi technologie ClearType](./media/wcpsdk-mmgraphics-text-cleartype-overview-01.png "wcpsdk_mmgraphics_text_cleartype_overview_01")  
Text zobrazený se staršími a novějšími verzemi technologie ClearType  
  
 Následující dva příklady porovnávají výstupy ze staršího vykreslovacího modulu ClearType s novou verzí vykreslovacího modulu ClearType. Umístění v dolním pixelu zobrazené na pravé straně výrazně vylepšuje velikost písma na obrazovce, zvláště u malých velikostí, kde rozdíl mezi dílčím pixelem a celým pixelem představuje značný podíl šířky glyfu. Všimněte si, že mezery mezi písmeny jsou i v druhém obrázku. Kumulativní výhoda umístění podpixelu na celkový vzhled obrazovky textu se značně zvýšila a představuje významný vývoj technologie ClearType.  
  
 ![Text zobrazený v dřívější verzi technologie ClearType](./media/wcpsdk-mmgraphics-text-cleartype-overview-02.png "wcpsdk_mmgraphics_text_cleartype_overview_02")  
Text se staršími a novějšími verzemi technologie ClearType  
  
<a name="y-direction_antialiasing"></a>   
## <a name="y-direction-antialiasing"></a>Směr Y – antialiasing  
 Dalším vylepšením technologie ClearType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] v nástroji je anti-aliasing pro směr y. Technologie ClearType v GDI bez vyhlazení proti směru y nabízí lepší rozlišení na ose x, ale ne na ose y. Na horních a dolních obrazovkách bez podkřivek se zubaté okraje odvolávat od jejich čitelnosti.  
  
 Následující příklad ukazuje účinek, který nemá žádné směrové antialiasing y. V takovém případě jsou zubaté okraje na horní a dolní straně písmen zjevné.  
  
 ![Text s zubatými hranami na] neomezených křivkách (./media/wcpsdk-mmgraphics-text-cleartype-overview-03.png "wcpsdk_mmgraphics_text_cleartype_overview_03")  
Text s zubatými hranami na neomezených křivkách  
  
 Technologie ClearType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] v systému poskytuje antialiasing na úrovni směr y, aby se vyplynuly zubaté hrany. To je obzvláště důležité pro zlepšení čitelnosti východoasijských jazyků, kde má znakové symboly skoro stejné množství vodorovné a svislé překrytí.  
  
 Následující příklad ukazuje účinek y-Direction antialiasing. V tomto případě se v horní a dolní části písmen zobrazuje hladká křivka.  
  
 ![Text with ClearType y&#45;direction anti&#45;aliasing](./media/wcpsdk-mmgraphics-text-cleartype-overview-04.png "wcpsdk_mmgraphics_text_cleartype_overview_04")  
Text pomocí technologie ClearType y-Direction antialiasing  
  
<a name="hardware_acceleration"></a>   
## <a name="hardware-acceleration"></a>Hardwarová akcelerace  
 Technologie ClearType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] v systému může využít hardwarovou akceleraci pro lepší výkon a snížení zatížení procesoru a systémových požadavků na paměť. Pomocí funkce pixel shadery a grafické paměti na kartě grafiky poskytuje technologie ClearType rychlejší vykreslování textu, zejména při použití animace.  
  
 Technologie ClearType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] v nástroji neupravuje nastavení technologie ClearType v rámci systému. Zakázání technologie [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] ClearType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] v sadě antialiasing do režimu stupňů šedi. Kromě toho technologie ClearType v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] neupravuje nastavení [PowerToy tuneru ClearType](https://www.microsoft.com/typography/ClearTypePowerToy.mspx).  
  
 Jedním z [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] rozhodnutí o návrhu architektury je mít řešení nezávislé na rozlišení lépe podporovat monitory DPI s vyšším rozlišením, které se stávají širším řešením. To má [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] za následek nepodporu vykreslování textu s aliasy nebo rastrových obrázků v některých východoasijských písmech, protože obě rozlišení jsou závislé.  
  
<a name="further_information"></a>   
## <a name="further-information"></a>Další informace  
 [Informace o technologii ClearType](https://www.microsoft.com/typography/ClearTypeInfo.mspx)  
  
 [PowerToy tuneru ClearType](https://www.microsoft.com/typography/ClearTypePowerToy.mspx)  
  
## <a name="see-also"></a>Viz také:

- [Nastavení registru ClearType](cleartype-registry-settings.md)
