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
ms.openlocfilehash: 19d0b284238ed662b25627d6077c1ebe6ecc6e86
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59323704"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button-using-the-designer"></a>Postupy: Definování ikony pro tlačítko ToolBar pomocí Návrháře
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> Ovládací prvek nahradí a přidá funkce, které <xref:System.Windows.Forms.ToolBar> řízení; však <xref:System.Windows.Forms.ToolBar> ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete.  
  
 <xref:System.Windows.Forms.ToolBar> tlačítka budou moct zobrazit ikony v nich pro snadnou identifikaci uživatelů. Toho můžete dosáhnout přidávání obrázků na <xref:System.Windows.Forms.ImageList> komponenty a přidružíte ho <xref:System.Windows.Forms.ToolBar> ovládacího prvku.  
  
 Následující postup vyžaduje, **aplikace Windows** projektu s formulář obsahující <xref:System.Windows.Forms.ToolBar> ovládacího prvku a <xref:System.Windows.Forms.ImageList> komponenty. Informace o nastavení takový projekt, naleznete v tématu [jak: Vytvoření projektu aplikace Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [jak: Přidání ovládacích prvků Windows Forms](how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-set-an-icon-for-a-toolbar-button-at-design-time"></a>Chcete-li nastavit ikonu pro tlačítko panelu nástrojů v době návrhu  
  
1. Přidání obrázků do <xref:System.Windows.Forms.ImageList> komponenty. Další informace najdete v tématu [jak: Přidávání a odebírání obrázků ImageList pomocí návrháře](how-to-add-or-remove-imagelist-images-with-the-designer.md).  
  
2. Vyberte <xref:System.Windows.Forms.ToolBar> ovládací prvek na formuláři.  
  
3. V **vlastnosti** okno, nastaveno <xref:System.Windows.Forms.ToolBar> ovládacího prvku <xref:System.Windows.Forms.ToolBar.ImageList%2A> vlastnost <xref:System.Windows.Forms.ImageList> komponenty.  
  
4. Klikněte na tlačítko <xref:System.Windows.Forms.ToolBar> ovládacího prvku <xref:System.Windows.Forms.ToolBar.Buttons%2A> vlastnost vyberte ho a klikněte na tlačítko se třemi tečkami (![snímek obrazovky VisualStudioEllipsesButton](../media/vbellipsesbutton.png "vbEllipsesButton")) tlačítko Otevřít **Editor kolekce ToolBarButton**.  
  
5. Použití **přidat** tlačítko pro přidání tlačítka <xref:System.Windows.Forms.ToolBar> ovládacího prvku.  
  
6. V **vlastnosti** okno, které se zobrazí v podokně na pravé straně **Editor kolekce ToolBarButton**, nastavte <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> vlastnost tlačítko panelu nástrojů na jednu z hodnot v seznamu, který přenesou z imagí, které jste přidali do <xref:System.Windows.Forms.ImageList> komponenty.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ToolBar>
- [Postupy: Spouštění událostí nabídky pro tlačítka ToolBar](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [ToolBar – ovládací prvek](toolbar-control-windows-forms.md)
- [Komponenta ImageList](imagelist-component-windows-forms.md)
