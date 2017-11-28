---
title: "Typy rastrových obrázků"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- jpeg files
- TIFF files
- gif files
- Graphics Interchange Format
- Joint Photographic Experts Group
- .jpeg files
- .gif files
- graphics [Windows Forms], file formats
- images [Windows Forms], file formats
- Portable Network Graphics
- .bmp files
- EXIF file format
- PNG files
- pictures [Windows Forms], file formats
- Tag Image File Format
- bitmaps [Windows Forms], file format
- Exchangeable Image File
ms.assetid: 6be085a2-2c13-47c8-b80a-c18b32777d8d
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b33e710e7f57e1a84372dc556d904e32584a75ea
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="types-of-bitmaps"></a>Typy rastrových obrázků
Rastrový obrázek je pole bitů, které určuje barvu každého obrazového bodu v obdélníková pole pixelů. Počet bitů věnované na jednotlivé pixelů určuje počet barev, které lze přiřadit k této pixelů. Například pokud každý pixelů je reprezentována 4 bits, pak dané pixelů lze přiřadit jedné z 16 různých barev (2 ^ 4 = 16). Následující tabulka uvádí několik příkladů počet barev, které mohou být přiřazeny pixelu reprezentované zadaný počet bitů.  
  
|Bitů na pixel|Počet barev, které lze přiřadit pixelu|  
|--------------------|------------------------------------------------------|  
|1|2^1 = 2|  
|2|2^2 = 4|  
|4|2^4 = 16|  
|8|2^8 = 256|  
|16|2^16 = 65,536|  
|24|2^24 = 16,777,216|  
  
 Soubory disku, které obvykle ukládají bitmap obsahovat jeden nebo více informačních bloků, které ukládají data jako počet bitů na pixel, počet pixelů v každém řádku a počet řádků v poli. Takový soubor může obsahovat také tabulce barev (někdy nazývané palety barev). Tabulky barev mapy čísla v souboru bitové mapy pro konkrétní barev. Následující obrázek znázorňuje image zvětšeným společně s jeho rastrového obrázku a barvy tabulky. Každý pixelů je reprezentována číslo 4-bit, proto nejsou 2 ^ 4 = 16 barvy v tabulce barev. Jednotlivé barvy v tabulce představuje číslo 24bitový: 8 bitů pro red, 8 bitů pro zelená a 8 bitů pro blue. Čísla, která se zobrazují v podobě šestnáctkové (základ 16): A = 10, B = 11, C = 12, D = 13, E = 14, F = 15.  
  
 ![Rastrový obrázek ukázkové](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art01.gif "AboutGdip03_Art01")  
  
 Podívejte se na pixel v řádku 3, sloupec 5 bitové kopie. Příslušné číslo v souboru bitové mapy je 1. Tabulky barev nám oznamuje, že 1 představuje červenou barvu tak, aby pixel red. Všechny položky v horním řádku bitmapy jsou 3. Tabulky barev nám oznamuje, že 3 představuje blue, takže všechny pixely horní řádek bitové kopie jsou modré.  
  
> [!NOTE]
>  Některé rastrové obrázky se ukládají ve formátu zdola nahoru. čísla na prvním řádku bitmapy odpovídají pixelů v dolním řádku bitové kopie.  
  
 Rastrový obrázek, který ukládá indexy v tabulce barev se nazývá Indexované palety rastrový obrázek. Některé bitmap mít nemusí tabulce barev. Například pokud rastrový obrázek používá 24 bitů na pixel, že rastrový obrázek můžete uložit indexy barvy sami spíše než do tabulky barev. Následující obrázek znázorňuje rastrového obrázku, který ukládá přímo barvy (24 bitů na pixel) místo pomocí tabulky barev. Na obrázku také ukazuje zvětšeným zobrazením odpovídající bitové kopie. V souboru bitové mapy FFFFFF představuje prázdné, FF0000 představuje red, 00FF00 představuje zelená a 0000FF představuje blue.  
  
 ![Rastrový obrázek ukázkové](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art02.gif "AboutGdip03_Art02")  
  
## <a name="graphics-file-formats"></a>Formáty souborů grafiky  
 Existuje mnoho standardní formáty pro ukládání bitmap ve souborů na disku. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]podporuje grafiky souboru formáty popsané v následujících odstavcích.  
  
### <a name="bmp"></a>BMP  
 BMP je standardní formát používaná systémem Windows pro uložení bitové kopie nezávislé na zařízení a nezávisle na aplikaci. V záhlaví souboru je zadaný počet bitů na pixel (1, 4, 8, 15, 24, 32 nebo 64) pro daný soubor BMP. Soubory BMP s 24 bitů na pixel jsou běžné. Soubory BMP nejsou obvykle komprimované a proto nejsou dobře hodí pro přenos přes Internet.  
  
