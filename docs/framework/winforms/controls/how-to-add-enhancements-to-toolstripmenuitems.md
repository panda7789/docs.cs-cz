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
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a><span data-ttu-id="4f625-102">Postupy: Přidání vylepšení do ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="4f625-102">How to: Add Enhancements to ToolStripMenuItems</span></span>
<span data-ttu-id="4f625-103">Použitelnost <xref:System.Windows.Forms.MenuStrip> a<xref:System.Windows.Forms.ContextMenuStrip> ovládacích prvků lze rozšířit následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="4f625-103">You can enhance the usability of <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> controls in the following ways:</span></span>  
  
- <span data-ttu-id="4f625-104">Přidáním značek zaškrtnutí můžete určit, zda je funkce zapnuta nebo vypnuta, například zda je zobrazeno pravítko podél okraje aplikace pro zpracování textu, nebo určit, který soubor je zobrazen v seznamu souborů, například v nabídce **okna** .</span><span class="sxs-lookup"><span data-stu-id="4f625-104">Add check marks to designate whether a feature is turned on or off, such as whether a ruler is displayed along the margin of a word-processing application, or to indicate which file in a list of files is being displayed, such as on a **Window** menu.</span></span>  
  
- <span data-ttu-id="4f625-105">Přidejte obrázky, které vizuálně reprezentují příkazy nabídky.</span><span class="sxs-lookup"><span data-stu-id="4f625-105">Add images that visually represent menu commands.</span></span>  
  
- <span data-ttu-id="4f625-106">Zobrazení klávesových zkratek pro alternativní použití myši k provádění příkazů</span><span class="sxs-lookup"><span data-stu-id="4f625-106">Display shortcut keys to provide a keyboard alternative to the mouse for performing commands.</span></span> <span data-ttu-id="4f625-107">Například stisknutím kombinace kláves CTRL + C provede příkaz **Kopírovat** .</span><span class="sxs-lookup"><span data-stu-id="4f625-107">For example, pressing CTRL+C performs the **Copy** command.</span></span>  
  
- <span data-ttu-id="4f625-108">Zobrazení přístupových kláves pro klávesovou zkratku myši pro navigaci v nabídce</span><span class="sxs-lookup"><span data-stu-id="4f625-108">Display access keys to provide a keyboard alternative to the mouse for menu navigation.</span></span> <span data-ttu-id="4f625-109">Například stisknutím kombinace kláves ALT + F zvolíte nabídku **soubor** .</span><span class="sxs-lookup"><span data-stu-id="4f625-109">For example, pressing ALT+F chooses the **File** menu.</span></span>  
  
- <span data-ttu-id="4f625-110">Zobrazením oddělovacích pruhů můžete seskupit související příkazy a usnadnit čtení nabídek.</span><span class="sxs-lookup"><span data-stu-id="4f625-110">Show separator bars to group related commands and make menus more readable.</span></span>  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a><span data-ttu-id="4f625-111">Zobrazení značky zaškrtnutí u příkazu nabídky</span><span class="sxs-lookup"><span data-stu-id="4f625-111">To display a check mark on a menu command</span></span>  
  
- <span data-ttu-id="4f625-112">Nastavte vlastnost na `true`hodnotu. <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A></span><span class="sxs-lookup"><span data-stu-id="4f625-112">Set its <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="4f625-113">Tím se také nastaví <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> vlastnost na `true`.</span><span class="sxs-lookup"><span data-stu-id="4f625-113">This also sets the <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> property to `true`.</span></span> <span data-ttu-id="4f625-114">Tento postup použijte pouze v případě, že se má příkaz nabídky Zobrazit jako zaškrtnutý ve výchozím nastavení, bez ohledu na to, zda je vybrán.</span><span class="sxs-lookup"><span data-stu-id="4f625-114">Use this procedure only if you want the menu command to appear as checked by default, regardless of whether it is selected.</span></span>  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a><span data-ttu-id="4f625-115">Chcete-li zobrazit zaškrtnutí, že při každém kliknutí se mění stav</span><span class="sxs-lookup"><span data-stu-id="4f625-115">To display a check mark that changes state with each click</span></span>  
  
