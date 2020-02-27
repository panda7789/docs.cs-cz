---
title: 'Návod: Poskytnutí standardních položek nabídky formuláři'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], standard
- toolbars [Windows Forms], walkthroughs
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: dac37d98-589e-4d6d-9673-6437e8943122
ms.openlocfilehash: ee80aad445c00bb4b98b49c80495fa512150bcef
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628771"
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a>Návod: Poskytnutí standardních položek nabídky formuláři

Pomocí ovládacího prvku <xref:System.Windows.Forms.MenuStrip> můžete poskytnout standardní nabídku pro vaše formuláře.

Tento návod ukazuje, jak pomocí ovládacího prvku <xref:System.Windows.Forms.MenuStrip> vytvořit standardní nabídku. Formulář také reaguje, když uživatel vybere položku nabídky. V tomto návodu jsou znázorněné následující úlohy:

- Vytvoření projektu model Windows Forms.

- Vytvoření standardní nabídky

- Vytvoření ovládacího prvku <xref:System.Windows.Forms.StatusStrip>.

- Zpracování výběru položky nabídky.

Po dokončení budete mít formulář se standardní nabídkou, která zobrazí výběr položek nabídky v ovládacím prvku <xref:System.Windows.Forms.StatusStrip>.

Chcete-li zkopírovat kód v tomto tématu jako jeden výpis, přečtěte si téma [Postup: poskytnutí standardních položek nabídky do formuláře](how-to-provide-standard-menu-items-to-a-form.md).

## <a name="prerequisites"></a>Předpoklady

K dokončení tohoto Názorného postupu budete potřebovat Visual Studio.

## <a name="create-the-project"></a>Vytvoření projektu

1. V aplikaci Visual Studio vytvořte projekt aplikace pro Windows s názvem **StandardMenuForm** (**File** > **New** > **Project** >  **C# Visual** nebo **Visual Basic** > **Classic Desktop** > **model Windows Forms aplikace**).

2. V Návrhář formulářů vyberte formulář.

## <a name="create-a-standard-menu"></a>Vytvořit standardní nabídku

Návrhář formulářů může automaticky naplnit ovládací prvek <xref:System.Windows.Forms.MenuStrip> pomocí standardních položek nabídky.

1. Z **panelu nástrojů**přetáhněte ovládací prvek <xref:System.Windows.Forms.MenuStrip> do formuláře.

2. Klikněte na piktogram akcí návrháře <xref:System.Windows.Forms.MenuStrip> (![malé černé šipky](./media/designer-actions-glyph.gif)) a vyberte **Vložit standardní položky**.

     Ovládací prvek <xref:System.Windows.Forms.MenuStrip> se naplní standardními položkami nabídky.

3. Kliknutím na položku nabídky **soubor** zobrazíte její výchozí položky nabídky a příslušné ikony.

## <a name="create-a-statusstrip-control"></a>Vytvoření ovládacího prvku StatusStrip

Pro zobrazení stavu aplikací model Windows Forms použijte ovládací prvek <xref:System.Windows.Forms.StatusStrip>. V aktuálním příkladu se položky nabídky vybrané uživatelem zobrazí v ovládacím prvku <xref:System.Windows.Forms.StatusStrip>.

1. Z **panelu nástrojů**přetáhněte ovládací prvek <xref:System.Windows.Forms.StatusStrip> do formuláře.

     Ovládací prvek <xref:System.Windows.Forms.StatusStrip> se automaticky ukotví do dolní části formuláře.

2. Klikněte na tlačítko rozevíracího seznamu <xref:System.Windows.Forms.StatusStrip>ho ovládacího prvku a výběrem **StatusLabel** přidejte ovládací prvek <xref:System.Windows.Forms.ToolStripStatusLabel> do ovládacího prvku <xref:System.Windows.Forms.StatusStrip>.

## <a name="handle-item-selection"></a>Zpracovat výběr položky

Zpracuje událost <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>, aby reagovala, když uživatel vybere položku nabídky.

1. Klikněte na položku nabídky **soubor** , kterou jste vytvořili v části vytvoření standardní nabídky.

2. V okně **vlastnosti** klikněte na položku **události**.

3. Dvakrát klikněte na událost <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>.

     Návrhář formulářů generuje obslužnou rutinu události pro událost <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>.

4. Do obslužné rutiny události vložte následující kód.

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]

5. Do formuláře vložte definici metody nástroje `UpdateStatus`.

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]

## <a name="checkpoint--test-your-form"></a>Kontrolní bod – testování formuláře

1. Pro zkompilování a spuštění formuláře stiskněte klávesu **F5** .

2. Kliknutím na položku nabídky **soubor** otevřete nabídku.

3. V nabídce **soubor** klikněte na jednu z položek a vyberte ji.

     Ovládací prvek <xref:System.Windows.Forms.StatusStrip> zobrazí vybranou položku.

## <a name="next-steps"></a>Další kroky

V tomto návodu jste vytvořili formulář se standardní nabídkou. <xref:System.Windows.Forms.ToolStrip> rodinu ovládacích prvků lze použít pro mnoho dalších účelů:

- Vytvořte místní nabídky pro ovládací prvky pomocí <xref:System.Windows.Forms.ContextMenuStrip>. Další informace najdete v tématu věnovaném [přehledu komponent](contextmenu-component-overview-windows-forms.md).

- Vytvořte formulář MDI (Multiple Document Interface) s ovládacími prvky docking <xref:System.Windows.Forms.ToolStrip>. Další informace najdete v tématu [Návod: Vytvoření formuláře MDI pomocí slučování nabídek a ovládacích prvků ToolStrip](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).

- Poskytněte vašemu <xref:System.Windows.Forms.ToolStrip> profesionální vzhled. Další informace naleznete v tématu [How to: set a Renderer ToolStrip pro aplikaci](how-to-set-the-toolstrip-renderer-for-an-application.md).

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [Ovládací prvek MenuStrip](menustrip-control-windows-forms.md)
