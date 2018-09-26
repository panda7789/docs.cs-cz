---
title: 'Postupy: Přidání vylepšení do ToolStripMenuItems'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- commands [Windows Forms], grouping on menus
- check marks [Windows Forms], adding to menus
- ToolStripMenuItems [Windows Forms], displaying access keys
- menus [Windows Forms], grouping commands
- menu items [Windows Forms], displaying shortcut keys
- ToolStripMenuItems
- separators [Windows Forms], displaying on menus
- menu items [Windows Forms], showing separators
- menu items [Windows Forms], adding check marks
- ToolStripMenuItems [Windows Forms], adding check marks
- menu items [Windows Forms], adding images
- ToolStripSeparators [Windows Forms], displaying on MenuStrips
- menu items [Windows Forms], displaying access keys
- ToolStripMenuItems [Windows Forms], displaying shortcut keys
- ToolStripMenuItems [Windows Forms], adding images
- keyboard shortcuts [Windows Forms], displaying on menus
- images [Windows Forms], adding to menus
- ToolStripMenuItems [Windows Forms], showing separator bars
ms.assetid: aa5f19bb-b545-4378-bfa6-36ba592f0d7c
ms.openlocfilehash: eb55796480bea896383da479fe23a5d8967a52e3
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47090523"
---
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a>Postupy: Přidání vylepšení do ToolStripMenuItems
Můžete zlepšit použitelnost <xref:System.Windows.Forms.MenuStrip> a <xref:System.Windows.Forms.ContextMenuStrip> ovládacích prvků následujícími způsoby:  
  
-   Přidání značek zaškrtnutí k určení, zda funkce je zapnout nebo vypnout, například zda pravítka se zobrazují podél na okraji aplikace pro zpracování textu, nebo k označení, který soubor v seznamu souborů, která má být zobrazeny, například jako na **okno** nabídka.  
  
-   Přidání bitové kopie, které vizuálně představují příkazy nabídky.  
  
-   Zobrazí klávesové zkratky, které poskytují alternativní klávesnice k myši pro provádění příkazů. Například provádí kombinace kláves CTRL + C **kopírování** příkazu.  
  
-   Zobrazení přístupových klíčů k poskytnutí klávesnice alternativou k myši pro navigační nabídky. Například stisknutím klávesy ALT + F klikne **souboru** nabídky.  
  
-   Zobrazení oddělovacích pruhů seskupovat související příkazy a nabídky čitelnost.  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a>Chcete-li zobrazit značku zaškrtnutí v příkazu nabídky  
  
-   Nastavte jeho <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> vlastnost `true`.  
  
     Zároveň se nastaví <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> vlastnost `true`. Pokud chcete, aby příkaz nabídky zobrazí jako zaškrtnuté ve výchozím nastavení, bez ohledu na to, zda je zaškrtnuto, pomocí tohoto postupu.  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a>Zobrazit značku zaškrtnutí, která změní stav každého kliknutím  
  
-   Nastavení příkazu nabídky <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> vlastnost `true`.  
  
### <a name="to-add-an-image-to-a-menu-command"></a>Chcete-li přidat bitovou kopii k příkazu nabídky  
  
-   Nastavení příkazu nabídky <xref:System.Windows.Forms.ToolStripItem.Image%2A> vlastnost na název obrázku. Pokud <xref:System.Windows.Forms.ToolStripItemDisplayStyle> tohoto příkazu nabídky je nastavena na <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> nebo <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, nelze zobrazit obrázek.  
  
> [!NOTE]
>  Okraji pro obrázek můžete také zobrazit zaškrtávací políčko Pokud se pro to rozhodnete. Kromě toho můžete nastavit <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> vlastnosti obrázku, který se `true`, a image se zobrazí s šrafované ohraničení kolem něj v době běhu.  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a>Chcete-li zobrazit klávesovou zkratku pro příkaz nabídky  
  
-   Nastavení příkazu nabídky <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> vlastnost kombinaci požadované klávesnice, jako je například CTRL + O pro **otevřít** příkaz nabídky a nastavte <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> vlastnost `true`.  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a>Chcete-li zobrazit vlastní klávesové zkratky pro příkaz nabídky  
  
-   Nastavení příkazu nabídky <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> kombinaci požadované klávesnice, jako je například CTRL + SHIFT + O spíše než CTRL + SHIFT + O a nastavte vlastnost <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> vlastnost `true`.  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a>Chcete-li zobrazit přístupový klíč pro příkaz nabídky  
  
-   Při nastavení <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost pro příkaz nabídky zadejte znak ampersand (&) před písmeno chcete podtržena jako přístupový klíč. Například zadáte `&Open` jako <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastností položky nabídky bude výsledkem příkazu nabídky, která se zobrazí jako <u>O</u>pera.
  
     Přejděte na tento příkaz nabídky, stiskněte klávesu ALT k nastavení fokusu na <xref:System.Windows.Forms.MenuStrip>a stiskněte klávesu přístupový klíč název nabídky. Když v nabídce se otevře a zobrazí položky se přístupové klíče, stačí ke stisknutí přístupové klávesy vyberete příkaz nabídky.  
  
> [!NOTE]
>  Vyhněte se definování duplicitní přístupové klávesy, jako je například definování ALT + F dvakrát ve stejném systému nabídky. Nelze zaručit pořadí výběru duplicitní přístupové klávesy.  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a>Chcete-li zobrazit oddělovač mezi příkazy nabídky  
  
-   Po definování vašich <xref:System.Windows.Forms.MenuStrip> a v položkách, bude obsahovat, použijte <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> nebo <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> metoda pro přidání příkazů nabídky a <xref:System.Windows.Forms.ToolStripSeparator> ovládacích prvků do <xref:System.Windows.Forms.MenuStrip> v pořadí, které chcete.  
  
    ```vb  
    ' This code adds a top-level File menu to the MenuStrip.  
    Me.menuStrip1.Items.Add(New ToolStripMenuItem() _  
    {Me.fileToolStripMenuItem})  
  
    ' This code adds the New and Open menu commands, a separator bar,   
    ' and the Save and Exit menu commands to the top-level File menu,   
    ' in that order.  
    Me.fileToolStripMenuItem.DropDownItems.AddRange(New _  
    ToolStripMenuItem() {Me.newToolStripMenuItem, _  
    Me.openToolStripMenuItem, Me.toolStripSeparator1, _  
    Me.saveToolStripMenuItem, Me.exitToolStripMenuItem})  
    ```  
  
    ```csharp  
    // This code adds a top-level File menu to the MenuStrip.  
    this.menuStrip1.Items.Add(new ToolStripItem[]_  
    {this.fileToolStripMenuItem});  
  
    // This code adds the New and Open menu commands, a separator bar,   
    // and the Save and Exit menu commands to the top-level File menu,   
    // in that order.  
    this.fileToolStripMenuItem.DropDownItems.AddRange(new _  
    ToolStripItem[] {  
    this.newToolStripMenuItem,  
    this.openToolStripMenuItem,  
    this.toolStripSeparator1,  
    this.saveToolStripMenuItem,  
    this.exitToolStripMenuItem});  
    ```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [Přehled ovládacího prvku MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
