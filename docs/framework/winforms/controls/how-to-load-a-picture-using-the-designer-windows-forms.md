---
title: 'Postupy: Načtení obrázku pomocí Návrháře (Windows Forms)'
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: 5eb85c6f3ca232f8b53ac01d57ee71f73415cf83
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a>Postupy: Načtení obrázku pomocí Návrháře (Windows Forms)
S Windows Forms <xref:System.Windows.Forms.PictureBox> ovládací prvek, můžete načíst a zobrazit obrázek v době návrhu nastavením ve formuláři <xref:System.Windows.Forms.PictureBox.Image%2A> vlastnost, která má platný obrázek. Následující tabulka uvádí typy souborů přijatelný.  
  
|Typ|Přípona názvu souboru|  
|----------|-------------------------|  
|Rastrový obrázek|.bmp|  
|Ikona|.ico|  
|GIF|.GIF|  
|Metafile|.wmf|  
|JPEG|.jpg|  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-a-picture-at-design-time"></a>Chcete-li zobrazit obrázek v době návrhu  
  
1.  Kreslení <xref:System.Windows.Forms.PictureBox> prvek na formuláři.  
  
2.  V okně Vlastnosti, vyberte <xref:System.Windows.Forms.PictureBox.Image%2A> vlastnost a potom klikněte na tlačítko se třemi tečkami zobrazíte **otevřete** dialogové okno.  
  
3.  Pokud hledáte určitý typ souboru (například soubory GIF), vyberte ho **soubory typu** pole.  
  
4.  Vyberte soubor, který chcete zobrazit.  
  
### <a name="to-clear-the-picture-at-design-time"></a>Chcete-li vymazat obrázek v době návrhu  
  
1.  Na **vlastnosti** vyberte <xref:System.Windows.Forms.PictureBox.Image%2A> vlastnost a klikněte pravým tlačítkem na malé miniatury, který se zobrazí nalevo od názvu objektu bitové kopie. Zvolte **resetovat**.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.PictureBox>  
 [Přehled ovládacího prvku PictureBox](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)  
 [Postupy: Změna velikosti či umístění obrázku za běhu](../../../../docs/framework/winforms/controls/how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)  
 [Postupy: Nastavení obrázků za běhu](../../../../docs/framework/winforms/controls/how-to-set-pictures-at-run-time-windows-forms.md)  
 [Ovládací prvek PictureBox](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)
