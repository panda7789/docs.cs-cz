---
title: 'Návod: Vytvoření formuláře MDI se slučováním nabídek a s ovládacími prvky ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms]
- MDI [Windows Forms], creating forms
- multiple document interface forms
- MDI forms
- ToolStrip control [Windows Forms]
- MDI forms [Windows Forms], creating
- MDI forms [Windows Forms], walkthroughs
ms.assetid: fbab4221-74af-42d0-bbf4-3c97f7b2e544
ms.openlocfilehash: e0343b98cb71521b35418e70550a93e0bfe20fa8
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628784"
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a>Návod: Vytvoření formuláře MDI se slučováním nabídek a s ovládacími prvky ToolStrip

Obor názvů <xref:System.Windows.Forms?displayProperty=nameWithType> podporuje aplikace MDI (Multiple Document Interface) a ovládací prvek <xref:System.Windows.Forms.MenuStrip> podporuje slučování nabídek. Formuláře MDI mohou také <xref:System.Windows.Forms.ToolStrip> ovládací prvky.

Tento návod ukazuje, jak používat <xref:System.Windows.Forms.ToolStripPanel> ovládací prvky s formulářem MDI. Formulář také podporuje slučování nabídek s podřízenými nabídkami. V tomto návodu jsou znázorněné následující úlohy:

- Vytvoření projektu model Windows Forms.

- Vytvoření hlavní nabídky pro formulář. Skutečný název nabídky se bude lišit.

- Přidání ovládacího prvku <xref:System.Windows.Forms.ToolStripPanel> do **panelu nástrojů**.

- Vytvoření podřízeného formuláře.

- Uspořádání ovládacích prvků <xref:System.Windows.Forms.ToolStripPanel> podle pořadí z.

Až budete hotovi, budete mít formulář MDI, který podporuje slučování nabídek a <xref:System.Windows.Forms.ToolStrip> ovládací prvky s pohyblivým ovládáním.

Chcete-li zkopírovat kód v tomto tématu jako jeden výpis, přečtěte si téma [Postup: Vytvoření formuláře MDI s nabídkou slučování a ovládacími prvky ToolStrip](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).

## <a name="prerequisites"></a>Předpoklady

K dokončení tohoto Názorného postupu budete potřebovat Visual Studio.

## <a name="create-the-project"></a>Vytvoření projektu

1. V aplikaci Visual Studio vytvořte projekt aplikace pro Windows s názvem **MDIForm** (**File** > **New** > **Project** >  **C# Visual** nebo **Visual Basic** > **Classic Desktop** > **model Windows Forms aplikace**).

2. V Návrhář formulářů vyberte formulář.

3. V okno Vlastnosti nastavte hodnotu <xref:System.Windows.Forms.Form.IsMdiContainer%2A> na `true`.

## <a name="create-the-main-menu"></a>Vytvoření hlavní nabídky

Nadřazený formulář MDI obsahuje hlavní nabídku. Hlavní nabídka obsahuje jednu položku nabídky s názvem **okno**. Pomocí položky nabídky **okno** můžete vytvořit podřízené formuláře. Položky nabídky z podřízených formulářů jsou sloučeny do hlavní nabídky.

1. Z **panelu nástrojů**přetáhněte ovládací prvek <xref:System.Windows.Forms.MenuStrip> do formuláře.

2. Přidejte <xref:System.Windows.Forms.ToolStripMenuItem> do ovládacího prvku <xref:System.Windows.Forms.MenuStrip> a pojmenujte ho v **okně**.

3. Vyberte ovládací prvek <xref:System.Windows.Forms.MenuStrip>.

4. V okno Vlastnosti nastavte hodnotu vlastnosti <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> na `ToolStripMenuItem1`.

5. Přidejte podpoložku do položky nabídky **okna** a pak pojmenujte podpoložku **novou**.

6. V okno Vlastnosti klikněte na položku **události**.

7. Dvakrát klikněte na událost <xref:System.Windows.Forms.ToolStripItem.Click>.

     Návrhář formulářů generuje obslužnou rutinu události pro událost <xref:System.Windows.Forms.ToolStripItem.Click>.

8. Do obslužné rutiny události vložte následující kód.

     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]

## <a name="add-the-toolstrippanel-control-to-the-toolbox"></a>Přidání ovládacího prvku ToolStripPanel do panelu nástrojů

Pokud používáte <xref:System.Windows.Forms.MenuStrip> ovládací prvky s formulářem MDI, je nutné mít ovládací prvek <xref:System.Windows.Forms.ToolStripPanel>. Chcete-li vytvořit formulář MDI v Návrhář formulářů, je nutné přidat ovládací prvek <xref:System.Windows.Forms.ToolStripPanel> do **panelu nástrojů** .

