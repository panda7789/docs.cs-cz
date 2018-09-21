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
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46529113"
---
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a><span data-ttu-id="72406-102">Postupy: Přidání vylepšení do ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="72406-102">How to: Add Enhancements to ToolStripMenuItems</span></span>
<span data-ttu-id="72406-103">Můžete zlepšit použitelnost <xref:System.Windows.Forms.MenuStrip> a <xref:System.Windows.Forms.ContextMenuStrip> ovládacích prvků následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="72406-103">You can enhance the usability of <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> controls in the following ways:</span></span>  
  
-   <span data-ttu-id="72406-104">Přidání značek zaškrtnutí k určení, zda funkce je zapnout nebo vypnout, například zda pravítka se zobrazují podél na okraji aplikace pro zpracování textu, nebo k označení, který soubor v seznamu souborů, která má být zobrazeny, například jako na **okno** nabídka.</span><span class="sxs-lookup"><span data-stu-id="72406-104">Add check marks to designate whether a feature is turned on or off, such as whether a ruler is displayed along the margin of a word-processing application, or to indicate which file in a list of files is being displayed, such as on a **Window** menu.</span></span>  
  
-   <span data-ttu-id="72406-105">Přidání bitové kopie, které vizuálně představují příkazy nabídky.</span><span class="sxs-lookup"><span data-stu-id="72406-105">Add images that visually represent menu commands.</span></span>  
  
-   <span data-ttu-id="72406-106">Zobrazí klávesové zkratky, které poskytují alternativní klávesnice k myši pro provádění příkazů.</span><span class="sxs-lookup"><span data-stu-id="72406-106">Display shortcut keys to provide a keyboard alternative to the mouse for performing commands.</span></span> <span data-ttu-id="72406-107">Například provádí kombinace kláves CTRL + C **kopírování** příkazu.</span><span class="sxs-lookup"><span data-stu-id="72406-107">For example, pressing CTRL+C performs the **Copy** command.</span></span>  
  
-   <span data-ttu-id="72406-108">Zobrazení přístupových klíčů k poskytnutí klávesnice alternativou k myši pro navigační nabídky.</span><span class="sxs-lookup"><span data-stu-id="72406-108">Display access keys to provide a keyboard alternative to the mouse for menu navigation.</span></span> <span data-ttu-id="72406-109">Například stisknutím klávesy ALT + F klikne **souboru** nabídky.</span><span class="sxs-lookup"><span data-stu-id="72406-109">For example, pressing ALT+F chooses the **File** menu.</span></span>  
  
-   <span data-ttu-id="72406-110">Zobrazení oddělovacích pruhů seskupovat související příkazy a nabídky čitelnost.</span><span class="sxs-lookup"><span data-stu-id="72406-110">Show separator bars to group related commands and make menus more readable.</span></span>  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a><span data-ttu-id="72406-111">Chcete-li zobrazit značku zaškrtnutí v příkazu nabídky</span><span class="sxs-lookup"><span data-stu-id="72406-111">To display a check mark on a menu command</span></span>  
  
-   <span data-ttu-id="72406-112">Nastavte jeho <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="72406-112">Set its <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="72406-113">Zároveň se nastaví <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="72406-113">This also sets the <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> property to `true`.</span></span> <span data-ttu-id="72406-114">Pokud chcete, aby příkaz nabídky zobrazí jako zaškrtnuté ve výchozím nastavení, bez ohledu na to, zda je zaškrtnuto, pomocí tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="72406-114">Use this procedure only if you want the menu command to appear as checked by default, regardless of whether it is selected.</span></span>  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a><span data-ttu-id="72406-115">Zobrazit značku zaškrtnutí, která změní stav každého kliknutím</span><span class="sxs-lookup"><span data-stu-id="72406-115">To display a check mark that changes state with each click</span></span>  
  
