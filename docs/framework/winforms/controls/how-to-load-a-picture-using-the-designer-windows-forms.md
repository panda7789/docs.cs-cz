---
title: 'Postupy: Načtení obrázku pomocí návrháře (Windows Forms)'
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: febe1fc616bd1405e699c03fa673814a45976769
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723068"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a>Postupy: Načtení obrázku pomocí návrháře (Windows Forms)
Pomocí Windows Forms <xref:System.Windows.Forms.PictureBox> ovládacího prvku, lze načíst a zobrazit obrázek na formulář v době návrhu tak, že nastavíte <xref:System.Windows.Forms.PictureBox.Image%2A> vlastnost platný obrázek. Následující tabulka uvádí typy souborů přijatelné.  
  
|Typ|Přípona názvu souboru|  
|----------|-------------------------|  
|Rastrový obrázek|BMP|  
|Ikona|.ico|  
|GIF|GIF|  
|Metasoubor|.wmf|  
|JPEG|.jpg|  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-display-a-picture-at-design-time"></a>Chcete-li zobrazit obrázek v době návrhu  
  
1.  Vykreslení <xref:System.Windows.Forms.PictureBox> ovládací prvek na formuláři.  
  
2.  V okně Vlastnosti vyberte <xref:System.Windows.Forms.PictureBox.Image%2A> vlastnost a potom klikněte na tlačítko se třemi tečkami zobrazíte **otevřít** dialogové okno.  
  
3.  Pokud chcete pro určitý typ souboru (například soubory GIF), vyberte ho **soubory typu** pole.  
  
4.  Vyberte soubor, který chcete zobrazit.  
  
### <a name="to-clear-the-picture-at-design-time"></a>Vymazat obrázek v době návrhu  
  
1.  Na **vlastnosti** okna, vyberte <xref:System.Windows.Forms.PictureBox.Image%2A> vlastnosti a kliknutím pravým tlačítkem na malé miniaturu, která se zobrazí nalevo od názvu objektu bitové kopie. Zvolte **resetování**.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.PictureBox>
- [Přehled ovládacího prvku PictureBox](picturebox-control-overview-windows-forms.md)
- [Postupy: Změna velikosti či umístění obrázku za běhu](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [Postupy: Nastavení obrázků za běhu](how-to-set-pictures-at-run-time-windows-forms.md)
- [Ovládací prvek PictureBox](picturebox-control-windows-forms.md)
