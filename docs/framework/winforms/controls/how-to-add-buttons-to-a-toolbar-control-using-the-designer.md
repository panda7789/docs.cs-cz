---
title: 'Postupy: Přidávání tlačítek do ovládacího prvku ToolBar pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding separators
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], adding drop-down menus
ms.assetid: d9ce3040-3e21-4e2d-80ae-b430982b2db8
ms.openlocfilehash: 133190426229a10ed6f637293326c229e808bfdb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084021"
---
# <a name="how-to-add-buttons-to-a-toolbar-control-using-the-designer"></a>Postupy: Přidávání tlačítek do ovládacího prvku ToolBar pomocí Návrháře
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> Ovládací prvek nahradí a přidá funkce, které <xref:System.Windows.Forms.ToolBar> řízení; však <xref:System.Windows.Forms.ToolBar> ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete.  
  
 Nedílnou součástí toho, <xref:System.Windows.Forms.ToolBar> je ovládací prvek tlačítka, přidejte do ní. To slouží k poskytování snadného přístupu k příkazům nabídky nebo Alternativně můžete umístit v jiné oblasti uživatelské rozhraní vaší aplikace k vystavení příkazy pro vaše uživatele, kteří nejsou k dispozici ve struktuře nabídky.  
  
 Následující postup vyžaduje, **aplikace Windows** projektu s formulář obsahující <xref:System.Windows.Forms.ToolBar> ovládacího prvku. Informace o nastavení takový projekt, naleznete v tématu [jak: Vytvoření projektu aplikace Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [jak: Přidání ovládacích prvků Windows Forms](how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-buttons-at-design-time"></a>Přidat tlačítka v době návrhu  
  
1.  Vyberte <xref:System.Windows.Forms.ToolBar> ovládacího prvku.  
  
2.  V **vlastnosti** okno, klikněte na tlačítko <xref:System.Windows.Forms.ToolBar.Buttons%2A> vlastnost vyberte ho a klikněte na tlačítko **tlačítko se třemi tečkami** (![VisualStudioEllipsesButton snímek obrazovky s](../media/vbellipsesbutton.png " vbEllipsesButton")) tlačítko Otevřít **Editor kolekce ToolBarButton**.  
  
3.  Použití **přidat** a **odebrat** tlačítka pro přidání a odebrání tlačítek <xref:System.Windows.Forms.ToolBar> ovládacího prvku.  
  
4.  Konfigurace vlastností jednotlivá tlačítka v **vlastnosti** okno, které se zobrazí v podokně na pravé straně editoru. V následující tabulce jsou uvedeny vzít v úvahu některé důležité vlastnosti.  
  
    |Vlastnost|Popis|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A>|Nastaví v nabídce zobrazeného na tlačítku rozevíracího seznamu nástrojů. Tlačítko panelu nástrojů <xref:System.Windows.Forms.ToolBarButton.Style%2A> musí být vlastnost nastavena na <xref:System.Windows.Forms.ToolBarButtonStyle.DropDownButton>. Tato vlastnost má instance <xref:System.Windows.Forms.ContextMenu> třídu jako odkaz.|  
    |<xref:System.Windows.Forms.ToolBarButton.PartialPush%2A>|Nastaví, zda je částečně stisknuté Přepnout styl tlačítka panelu nástrojů. Tlačítko panelu nástrojů <xref:System.Windows.Forms.ToolBarButton.Style%2A> musí být vlastnost nastavena na <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>.|  
    |<xref:System.Windows.Forms.ToolBarButton.Pushed%2A>|Nastaví, zda přepínač – vizuální styl tlačítka panelu nástrojů je aktuálně ve stavu vložené. Tlačítko panelu nástrojů <xref:System.Windows.Forms.ToolBarButton.Style%2A> musí být vlastnost nastavena na <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton> nebo <xref:System.Windows.Forms.ToolBarButtonStyle.PushButton>.|  
    |<xref:System.Windows.Forms.ToolBarButton.Style%2A>|Nastaví styl tlačítka panelu nástrojů. Musí být jedna z hodnot v <xref:System.Windows.Forms.ToolBarButtonStyle> výčtu.|  
    |<xref:System.Windows.Forms.ToolBarButton.Text%2A>|Textový řetězec zobrazený tlačítkem.|  
    |<xref:System.Windows.Forms.ToolBarButton.ToolTipText%2A>|Text, který se zobrazí jako popisek tlačítka.|  
  
5.  Klikněte na tlačítko **OK** a zavřete dialogové okno vytvořit panely, které jste zadali.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ToolBar>
- [Postupy: Definování ikony pro tlačítko ToolBar](how-to-define-an-icon-for-a-toolbar-button.md)
- [Postupy: Spouštění událostí nabídky pro tlačítka ToolBar](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [Přehled ovládacího prvku ToolBar](toolbar-control-overview-windows-forms.md)
- [ToolBar – ovládací prvek](toolbar-control-windows-forms.md)