1. Otevřete **sadu nástrojů**a potom kliknutím na kartu **Všechny model Windows Forms** zobrazte dostupné model Windows Forms ovládací prvky.

2. Kliknutím pravým tlačítkem otevřete místní nabídku a vyberte **možnost vybrat položky**.

3. V dialogovém okně **zvolit položky sady nástrojů** přejděte dolů na sloupec **název** , dokud nenajdete **ToolStripPanel**.

4. Zaškrtněte políčko na **ToolStripPanel**a pak klikněte na **OK**.

     Ovládací prvek <xref:System.Windows.Forms.ToolStripPanel> se zobrazí v **sadě nástrojů**.

## <a name="create-a-child-form"></a>Vytvoření podřízeného formuláře

V tomto postupu definujete samostatnou podřízenou třídu formuláře, která má svůj vlastní ovládací prvek <xref:System.Windows.Forms.MenuStrip>. Položky nabídky tohoto formuláře jsou sloučeny s prvky nadřazeného formuláře.

1. Přidejte do projektu nový formulář s názvem `ChildForm`.

     Další informace naleznete v tématu [How to: Add model Windows Forms to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y2xxdce3(v=vs.100)).

2. Z **panelu nástrojů**přetáhněte ovládací prvek <xref:System.Windows.Forms.MenuStrip> do podřízeného formuláře.

3. Klikněte na glyf akcí návrháře <xref:System.Windows.Forms.MenuStrip> (![malé černé šipky](./media/designer-actions-glyph.gif)) a pak vyberte **Upravit položky**.

4. V dialogovém okně **Editor kolekce položek** přidejte do podřízené nabídky nový <xref:System.Windows.Forms.ToolStripMenuItem> s názvem **ChildMenuItem** .

     Další informace naleznete v tématu [Editor kolekce položek ovládacího prvku ToolStrip](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100)).

## <a name="test-the-form"></a>Testování formuláře

1. Pro zkompilování a spuštění formuláře stiskněte klávesu **F5** .

2. Kliknutím na položku nabídky **okno** otevřete nabídku a potom klikněte na tlačítko **Nový**.

     V klientské oblasti MDI formuláře se vytvoří nový podřízený formulář. Nabídka podřízeného formuláře je sloučena s hlavní nabídkou.

3. Zavřete podřízený formulář.

     Nabídka podřízeného formuláře je odebrána z hlavní nabídky.

4. Klikněte několikrát na **Nový** .

     Podřízené formuláře jsou automaticky uvedeny v položce nabídky **okna** , protože je přiřazena vlastnost <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> ovládacího prvku <xref:System.Windows.Forms.MenuStrip>.

## <a name="add-toolstrip-support"></a>Přidat podporu prvku ToolStrip

V tomto postupu přidáte čtyři ovládací prvky <xref:System.Windows.Forms.ToolStrip> do nadřazeného formuláře MDI. Každý <xref:System.Windows.Forms.ToolStrip> ovládací prvek je přidán do ovládacího prvku <xref:System.Windows.Forms.ToolStripPanel>, který je ukotven k okraji formuláře.

1. Z **panelu nástrojů**přetáhněte ovládací prvek <xref:System.Windows.Forms.ToolStripPanel> do formuláře.

2. Po výběru ovládacího prvku <xref:System.Windows.Forms.ToolStripPanel> dvakrát klikněte na ovládací prvek <xref:System.Windows.Forms.ToolStrip> v sadě **nástrojů**.

     V ovládacím prvku <xref:System.Windows.Forms.ToolStripPanel> je vytvořen ovládací prvek <xref:System.Windows.Forms.ToolStrip>.

3. Vyberte ovládací prvek <xref:System.Windows.Forms.ToolStripPanel>.

4. V okno Vlastnosti změňte hodnotu vlastnosti <xref:System.Windows.Forms.Control.Dock%2A> ovládacího prvku na <xref:System.Windows.Forms.DockStyle.Left>.

     Ovládací prvek <xref:System.Windows.Forms.ToolStripPanel> Docker na levou stranu formuláře pod hlavní nabídkou. Oblast klienta MDI se mění tak, aby odpovídala ovládacímu prvku <xref:System.Windows.Forms.ToolStripPanel>.

