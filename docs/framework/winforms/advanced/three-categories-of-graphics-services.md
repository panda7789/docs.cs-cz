---
title: Tři kategorie grafických služeb
ms.date: 03/30/2017
helpviewer_keywords:
- imaging
- graphics [Windows Forms], categories
- 2-D vector graphics
- vector graphics
- typography
ms.assetid: 068c0ef3-f6ee-4d58-a7b6-eb2531ead408
ms.openlocfilehash: 5621a2c0bba2e922e62006feba9ca0381181c780
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="three-categories-of-graphics-services"></a>Tři kategorie grafických služeb
Nabídky grafiky ve Windows Forms lze rozdělit do těchto tří široký kategorií:  
  
-   Dvourozměrná (2-D) vektorová grafika  
  
-   Vytvoření bitové kopie  
  
-   Typografie  
  
## <a name="2-d-vector-graphics"></a>2D vektorová grafika  
 Dvourozměrná vektorová grafika jsou primitiv; například čar, křivek a obrázky; která jsou určena sady bodů na souřadnicový systém. Například přímku je zadána jeho dva koncové body a obdélníku je zadána bod poskytnutí umístění jeho levého horního rohu a pár čísel, která poskytuje svou šířku a výšku. Jednoduché cesta je určena pole bodů, která jsou připojena linkami přímých. Bézierovy křivky je sofistikované křivky určeného čtyři kontrolní body.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] poskytuje třídy a struktury, které obsahují informace o primitiv sami, třídy, které obsahují informace o tom, jak se budou vykreslovat primitivní elementy a třídy, které skutečně provést kreslení. Například <xref:System.Drawing.Rectangle> struktura ukládá umístění a velikost obdélníku; <xref:System.Drawing.Pen> třída ukládá informace o řádku barvu, šířku čáry a styl čáry; a <xref:System.Drawing.Graphics> třída obsahuje metody pro kreslení obdélníků řádky, cesty, a Další údaje. Existují také některé <xref:System.Drawing.Brush> třídy, které obsahují informace o tom, zavře obrázky a cesty bude vyplněn barvy nebo vzory.  
  
 Můžete zaznamenat bitovou kopii vektoru, což je posloupnost grafiky příkazy, metasoubory. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] poskytuje <xref:System.Drawing.Imaging.Metafile> třídu pro zaznamenání, zobrazení a uložení metasoubory. Pomocí <xref:System.Drawing.Imaging.MetafileHeader> a <xref:System.Drawing.Imaging.MetaHeader> třídy, si můžete prohlédnout data uložená v hlavičce metafile.  
  
## <a name="imaging"></a>Vytvoření bitové kopie  
 Některé typy obrázků se obtížně nebo dokonce znemožňují zobrazíte pomocí technik vektorová grafika. Obrázky na tlačítka panelu nástrojů a obrázky, které se zobrazují jako ikony jsou například obtížné určit jako kolekce čar a křivek. S vysokým rozlišením digitální fotografie frekventované baseballové stadium je ještě obtížnější vytvoření pomocí vektoru techniky. Bitové kopie tohoto typu jsou uloženy jako rastrové obrázky, které jsou pole čísla, která představují barvy jednotlivých tečky na obrazovce. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] poskytuje <xref:System.Drawing.Bitmap> třídu pro zobrazení, manipulace a ukládání bitmap.  
  
## <a name="typography"></a>Typografie  
 Typografie je zobrazení textu v různých písma, velikosti a stylů. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] poskytuje rozsáhlou podporu pro tento složitý úkol. Jeden z nových funkcí v [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] subpixel vyhlazení, která umožňuje text vykreslení v displeje hladší vzhled.  
  
 Kromě toho Windows Forms nabízí možnost kreslení textu pomocí [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] možnosti v jeho <xref:System.Windows.Forms.TextRenderer> třídy.  
  
## <a name="see-also"></a>Viz také  
 [Přehled grafiky](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 [Informace o spravovaném kódu GDI+](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 [Použití spravovaných grafických tříd](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)
