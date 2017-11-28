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
ms.openlocfilehash: 2701094ffcbcf7eeb14444163b995816398876fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a><span data-ttu-id="57d2d-102">Postupy: Přidání vylepšení do ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="57d2d-102">How to: Add Enhancements to ToolStripMenuItems</span></span>
<span data-ttu-id="57d2d-103">Můžete vylepšit použitelnost <xref:System.Windows.Forms.MenuStrip> a <xref:System.Windows.Forms.ContextMenuStrip> ovládací prvky následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="57d2d-103">You can enhance the usability of <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> controls in the following ways:</span></span>  
  
-   <span data-ttu-id="57d2d-104">Přidání značek zaškrtnutí k označení, zda funkce je zapnout nebo vypnout, například zda pravítko se zobrazují podél na okraji textového procesoru, a který soubor v seznam souborů, která má být zobrazeny, například jako na **okno** nabídky.</span><span class="sxs-lookup"><span data-stu-id="57d2d-104">Add check marks to designate whether a feature is turned on or off, such as whether a ruler is displayed along the margin of a word-processing application, or to indicate which file in a list of files is being displayed, such as on a **Window** menu.</span></span>  
  
-   <span data-ttu-id="57d2d-105">Přidání bitové kopie, které představují vizuální příkazy nabídky.</span><span class="sxs-lookup"><span data-stu-id="57d2d-105">Add images that visually represent menu commands.</span></span>  
  
-   <span data-ttu-id="57d2d-106">Zobrazit klávesové zkratky, které poskytují klávesnice alternativa k přesunutí myši pro provádění příkazů.</span><span class="sxs-lookup"><span data-stu-id="57d2d-106">Display shortcut keys to provide a keyboard alternative to the mouse for performing commands.</span></span> <span data-ttu-id="57d2d-107">Například kombinace kláves CTRL + C provádí **kopie** příkaz.</span><span class="sxs-lookup"><span data-stu-id="57d2d-107">For example, pressing CTRL+C performs the **Copy** command.</span></span>  
  
-   <span data-ttu-id="57d2d-108">Zobrazení přístupových kláves zajistit klávesnice alternativa k přesunutí myši pro navigační nabídky.</span><span class="sxs-lookup"><span data-stu-id="57d2d-108">Display access keys to provide a keyboard alternative to the mouse for menu navigation.</span></span> <span data-ttu-id="57d2d-109">Například stisknutím ALT + F rozhodne **souboru** nabídky.</span><span class="sxs-lookup"><span data-stu-id="57d2d-109">For example, pressing ALT+F chooses the **File** menu.</span></span>  
  
-   <span data-ttu-id="57d2d-110">Zobrazení oddělovacích pruhů k seskupení souvisejících s příkazy a čitelnost nabídky.</span><span class="sxs-lookup"><span data-stu-id="57d2d-110">Show separator bars to group related commands and make menus more readable.</span></span>  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a><span data-ttu-id="57d2d-111">Chcete-li zobrazit zaškrtnutí příkazu nabídky</span><span class="sxs-lookup"><span data-stu-id="57d2d-111">To display a check mark on a menu command</span></span>  
  
-   <span data-ttu-id="57d2d-112">Nastavte její <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="57d2d-112">Set its <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="57d2d-113">Zároveň se nastaví <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="57d2d-113">This also sets the <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> property to `true`.</span></span> <span data-ttu-id="57d2d-114">Tento postup použijte, pouze pokud chcete, aby příkaz nabídky zobrazit ve výchozím nastavení, bez ohledu na to, jestli je vybraná jako zaškrtnuté.</span><span class="sxs-lookup"><span data-stu-id="57d2d-114">Use this procedure only if you want the menu command to appear as checked by default, regardless of whether it is selected.</span></span>  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a><span data-ttu-id="57d2d-115">Chcete-li zobrazit zaškrtnutí, které změní stav každého kliknutím</span><span class="sxs-lookup"><span data-stu-id="57d2d-115">To display a check mark that changes state with each click</span></span>  
  
