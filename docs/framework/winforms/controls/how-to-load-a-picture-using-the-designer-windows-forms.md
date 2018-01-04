---
title: "Postupy: Načtení obrázku pomocí Návrháře (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9ca3e3eef1aa9e7414d3c279de5943585703bf9f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a>Postupy: Načtení obrázku pomocí Návrháře (Windows Forms)
S Windows Forms <xref:System.Windows.Forms.PictureBox> ovládací prvek, můžete načíst a zobrazit obrázek v době návrhu nastavením ve formuláři <xref:System.Windows.Forms.PictureBox.Image%2A> vlastnost, která má platný obrázek. Následující tabulka uvádí typy souborů přijatelný.  
  
|Typ|Přípona názvu souboru|  
|----------|-------------------------|  
|Rastrový obrázek|.bmp|  
|Ikona|.ico, který|  
|GIF|.GIF|  
|Metafile|WMF|  
|JPEG|.jpg|  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
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
