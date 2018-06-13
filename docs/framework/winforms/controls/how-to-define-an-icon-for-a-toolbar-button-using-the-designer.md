---
title: 'Postupy: Definování ikony pro tlačítko ToolBar pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding icons to buttons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- buttons [Windows Forms], images
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: d848f38e-67f2-49d4-8e88-01c845c06c02
ms.openlocfilehash: a6c08d33682e5e2cc936c3aa6aa109ad3389a367
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532896"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button-using-the-designer"></a>Postupy: Definování ikony pro tlačítko ToolBar pomocí Návrháře
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> Řízení nahrazuje a přidá funkce <xref:System.Windows.Forms.ToolBar> řízení; však <xref:System.Windows.Forms.ToolBar> řízení se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte.  
  
 <xref:System.Windows.Forms.ToolBar> tlačítka jsou moci zobrazit ikony v nich pro snazší identifikaci uživatelů. Toho je dosaženo pomocí přidávání obrázků na <xref:System.Windows.Forms.ImageList> součástí a její přidružení <xref:System.Windows.Forms.ToolBar> ovládacího prvku.  
  
 Následující postup vyžaduje **aplikace Windows** projekt pomocí formuláře obsahující <xref:System.Windows.Forms.ToolBar> řízení a <xref:System.Windows.Forms.ImageList> součásti. Informace o nastavení tohoto projektu najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) a [postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-set-an-icon-for-a-toolbar-button-at-design-time"></a>Chcete-li nastavit ikonu pro tlačítka panelu nástrojů v době návrhu  
  
1.  Přidat Image do <xref:System.Windows.Forms.ImageList> součásti. Další informace najdete v tématu [postupy: Přidání nebo odebrání obrázků ImageList pomocí návrháře](../../../../docs/framework/winforms/controls/how-to-add-or-remove-imagelist-images-with-the-designer.md).  
  
2.  Vyberte <xref:System.Windows.Forms.ToolBar> ovládací prvek na formuláři.  
  
3.  V **vlastnosti** nastavte <xref:System.Windows.Forms.ToolBar> ovládacího prvku <xref:System.Windows.Forms.ToolBar.ImageList%2A> vlastnost, která má <xref:System.Windows.Forms.ImageList> součásti.  
  
4.  Klikněte <xref:System.Windows.Forms.ToolBar> ovládacího prvku <xref:System.Windows.Forms.ToolBar.Buttons%2A> vlastnost vyberte ho a klikněte na tlačítko se třemi tečkami (![VisualStudioEllipsesButton – snímek obrazovky](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) tlačítko Otevřít **Editor kolekce ToolBarButton**.  
  
5.  Použití **přidat** tlačítko pro přidání tlačítek <xref:System.Windows.Forms.ToolBar> ovládací prvek.  
  
6.  V **vlastnosti** okno, které se zobrazí v podokně na pravé straně **Editor kolekce ToolBarButton**, nastavte <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> vlastnost tlačítko panelu nástrojů na jednu z hodnot v seznamu, který výběr pochází z Image přidat do <xref:System.Windows.Forms.ImageList> součásti.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ToolBar>  
 [Postupy: Spouštění událostí nabídky pro tlačítka panelu nástrojů](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 [Ovládací prvek ToolBar](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)  
 [Komponenta ImageList](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
