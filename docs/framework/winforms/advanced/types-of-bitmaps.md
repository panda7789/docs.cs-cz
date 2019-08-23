---
title: Typy rastrových obrázků
ms.date: 03/30/2017
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
ms.openlocfilehash: 2243c9ce2d8ba741143d301c38e8b88d7b196c98
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914825"
---
# <a name="types-of-bitmaps"></a>Typy rastrových obrázků
Rastrový obrázek je pole bitů, které určují barvu jednotlivých pixelů v obdélníkovém poli pixelů. Počet bitů, které jsou pro jednotlivé pixely vyčleněny, určuje počet barev, které lze přiřadit k danému obrazovému bodu. Například pokud je každý pixel reprezentován 4 bity, pak je možné přiřadit k určitému pixelu jednu z 16 různých barev (2 ^ 4 = 16). Následující tabulka ukazuje několik příkladů počtu barev, které lze přiřadit k pixelu reprezentovanému daným počtem bitů.  
  
|Bitů na pixel|Počet barev, které lze přiřadit k obrazovému bodu|  
|--------------------|------------------------------------------------------|  
|1|2^1 = 2|  
|2|2^2 = 4|  
|4|2^4 = 16|  
|8|2^8 = 256|  
|16|2^16 = 65,536|  
|24|2^24 = 16,777,216|  
  
 Soubory na disku, které ukládají rastry, obvykle obsahují jeden nebo více bloků s informacemi, které ukládají informace, jako je počet bitů na pixel, počet pixelů v každém řádku a počet řádků v poli. Takový soubor může obsahovat také tabulku barev (někdy označovanou jako paleta barev). Tabulka barev mapuje čísla v rastrovém obrázku na konkrétní barvy. Následující obrázek znázorňuje zvětšený obrázek spolu s jeho rastrovou a barevnou tabulkou. Každý pixel je reprezentován číslem 4 bitů, takže v tabulce barev je 2 ^ 4 = 16 barev. Jednotlivé barvy v tabulce jsou reprezentovány pomocí 16bitového čísla: 8 bitů pro červenou, 8 bitů pro zelenou a 8 bitů pro modrou. Čísla jsou uvedena v šestnáctkovém formátu (základní 16): A = 10, B = 11, C = 12, D = 13, E = 14, F = 15.  
  
 ![Ukázka rastrového obrázku](./media/aboutgdip03-art01.gif "AboutGdip03_Art01")  
  
 Podívejte se na pixel v řádku 3, ve sloupci 5 obrázku. Odpovídající číslo v rastrovém obrázku je 1. Tabulka Color oznamuje, že 1 představuje červenou barvu, aby pixel byl červený. Všechny položky v horním řádku rastrového obrázku jsou 3. Tabulka Color oznamuje, že 3 představuje modrou, takže všechny pixely v horním řádku obrázku jsou modré.  
  
> [!NOTE]
> Některé bitmapy jsou uloženy ve formátu zdola nahoru. čísla v prvním řádku rastrového obrázku odpovídají pixelům v dolním řádku obrázku.  
  
 Rastrový obrázek, který ukládá indexy do tabulky barev, se nazývá rastrový obrázek s indexovaný paletou. Některé rastrové obrázky nejsou nutné pro tabulku barev. Například pokud rastr používá 24 bitů na pixel, může tato bitmapa ukládat samotné barvy místo indexů do tabulky barev. Následující ilustrace znázorňuje rastrový obrázek, který přímo ukládá barvy (24 bitů na pixel) místo použití tabulky barev. Ilustrace znázorňuje také zvětšený pohled na odpovídající obrázek. V bitmapě představuje FFFFFF bílou, FF0000 představuje Red, 00FF00 představuje zelenou a 0000FF představuje modrou.  
  
 ![Ukázka rastrového obrázku](./media/aboutgdip03-art02.gif "AboutGdip03_Art02")  
  
## <a name="graphics-file-formats"></a>Formáty grafických souborů  
 Existuje mnoho standardních formátů pro ukládání rastrových obrázků do souborů na disku. GDI+ podporuje formáty grafických souborů, které jsou popsány v následujících odstavcích.  
  
### <a name="bmp"></a>BMP  
 BMP je standardní formát používaný systémem Windows k ukládání imagí nezávislých na zařízení a aplikací nezávislých na aplikacích. V hlavičce souboru je určen počet bitů na pixel (1, 4, 8, 15, 24, 32 nebo 64) pro daný soubor BMP. Soubory BMP s 24 bity na pixel jsou běžné. Soubory BMP nejsou obvykle komprimovány, a proto nejsou vhodné pro přenos přes Internet.  
  
### <a name="graphics-interchange-format-gif"></a>GIF (Graphics Interchange Format)  
 GIF je běžný formát pro obrázky, které se zobrazují na webových stránkách. Soubory GIF fungují dobře pro čárové kresby, obrázky s bloky plné barvy a obrázky s ostrými hranicemi mezi barvami. Soubory GIF jsou komprimovány, ale v kompresním procesu nejsou ztraceny žádné informace; dekomprimovaný obrázek je přesně stejný jako původní. Jedna barva ve formátu GIF může být označena jako průhledná, takže obrázek bude mít barvu pozadí jakékoli webové stránky, která je zobrazí. K vytvoření animovaného obrázku ve formátu GIF lze v jednom souboru uložit sekvenci obrázků GIF. Úložiště GIF má maximálně 8 bitů na pixel, takže jsou omezeny na 256 barev.  
  