-   <span data-ttu-id="72406-116">Nastavení příkazu nabídky <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="72406-116">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true`.</span></span>  
  
### <a name="to-add-an-image-to-a-menu-command"></a><span data-ttu-id="72406-117">Chcete-li přidat bitovou kopii k příkazu nabídky</span><span class="sxs-lookup"><span data-stu-id="72406-117">To add an image to a menu command</span></span>  
  
-   <span data-ttu-id="72406-118">Nastavení příkazu nabídky <xref:System.Windows.Forms.ToolStripItem.Image%2A> vlastnost na název obrázku.</span><span class="sxs-lookup"><span data-stu-id="72406-118">Set the menu command's <xref:System.Windows.Forms.ToolStripItem.Image%2A> property to the name of the image.</span></span> <span data-ttu-id="72406-119">Pokud <xref:System.Windows.Forms.ToolStripItemDisplayStyle> tohoto příkazu nabídky je nastavena na <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> nebo <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, nelze zobrazit obrázek.</span><span class="sxs-lookup"><span data-stu-id="72406-119">If the <xref:System.Windows.Forms.ToolStripItemDisplayStyle> property of this menu command is set to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> or <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, the image cannot be displayed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72406-120">Okraji pro obrázek můžete také zobrazit zaškrtávací políčko Pokud se pro to rozhodnete.</span><span class="sxs-lookup"><span data-stu-id="72406-120">The image margin can also show a check mark if you so choose.</span></span> <span data-ttu-id="72406-121">Kromě toho můžete nastavit <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> vlastnosti obrázku, který se `true`, a image se zobrazí s šrafované ohraničení kolem něj v době běhu.</span><span class="sxs-lookup"><span data-stu-id="72406-121">Also, you can set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property of the image to `true`, and the image will appear with a hatched border around it at run time.</span></span>  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a><span data-ttu-id="72406-122">Chcete-li zobrazit klávesovou zkratku pro příkaz nabídky</span><span class="sxs-lookup"><span data-stu-id="72406-122">To display a shortcut key for a menu command</span></span>  
  
-   <span data-ttu-id="72406-123">Nastavení příkazu nabídky <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> vlastnost kombinaci požadované klávesnice, jako je například CTRL + O pro **otevřít** příkaz nabídky a nastavte <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="72406-123">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> property to the desired keyboard combination, such as CTRL+O for the **Open** menu command, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a><span data-ttu-id="72406-124">Chcete-li zobrazit vlastní klávesové zkratky pro příkaz nabídky</span><span class="sxs-lookup"><span data-stu-id="72406-124">To display custom shortcut keys for a menu command</span></span>  
  
-   <span data-ttu-id="72406-125">Nastavení příkazu nabídky <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> kombinaci požadované klávesnice, jako je například CTRL + SHIFT + O spíše než CTRL + SHIFT + O a nastavte vlastnost <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="72406-125">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> property to the desired keyboard combination, such as CTRL+SHIFT+O rather than SHIFT+CTRL+O, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a><span data-ttu-id="72406-126">Chcete-li zobrazit přístupový klíč pro příkaz nabídky</span><span class="sxs-lookup"><span data-stu-id="72406-126">To display an access key for a menu command</span></span>  
  
-   <span data-ttu-id="72406-127">Při nastavení <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost pro příkaz nabídky zadejte znak ampersand (&) před písmeno chcete podtržena jako přístupový klíč.</span><span class="sxs-lookup"><span data-stu-id="72406-127">When you set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property for the menu command, enter an ampersand (&) before the letter you want to be underlined as the access key.</span></span> <span data-ttu-id="72406-128">Například zadáte `&Open` jako <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastností položky nabídky bude výsledkem příkazu nabídky, která se zobrazí jako <u>O</u>pera.</span><span class="sxs-lookup"><span data-stu-id="72406-128">For example, typing `&Open` as the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of a menu item will result in a menu command that appears as <u>O</u>pen.</span></span>
  
     <span data-ttu-id="72406-129">Přejděte na tento příkaz nabídky, stiskněte klávesu ALT k nastavení fokusu na <xref:System.Windows.Forms.MenuStrip>a stiskněte klávesu přístupový klíč název nabídky.</span><span class="sxs-lookup"><span data-stu-id="72406-129">To navigate to this menu command, press ALT to give focus to the <xref:System.Windows.Forms.MenuStrip>, and press the access key of the menu name.</span></span> <span data-ttu-id="72406-130">Když v nabídce se otevře a zobrazí položky se přístupové klíče, stačí ke stisknutí přístupové klávesy vyberete příkaz nabídky.</span><span class="sxs-lookup"><span data-stu-id="72406-130">When the menu opens and shows items with access keys, you only need to press the access key to select the menu command.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72406-131">Vyhněte se definování duplicitní přístupové klávesy, jako je například definování ALT + F dvakrát ve stejném systému nabídky.</span><span class="sxs-lookup"><span data-stu-id="72406-131">Avoid defining duplicate access keys, such as defining ALT+F twice in the same menu system.</span></span> <span data-ttu-id="72406-132">Nelze zaručit pořadí výběru duplicitní přístupové klávesy.</span><span class="sxs-lookup"><span data-stu-id="72406-132">The selection order of duplicate access keys cannot be guaranteed.</span></span>  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a><span data-ttu-id="72406-133">Chcete-li zobrazit oddělovač mezi příkazy nabídky</span><span class="sxs-lookup"><span data-stu-id="72406-133">To display a separator bar between menu commands</span></span>  
  
-   <span data-ttu-id="72406-134">Po definování vašich <xref:System.Windows.Forms.MenuStrip> a v položkách, bude obsahovat, použijte <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> nebo <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> metoda pro přidání příkazů nabídky a <xref:System.Windows.Forms.ToolStripSeparator> ovládacích prvků do <xref:System.Windows.Forms.MenuStrip> v pořadí, které chcete.</span><span class="sxs-lookup"><span data-stu-id="72406-134">After you define your <xref:System.Windows.Forms.MenuStrip> and the items it will contain, use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> or <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> method to add the menu commands and <xref:System.Windows.Forms.ToolStripSeparator> controls to the <xref:System.Windows.Forms.MenuStrip> in the order you want.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="72406-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="72406-135">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="72406-136">Přehled ovládacího prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="72406-136">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