-   <span data-ttu-id="57d2d-116">Nastavit příkaz nabídky <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="57d2d-116">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true`.</span></span>  
  
### <a name="to-add-an-image-to-a-menu-command"></a><span data-ttu-id="57d2d-117">Chcete-li přidat bitovou kopii k příkazu nabídky</span><span class="sxs-lookup"><span data-stu-id="57d2d-117">To add an image to a menu command</span></span>  
  
-   <span data-ttu-id="57d2d-118">Nastavit příkaz nabídky <xref:System.Windows.Forms.ToolStripItem.Image%2A> vlastnost na název obrázku.</span><span class="sxs-lookup"><span data-stu-id="57d2d-118">Set the menu command's <xref:System.Windows.Forms.ToolStripItem.Image%2A> property to the name of the image.</span></span> <span data-ttu-id="57d2d-119">Pokud <xref:System.Windows.Forms.ToolStripItemDisplayStyle> tohoto příkazu nabídky je nastavena na <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> nebo <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, bitovou kopii nelze zobrazit.</span><span class="sxs-lookup"><span data-stu-id="57d2d-119">If the <xref:System.Windows.Forms.ToolStripItemDisplayStyle> property of this menu command is set to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> or <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, the image cannot be displayed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57d2d-120">Okraj bitové kopie můžete také zobrazit zaškrtnutí Pokud proto zvolte.</span><span class="sxs-lookup"><span data-stu-id="57d2d-120">The image margin can also show a check mark if you so choose.</span></span> <span data-ttu-id="57d2d-121">Také můžete nastavit <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> vlastnost bitové kopie a `true`, a bitovou kopii se zobrazí s šrafované ohraničení za běhu.</span><span class="sxs-lookup"><span data-stu-id="57d2d-121">Also, you can set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property of the image to `true`, and the image will appear with a hatched border around it at run time.</span></span>  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a><span data-ttu-id="57d2d-122">Chcete-li zobrazit klávesovou zkratku příkazu nabídky</span><span class="sxs-lookup"><span data-stu-id="57d2d-122">To display a shortcut key for a menu command</span></span>  
  
-   <span data-ttu-id="57d2d-123">Nastavit příkaz nabídky <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> vlastnost na kombinaci požadované klávesnice, jako je například CTRL + O pro **otevřete** příkazu v nabídce a nastavte <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="57d2d-123">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> property to the desired keyboard combination, such as CTRL+O for the **Open** menu command, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a><span data-ttu-id="57d2d-124">Chcete-li zobrazit vlastní klávesové zkratky pro příkaz nabídky</span><span class="sxs-lookup"><span data-stu-id="57d2d-124">To display custom shortcut keys for a menu command</span></span>  
  
-   <span data-ttu-id="57d2d-125">Nastavit příkaz nabídky <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> vlastnost na kombinaci požadované klávesnice, jako je například CTRL + SHIFT + O spíše než CTRL + SHIFT + O a nastavte <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="57d2d-125">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> property to the desired keyboard combination, such as CTRL+SHIFT+O rather than SHIFT+CTRL+O, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a><span data-ttu-id="57d2d-126">Chcete-li zobrazit přístupový klíč pro příkaz nabídky</span><span class="sxs-lookup"><span data-stu-id="57d2d-126">To display an access key for a menu command</span></span>  
  
-   <span data-ttu-id="57d2d-127">Když nastavíte <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost pro příkaz nabídky zadejte ampersand (&) před písmeno, které chcete být podtržené jako přístupový klíč.</span><span class="sxs-lookup"><span data-stu-id="57d2d-127">When you set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property for the menu command, enter an ampersand (&) before the letter you want to be underlined as the access key.</span></span> <span data-ttu-id="57d2d-128">Například zadáním `&Open` jako <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnosti položky nabídky bude mít za následek příkaz nabídky, která se zobrazí jako **O**pera.</span><span class="sxs-lookup"><span data-stu-id="57d2d-128">For example, typing `&Open` as the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of a menu item will result in a menu command that appears as **O**pen.</span></span>  
  
     <span data-ttu-id="57d2d-129">Přejděte na tento příkaz nabídky, stiskněte klávesu ALT umožnit zaměření <xref:System.Windows.Forms.MenuStrip>a stiskněte klávesu přístupovým klíčem název nabídky.</span><span class="sxs-lookup"><span data-stu-id="57d2d-129">To navigate to this menu command, press ALT to give focus to the <xref:System.Windows.Forms.MenuStrip>, and press the access key of the menu name.</span></span> <span data-ttu-id="57d2d-130">Když v nabídce otevře a zobrazuje položky s přístupové klíče, stačí stisknutím klávesy vyberte příkaz nabídky.</span><span class="sxs-lookup"><span data-stu-id="57d2d-130">When the menu opens and shows items with access keys, you only need to press the access key to select the menu command.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57d2d-131">Nedefinujte duplicitní přístupové klíče, jako je například definování ALT + F dvakrát ve stejném systému nabídky.</span><span class="sxs-lookup"><span data-stu-id="57d2d-131">Avoid defining duplicate access keys, such as defining ALT+F twice in the same menu system.</span></span> <span data-ttu-id="57d2d-132">Výběr pořadí duplicitní přístupové klíče nemůže zaručit.</span><span class="sxs-lookup"><span data-stu-id="57d2d-132">The selection order of duplicate access keys cannot be guaranteed.</span></span>  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a><span data-ttu-id="57d2d-133">Chcete-li zobrazit oddělovač mezi příkazy nabídky</span><span class="sxs-lookup"><span data-stu-id="57d2d-133">To display a separator bar between menu commands</span></span>  
  
-   <span data-ttu-id="57d2d-134">Po definování vaše <xref:System.Windows.Forms.MenuStrip> a v položkách, bude obsahovat, použijte <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> nebo <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> metody přidat příkazy nabídky a <xref:System.Windows.Forms.ToolStripSeparator> prvky <xref:System.Windows.Forms.MenuStrip> v pořadí, které chcete.</span><span class="sxs-lookup"><span data-stu-id="57d2d-134">After you define your <xref:System.Windows.Forms.MenuStrip> and the items it will contain, use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> or <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> method to add the menu commands and <xref:System.Windows.Forms.ToolStripSeparator> controls to the <xref:System.Windows.Forms.MenuStrip> in the order you want.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="57d2d-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="57d2d-135">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="57d2d-136">Přehled ovládacího prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="57d2d-136">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
