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
ms.openlocfilehash: a78c84e82ac8507ad40cf3a9fdb44d58858a38d2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713212"
---
# <a name="types-of-bitmaps"></a>Typy rastrových obrázků
Rastrový obrázek je pole bitů, které určují barvu každého obrazového bodu obdélníkové pole v pixelech. Počet bitů věnovaný jednotlivých obrazových bodů určuje počet barev, které lze přiřadit k obrazového bodu. Například pokud každý pixel, je reprezentována 4 bitů, daný pixelů může se mu přiřadit jednu z 16 různé barvy (2 ^ 4 = 16). Následující tabulka ukazuje několik příkladů počet barev, které lze přiřadit k pixelu vyjádřena daný počet bitů.  
  
|Počet bitů na pixel|Počet barev, které je možné přiřadit na pixel|  
|--------------------|------------------------------------------------------|  
|1|2^1 = 2|  
|2|2^2 = 4|  
|4|2^4 = 16|  
|8|2^8 = 256|  
|16|2^16 = 65,536|  
|24|2^24 = 16,777,216|  
  
 Soubory disku, které obvykle ukládají rastrové obrázky obsahují jeden nebo více bloků s informacemi, které obsahují informace, jako je počet bitů na pixel, počet pixelů na každém řádku a počet řádků v poli. Tento soubor může obsahovat také tabulky barev (říká se jim paletu barev). Tabulky barev mapuje čísla rastrového obrázku nastaven na určitých barev. Následující obrázek znázorňuje zvětšeným image spolu s jeho tabulky rastrového obrázku a barvu. Každý pixel je reprezentována číslo 4 bitů, tedy 2 ^ 4 = 16 barev v tabulce barev. Každá barva v tabulce je reprezentována 24-bit číslo: 8 bitů pro red, 8 bitů pro zelenou a 8 bitů pro modrou. Číslo se zobrazuje ve formuláři šestnáctkové (základní 16): A = 10, B = 11, C = 12, D = 13, E = 14, F = 15.  
  
 ![Bitmap sample](./media/aboutgdip03-art01.gif "AboutGdip03_Art01")  
  
 Podívejte se na pixel na řádku 3 sloupci 5 bitové kopie. Odpovídající číslo rastrového obrázku nastaven je 1. Tabulky barev manažerech, že 1 představuje červenou barvu, je pixel je red. Jsou všechny položky v horním řádku rastrového obrázku 3. Tabulky barev víme, že 3 představuje modrá, tak, aby byly všechny pixely obrázku do horního řádku modrá.  
  
> [!NOTE]
>  Některé rastrové obrázky jsou uloženy ve formátu zdola nahoru. čísla v prvním řádku rastrového obrázku odpovídají pixelů v dolním řádku bitové kopie.  
  
 Rastrový obrázek, který ukládá indexy v tabulce barev je volána indexovat palety rastrový obrázek. Některé rastrové obrázky nepotřebujete tabulky barev. Například pokud rastrový obrázek používá 24 bitů na pixel, tento rastrový obrázek uložit barvy sami místo indexy v tabulce barev. Následující obrázek znázorňuje rastrový obrázek, který ukládá přímo barvy (24 bitů na pixel) namísto tabulky barev. Tento obrázek také ukazuje zvětšeným zobrazením příslušné bitové kopie. Rastrového obrázku nastaven FFFFFF představuje white, FF0000 představuje červená, 00FF00 představuje zelené a 0000FF představuje modrou.  
  
 ![Bitmap sample](./media/aboutgdip03-art02.gif "AboutGdip03_Art02")  
  
## <a name="graphics-file-formats"></a>Formáty souborů grafiky  
 Existuje mnoho standardní formáty pro ukládání bitmap ve soubory na disku. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] podporuje grafiky souboru formáty popsané v následujících odstavcích.  
  
### <a name="bmp"></a>BMP  
 BMP je standardní formát, který se používá k ukládání imagí nezávislých na zařízení a nezávisle na aplikaci ve Windows. Počet bitů na pixel (1, 4, 8, 15, 24, 32 nebo 64) pro daný soubor BMP je zadat v hlavičce souboru. Soubory BMP s 24 bitů na pixel jsou běžné. Soubory BMP nejsou obvykle komprimované a proto se dobře nehodí pro přenos přes Internet.  
  
### <a name="graphics-interchange-format-gif"></a>GIF (Graphics Interchange Format)  
 GIF je běžný formát pro Image, které se zobrazují na webových stránkách. GIF fungovat dobře pro kreslení čáry, obrázky bloky plnou barvu a obrázky s sharp hranice mezi barvami. GIF jsou komprimované, ale žádné informace o je ztraceno v procesu komprese. dekomprimovaný image je přesně stejný jako původní. Jednu barvu ve formátu GIF lze označit jako transparentní, tak, aby image bude mít barvu pozadí jakékoli webové stránky, která se zobrazí. Posloupnost obrázků GIF mohou být uloženy v jednom souboru a vytvoří animovaný obrázek GIF. GIF ukládat maximálně 8 bitů na pixel, takže jsou omezené na 256 barev.  
  
