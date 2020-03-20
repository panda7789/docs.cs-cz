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
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a><span data-ttu-id="ffb1e-102">Postupy: Přidání vylepšení do ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="ffb1e-102">How to: Add Enhancements to ToolStripMenuItems</span></span>
<span data-ttu-id="ffb1e-103">Použitelnost a <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ContextMenuStrip> ovládací prvky můžete zvýšit následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="ffb1e-103">You can enhance the usability of <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> controls in the following ways:</span></span>  
  
- <span data-ttu-id="ffb1e-104">Přidejte zaškrtnutí, chcete-li určit, zda je funkce zapnutá nebo vypnutá, například zda je pravítko zobrazeno podél okraje aplikace pro zpracování textu, nebo k označení, který soubor v seznamu souborů se zobrazuje, například v nabídce **Okno.**</span><span class="sxs-lookup"><span data-stu-id="ffb1e-104">Add check marks to designate whether a feature is turned on or off, such as whether a ruler is displayed along the margin of a word-processing application, or to indicate which file in a list of files is being displayed, such as on a **Window** menu.</span></span>  
  
- <span data-ttu-id="ffb1e-105">Přidejte obrázky, které vizuálně představují příkazy nabídky.</span><span class="sxs-lookup"><span data-stu-id="ffb1e-105">Add images that visually represent menu commands.</span></span>  
  
- <span data-ttu-id="ffb1e-106">Zobrazení klávesových zkratek poskytuje alternativu klávesnice k myši pro provádění příkazů.</span><span class="sxs-lookup"><span data-stu-id="ffb1e-106">Display shortcut keys to provide a keyboard alternative to the mouse for performing commands.</span></span> <span data-ttu-id="ffb1e-107">Například stisknutím kombinace kláves CTRL+C provedete příkaz **Kopírovat.**</span><span class="sxs-lookup"><span data-stu-id="ffb1e-107">For example, pressing CTRL+C performs the **Copy** command.</span></span>  
  
- <span data-ttu-id="ffb1e-108">Zobrazení přístupových kláves poskytuje alternativu klávesnice k myši pro navigaci v nabídce.</span><span class="sxs-lookup"><span data-stu-id="ffb1e-108">Display access keys to provide a keyboard alternative to the mouse for menu navigation.</span></span> <span data-ttu-id="ffb1e-109">Například stisknutím kláves ALT+F se vybere nabídka **Soubor.**</span><span class="sxs-lookup"><span data-stu-id="ffb1e-109">For example, pressing ALT+F chooses the **File** menu.</span></span>  
  
- <span data-ttu-id="ffb1e-110">Zobrazí oddělovací pruhy pro seskupit související příkazy a zpřehlední nabídky.</span><span class="sxs-lookup"><span data-stu-id="ffb1e-110">Show separator bars to group related commands and make menus more readable.</span></span>  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a><span data-ttu-id="ffb1e-111">Zobrazení zaškrtnutí příkazu nabídky</span><span class="sxs-lookup"><span data-stu-id="ffb1e-111">To display a check mark on a menu command</span></span>  
  
- <span data-ttu-id="ffb1e-112">Nastavte <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> jeho `true`vlastnost na .</span><span class="sxs-lookup"><span data-stu-id="ffb1e-112">Set its <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="ffb1e-113">Tím se <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> také `true`nastaví vlastnost .</span><span class="sxs-lookup"><span data-stu-id="ffb1e-113">This also sets the <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> property to `true`.</span></span> <span data-ttu-id="ffb1e-114">Tento postup použijte pouze v případě, že chcete, aby se příkaz nabídky zobrazoval ve výchozím nastavení jako kontrolovaný, bez ohledu na to, zda je vybrán.</span><span class="sxs-lookup"><span data-stu-id="ffb1e-114">Use this procedure only if you want the menu command to appear as checked by default, regardless of whether it is selected.</span></span>  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a><span data-ttu-id="ffb1e-115">Zobrazení zaškrtnutí, které mění stav při každém kliknutí</span><span class="sxs-lookup"><span data-stu-id="ffb1e-115">To display a check mark that changes state with each click</span></span>  
  