- <span data-ttu-id="4f625-116">Nastavte <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> vlastnost příkazu nabídky na `true`.</span><span class="sxs-lookup"><span data-stu-id="4f625-116">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true`.</span></span>  
  
### <a name="to-add-an-image-to-a-menu-command"></a><span data-ttu-id="4f625-117">Přidání obrázku do příkazu nabídky</span><span class="sxs-lookup"><span data-stu-id="4f625-117">To add an image to a menu command</span></span>  
  
- <span data-ttu-id="4f625-118">Nastavte <xref:System.Windows.Forms.ToolStripItem.Image%2A> vlastnost příkazu nabídky na název obrázku.</span><span class="sxs-lookup"><span data-stu-id="4f625-118">Set the menu command's <xref:System.Windows.Forms.ToolStripItem.Image%2A> property to the name of the image.</span></span> <span data-ttu-id="4f625-119">Pokud je <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>vlastnost tohoto příkazu nabídky nastavená na nebo, obrázek se nedá zobrazit. <xref:System.Windows.Forms.ToolStripItemDisplayStyle></span><span class="sxs-lookup"><span data-stu-id="4f625-119">If the <xref:System.Windows.Forms.ToolStripItemDisplayStyle> property of this menu command is set to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> or <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, the image cannot be displayed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4f625-120">Pokud si zvolíte, okraj pro obrázek může také zobrazit značku zaškrtnutí.</span><span class="sxs-lookup"><span data-stu-id="4f625-120">The image margin can also show a check mark if you so choose.</span></span> <span data-ttu-id="4f625-121">Také můžete nastavit <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> vlastnost obrázku na `true`a obrázek se zobrazí s šrafované ohraničení v době běhu.</span><span class="sxs-lookup"><span data-stu-id="4f625-121">Also, you can set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property of the image to `true`, and the image will appear with a hatched border around it at run time.</span></span>  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a><span data-ttu-id="4f625-122">Zobrazení klávesových zkratek pro příkaz nabídky</span><span class="sxs-lookup"><span data-stu-id="4f625-122">To display a shortcut key for a menu command</span></span>  
  
- <span data-ttu-id="4f625-123">Nastavte <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> vlastnost příkazu nabídky na požadovanou kombinaci kláves, jako je například CTRL + O pro příkaz **otevřít** nabídku a nastavte <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> vlastnost na `true`hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4f625-123">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> property to the desired keyboard combination, such as CTRL+O for the **Open** menu command, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a><span data-ttu-id="4f625-124">Zobrazení vlastních klávesových zkratek pro příkaz nabídky</span><span class="sxs-lookup"><span data-stu-id="4f625-124">To display custom shortcut keys for a menu command</span></span>  
  
- <span data-ttu-id="4f625-125">Nastavte <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> vlastnost příkazu nabídky na požadovanou kombinaci kláves, například CTRL + SHIFT + o, místo kombinace kláves Shift + Ctrl + o a <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> nastavte vlastnost na `true`hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4f625-125">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> property to the desired keyboard combination, such as CTRL+SHIFT+O rather than SHIFT+CTRL+O, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a><span data-ttu-id="4f625-126">Zobrazení přístupové klávesy pro příkaz nabídky</span><span class="sxs-lookup"><span data-stu-id="4f625-126">To display an access key for a menu command</span></span>  
  
- <span data-ttu-id="4f625-127">Když nastavíte <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost příkazu nabídky, zadejte ampersand (&) před písmeno, které má být podtržené jako přístupový klíč.</span><span class="sxs-lookup"><span data-stu-id="4f625-127">When you set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property for the menu command, enter an ampersand (&) before the letter you want to be underlined as the access key.</span></span> <span data-ttu-id="4f625-128">Například zadání `&Open` <xref:System.Windows.Forms.ToolStripItem.Text%2A> jako vlastnost položky nabídky má za následek příkaz nabídky, který se zobrazí jako <u>O</u>Peru.</span><span class="sxs-lookup"><span data-stu-id="4f625-128">For example, typing `&Open` as the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of a menu item will result in a menu command that appears as <u>O</u>pen.</span></span>
  
     <span data-ttu-id="4f625-129">Chcete-li přejít do tohoto příkazu nabídky, stiskněte klávesu ALT <xref:System.Windows.Forms.MenuStrip>, aby se zadala fokus, a stiskněte přístupový klíč názvu nabídky.</span><span class="sxs-lookup"><span data-stu-id="4f625-129">To navigate to this menu command, press ALT to give focus to the <xref:System.Windows.Forms.MenuStrip>, and press the access key of the menu name.</span></span> <span data-ttu-id="4f625-130">Po otevření nabídky a zobrazení položek s přístupovými klíči stačí stisknout přístupovou klávesu a vybrat příkaz nabídky.</span><span class="sxs-lookup"><span data-stu-id="4f625-130">When the menu opens and shows items with access keys, you only need to press the access key to select the menu command.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4f625-131">Vyhněte se definování duplicitních přístupových klíčů, například definování ALT + F dvakrát ve stejném systému nabídek.</span><span class="sxs-lookup"><span data-stu-id="4f625-131">Avoid defining duplicate access keys, such as defining ALT+F twice in the same menu system.</span></span> <span data-ttu-id="4f625-132">Nelze zaručit pořadí výběru duplicitních přístupových klíčů.</span><span class="sxs-lookup"><span data-stu-id="4f625-132">The selection order of duplicate access keys cannot be guaranteed.</span></span>  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a><span data-ttu-id="4f625-133">Zobrazení oddělovacího panelu mezi příkazy nabídky</span><span class="sxs-lookup"><span data-stu-id="4f625-133">To display a separator bar between menu commands</span></span>  
  
- <span data-ttu-id="4f625-134">Po <xref:System.Windows.Forms.MenuStrip> definování a položek, které bude obsahovat, <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> použijte metodu nebo <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> pro <xref:System.Windows.Forms.MenuStrip> Přidání příkazů nabídky a <xref:System.Windows.Forms.ToolStripSeparator> ovládacích prvků do v požadovaném pořadí.</span><span class="sxs-lookup"><span data-stu-id="4f625-134">After you define your <xref:System.Windows.Forms.MenuStrip> and the items it will contain, use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> or <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> method to add the menu commands and <xref:System.Windows.Forms.ToolStripSeparator> controls to the <xref:System.Windows.Forms.MenuStrip> in the order you want.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4f625-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4f625-135">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="4f625-136">Přehled ovládacího prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="4f625-136">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