### <a name="joint-photographic-experts-group-jpeg"></a>Joint Photographic Experts Group (JPEG)  
 JPEG je schéma komprese, který funguje dobře pro fyzické scény například prohledaná fotografie. Ke ztrátě některých informací v procesu komprese, ale často je ztráta nepostřehnutelný z pohledu uživatele. JPEG ukládání 24 bitů na pixel, takže jsou schopná zobrazit více než 16 milionů barvy. JPEG nepodporují průhlednost nebo animace.  
  
 Úroveň komprese obrázků JPEG je možné konfigurovat, ale vyšší úrovně komprese (menší soubory) způsobit ztrátu Další informace. 20:1 kompresního poměru často výsledný obraz, který hledá těžko odlišili od původního z pohledu uživatele. Následující obrázek znázorňuje obrázku Bpm na obrázek a dvě obrázků JPEG, které byly z tohoto obrázku Bpm na obrázek komprimované. První JPEG má kompresní poměr 4:1 a druhý JPEG kompresní poměr přibližně 8:1.  
  
 ![Ukázky FileType](./media/aboutgdip03-art03.gif "AboutGdip03_Art03")  
  
 Komprese JPEG nepodporuje fungovat dobře pro kreslení čáry, bloky plnou barvou a ostrých hranice. Následující obrázek znázorňuje BMP spolu s dvěma JPEG a formátu GIF. JPEG a GIF byly komprimované z BMP. Kompresní poměr je 4:1 pro GIF, 4:1 pro menší JPEG a 8:3 pro větší JPEG. Všimněte si, že GIF udržuje sharp hranice podél řádky, ale JPEG mají tendenci rozostření hranice.  
  
 ![Filetypes](./media/aboutgdip03-art03a.gif "AboutGdip03_Art03A")  
  
 JPEG je schéma komprese, formát souboru. JPEG souboru Interchange Format (JFIF) formát souboru je obvykle používají pro ukládání a přenos bitové kopie, které komprimované podle schématu JPEG. Soubory JFIF zobrazeného ve webových prohlížečích používají příponu JPG.  
  
### <a name="exchangeable-image-file-exif"></a>Formát Exchangeable Image File (EXIF)  
 EXIF je formát souborů používaný pro fotografie nezachytává digitální fotoaparáty. Soubor s příponou EXIF obsahuje bitovou kopii, která je komprimován podle specifikace formátu JPEG. Soubor s příponou EXIF také obsahuje informace o fotografie (datum pořízení, příčky rychlost, zkrátit dobu expozice a tak dále) a informace o fotoaparátu (výrobce, model a tak dále).  
  
### <a name="portable-network-graphics-png"></a>PNG (Portable Network Graphics)  
 Formát PNG uchovává mnohé z výhod formátu GIF, ale navíc poskytuje funkce nad rámec těch, které ve formátu GIF. Stejně jako soubory ve formátu GIF PNG soubory komprimování bez ztráty informací. Soubory PNG můžete uložit barvy s 8, 24 nebo 48 bitů na pixel a stupňů šedi s 1, 2, 4, 8 nebo 16 bitů na pixel. Soubory GIF naproti tomu slouží pouze 1, 2, 4 nebo 8 bitů na pixel. Soubor PNG lze také ukládat alfa hodnotu pro každý pixel, který určuje, do jaké míry, do které jsou prolnuty barva obrazového bodu barvou pozadí.  
  
 PNG zlepšuje na GIF v jeho schopnost postupně zobrazte obrázek (to znamená, zobrazíte vyšší a vyšší rovin útoku obrázku jako jeho doručení přes síťové připojení). Soubory PNG může obsahovat informace o opravě gama korekce a barvu tak, že Image lze přesně vykreslit na celé řadě zařízení s displejem.  
  
### <a name="tag-image-file-format-tiff"></a>Formát TIFF (TIFF)  
 TIFF je flexibilní a rozšiřitelná formát, který podporuje širokou škálu platformy a zpracování obrazu aplikace. Soubory TIFF můžete ukládání imagí s využitím libovolného počtu bitů na pixel a můžete použít různé algoritmy komprese. Několik imagí mohou být uloženy v souboru ve formátu TIFF jeden, více stránek. Informace související s bitovou kopii (Zkontrolujte skener, hostitelského počítače, typ komprese, orientace, ukázky každý pixel a tak dále) lze uložené v souboru a uspořádat pomocí značek. Formát TIFF je možné rozšířit podle potřeby tak, že schválení a přidání nové značky.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Drawing.Image?displayProperty=nameWithType>
- <xref:System.Drawing.Bitmap?displayProperty=nameWithType>
- <xref:System.Drawing.Imaging.PixelFormat?displayProperty=nameWithType>
- [Obrázky, rastrové obrázky a metasoubory](images-bitmaps-and-metafiles.md)
- [Práce s obrázky, rastrovými obrázky, ikonami a metasoubory](working-with-images-bitmaps-icons-and-metafiles.md)