### <a name="joint-photographic-experts-group-jpeg"></a>Společný fotografický Experts Group (JPEG)  
 JPEG je kompresní schéma, které funguje dobře pro přirozené scény, jako jsou naskenované fotografie. Některé informace jsou ztraceny v kompresním procesu, ale často je ztrátou lidského oka. Soubory JPEG ukládají 24 bitů na pixel, takže jsou schopny zobrazit více než 16 000 000 barev. Soubory JPEG nepodporují transparentnost ani animace.  
  
 Úroveň komprese v obrazech JPEG je konfigurovatelná, ale vyšší úrovně komprese (menší soubory) vede k větší ztrátě informací. Kompresní poměr 20:1 často vytváří obrázek, který člověk v lidském oka obtížně rozlišuje od originálu. Následující ilustrace znázorňuje obrázek BMP a dva obrázky JPEG, které byly zkomprimovány z tohoto obrázku BMP. První JPEG má kompresní poměr 4:1 a druhý JPEG má kompresní poměr přibližně 8:1.  
  
 ![Ukázky pro typ] souboru (./media/aboutgdip03-art03.gif "AboutGdip03_Art03")  
  
 Komprese JPEG nefunguje dobře pro čárové kresby, bloky plných barev a ostré hranice. Následující ilustrace znázorňuje BMP spolu se dvěma JPEG a GIF. Soubory JPEG a GIF byly komprimovány z BMP. Kompresní poměr je 4:1 pro GIF, 4:1 pro menší formát JPEG a 8:3 pro větší formát JPEG. Všimněte si, že GIF udržuje ostré hranice podél čar, ale JPEG obvykle rozostří hranice.  
  
 ![Filetypes](./media/aboutgdip03-art03a.gif "AboutGdip03_Art03A")  
  
 JPEG je kompresní schéma, nikoli formát souboru. Formát JPEG File Interchange Format (JFIF) je formát souboru, který se běžně používá pro ukládání a přenos imagí komprimovaných podle schématu JPEG. Soubory JFIF zobrazované webovými prohlížeči používají příponu. jpg.  
  
### <a name="exchangeable-image-file-exif"></a>Soubor s navzájemnou imagí (EXIF)  
 EXIF je formát souboru, který se používá pro fotografie zachycené digitálními fotoaparáty. Soubor EXIF obsahuje obrázek, který se komprimuje podle specifikace JPEG. Soubor EXIF obsahuje také informace o fotografii (datum pořízení, rychlost expozice, doba působení atd.) a informace o kameře (výrobce, modelu atd.).  
  
### <a name="portable-network-graphics-png"></a>PNG (Portable Network Graphics)  
 Formát PNG uchovává spoustu výhod formátu GIF, ale poskytuje i možnosti nad rámec formátu GIF. Podobně jako soubory GIF se soubory PNG komprimují bez ztráty informací. Soubory PNG mohou ukládat barvy s 8, 24 nebo 48 bity na pixel a stupně šedi s 1, 2, 4, 8 nebo 16 bity na pixel. Naproti tomu soubory GIF můžou používat jenom 1, 2, 4 nebo 8 bitů na pixel. Soubor PNG také může uložit hodnotu alfa pro každý pixel, která určuje, do jaké míry je barva tohoto pixelu smíchána s barvou pozadí.  
  
 PNG vylepšuje ve formátu GIF, aby postupně zobrazila obrázek (což znamená, že se má zobrazit lepší a lepší Přibližná aproximace obrázku při doručení přes síťové připojení). Soubory PNG mohou obsahovat informace o korekci hodnoty gamma a korekci barev, aby bylo možné obrázky přesně vykreslovat na různých zobrazovacích zařízeních.  
  
### <a name="tag-image-file-format-tiff"></a>TIFF (tag Image File Format)  
 TIFF je flexibilní a přizpůsobitelný formát, který podporuje širokou škálu platforem a aplikací pro zpracování obrázků. Soubory TIFF můžou ukládat obrázky s libovolným počtem bitů na pixel a můžou využívat nejrůznější algoritmy komprese. Několik imagí může být uloženo v jednom souboru TIFF s více stránkami. Informace související s imagí (provedený skener, hostitelský počítač, typ komprese, orientace, vzorky na pixel atd.) mohou být uloženy v souboru a uspořádány pomocí značek. Formát TIFF lze podle potřeby rozšířit o schválení a přidání nových značek.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Image?displayProperty=nameWithType>
- <xref:System.Drawing.Bitmap?displayProperty=nameWithType>
- <xref:System.Drawing.Imaging.PixelFormat?displayProperty=nameWithType>
- [Obrázky, rastrové obrázky a metasoubory](images-bitmaps-and-metafiles.md)
- [Práce s obrázky, rastrovými obrázky, ikonami a metasoubory](working-with-images-bitmaps-icons-and-metafiles.md)
