---
title: "Postupy: Přidání vylepšení do ToolStripMenuItems"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 075370b56ab9e73434394e15a25cd5ce6cd043bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a>Postupy: Přidání vylepšení do ToolStripMenuItems
Můžete vylepšit použitelnost <xref:System.Windows.Forms.MenuStrip> a <xref:System.Windows.Forms.ContextMenuStrip> ovládací prvky následujícími způsoby:  
  
-   Přidání značek zaškrtnutí k označení, zda funkce je zapnout nebo vypnout, například zda pravítko se zobrazují podél na okraji textového procesoru, a který soubor v seznam souborů, která má být zobrazeny, například jako na **okno** nabídky.  
  
-   Přidání bitové kopie, které představují vizuální příkazy nabídky.  
  
-   Zobrazit klávesové zkratky, které poskytují klávesnice alternativa k přesunutí myši pro provádění příkazů. Například kombinace kláves CTRL + C provádí **kopie** příkaz.  
  
-   Zobrazení přístupových kláves zajistit klávesnice alternativa k přesunutí myši pro navigační nabídky. Například stisknutím ALT + F rozhodne **souboru** nabídky.  
  
-   Zobrazení oddělovacích pruhů k seskupení souvisejících s příkazy a čitelnost nabídky.  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a>Chcete-li zobrazit zaškrtnutí příkazu nabídky  
  
-   Nastavte její <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> vlastnost `true`.  
  
     Zároveň se nastaví <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> vlastnost `true`. Tento postup použijte, pouze pokud chcete, aby příkaz nabídky zobrazit ve výchozím nastavení, bez ohledu na to, jestli je vybraná jako zaškrtnuté.  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a>Chcete-li zobrazit zaškrtnutí, které změní stav každého kliknutím  
  
-   Nastavit příkaz nabídky <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> vlastnost `true`.  
  
### <a name="to-add-an-image-to-a-menu-command"></a>Chcete-li přidat bitovou kopii k příkazu nabídky  
  
-   Nastavit příkaz nabídky <xref:System.Windows.Forms.ToolStripItem.Image%2A> vlastnost na název obrázku. Pokud <xref:System.Windows.Forms.ToolStripItemDisplayStyle> tohoto příkazu nabídky je nastavena na <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> nebo <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, bitovou kopii nelze zobrazit.  
  
> [!NOTE]
>  Okraj bitové kopie můžete také zobrazit zaškrtnutí Pokud proto zvolte. Také můžete nastavit <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> vlastnost bitové kopie a `true`, a bitovou kopii se zobrazí s šrafované ohraničení za běhu.  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a>Chcete-li zobrazit klávesovou zkratku příkazu nabídky  
  
-   Nastavit příkaz nabídky <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> vlastnost na kombinaci požadované klávesnice, jako je například CTRL + O pro **otevřete** příkazu v nabídce a nastavte <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> vlastnost `true`.  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a>Chcete-li zobrazit vlastní klávesové zkratky pro příkaz nabídky  
  
-   Nastavit příkaz nabídky <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> vlastnost na kombinaci požadované klávesnice, jako je například CTRL + SHIFT + O spíše než CTRL + SHIFT + O a nastavte <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> vlastnost `true`.  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a>Chcete-li zobrazit přístupový klíč pro příkaz nabídky  
  
-   Když nastavíte <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost pro příkaz nabídky zadejte ampersand (&) před písmeno, které chcete být podtržené jako přístupový klíč. Například zadáním `&Open` jako <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnosti položky nabídky bude mít za následek příkaz nabídky, která se zobrazí jako **O**pera.  
  
     Přejděte na tento příkaz nabídky, stiskněte klávesu ALT umožnit zaměření <xref:System.Windows.Forms.MenuStrip>a stiskněte klávesu přístupovým klíčem název nabídky. Když v nabídce otevře a zobrazuje položky s přístupové klíče, stačí stisknutím klávesy vyberte příkaz nabídky.  
  
> [!NOTE]
>  Nedefinujte duplicitní přístupové klíče, jako je například definování ALT + F dvakrát ve stejném systému nabídky. Výběr pořadí duplicitní přístupové klíče nemůže zaručit.  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a>Chcete-li zobrazit oddělovač mezi příkazy nabídky  
  
-   Po definování vaše <xref:System.Windows.Forms.MenuStrip> a v položkách, bude obsahovat, použijte <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> nebo <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> metody přidat příkazy nabídky a <xref:System.Windows.Forms.ToolStripSeparator> prvky <xref:System.Windows.Forms.MenuStrip> v pořadí, které chcete.  
  
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
