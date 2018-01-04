---
title: "Postupy: Přidávání tlačítek do ovládacího prvku ToolBar pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding separators
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], adding drop-down menus
ms.assetid: d9ce3040-3e21-4e2d-80ae-b430982b2db8
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ccd63cb88661db7601b87eec6bdf3a959afb8bbf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-buttons-to-a-toolbar-control-using-the-designer"></a>Postupy: Přidávání tlačítek do ovládacího prvku ToolBar pomocí Návrháře
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> Řízení nahrazuje a přidá funkce <xref:System.Windows.Forms.ToolBar> řízení; však <xref:System.Windows.Forms.ToolBar> řízení se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte.  
  
 Nedílnou součástí <xref:System.Windows.Forms.ToolBar> ovládací prvek je přidejte do ní tlačítek. To slouží k poskytování snadného přístupu k příkazům nabídky nebo Alternativně můžete umístit v jiné oblasti uživatelského rozhraní pro vaší aplikace, která zveřejňuje příkazy pro vaše uživatele, kteří nejsou k dispozici ve struktuře nabídky.  
  
 Následující postup vyžaduje **aplikace Windows** projekt pomocí formuláře obsahující <xref:System.Windows.Forms.ToolBar> ovládacího prvku. Informace o nastavení tohoto projektu najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) a [postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-buttons-at-design-time"></a>Přidání tlačítka v době návrhu  
  
1.  Vyberte <xref:System.Windows.Forms.ToolBar> ovládacího prvku.  
  
2.  V **vlastnosti** okně klikněte na tlačítko <xref:System.Windows.Forms.ToolBar.Buttons%2A> vlastnost vyberte ho a klikněte na tlačítko **třemi tečkami** (![VisualStudioEllipsesButton snímek] (../../../../docs/framework/winforms/media/vbellipsesbutton.png " vbEllipsesButton")) tlačítko Otevřít **Editor kolekce ToolBarButton**.  
  
3.  Použití **přidat** a **odebrat** tlačítka přidávat a odebírat tlačítka z <xref:System.Windows.Forms.ToolBar> ovládacího prvku.  
  
4.  Konfigurovat vlastnosti jednotlivých tlačítka v **vlastnosti** okno, které se zobrazí v podokně na pravé straně editoru. V následující tabulce jsou uvedeny některé důležité vlastnosti vzít v úvahu.  
  
    |Vlastnost|Popis|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A>|Nastaví v nabídce Zobrazit v tlačítko panelu nástrojů rozevíracího seznamu. Tlačítka panelu nástrojů <xref:System.Windows.Forms.ToolBarButton.Style%2A> musí být nastavena na <xref:System.Windows.Forms.ToolBarButtonStyle.DropDownButton>. Tato vlastnost přijímá instanci <xref:System.Windows.Forms.ContextMenu> třída jako odkaz.|  
    |<xref:System.Windows.Forms.ToolBarButton.PartialPush%2A>|Nastaví, zda je částečně nabídnutých Přepnout styl tlačítka panelu nástrojů. Tlačítka panelu nástrojů <xref:System.Windows.Forms.ToolBarButton.Style%2A> musí být nastavena na <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>.|  
    |<xref:System.Windows.Forms.ToolBarButton.Pushed%2A>|Nastaví, zda tlačítka panelu nástrojů Přepnout styl je momentálně v stisknutí stavu. Tlačítka panelu nástrojů <xref:System.Windows.Forms.ToolBarButton.Style%2A> musí být nastavena na <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton> nebo <xref:System.Windows.Forms.ToolBarButtonStyle.PushButton>.|  
    |<xref:System.Windows.Forms.ToolBarButton.Style%2A>|Nastavuje styl tlačítka panelu nástrojů. Musí být jedna z hodnot v <xref:System.Windows.Forms.ToolBarButtonStyle> výčtu.|  
    |<xref:System.Windows.Forms.ToolBarButton.Text%2A>|Textový řetězec zobrazí tlačítko.|  
    |<xref:System.Windows.Forms.ToolBarButton.ToolTipText%2A>|Text, který se zobrazí jako popisek pro tlačítko.|  
  
5.  Klikněte na tlačítko **OK** a zavřete dialogové okno Vytvořit panelů jste zadali.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ToolBar>  
 [Postupy: Definování ikony pro tlačítko ToolBar](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)  
 [Postupy: Spouštění událostí nabídky pro tlačítka panelu nástrojů](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 [Přehled ovládacího prvku ToolBar](../../../../docs/framework/winforms/controls/toolbar-control-overview-windows-forms.md)  
 [Ovládací prvek ToolBar](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)
