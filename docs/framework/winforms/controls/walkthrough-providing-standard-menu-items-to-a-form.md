---
title: 'Návod: Zajištění standardních položek nabídky pro formulář'
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
ms.openlocfilehash: b4957a3f2efcb31594806a188e3d3bb10c2dac09
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59296391"
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a>Návod: Zajištění standardních položek nabídky pro formulář
Můžete zadat standardní nabídky formuláře s <xref:System.Windows.Forms.MenuStrip> ovládacího prvku.  
  
 Tento návod ukazuje, jak používat <xref:System.Windows.Forms.MenuStrip> řízení vytvořit standardní nabídku. Formuláře také reaguje, když uživatel vybere položku nabídky. Tyto úlohy jsou uvedené v tomto návodu:  
  
-   Vytvoření projektu Windows Forms.  
  
-   Vytvoření standardní nabídky.  
  
-   Vytváření <xref:System.Windows.Forms.StatusStrip> ovládacího prvku.  
  
-   Zpracování výběru položky nabídky.  
  
 Až budete hotovi, budete mít formulář s standardní nabídky, která zobrazuje výběru položky nabídky v <xref:System.Windows.Forms.StatusStrip> ovládacího prvku.  
  
 Pokud chcete zkopírovat kód v tomto tématu jako jeden seznam, naleznete v tématu [jak: Zajištění standardních položek nabídky pro formulář](how-to-provide-standard-menu-items-to-a-form.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat:  
  
-   Dostatečná oprávnění k vytvoření a spuštění projektů aplikace Windows Forms v počítači nainstalovanou aplikaci Visual Studio.  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu a nastavení formuláře.  
  
#### <a name="to-create-the-project"></a>Vytvoření projektu  
  
1. Vytvoření projektu aplikace Windows volá **StandardMenuForm** (**souboru** > **nový** > **projektu**  >  **Visual C#** nebo **jazyka Visual Basic** > **klasický desktopový** > **Windows Forms Aplikace**).  
  
2. V Návrháři formulářů Windows vyberte formulář.  
  
## <a name="creating-a-standard-menu"></a>Vytvoření standardní nabídky  
 Návrhář formulářů Windows můžete automaticky naplnit <xref:System.Windows.Forms.MenuStrip> ovládací prvek s standardních položek nabídky.  
  
#### <a name="to-create-a-standard-menu"></a>Chcete-li vytvořit standardní nabídky  
  
1. Z **nástrojů**, přetáhněte <xref:System.Windows.Forms.MenuStrip> ovládacího prvku na formulář.  
  
2. Klikněte na tlačítko <xref:System.Windows.Forms.MenuStrip> piktogram inteligentní značky ovládacího prvku (![piktogram inteligentní](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) a vyberte **vložit standardní položky**.  
  
     <xref:System.Windows.Forms.MenuStrip> Ovládací prvek se vyplní standardních položek nabídky.  
  
3. Klikněte na tlačítko **souboru** položka nabídky zobrazit jeho výchozí položky nabídky a odpovídajících ikon.  
  
## <a name="creating-a-statusstrip-control"></a>Vytvoření ovládacího prvku StatusStrip  
 Použití <xref:System.Windows.Forms.StatusStrip> ovládací prvek pro zobrazení stavu pro aplikace Windows Forms. V uvedeném příkladě se zobrazí položky nabídky vybraných uživatelem v <xref:System.Windows.Forms.StatusStrip> ovládacího prvku.  
  
#### <a name="to-create-a-statusstrip-control"></a>Vytvoření ovládacího prvku StatusStrip  
  
1. Z **nástrojů**, přetáhněte <xref:System.Windows.Forms.StatusStrip> ovládacího prvku na formulář.  
  
     <xref:System.Windows.Forms.StatusStrip> Ovládací prvek automaticky ukotvené do dolní části formuláře.  
  
2. Klikněte na tlačítko <xref:System.Windows.Forms.StatusStrip> ovládacího prvku tlačítko rozevíracího seznamu a vyberte **StatusLabel** přidáte <xref:System.Windows.Forms.ToolStripStatusLabel> ovládací prvek <xref:System.Windows.Forms.StatusStrip> ovládacího prvku.  
  
## <a name="handling-item-selection"></a>Výběr položek zpracování  
 Zpracování <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> události a reagovat, když uživatel vybere položku nabídky.  
  
#### <a name="to-handle-item-selection"></a>Pro zpracování výběr položky  
  
1. Klikněte na tlačítko **soubor** položku nabídky, kterou jste vytvořili v části Vytvoření oddílu standardní nabídky.  
  
2. V **vlastnosti** okna, klikněte na tlačítko **události**.  
  
3. Dvakrát klikněte <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> událostí.  
  
     Návrhář formulářů Windows generuje obslužná rutina události <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> událostí.  
  
4. Vložte následující kód do obslužné rutiny události.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]  
  
5. Vložit `UpdateStatus` nástroj definici metody do formuláře.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]  
  
## <a name="checkpoint"></a>CheckPoint  
  
#### <a name="to-test-your-form"></a>K otestování formuláře  
  
1. Stisknutím klávesy F5 kompilace a spuštění formuláře.  
  
2. Klikněte na tlačítko **souboru** položky nabídky a otevřete nabídku.  
  
3. Na **souboru** nabídky, klikněte na jednu z položek, vyberte ho.  
  
     <xref:System.Windows.Forms.StatusStrip> Ovládací prvek zobrazuje vybrané položky.  
  
## <a name="next-steps"></a>Další kroky  
 V tomto návodu jste vytvořili, pomocí standardní nabídky formuláře. Můžete použít <xref:System.Windows.Forms.ToolStrip> řady ovládacích prvků pro mnoho dalších důvodů:  
  
-   Vytváření místních nabídek pro vaše ovládací prvky s <xref:System.Windows.Forms.ContextMenuStrip>. Další informace najdete v tématu [ContextMenu – přehled komponenty](contextmenu-component-overview-windows-forms.md).  
  
-   Vytvoření více formuláře (MDI interface) dokumentu s ukotvení <xref:System.Windows.Forms.ToolStrip> ovládacích prvků. Další informace najdete v tématu [názorný postup: Vytvoření formuláře MDI s ovládacími prvky ToolStrip a slučování nabídek](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).  
  
-   Zadejte vaše <xref:System.Windows.Forms.ToolStrip> řídí profesionální vzhled. Další informace najdete v tématu [jak: Nastavení vykreslovacího modulu prvku ToolStrip pro aplikaci](how-to-set-the-toolstrip-renderer-for-an-application.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [Ovládací prvek MenuStrip](menustrip-control-windows-forms.md)
