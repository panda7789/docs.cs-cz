---
title: Tři kategorie grafických služeb
ms.date: 03/30/2017
helpviewer_keywords:
- imaging
- graphics [Windows Forms], categories
- 2D vector graphics
- vector graphics
- typography
ms.assetid: 068c0ef3-f6ee-4d58-a7b6-eb2531ead408
ms.openlocfilehash: fa7391ef0f7170ddb9d9d24aa5a1a03635bf46e0
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291730"
---
# <a name="three-categories-of-graphics-services"></a>Tři kategorie grafických služeb
Grafické nabídky ve Windows Forms spadají do následujících tří širokých kategorií:  
  
- Dvourozměrná (2D) vektorová grafika  
  
- Zobrazovací  
  
- Typografie  
  
## <a name="2d-vector-graphics"></a>2D vektorová grafika  
 Dvourozměrná vektorová grafika, například čáry, křivky a obrázky, jsou primitiva, která jsou určena sadami bodů v souřadnicovém systému. Například přímka je určena dvěma koncovými body a obdélník je určen bodem, který udává umístění levého horního rohu a dvojici čísel udávajících jeho šířku a výšku. Jednoduchá cesta je určena polem bodů, které jsou spojeny rovnými čarami. Bézierova křivka je sofistikovaná křivka určená čtyřmi řídicími body.  
  
 GDI+ poskytuje třídy a struktury, které ukládají informace o samotných primitivech, třídy, které ukládají informace o tom, jak budou primitiva nakreslena, a třídy, které ve skutečnosti provádějí výkres. Struktura například <xref:System.Drawing.Rectangle> ukládá umístění a velikost obdélníku; třída <xref:System.Drawing.Pen> ukládá informace o barvě čáry, šířce čáry a stylu čáry; a <xref:System.Drawing.Graphics> třída má metody pro kreslení čar, obdélníků, cest a dalších obrázků. Existuje také <xref:System.Drawing.Brush> několik tříd, které ukládají informace o tom, jak budou uzavřené obrázky a cesty vyplněny barvami nebo vzory.  
  
 Můžete zaznamenat vektorový obraz, což je posloupnost grafických příkazů, v metasouboru. GDI+ poskytuje <xref:System.Drawing.Imaging.Metafile> třídu pro nahrávání, zobrazování a ukládání metasouborů. Pomocí <xref:System.Drawing.Imaging.MetafileHeader> tříd <xref:System.Drawing.Imaging.MetaHeader> a můžete zkontrolovat data uložená v záhlaví metasouboru.  
  
## <a name="imaging"></a>Zobrazovací  
 Některé druhy obrázků jsou obtížné nebo nemožné zobrazit s technikami vektorové grafiky. Například obrázky na panelu nástrojů tlačítka a obrázky, které se zobrazí jako ikony je obtížné určit jako kolekce čar a křivek. Digitální fotografie přeplněného baseballového stadionu s vysokým rozlišením je ještě obtížnější vytvořit pomocí vektorových technik. Obrazy tohoto typu jsou uloženy jako bitmapy, což jsou pole čísel, která představují barvy jednotlivých tesek na obrazovce. GDI+ poskytuje <xref:System.Drawing.Bitmap> třídu pro zobrazení, manipulaci a ukládání bitmap.  
  
## <a name="typography"></a>Typografie  
 Typografie je zobrazení textu v různých písmech, velikostech a stylech. GDI+ poskytuje rozsáhlou podporu pro tento složitý úkol. Jednou z nových funkcí v GDI+ je subpixelové vyhlazení, které dává textu vykreslenému na lcd obrazovce hladší vzhled.  
  
 Kromě toho Windows Forms nabízí možnost kreslit text s <xref:System.Windows.Forms.TextRenderer> funkcemi GDI ve své třídě.  
  
## <a name="see-also"></a>Viz také

- [Přehled grafiky](graphics-overview-windows-forms.md)
- [Informace o spravovaném kódu GDI+](about-gdi-managed-code.md)
- [Použití spravovaných grafických tříd](using-managed-graphics-classes.md)
