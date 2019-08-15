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
ms.openlocfilehash: 5de7645ecbf2123df849046a152643cd629b4898
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038228"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button-using-the-designer"></a>Postupy: Definování ikony pro tlačítko ToolBar pomocí Návrháře

> [!NOTE]
> Ovládací prvek nahrazuje a přidává funkce <xref:System.Windows.Forms.ToolBar> <xref:System.Windows.Forms.ToolBar> ovládacímu prvku. ovládací prvek je však ponechán pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. <xref:System.Windows.Forms.ToolStrip>

<xref:System.Windows.Forms.ToolBar>tlačítka jsou schopna zobrazit ikony, aby je uživatelé mohli snadno identifikovat. Toho lze dosáhnout přidáním obrázků do <xref:System.Windows.Forms.ImageList> komponenty a jejich <xref:System.Windows.Forms.ToolBar> přidružením k ovládacímu prvku.

Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje <xref:System.Windows.Forms.ToolBar> ovládací prvek a <xref:System.Windows.Forms.ImageList> komponentu. Informace o nastavení takového projektu naleznete v tématu [How to: Vytvořte projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikace model Windows Forms a [postupujte takto: Přidejte ovládací prvky do](how-to-add-controls-to-windows-forms.md)model Windows Forms.


### <a name="to-set-an-icon-for-a-toolbar-button-at-design-time"></a>Nastavení ikony pro tlačítko panelu nástrojů v době návrhu

1. Přidejte obrázky do <xref:System.Windows.Forms.ImageList> komponenty. Další informace najdete v tématu [jak: Přidejte nebo odeberte obrázky ImageList pomocí návrháře](how-to-add-or-remove-imagelist-images-with-the-designer.md).

2. <xref:System.Windows.Forms.ToolBar> Vyberte ovládací prvek ve formuláři.

3. V okně **vlastnosti** nastavte <xref:System.Windows.Forms.ToolBar> <xref:System.Windows.Forms.ToolBar.ImageList%2A> vlastnost ovládacího prvku na <xref:System.Windows.Forms.ImageList> součást.

4. <xref:System.Windows.Forms.ToolBar.Buttons%2A> ![](./media/visual-studio-ellipsis-button.png)Kliknutím na vlastnost ovládacíhoprvkujivyberteakliknutímnatlačítkosetřemitečkami(...)voknoVlastnostisadyVisualStudio.)otevřeteEditorkolekceToolBarButton.<xref:System.Windows.Forms.ToolBar>

5. K přidání tlačítek do <xref:System.Windows.Forms.ToolBar> ovládacího prvku použijte tlačítko Přidat.

6. V okně **vlastnosti** , které se zobrazí v podokně na pravé straně **editoru kolekce ToolBarButton** <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> , nastavte vlastnost každého tlačítka panelu nástrojů na jednu z hodnot v seznamu, která je vykreslena z obrázků přidaných do <xref:System.Windows.Forms.ImageList> součást.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ToolBar>
- [Postupy: Aktivace událostí nabídky pro tlačítka panelu nástrojů](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [Ovládací prvek ToolBar](toolbar-control-windows-forms.md)
- [Komponenta ImageList](imagelist-component-windows-forms.md)