5. Opakujte kroky 1 až 4.

     Ukotvěte nový ovládací prvek <xref:System.Windows.Forms.ToolStripPanel> do horní části formuláře.

     Ovládací prvek <xref:System.Windows.Forms.ToolStripPanel> je ukotven pod hlavní nabídkou, ale napravo od prvního ovládacího prvku <xref:System.Windows.Forms.ToolStripPanel>. Tento krok ukazuje důležitost pořadí vykreslování při správném umísťování <xref:System.Windows.Forms.ToolStripPanel>ch ovládacích prvků.

6. Opakujte kroky 1 až 4 pro dva další <xref:System.Windows.Forms.ToolStripPanel> ovládací prvky.

     Ukotvěte nové ovládací prvky <xref:System.Windows.Forms.ToolStripPanel> doprava a dolů formuláře.

## <a name="arrange-toolstrippanel-controls-by-z-order"></a>Uspořádat ovládací prvky ToolStripPanel podle pořadí Z

Pozice ukotveného ovládacího prvku <xref:System.Windows.Forms.ToolStripPanel> ve formuláři MDI je určena pozicí ovládacího prvku v pořadí vykreslování. Pořadí vykreslování ovládacích prvků lze snadno uspořádat v okně Osnova dokumentu.

1. V nabídce **zobrazení** klikněte na položku **ostatní okna**a potom klikněte na položku **Osnova dokumentu**.

     Uspořádání ovládacích prvků <xref:System.Windows.Forms.ToolStripPanel> z předchozího postupu je nestandardní. Je to proto, že pořadí vykreslování není správné. Pomocí okna Osnova dokumentu můžete změnit pořadí vykreslování ovládacích prvků.

2. V okně Osnova dokumentu vyberte **ToolStripPanel4**.

3. Opakovaně klikněte na tlačítko se šipkou dolů, dokud **ToolStripPanel4** není v dolní části seznamu.

     Ovládací prvek **ToolStripPanel4** je ukotven na spodní straně formuláře pod ostatními ovládacími prvky.

4. Vyberte **ToolStripPanel2**.

5. Pokud chcete ovládací prvek umístit třetí v seznamu, klikněte na tlačítko se šipkou dolů jen jednou.

     Ovládací prvek **ToolStripPanel2** je ukotvený v horní části formuláře pod hlavní nabídkou a nad ostatními ovládacími prvky.

6. V okně **Osnova dokumentu** vyberte různé ovládací prvky a přesuňte je na jiné pozice v pořadí z. Poznamenejte si účinek pořadí vykreslování na umístění ukotvených ovládacích prvků. Pomocí kombinace kláves CTRL + Z nebo **příkazu zpět** v nabídce **Upravit** můžete změny vrátit zpět.

## <a name="checkpoint---test-your-form"></a>Kontrolní bod – testování formuláře

1. Pro zkompilování a spuštění formuláře stiskněte klávesu **F5** .

2. Klikněte na úchyt ovládacího prvku <xref:System.Windows.Forms.ToolStrip> a přetáhněte ovládací prvek na jiné pozice ve formuláři.

     Ovládací prvek <xref:System.Windows.Forms.ToolStrip> lze přetáhnout z jednoho ovládacího prvku <xref:System.Windows.Forms.ToolStripPanel> na jiný.

## <a name="next-steps"></a>Další kroky

V tomto návodu jste vytvořili nadřazený formulář MDI s ovládacími prvky <xref:System.Windows.Forms.ToolStrip> a slučováním nabídek. <xref:System.Windows.Forms.ToolStrip> rodinu ovládacích prvků lze použít pro mnoho dalších účelů:

- Vytvořte místní nabídky pro ovládací prvky pomocí <xref:System.Windows.Forms.ContextMenuStrip>. Další informace najdete v tématu věnovaném [přehledu komponent](contextmenu-component-overview-windows-forms.md).

- Vytvořili jste formulář s automaticky vyplněnou standardní nabídkou. Další informace najdete v tématu [Návod: poskytnutí standardních položek nabídky formuláři](walkthrough-providing-standard-menu-items-to-a-form.md).

- Poskytněte vašemu <xref:System.Windows.Forms.ToolStrip> profesionální vzhled. Další informace naleznete v tématu [How to: set a Renderer ToolStrip pro aplikaci](how-to-set-the-toolstrip-renderer-for-an-application.md).

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [Postupy: Vytváření nadřazených formulářů MDI](../advanced/how-to-create-mdi-parent-forms.md)
- [Postupy: Vytváření podřízených formulářů MDI](../advanced/how-to-create-mdi-child-forms.md)
- [Postupy: Vložení prvku MenuStrip do rozevíracího seznamu MDI](how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)
- [Ovládací prvek ToolStrip](toolstrip-control-windows-forms.md)