- <span data-ttu-id="ffb1e-116">Nastavte <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> vlastnost příkazu nabídky `true`na .</span><span class="sxs-lookup"><span data-stu-id="ffb1e-116">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true`.</span></span>  
  
### <a name="to-add-an-image-to-a-menu-command"></a><span data-ttu-id="ffb1e-117">Přidání obrázku do příkazu nabídky</span><span class="sxs-lookup"><span data-stu-id="ffb1e-117">To add an image to a menu command</span></span>  
  
- <span data-ttu-id="ffb1e-118">Nastavte <xref:System.Windows.Forms.ToolStripItem.Image%2A> vlastnost příkazu nabídky na název obrázku.</span><span class="sxs-lookup"><span data-stu-id="ffb1e-118">Set the menu command's <xref:System.Windows.Forms.ToolStripItem.Image%2A> property to the name of the image.</span></span> <span data-ttu-id="ffb1e-119">Pokud <xref:System.Windows.Forms.ToolStripItemDisplayStyle> je vlastnost tohoto příkazu <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>nabídky nastavena na nebo , obraz nelze zobrazit.</span><span class="sxs-lookup"><span data-stu-id="ffb1e-119">If the <xref:System.Windows.Forms.ToolStripItemDisplayStyle> property of this menu command is set to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> or <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, the image cannot be displayed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ffb1e-120">Okraj obrázku může také zobrazit zaškrtnutí, pokud tak zvolíte.</span><span class="sxs-lookup"><span data-stu-id="ffb1e-120">The image margin can also show a check mark if you so choose.</span></span> <span data-ttu-id="ffb1e-121">Můžete také nastavit <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> vlastnost obrazu na `true`a obraz se zobrazí se šrafovaným ohraničením kolem něj za běhu.</span><span class="sxs-lookup"><span data-stu-id="ffb1e-121">Also, you can set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property of the image to `true`, and the image will appear with a hatched border around it at run time.</span></span>  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a><span data-ttu-id="ffb1e-122">Zobrazení klávesové zkratky pro příkaz nabídky</span><span class="sxs-lookup"><span data-stu-id="ffb1e-122">To display a shortcut key for a menu command</span></span>  
  
- <span data-ttu-id="ffb1e-123">Nastavte <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> vlastnost příkazu nabídky na požadovanou kombinaci kláves, například CTRL+O pro `true`příkaz **Otevřít** nabídku, <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> a nastavte vlastnost na .</span><span class="sxs-lookup"><span data-stu-id="ffb1e-123">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> property to the desired keyboard combination, such as CTRL+O for the **Open** menu command, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a><span data-ttu-id="ffb1e-124">Zobrazení vlastních klávesových zkratek pro příkaz nabídky</span><span class="sxs-lookup"><span data-stu-id="ffb1e-124">To display custom shortcut keys for a menu command</span></span>  
  
- <span data-ttu-id="ffb1e-125">Nastavte <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> vlastnost příkazu nabídky na požadovanou kombinaci kláves, například CTRL+SHIFT+O namísto <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> SHIFT+CTRL+O, a nastavte vlastnost na `true`.</span><span class="sxs-lookup"><span data-stu-id="ffb1e-125">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> property to the desired keyboard combination, such as CTRL+SHIFT+O rather than SHIFT+CTRL+O, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a><span data-ttu-id="ffb1e-126">Zobrazení přístupového klíče pro příkaz nabídky</span><span class="sxs-lookup"><span data-stu-id="ffb1e-126">To display an access key for a menu command</span></span>  
  
- <span data-ttu-id="ffb1e-127">Když nastavíte <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost příkazu nabídky, zadejte ampersand (&) před písmeno, které chcete podtrženo jako přístupový klíč.</span><span class="sxs-lookup"><span data-stu-id="ffb1e-127">When you set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property for the menu command, enter an ampersand (&) before the letter you want to be underlined as the access key.</span></span> <span data-ttu-id="ffb1e-128">Například zadáním `&Open` jako <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost položky nabídky bude příkaz nabídky, který se zobrazí jako <u>pero O.</u></span><span class="sxs-lookup"><span data-stu-id="ffb1e-128">For example, typing `&Open` as the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of a menu item will result in a menu command that appears as <u>O</u>pen.</span></span>
  
     <span data-ttu-id="ffb1e-129">Chcete-li přejít na tento příkaz nabídky, stisknutím klávesy ALT zaostřete na položku <xref:System.Windows.Forms.MenuStrip>a stiskněte přístupovou klávesu názvu nabídky.</span><span class="sxs-lookup"><span data-stu-id="ffb1e-129">To navigate to this menu command, press ALT to give focus to the <xref:System.Windows.Forms.MenuStrip>, and press the access key of the menu name.</span></span> <span data-ttu-id="ffb1e-130">Když se nabídka otevře a zobrazí položky s přístupovými klávesami, stačí pouze stisknutím klávesy pro přístup vybrat příkaz nabídky.</span><span class="sxs-lookup"><span data-stu-id="ffb1e-130">When the menu opens and shows items with access keys, you only need to press the access key to select the menu command.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ffb1e-131">Vyhněte se definování duplicitních přístupových kláves, jako je například definování kláves ALT+F dvakrát ve stejném systému nabídek.</span><span class="sxs-lookup"><span data-stu-id="ffb1e-131">Avoid defining duplicate access keys, such as defining ALT+F twice in the same menu system.</span></span> <span data-ttu-id="ffb1e-132">Pořadí výběru duplicitních přístupových klíčů nelze zaručit.</span><span class="sxs-lookup"><span data-stu-id="ffb1e-132">The selection order of duplicate access keys cannot be guaranteed.</span></span>  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a><span data-ttu-id="ffb1e-133">Zobrazení oddělovacího pruhu mezi příkazy nabídky</span><span class="sxs-lookup"><span data-stu-id="ffb1e-133">To display a separator bar between menu commands</span></span>  
  
- <span data-ttu-id="ffb1e-134">Po definování <xref:System.Windows.Forms.MenuStrip> vašich a položek, které <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> bude obsahovat, použijte <xref:System.Windows.Forms.ToolStripSeparator> metodu <xref:System.Windows.Forms.MenuStrip> nebo pro přidání příkazů a ovládacích prvků nabídky do požadovaného pořadí.</span><span class="sxs-lookup"><span data-stu-id="ffb1e-134">After you define your <xref:System.Windows.Forms.MenuStrip> and the items it will contain, use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> or <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> method to add the menu commands and <xref:System.Windows.Forms.ToolStripSeparator> controls to the <xref:System.Windows.Forms.MenuStrip> in the order you want.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ffb1e-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="ffb1e-135">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="ffb1e-136">MenuStrip – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="ffb1e-136">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
