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
ms.openlocfilehash: 9e95c3623bf9bad8395f586392a0557ad1cde880
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912588"
---
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a>Postupy: Přidání vylepšení do ToolStripMenuItems
Použitelnost <xref:System.Windows.Forms.MenuStrip> a<xref:System.Windows.Forms.ContextMenuStrip> ovládacích prvků lze rozšířit následujícími způsoby:  
  
- Přidáním značek zaškrtnutí můžete určit, zda je funkce zapnuta nebo vypnuta, například zda je zobrazeno pravítko podél okraje aplikace pro zpracování textu, nebo určit, který soubor je zobrazen v seznamu souborů, například v nabídce **okna** .  
  
- Přidejte obrázky, které vizuálně reprezentují příkazy nabídky.  
  
- Zobrazení klávesových zkratek pro alternativní použití myši k provádění příkazů Například stisknutím kombinace kláves CTRL + C provede příkaz **Kopírovat** .  
  
- Zobrazení přístupových kláves pro klávesovou zkratku myši pro navigaci v nabídce Například stisknutím kombinace kláves ALT + F zvolíte nabídku **soubor** .  
  
- Zobrazením oddělovacích pruhů můžete seskupit související příkazy a usnadnit čtení nabídek.  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a>Zobrazení značky zaškrtnutí u příkazu nabídky  
  
- Nastavte vlastnost na `true`hodnotu. <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>  
  
     Tím se také nastaví <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> vlastnost na `true`. Tento postup použijte pouze v případě, že se má příkaz nabídky Zobrazit jako zaškrtnutý ve výchozím nastavení, bez ohledu na to, zda je vybrán.  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a>Chcete-li zobrazit zaškrtnutí, že při každém kliknutí se mění stav  
  
- Nastavte <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> vlastnost příkazu nabídky na `true`.  
  
### <a name="to-add-an-image-to-a-menu-command"></a>Přidání obrázku do příkazu nabídky  
  
- Nastavte <xref:System.Windows.Forms.ToolStripItem.Image%2A> vlastnost příkazu nabídky na název obrázku. Pokud je <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>vlastnost tohoto příkazu nabídky nastavená na nebo, obrázek se nedá zobrazit. <xref:System.Windows.Forms.ToolStripItemDisplayStyle>  
  
> [!NOTE]
> Pokud si zvolíte, okraj pro obrázek může také zobrazit značku zaškrtnutí. Také můžete nastavit <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> vlastnost obrázku na `true`a obrázek se zobrazí s šrafované ohraničení v době běhu.  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a>Zobrazení klávesových zkratek pro příkaz nabídky  
  
- Nastavte <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> vlastnost příkazu nabídky na požadovanou kombinaci kláves, jako je například CTRL + O pro příkaz **otevřít** nabídku a nastavte <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> vlastnost na `true`hodnotu.  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a>Zobrazení vlastních klávesových zkratek pro příkaz nabídky  
  
- Nastavte <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> vlastnost příkazu nabídky na požadovanou kombinaci kláves, například CTRL + SHIFT + o, místo kombinace kláves Shift + Ctrl + o a <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> nastavte vlastnost na `true`hodnotu.  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a>Zobrazení přístupové klávesy pro příkaz nabídky  
  
- Když nastavíte <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost příkazu nabídky, zadejte ampersand (&) před písmeno, které má být podtržené jako přístupový klíč. Například zadání `&Open` <xref:System.Windows.Forms.ToolStripItem.Text%2A> jako vlastnost položky nabídky má za následek příkaz nabídky, který se zobrazí jako <u>O</u>Peru.
  
     Chcete-li přejít do tohoto příkazu nabídky, stiskněte klávesu ALT <xref:System.Windows.Forms.MenuStrip>, aby se zadala fokus, a stiskněte přístupový klíč názvu nabídky. Po otevření nabídky a zobrazení položek s přístupovými klíči stačí stisknout přístupovou klávesu a vybrat příkaz nabídky.  
  
> [!NOTE]
> Vyhněte se definování duplicitních přístupových klíčů, například definování ALT + F dvakrát ve stejném systému nabídek. Nelze zaručit pořadí výběru duplicitních přístupových klíčů.  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a>Zobrazení oddělovacího panelu mezi příkazy nabídky  
  
- Po <xref:System.Windows.Forms.MenuStrip> definování a položek, které bude obsahovat, <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> použijte metodu nebo <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> pro <xref:System.Windows.Forms.MenuStrip> Přidání příkazů nabídky a <xref:System.Windows.Forms.ToolStripSeparator> ovládacích prvků do v požadovaném pořadí.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [Přehled ovládacího prvku MenuStrip](menustrip-control-overview-windows-forms.md)