### <a name="graphics-interchange-format-gif"></a>GIF (Graphics Interchange Format)  
 GIF je běžný formát pro bitové kopie, které se zobrazují na webových stránkách. GIF fungovat dobře u kresby na řádku, s bloky plnou barvou obrázky a obrázky s sharp hranice mezi barvy. Jsou komprimované soubory GIF, ale žádné informace budou ztraceny v procesu komprese. dekomprimovaných image je přesně stejný jako původní. Jednu barvu ve formátu GIF může být označeno jako transparentní, tak, aby měla barvu pozadí webové stránky, která se zobrazuje bitovou kopii. Posloupnost obrázky GIF mohou být uloženy ve formuláři animovaný GIF jednoho souboru. GIF uložení maximálně 8 bitů na pixel, takže jsou omezeny na 256 barev.  
  
### <a name="joint-photographic-experts-group-jpeg"></a>Joint Photographic Experts Group (JPEG)  
 JPEG je schéma komprese, který funguje dobře pro přirozené scény například skenované fotografie. Ke ztrátě některých informací v procesu komprese, ale často je nepostřehnutelný pro lidské oko ztrátu. JPEG ukládat 24 bitů na pixel, takže jsou k schopná zobrazit více než 16 miliónů barev. JPEG nepodporují průhlednost nebo animace.  
  
 Je možné konfigurovat úroveň komprese v JPEG – obrázky, ale vyšší úrovně komprese (menší soubory) dojít ke ztrátě více informací. 20:1 kompresní poměr často vytvoří obrázek, který vyhledá lidské oko obtížné odlišit od původní. Následující obrázek znázorňuje obrázku Bpm na obrázek a dvě bitové kopie JPEG, které byly z této bitové kopie BMP komprimovány. První JPEG má kompresní poměr 4:1 a druhý JPEG kompresní poměr přibližně 8:1.  
  
 ![Typ souboru ukázky](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art03.gif "AboutGdip03_Art03")  
  
 Komprese JPEG nepodporuje fungují dobře u kresby na řádek, bloky plnou barvou a ostré hranice. Následující obrázek znázorňuje BMP spolu se dvěma JPEG a formátu GIF. JPEG a GIF byly komprimované z BMP. Kompresní poměr je 4:1 pro GIF, 4:1 pro menší JPEG a 8:3 pro větší JPEG. Všimněte si, že GIF udržuje sharp hranice podél řádky, ale JPEG zpravidla rozostření hranice.  
  
 ![Typ souborů](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art03a.gif "AboutGdip03_Art03A")  
  
 JPEG je schéma komprese, formát souboru. JPEG File Interchange Format (JFIF) je formát souboru běžně používá pro uložení a přenosu bitové kopie, které byly komprimovány podle schéma JPEG. Soubory JFIF zobrazené webovými prohlížeči použít příponu JPG.  
  
### <a name="exchangeable-image-file-exif"></a>Formát Exchangeable Image File (EXIF)  
 EXIF je formát souborů používaný pro fotografie zachycenou digitální fotoaparáty. Soubor EXIF obsahuje obrázek, který se komprimují podle specifikace JPEG. Soubor EXIF také obsahuje informace o fotografie (datum pořízení, přihrádku rychlosti, ohrožení čas a tak dále) a informace o fotoaparát (výrobce, model a tak dále).  
  
### <a name="portable-network-graphics-png"></a>PNG (Portable Network Graphics)  
 Formát PNG použije mnoho výhod formátu GIF, ale taky nabízí funkce nad rámec těch GIF. Stejně jako soubory GIF jsou komprimované soubory PNG bez ztráty informací. Soubory PNG můžete uložit barvy s 8, 24, nebo 48 bitů na pixel a stupňů šedi s 1, 2, 4, 8 nebo 16 bitů na pixel. Naproti tomu GIF – soubory můžete použít pouze 1, 2, 4 nebo 8 bitů na pixel. Soubor PNG také můžete uložit hodnotu alfa pro každý pixelů, který určuje úroveň, ke kterému je barvu tohoto pixelů smíšení barvou pozadí.  
  
 PNG zlepšuje na GIF ve své schopnosti progresivně zobrazte obrázek (to znamená, zobrazíte lepší a lepší aproximace bitové kopie jak dorazí přes síťové připojení). Soubory PNG může obsahovat informace o korekce gama korekce a barvu, aby bitové kopie mohou být vykresleny přesně na různých zobrazení zařízení.  
  
### <a name="tag-image-file-format-tiff"></a>Formát TIFF (TIFF)  
 Formát TIFF je flexibilní a rozšiřitelná formátu, který podporuje širokou škálu platformy a aplikace zpracování obrázků. Soubory TIFF můžete ukládat obrázky s libovolný počet bitů na pixel a můžete použít různé algoritmy komprese. Několik Image můžete uložené v souboru ve formátu TIFF jeden, více stránek. Informace týkající se bitovou kopii (Zkontrolujte skener, hostitelský počítač, typ komprese, orientaci, ukázky za pixelů a tak dále) můžete uložené v souboru a uspořádané prostřednictvím značky. Formát TIFF lze rozšířit, podle potřeby schválení a přidání nové značky.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.Image?displayProperty=nameWithType>  
 <xref:System.Drawing.Bitmap?displayProperty=nameWithType>  
 <xref:System.Drawing.Imaging.PixelFormat?displayProperty=nameWithType>  
 [Obrázky, rastrové obrázky a metasoubory](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Práce s obrázky, rastrové obrázky, ikony a metasoubory](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
