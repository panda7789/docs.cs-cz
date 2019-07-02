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
ms.openlocfilehash: a69fa7a1ccad353c879731de05dc47f0d6ae8795
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505229"
---
# <a name="three-categories-of-graphics-services"></a>Tři kategorie grafických služeb
Nabídky grafiky ve Windows Forms spadají do následujících tří hlavních kategorií:  
  
- Dvourozměrné (2-D) vektorové grafiky  
  
- Vytvoření bitové kopie  
  
- Typografie  
  
## <a name="2-d-vector-graphics"></a>2D vektorová grafika  
 Primitiv; jsou dvojrozměrná vektorová grafika například čáry, křivky a údaje. která jsou určena pomocí sady bodů na systém souřadnic. Například rovné čáry je určená jeho dva koncové body a je určen bod poskytuje místo jeho levého horního rohu a dvojici čísel poskytuje svou šířku a výšku obdélníku. Jednoduché cesta je určena pole body, které jsou spojeny čarami přímo. Bézierovy křivky je sofistikované křivky určené čtyři kontrolní body.  
  
 Rozhraní GDI + poskytuje třídy a struktury, které ukládají informace o primitiv v samotné, třídy, které ukládají informace o tom, jak bude vykreslen primitiv a třídy, které se dělají výkresu. Například <xref:System.Drawing.Rectangle> struktura ukládá umístění a velikost obdélník; <xref:System.Drawing.Pen> třídy ukládá informace o barvu čáry, šířku čáry a styl čáry; a <xref:System.Drawing.Graphics> třída obsahuje metody pro kreslení čáry, obdélníky, cesty, a Další údaje. Existuje také několik <xref:System.Drawing.Brush> uzavřeny třídy, které ukládají informace o tom, obrázky a cesty bude vyplněn barev nebo vzorů.  
  
 Můžete zaznamenat bitovou kopii vektoru, což je sekvence příkazů grafiky, do metasouboru. Poskytuje rozhraní GDI + <xref:System.Drawing.Imaging.Metafile> třídy pro zaznamenání, zobrazení a uložení metasoubory. S <xref:System.Drawing.Imaging.MetafileHeader> a <xref:System.Drawing.Imaging.MetaHeader> třídy, můžete si prohlédnout data uložená v hlavičce metasouboru.  
  
## <a name="imaging"></a>Vytvoření bitové kopie  
 Některé typy obrázků je obtížné nebo nemožné zobrazit pomocí technik vektorovou grafiku. Například je obtížné určit jako kolekce čar a křivek obrázků na tlačítka na panelu nástrojů a obrázky, které se zobrazují jako ikony. Ve vysokém rozlišení digitální fotografie přeplněném baseballu stadionem je dál složitější vytvořit s technikami vektoru. Image tohoto typu se ukládají jako rastrové obrázky, což jsou pole čísla, která představují barvy jednotlivé tečky na obrazovce. Poskytuje rozhraní GDI + <xref:System.Drawing.Bitmap> třídu pro zobrazení, zpracování a ukládání bitmap.  
  
## <a name="typography"></a>Typografie  
 Typografie je zobrazení textu v různých písma, velikosti a styly. Rozhraní GDI + poskytuje rozsáhlou podporu pro tento složitý úkol. Jedním z nových funkcí v rozhraní GDI + je vyhlazení subpixel, která poskytuje textu vykresleného v displeje hladší vzhled.  
  
 Kromě toho také nabízí možnost kreslení textu pomocí GDI možnosti ve Windows Forms jeho <xref:System.Windows.Forms.TextRenderer> třídy.  
  
## <a name="see-also"></a>Viz také:

- [Přehled grafiky](graphics-overview-windows-forms.md)
- [Informace o spravovaném kódu GDI+](about-gdi-managed-code.md)
- [Použití spravovaných grafických tříd](using-managed-graphics-classes.md)
