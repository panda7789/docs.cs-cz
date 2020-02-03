---
title: 'Postupy: Zobrazení tlačítek možností v MenuStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
ms.openlocfilehash: f3010e71396ce562e9dbdefd4b75b36f3a81ffb3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735523"
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a><span data-ttu-id="2a0dc-102">Postupy: Zobrazení tlačítek možností v MenuStrip (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="2a0dc-102">How to: Display Option Buttons in a MenuStrip (Windows Forms)</span></span>

<span data-ttu-id="2a0dc-103">Tlačítka možností, označovaná také jako přepínací tlačítko, jsou podobně jako zaškrtávací políčka s tím rozdílem, že uživatelé mohou vybírat pouze jeden z nich.</span><span class="sxs-lookup"><span data-stu-id="2a0dc-103">Option buttons, also known as radio buttons, are similar to check boxes except that users can select only one at a time.</span></span> <span data-ttu-id="2a0dc-104">I když ve výchozím nastavení třída <xref:System.Windows.Forms.ToolStripMenuItem> neposkytuje chování přepínače, třída poskytuje chování funkce zaškrtávací políčko, které lze přizpůsobit, aby implementovala chování možností tlačítek pro položky nabídky v ovládacím prvku <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="2a0dc-104">Although by default the <xref:System.Windows.Forms.ToolStripMenuItem> class does not provide option-button behavior, the class does provide check-box behavior that you can customize to implement option-button behavior for menu items in a <xref:System.Windows.Forms.MenuStrip> control.</span></span>

<span data-ttu-id="2a0dc-105">Když je `true`vlastnost <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> položky nabídky, uživatelé můžou kliknout na položku a přepnout tak zobrazení zaškrtnutí.</span><span class="sxs-lookup"><span data-stu-id="2a0dc-105">When the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property of a menu item is `true`, users can click the item to toggle the display of a check mark.</span></span> <span data-ttu-id="2a0dc-106">Vlastnost <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> označuje aktuální stav položky.</span><span class="sxs-lookup"><span data-stu-id="2a0dc-106">The <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property indicates the current state of the item.</span></span> <span data-ttu-id="2a0dc-107">Chcete-li implementovat základní chování přepínače, je nutné zajistit, aby při výběru položky byla vlastnost <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> pro dříve vybranou položku nastavena na hodnotu `false`.</span><span class="sxs-lookup"><span data-stu-id="2a0dc-107">To implement basic option-button behavior, you must ensure that when an item is selected, you set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property for the previously selected item to `false`.</span></span>

<span data-ttu-id="2a0dc-108">Následující postupy popisují, jak implementovat tuto a další funkce ve třídě, která dědí třídu <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="2a0dc-108">The following procedures describe how to implement this and additional functionality in a class that inherits the <xref:System.Windows.Forms.ToolStripMenuItem> class.</span></span> <span data-ttu-id="2a0dc-109">Třída `ToolStripRadioButtonMenuItem` Přepisuje členy, jako je například <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> a <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A>, k poskytnutí chování výběr a vzhled tlačítek možností.</span><span class="sxs-lookup"><span data-stu-id="2a0dc-109">The `ToolStripRadioButtonMenuItem` class overrides members such as <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> and <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> to provide the selection behavior and appearance of option buttons.</span></span> <span data-ttu-id="2a0dc-110">Kromě toho tato třída Přepisuje vlastnost <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> tak, aby byly možnosti v podnabídce zakázané, pokud není vybraná nadřazená položka.</span><span class="sxs-lookup"><span data-stu-id="2a0dc-110">Additionally, this class overrides the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that options on a submenu are disabled unless the parent item is selected.</span></span>

## <a name="to-implement-option-button-selection-behavior"></a><span data-ttu-id="2a0dc-111">Implementace chování výběru přepínačů</span><span class="sxs-lookup"><span data-stu-id="2a0dc-111">To implement option-button selection behavior</span></span>

1. <span data-ttu-id="2a0dc-112">Chcete-li povolit výběr položky, inicializujte vlastnost <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> na `true`.</span><span class="sxs-lookup"><span data-stu-id="2a0dc-112">Initialize the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true` to enable item selection.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#110](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]

2. <span data-ttu-id="2a0dc-113">Přepsat metodu <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> pro vymazání výběru dříve vybrané položky, když je vybrána nová položka.</span><span class="sxs-lookup"><span data-stu-id="2a0dc-113">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> method to clear the selection of the previously selected item when a new item is selected.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#120](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]

3. <span data-ttu-id="2a0dc-114">Přepište metodu <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A>, aby se zajistilo, že kliknete na položku, která již byla vybrána, nebude výběr vymazán.</span><span class="sxs-lookup"><span data-stu-id="2a0dc-114">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> method to ensure that clicking an item that has already been selected will not clear the selection.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#130](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]

## <a name="to-modify-the-appearance-of-the-option-button-items"></a><span data-ttu-id="2a0dc-115">Úprava vzhledu položek přepínačů</span><span class="sxs-lookup"><span data-stu-id="2a0dc-115">To modify the appearance of the option-button items</span></span>

1. <span data-ttu-id="2a0dc-116">Přepište metodu <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> pro nahrazení výchozího kontrolního panelu pomocí přepínače pomocí <xref:System.Windows.Forms.RadioButtonRenderer> třídy.</span><span class="sxs-lookup"><span data-stu-id="2a0dc-116">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method to replace the default check-mark with an option button by using the <xref:System.Windows.Forms.RadioButtonRenderer> class.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#140](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]

2. <span data-ttu-id="2a0dc-117">Přepište metody <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>a <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> pro sledování stavu myši a zajistěte, že metoda <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> vykreslí správný stav tlačítka Možnosti.</span><span class="sxs-lookup"><span data-stu-id="2a0dc-117">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>, and <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> methods to track the state of the mouse and ensure that the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method paints the correct option-button state.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#150](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]

## <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a><span data-ttu-id="2a0dc-118">Zakázání možností v podnabídce, když není vybraná nadřazená položka</span><span class="sxs-lookup"><span data-stu-id="2a0dc-118">To disable options on a submenu when the parent item is not selected</span></span>

1. <span data-ttu-id="2a0dc-119">Přepište vlastnost <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>, aby byla položka neaktivní, když má nadřazenou položku s hodnotou <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> `true` a <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> hodnotou `false`.</span><span class="sxs-lookup"><span data-stu-id="2a0dc-119">Override the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that the item is disabled when it has a parent item with both a <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> value of `true` and a <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> value of `false`.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#160](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]

2. <span data-ttu-id="2a0dc-120">Přepište metodu <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> pro přihlášení k odběru události <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> nadřazené položky.</span><span class="sxs-lookup"><span data-stu-id="2a0dc-120">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> method to subscribe to the <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event of the parent item.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#170](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]

3. <span data-ttu-id="2a0dc-121">V obslužné rutině události <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> nadřazených položek zruší platnost položky pro zobrazení aktualizace s novým stavem Enabled.</span><span class="sxs-lookup"><span data-stu-id="2a0dc-121">In the handler for the parent-item <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event, invalidate the item to update the display with the new enabled state.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#180](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]

## <a name="example"></a><span data-ttu-id="2a0dc-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="2a0dc-122">Example</span></span>

<span data-ttu-id="2a0dc-123">Následující příklad kódu poskytuje úplnou třídu `ToolStripRadioButtonMenuItem` a třídu <xref:System.Windows.Forms.Form> a třídu `Program` k předvedení chování možností tlačítek.</span><span class="sxs-lookup"><span data-stu-id="2a0dc-123">The following code example provides the complete `ToolStripRadioButtonMenuItem` class, and a <xref:System.Windows.Forms.Form> class and `Program` class to demonstrate the option-button behavior.</span></span>

[!code-csharp[ToolStripRadioButtonMenuItem#000](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
[!code-vb[ToolStripRadioButtonMenuItem#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]

## <a name="compiling-the-code"></a><span data-ttu-id="2a0dc-124">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="2a0dc-124">Compiling the Code</span></span>

<span data-ttu-id="2a0dc-125">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="2a0dc-125">This example requires:</span></span>

- <span data-ttu-id="2a0dc-126">Odkazy na sestavení System, System. Drawing a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="2a0dc-126">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a0dc-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="2a0dc-127">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RadioButtonRenderer>
- [<span data-ttu-id="2a0dc-128">Ovládací prvek MenuStrip</span><span class="sxs-lookup"><span data-stu-id="2a0dc-128">MenuStrip Control</span></span>](menustrip-control-windows-forms.md)
- [<span data-ttu-id="2a0dc-129">Postupy: Implementace vlastního prvku ToolStripRenderer</span><span class="sxs-lookup"><span data-stu-id="2a0dc-129">How to: Implement a Custom ToolStripRenderer</span></span>](how-to-implement-a-custom-toolstriprenderer.md)
