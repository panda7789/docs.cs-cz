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
ms.openlocfilehash: 61a79b9bbe101d7bf694240bdffdecee5187adf2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182325"
---
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a>Postupy: Přidání vylepšení do ToolStripMenuItems
Použitelnost a <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ContextMenuStrip> ovládací prvky můžete zvýšit následujícími způsoby:  
  
- Přidejte zaškrtnutí, chcete-li určit, zda je funkce zapnutá nebo vypnutá, například zda je pravítko zobrazeno podél okraje aplikace pro zpracování textu, nebo k označení, který soubor v seznamu souborů se zobrazuje, například v nabídce **Okno.**  
  
- Přidejte obrázky, které vizuálně představují příkazy nabídky.  
  
- Zobrazení klávesových zkratek poskytuje alternativu klávesnice k myši pro provádění příkazů. Například stisknutím kombinace kláves CTRL+C provedete příkaz **Kopírovat.**  
  
- Zobrazení přístupových kláves poskytuje alternativu klávesnice k myši pro navigaci v nabídce. Například stisknutím kláves ALT+F se vybere nabídka **Soubor.**  
  
- Zobrazí oddělovací pruhy pro seskupit související příkazy a zpřehlední nabídky.  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a>Zobrazení zaškrtnutí příkazu nabídky  
  
- Nastavte <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> jeho `true`vlastnost na .  
  
     Tím se <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> také `true`nastaví vlastnost . Tento postup použijte pouze v případě, že chcete, aby se příkaz nabídky zobrazoval ve výchozím nastavení jako kontrolovaný, bez ohledu na to, zda je vybrán.  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a>Zobrazení zaškrtnutí, které mění stav při každém kliknutí  
  
- Nastavte <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> vlastnost příkazu nabídky `true`na .  
  
### <a name="to-add-an-image-to-a-menu-command"></a>Přidání obrázku do příkazu nabídky  
  
- Nastavte <xref:System.Windows.Forms.ToolStripItem.Image%2A> vlastnost příkazu nabídky na název obrázku. Pokud <xref:System.Windows.Forms.ToolStripItemDisplayStyle> je vlastnost tohoto příkazu <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>nabídky nastavena na nebo , obraz nelze zobrazit.  
  
> [!NOTE]
> Okraj obrázku může také zobrazit zaškrtnutí, pokud tak zvolíte. Můžete také nastavit <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> vlastnost obrazu na `true`a obraz se zobrazí se šrafovaným ohraničením kolem něj za běhu.  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a>Zobrazení klávesové zkratky pro příkaz nabídky  
  
- Nastavte <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> vlastnost příkazu nabídky na požadovanou kombinaci kláves, například CTRL+O pro `true`příkaz **Otevřít** nabídku, <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> a nastavte vlastnost na .  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a>Zobrazení vlastních klávesových zkratek pro příkaz nabídky  
  
- Nastavte <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> vlastnost příkazu nabídky na požadovanou kombinaci kláves, například CTRL+SHIFT+O namísto <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> SHIFT+CTRL+O, a nastavte vlastnost na `true`.  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a>Zobrazení přístupového klíče pro příkaz nabídky  
  
- Když nastavíte <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost příkazu nabídky, zadejte ampersand (&) před písmeno, které chcete podtrženo jako přístupový klíč. Například zadáním `&Open` jako <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost položky nabídky bude příkaz nabídky, který se zobrazí jako <u>pero O.</u>
  
     Chcete-li přejít na tento příkaz nabídky, stisknutím klávesy ALT zaostřete na položku <xref:System.Windows.Forms.MenuStrip>a stiskněte přístupovou klávesu názvu nabídky. Když se nabídka otevře a zobrazí položky s přístupovými klávesami, stačí pouze stisknutím klávesy pro přístup vybrat příkaz nabídky.  
  
> [!NOTE]
> Vyhněte se definování duplicitních přístupových kláves, jako je například definování kláves ALT+F dvakrát ve stejném systému nabídek. Pořadí výběru duplicitních přístupových klíčů nelze zaručit.  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a>Zobrazení oddělovacího pruhu mezi příkazy nabídky  
  
- Po definování <xref:System.Windows.Forms.MenuStrip> vašich a položek, které <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> bude obsahovat, použijte <xref:System.Windows.Forms.ToolStripSeparator> metodu <xref:System.Windows.Forms.MenuStrip> nebo pro přidání příkazů a ovládacích prvků nabídky do požadovaného pořadí.  
  
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

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [MenuStrip – přehled ovládacího prvku](menustrip-control-overview-windows-forms.md)
