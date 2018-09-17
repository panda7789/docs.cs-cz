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
ms.openlocfilehash: 6236190340833e3f8810387e51ad53e1cb10d37b
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45743545"
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a>Návod: Vytvoření formuláře MDI se slučováním nabídek a s ovládacími prvky ToolStrip
<xref:System.Windows.Forms?displayProperty=nameWithType> Obor názvů podporuje více dokumentů aplikace (MDI interface) a <xref:System.Windows.Forms.MenuStrip> ovládací prvek podporuje slučování nabídek. MDI formuláře můžete také <xref:System.Windows.Forms.ToolStrip> ovládacích prvků.  
  
 Tento návod ukazuje, jak používat <xref:System.Windows.Forms.ToolStripPanel> ovládacích prvků formuláře MDI. Formulář podporuje také s nabídkami podřízené slučováním nabídek. Tyto úlohy jsou uvedené v tomto návodu:  
  
-   Vytvoření projektu Windows Forms.  
  
-   Vytvoření hlavní nabídky pro formulář. Skutečný název nabídky se liší.  
  
-   Přidávání <xref:System.Windows.Forms.ToolStripPanel> ovládací prvek **nástrojů**.  
  
-   Vytváří se podřízený formulář.  
  
-   Uspořádání <xref:System.Windows.Forms.ToolStripPanel> ovládací prvky podle pořadí vykreslování.  
  
 Až budete hotovi, budete mít formuláře MDI, která podporuje menu merging a přesouvatelných <xref:System.Windows.Forms.ToolStrip> ovládacích prvků.  
  
 Pokud chcete zkopírovat kód v tomto tématu jako jeden seznam, naleznete v tématu [postupy: vytvoření formuláře MDI s ovládacími prvky ToolStrip a slučování nabídek](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat:  
  
-   Dostatečná oprávnění k vytvoření a spuštění projektů aplikace Windows Forms v počítači nainstalovanou aplikaci Visual Studio.  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu a nastavení formuláře.  
  
#### <a name="to-create-the-project"></a>Vytvoření projektu  
  
1.  Vytvořte projekt aplikace Windows s názvem **MdiForm** (**souboru** > **nový** > **projektu**  >  **Visual C#** nebo **jazyka Visual Basic** > **klasický desktopový** > **Windows Forms aplikace**).  
  
2.  V Návrháři formulářů Windows vyberte formulář.  
  
3.  V okně Vlastnosti nastavte hodnotu <xref:System.Windows.Forms.Form.IsMdiContainer%2A> k `true`.  
  
## <a name="creating-the-main-menu"></a>Vytvoření hlavní nabídky  
 Nadřazený formulář MDI obsahuje hlavní nabídky. V hlavní nabídce má jedna položka nabídky s názvem **okno**. S **okno** položku nabídky, můžete vytvořit podřízené formuláře. Položky nabídky z podřízené formuláře jsou sloučeny do hlavní nabídky.  
  
#### <a name="to-create-the-main-menu"></a>Chcete-li vytvořit hlavní nabídky  
  
1.  Z **nástrojů**, přetáhněte <xref:System.Windows.Forms.MenuStrip> ovládací prvek na formuláři.  
  
2.  Přidat <xref:System.Windows.Forms.ToolStripMenuItem> k <xref:System.Windows.Forms.MenuStrip> řídit a pojmenujte ho **okno**.  
  
3.  Vyberte <xref:System.Windows.Forms.MenuStrip> ovládacího prvku.  
  
4.  V okně Vlastnosti nastavte hodnotu <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> vlastnost `ToolStripMenuItem1`.  
  
5.  Přidat podřízenou položku k **okno** položky nabídky a pojmenujte podřízenou položku **nový**.  
  
6.  V okně Vlastnosti klikněte na tlačítko **události**.  
  
7.  Dvakrát klikněte <xref:System.Windows.Forms.ToolStripItem.Click> událostí.  
  
     Návrhář formulářů Windows generuje obslužná rutina události <xref:System.Windows.Forms.ToolStripItem.Click> událostí.  
  
8.  Vložte následující kód do obslužné rutiny události.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]  
  
## <a name="adding-the-toolstrippanel-control-to-the-toolbox"></a>Přidání ovládacího prvku ToolStripPanel na panelu nástrojů  
 Při použití <xref:System.Windows.Forms.MenuStrip> ovládacích prvků formuláře MDI musí mít <xref:System.Windows.Forms.ToolStripPanel> ovládacího prvku. Je nutné přidat <xref:System.Windows.Forms.ToolStripPanel> ovládací prvek **nástrojů** k vytvoření formuláře MDI v Návrháři formulářů Windows.  
  
#### <a name="to-add-the-toolstrippanel-control-to-the-toolbox"></a>Přidání ovládacího prvku ToolStripPanel do panelu nástrojů  
  
1.  Otevřít **nástrojů**a potom klikněte na tlačítko **všechny formuláře Windows** zobrazte dostupné ovládací prvky Windows Forms.  
  
2.  Klikněte pravým tlačítkem na otevřete místní nabídku a vyberte **zvolit položky**.  
  
3.  V **zvolit položky nástrojů** dialogové okno, přejděte dolů **název** sloupce, dokud nenajdete **ToolStripPanel**.  
  
4.  Zaškrtněte políčko podle **ToolStripPanel**a potom klikněte na tlačítko **OK**.  
  
     <xref:System.Windows.Forms.ToolStripPanel> Ovládací prvek zobrazí **nástrojů**.  
  
## <a name="creating-a-child-form"></a>Vytváří se podřízený formulář  
 V tomto postupu bude definujete třídu samostatnou podřízenou formulář, který má vlastní <xref:System.Windows.Forms.MenuStrip> ovládacího prvku. Položky nabídky pro tento formulář jsou sloučeny s těmi nadřazeného formuláře.  
  
#### <a name="to-define-a-child-form"></a>Chcete-li definovat podřízené formuláře  
  
1.  Přidat nový formulář s názvem `ChildForm` do projektu.  
  
     Další informace najdete v tématu [postupy: Přidání Windows Forms do projektu](https://msdn.microsoft.com/library/3d7bb25f-fd90-47cf-9378-fa0d764686c1).  
  
2.  Z **nástrojů**, přetáhněte <xref:System.Windows.Forms.MenuStrip> ovládací prvek na podřízeném formuláři.  
  
3.  Klikněte na tlačítko <xref:System.Windows.Forms.MenuStrip> piktogram inteligentní značky ovládacího prvku (![piktogram inteligentní](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) a pak vyberte **upravit položky**.  
  
4.  V **Editor kolekce položek** dialogovém okně přidejte nový <xref:System.Windows.Forms.ToolStripMenuItem> s názvem **ChildMenuItem** do nabídky podřízené.  
  
     Další informace najdete v tématu [Editor kolekce položek ovládacího prvku ToolStrip](https://msdn.microsoft.com/library/e681f3ab-94ba-4b2b-ac64-1dfad46caa25).  
  
## <a name="testing-the-form"></a>Testování formuláře  
  
#### <a name="to-test-your-form"></a>K otestování formuláře  
  
1.  Stisknutím klávesy F5 kompilace a spuštění formuláře.  
  
2.  Klikněte na tlačítko **okno** otevřete nabídku a pak klikněte na položku nabídky **nový**.  
  
     V klientské oblasti formuláře MDI se vytvoří nový podřízený formulář. Nabídky podřízené formuláře je sloučen s hlavní nabídky.  
  
3.  Podřízený formulář zavřete.  
  
     Nabídky podřízené formuláře se odebere z hlavní nabídky.  
  
4.  Klikněte na tlačítko **nový** několikrát.  
  
     Podřízené formuláře se automaticky zobrazí **okno** položky nabídky, protože <xref:System.Windows.Forms.MenuStrip> ovládacího prvku <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> přiřadit vlastnosti.  
  
## <a name="adding-toolstrip-support"></a>Přidání podpory pro ovládací prvek ToolStrip  
 V tomto postupu přidáte čtyři <xref:System.Windows.Forms.ToolStrip> ovládacích prvků na nadřazený formulář MDI. Každý <xref:System.Windows.Forms.ToolStrip> ovládací prvek je přidán uvnitř <xref:System.Windows.Forms.ToolStripPanel> ovládací prvek, který je ukotven k okraji formuláře.  
  
#### <a name="to-add-toolstrip-controls-to-the-mdi-parent-form"></a>Přidání ovládacích prvků ToolStrip nadřazený formulář MDI  
  
1.  Z **nástrojů**, přetáhněte <xref:System.Windows.Forms.ToolStripPanel> ovládací prvek na formuláři.  
  
2.  S <xref:System.Windows.Forms.ToolStripPanel> vybraný ovládací prvek, dvakrát klikněte <xref:System.Windows.Forms.ToolStrip> v ovládacím prvku **nástrojů**.  
  
     A <xref:System.Windows.Forms.ToolStrip> ovládací prvek je vytvořen v <xref:System.Windows.Forms.ToolStripPanel> ovládacího prvku.  
  
3.  Vyberte <xref:System.Windows.Forms.ToolStripPanel> ovládacího prvku.  
  
4.  V okně Vlastnosti změňte hodnotu ovládacího prvku <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Left>.  
  
     <xref:System.Windows.Forms.ToolStripPanel> Řídit ukotví na levou stranu formuláře pod hlavní nabídky. V oblasti klienta MDI přizpůsobí svou velikost <xref:System.Windows.Forms.ToolStripPanel> ovládacího prvku.  
  
5.  Opakujte kroky 1 až 4.  
  
     Ukotvit nové <xref:System.Windows.Forms.ToolStripPanel> ovládacího prvku do horní části formuláře.  
  
     <xref:System.Windows.Forms.ToolStripPanel> Ovládací prvek ukotven pod hlavní nabídky, ale napravo od prvního <xref:System.Windows.Forms.ToolStripPanel> ovládacího prvku. Tento krok ukazuje důležitost pořadí vykreslování v správně umístění <xref:System.Windows.Forms.ToolStripPanel> ovládacích prvků.  
  
6.  Opakujte kroky 1 až 4 pro dva další <xref:System.Windows.Forms.ToolStripPanel> ovládacích prvků.  
  
     Ukotvit nové <xref:System.Windows.Forms.ToolStripPanel> ovládacích prvků doprava a dolní části formuláře.  
  
## <a name="arranging-toolstrippanel-controls-by-z-order"></a>Uspořádání ToolStripPanel – ovládací prvky podle pořadí vykreslování  
 Pozice ukotvených <xref:System.Windows.Forms.ToolStripPanel> ovládací prvek formuláře MDI se určuje podle pozice ovládacího prvku v pořadí vykreslování. Snadno můžete uspořádat pořadí vykreslování ovládacích prvků v okně osnovy dokumentu.  
  
#### <a name="to-arrange-toolstrippanel-controls-by-z-order"></a>Uspořádat podle pořadí vykreslování ovládacími prvky ToolStripPanel  
  
1.  V **zobrazení** nabídky, klikněte na tlačítko **ostatní Windows**a potom klikněte na tlačítko **Osnova dokumentu**.  
  
     Uspořádání vašich <xref:System.Windows.Forms.ToolStripPanel> ovládací prvky z předchozího postupu je nestandardní. Je to proto, že pořadí vykreslování není správný. Chcete-li změnit pořadí vykreslování ovládacích prvků použijte okno osnovy dokumentu.  
  
2.  V okně Osnova dokumentu vyberte **ToolStripPanel4**.  
  
3.  Klikněte na tlačítko se šipkou dolů opakovaně, dokud **ToolStripPanel4** je v dolní části seznamu.  
  
     **ToolStripPanel4** ovládací prvek ukotven k dolní části formuláře, pod ostatní ovládací prvky.  
  
4.  Vyberte **ToolStripPanel2**.  
  
5.  Kliknutím na tlačítko se šipkou dolů jednou třetí umístění ovládacího prvku v seznamu.  
  
     **ToolStripPanel2** ovládací prvek ukotven k hornímu okraji pod hlavní nabídky a vyšší než ostatní ovládací prvky formulář.  
  
6.  Vyberte různé ovládací prvky v **Osnova dokumentu** okno a přesouvat je na jinou pozici v pořadí vykreslování. Všimněte si vliv pořadí vykreslování na umístění ukotvených ovládacích prvků. Pomocí CTRL-Z nebo **zpět** na **upravit** nabídky vrátit zpět provedené změny.  
  
## <a name="checkpoint"></a>Kontrolní bod  
  
#### <a name="to-test-your-form"></a>K otestování formuláře  
  
1.  Stisknutím klávesy F5 kompilace a spuštění formuláře.  
  
2.  Klikněte na úchytu o <xref:System.Windows.Forms.ToolStrip> řídit a přetáhněte jej na různých místech ve formuláři.  
  
     Můžete přetáhnout <xref:System.Windows.Forms.ToolStrip> ovládacího prvku z jednoho <xref:System.Windows.Forms.ToolStripPanel> ovládacího prvku do jiného.  
  
## <a name="next-steps"></a>Další kroky  
 V tomto návodu vytvoříte nadřazené formuláře MDI s <xref:System.Windows.Forms.ToolStrip> ovládací prvky a slučování nabídek. Můžete použít <xref:System.Windows.Forms.ToolStrip> řady ovládacích prvků pro mnoho dalších důvodů:  
  
-   Vytváření místních nabídek pro vaše ovládací prvky s <xref:System.Windows.Forms.ContextMenuStrip>. Další informace najdete v tématu [ContextMenu – přehled komponenty](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).  
  
-   Vytvoření formuláře se automaticky vyplněná standardní nabídky. Další informace najdete v tématu [návod: poskytnutí standardních položek nabídky do formuláře](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).  
  
-   Zadejte vaše <xref:System.Windows.Forms.ToolStrip> řídí profesionální vzhled. Další informace najdete v tématu [postupy: nastavení vykreslovacího modulu prvku ToolStrip pro aplikaci](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [Postupy: Vytváření nadřazených formulářů MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [Postupy: Vytváření podřízených formulářů MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [Postupy: Vložení prvku MenuStrip do rozevíracího seznamu MDI](../../../../docs/framework/winforms/controls/how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)  
 [Ovládací prvek ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
