---
title: 'Postupy: Zobrazení tlačítek možností v MenuStrip (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
ms.openlocfilehash: e764c7e181870d8faf6157cacc13164977ce2e3b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59306232"
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a><span data-ttu-id="2d71b-102">Postupy: Zobrazení tlačítek možností v MenuStrip (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="2d71b-102">How to: Display Option Buttons in a MenuStrip (Windows Forms)</span></span>
<span data-ttu-id="2d71b-103">Přepínače, označované také jako přepínačů, jsou podobné zaškrtněte políčka s tím rozdílem, že uživatelé mohou vybrat pouze jeden po druhém.</span><span class="sxs-lookup"><span data-stu-id="2d71b-103">Option buttons, also known as radio buttons, are similar to check boxes except that users can select only one at a time.</span></span> <span data-ttu-id="2d71b-104">I když se ve výchozím nastavení <xref:System.Windows.Forms.ToolStripMenuItem> třída neposkytuje přepínač chování, třída poskytuje chování zaškrtávací políčko, které si můžete přizpůsobit pro implementaci přepínač chování pro položky nabídky v <xref:System.Windows.Forms.MenuStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2d71b-104">Although by default the <xref:System.Windows.Forms.ToolStripMenuItem> class does not provide option-button behavior, the class does provide check-box behavior that you can customize to implement option-button behavior for menu items in a <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="2d71b-105">Když <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> vlastnost položky nabídky `true`, uživatelů můžete kliknutím na položku přepínat zobrazení zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="2d71b-105">When the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property of a menu item is `true`, users can click the item to toggle the display of a check mark.</span></span> <span data-ttu-id="2d71b-106"><xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> Vlastnost označuje aktuální stav položky.</span><span class="sxs-lookup"><span data-stu-id="2d71b-106">The <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property indicates the current state of the item.</span></span> <span data-ttu-id="2d71b-107">K implementaci chování základní přepínač, musíte zajistit, že při výběru položky, je nastavit <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> vlastnost dříve vybrané položky do `false`.</span><span class="sxs-lookup"><span data-stu-id="2d71b-107">To implement basic option-button behavior, you must ensure that when an item is selected, you set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property for the previously selected item to `false`.</span></span>  
  
 <span data-ttu-id="2d71b-108">Následující postupy popisují, jak implementovat tato a další funkce do třídy, která dědí <xref:System.Windows.Forms.ToolStripMenuItem> třídy.</span><span class="sxs-lookup"><span data-stu-id="2d71b-108">The following procedures describe how to implement this and additional functionality in a class that inherits the <xref:System.Windows.Forms.ToolStripMenuItem> class.</span></span> <span data-ttu-id="2d71b-109">`ToolStripRadioButtonMenuItem` Třídy nahradí členy jako <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> a <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> poskytnout výběr chování a vzhled tlačítek možností.</span><span class="sxs-lookup"><span data-stu-id="2d71b-109">The `ToolStripRadioButtonMenuItem` class overrides members such as <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> and <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> to provide the selection behavior and appearance of option buttons.</span></span> <span data-ttu-id="2d71b-110">Kromě toho tato třída přepíše <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> vlastnost tak, která podnabídky možnosti jsou zakázáno, pokud vybrané nadřazené položky.</span><span class="sxs-lookup"><span data-stu-id="2d71b-110">Additionally, this class overrides the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that options on a submenu are disabled unless the parent item is selected.</span></span>  
  
### <a name="to-implement-option-button-selection-behavior"></a><span data-ttu-id="2d71b-111">K implementaci chování výběru – přepínač</span><span class="sxs-lookup"><span data-stu-id="2d71b-111">To implement option-button selection behavior</span></span>  
  
1. <span data-ttu-id="2d71b-112">Inicializovat <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> vlastnost `true` umožňující výběr položek.</span><span class="sxs-lookup"><span data-stu-id="2d71b-112">Initialize the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true` to enable item selection.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#110](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]  
  
2. <span data-ttu-id="2d71b-113">Přepsat <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> metoda při výběru nové položky, zrušte zaškrtnutí políčka dříve vybrané položky.</span><span class="sxs-lookup"><span data-stu-id="2d71b-113">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> method to clear the selection of the previously selected item when a new item is selected.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#120](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]  
  
3. <span data-ttu-id="2d71b-114">Přepsat <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> metodou, jak zajistit, že kliknete na položku, která již byla vybrána nebude zrušte zaškrtnutí políčka.</span><span class="sxs-lookup"><span data-stu-id="2d71b-114">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> method to ensure that clicking an item that has already been selected will not clear the selection.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#130](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]  
  
### <a name="to-modify-the-appearance-of-the-option-button-items"></a><span data-ttu-id="2d71b-115">K úpravě vzhledu položky – přepínač</span><span class="sxs-lookup"><span data-stu-id="2d71b-115">To modify the appearance of the option-button items</span></span>  
  
1. <span data-ttu-id="2d71b-116">Přepsat <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> metoda nahradit výchozí zaškrtnutí přepínač pomocí <xref:System.Windows.Forms.RadioButtonRenderer> třídy.</span><span class="sxs-lookup"><span data-stu-id="2d71b-116">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method to replace the default check-mark with an option button by using the <xref:System.Windows.Forms.RadioButtonRenderer> class.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#140](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]  
  
2. <span data-ttu-id="2d71b-117">Přepsat <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>, a <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> metody pro sledování stavu myší a ujistěte se, že <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> metody jsou vykreslovány stavu správné přepínač.</span><span class="sxs-lookup"><span data-stu-id="2d71b-117">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>, and <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> methods to track the state of the mouse and ensure that the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method paints the correct option-button state.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#150](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]  
  
### <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a><span data-ttu-id="2d71b-118">Zakázání možností na podnabídky, pokud není vybraná nadřazená položka</span><span class="sxs-lookup"><span data-stu-id="2d71b-118">To disable options on a submenu when the parent item is not selected</span></span>  
  
1. <span data-ttu-id="2d71b-119">Přepsat <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> vlastnost tak, že položka je zakázaná, pokud má nadřazená položka s oběma <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> hodnotu `true` a <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> hodnotu `false`.</span><span class="sxs-lookup"><span data-stu-id="2d71b-119">Override the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that the item is disabled when it has a parent item with both a <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> value of `true` and a <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> value of `false`.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#160](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]  
  
2. <span data-ttu-id="2d71b-120">Přepsat <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> metodu pro přihlášení k odběru <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> událost nadřazené položky.</span><span class="sxs-lookup"><span data-stu-id="2d71b-120">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> method to subscribe to the <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event of the parent item.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#170](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]  
  
3. <span data-ttu-id="2d71b-121">V obslužné rutině pro nadřazené položky <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> události, zrušte platnost položky aktualizovat zobrazení s novou povoleného stavu.</span><span class="sxs-lookup"><span data-stu-id="2d71b-121">In the handler for the parent-item <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event, invalidate the item to update the display with the new enabled state.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#180](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]  
  
## <a name="example"></a><span data-ttu-id="2d71b-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="2d71b-122">Example</span></span>  
 <span data-ttu-id="2d71b-123">Následující příklad kódu poskytuje kompletní `ToolStripRadioButtonMenuItem` třídy a <xref:System.Windows.Forms.Form> třídy a `Program` třídy k předvedení přepínač chování.</span><span class="sxs-lookup"><span data-stu-id="2d71b-123">The following code example provides the complete `ToolStripRadioButtonMenuItem` class, and a <xref:System.Windows.Forms.Form> class and `Program` class to demonstrate the option-button behavior.</span></span>  
  
 [!code-csharp[ToolStripRadioButtonMenuItem#000](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
 [!code-vb[ToolStripRadioButtonMenuItem#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2d71b-124">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="2d71b-124">Compiling the Code</span></span>  
 <span data-ttu-id="2d71b-125">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="2d71b-125">This example requires:</span></span>  
  
-   <span data-ttu-id="2d71b-126">Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="2d71b-126">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d71b-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d71b-127">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RadioButtonRenderer>
- [<span data-ttu-id="2d71b-128">Ovládací prvek MenuStrip</span><span class="sxs-lookup"><span data-stu-id="2d71b-128">MenuStrip Control</span></span>](menustrip-control-windows-forms.md)
- [<span data-ttu-id="2d71b-129">Postupy: Implementace vlastního prvku ToolStripRenderer</span><span class="sxs-lookup"><span data-stu-id="2d71b-129">How to: Implement a Custom ToolStripRenderer</span></span>](how-to-implement-a-custom-toolstriprenderer.md)
