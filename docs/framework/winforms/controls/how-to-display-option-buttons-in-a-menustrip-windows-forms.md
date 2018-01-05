---
title: "Postupy: Zobrazení tlačítek možností v MenuStrip (Windows Forms)"
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
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f0de3b8596bc06c79f391141ef85fec65ac343d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a><span data-ttu-id="c1667-102">Postupy: Zobrazení tlačítek možností v MenuStrip (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="c1667-102">How to: Display Option Buttons in a MenuStrip (Windows Forms)</span></span>
<span data-ttu-id="c1667-103">Přepínače, také známé jako přepínače, jsou podobná zaškrtněte políčka s tím rozdílem, že uživatelé mohou vybrat vždy pouze jednu.</span><span class="sxs-lookup"><span data-stu-id="c1667-103">Option buttons, also known as radio buttons, are similar to check boxes except that users can select only one at a time.</span></span> <span data-ttu-id="c1667-104">I když ve výchozím nastavení <xref:System.Windows.Forms.ToolStripMenuItem> třída nenabízí možnost tlačítko chování, třída poskytuje chování zaškrtávací políčko, kterou si můžete přizpůsobit pro implementaci – tlačítko chování položek nabídky v <xref:System.Windows.Forms.MenuStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c1667-104">Although by default the <xref:System.Windows.Forms.ToolStripMenuItem> class does not provide option-button behavior, the class does provide check-box behavior that you can customize to implement option-button behavior for menu items in a <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="c1667-105">Když <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> vlastnost položky nabídky je `true`, uživatelé kliknutím na položku k přepnutí zobrazení zaškrtnutí.</span><span class="sxs-lookup"><span data-stu-id="c1667-105">When the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property of a menu item is `true`, users can click the item to toggle the display of a check mark.</span></span> <span data-ttu-id="c1667-106"><xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> Vlastnost označuje aktuální stav položky.</span><span class="sxs-lookup"><span data-stu-id="c1667-106">The <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property indicates the current state of the item.</span></span> <span data-ttu-id="c1667-107">Chcete-li implementovat chování základní přepínač, je nutné zajistit, pokud je vybrána položka, můžete nastavit <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> vlastnost dříve vybrané položky do `false`.</span><span class="sxs-lookup"><span data-stu-id="c1667-107">To implement basic option-button behavior, you must ensure that when an item is selected, you set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property for the previously selected item to `false`.</span></span>  
  
 <span data-ttu-id="c1667-108">Následující postupy popisují, jak tuto funkci implementovat a další funkce ve třídě, která dědí <xref:System.Windows.Forms.ToolStripMenuItem> třídy.</span><span class="sxs-lookup"><span data-stu-id="c1667-108">The following procedures describe how to implement this and additional functionality in a class that inherits the <xref:System.Windows.Forms.ToolStripMenuItem> class.</span></span> <span data-ttu-id="c1667-109">`ToolStripRadioButtonMenuItem` Třída nahradí členy, jako <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> a <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> vám umožňuje výběr chování a vzhled tlačítek možností.</span><span class="sxs-lookup"><span data-stu-id="c1667-109">The `ToolStripRadioButtonMenuItem` class overrides members such as <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> and <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> to provide the selection behavior and appearance of option buttons.</span></span> <span data-ttu-id="c1667-110">Kromě toho tato třída přepsání <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> vlastnosti, které možnosti na podnabídky jsou zakázané, pokud je vybrána nadřazené položky.</span><span class="sxs-lookup"><span data-stu-id="c1667-110">Additionally, this class overrides the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that options on a submenu are disabled unless the parent item is selected.</span></span>  
  
### <a name="to-implement-option-button-selection-behavior"></a><span data-ttu-id="c1667-111">K implementaci chování výběru – tlačítko</span><span class="sxs-lookup"><span data-stu-id="c1667-111">To implement option-button selection behavior</span></span>  
  
1.  <span data-ttu-id="c1667-112">Inicializace <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> vlastnost `true` umožňující výběr položek.</span><span class="sxs-lookup"><span data-stu-id="c1667-112">Initialize the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true` to enable item selection.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]  
  
2.  <span data-ttu-id="c1667-113">Přepsání <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> metoda zrušte výběr dříve vybrané položky, pokud je vybrána novou položku.</span><span class="sxs-lookup"><span data-stu-id="c1667-113">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> method to clear the selection of the previously selected item when a new item is selected.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]  
  
3.  <span data-ttu-id="c1667-114">Přepsání <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> metodou, jak zajistit, že kliknete na položku, která již byla vybrána nebude zrušte zaškrtnutí políčka.</span><span class="sxs-lookup"><span data-stu-id="c1667-114">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> method to ensure that clicking an item that has already been selected will not clear the selection.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]  
  
### <a name="to-modify-the-appearance-of-the-option-button-items"></a><span data-ttu-id="c1667-115">Chcete-li změnit vzhled položky – tlačítko</span><span class="sxs-lookup"><span data-stu-id="c1667-115">To modify the appearance of the option-button items</span></span>  
  
1.  <span data-ttu-id="c1667-116">Přepsat <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> metody lze nahradit výchozí zaškrtnutí obsahuje přepínač s pomocí <xref:System.Windows.Forms.RadioButtonRenderer> třída.</span><span class="sxs-lookup"><span data-stu-id="c1667-116">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method to replace the default check-mark with an option button by using the <xref:System.Windows.Forms.RadioButtonRenderer> class.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]  
  
2.  <span data-ttu-id="c1667-117">Přepsání <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>, a <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> metody pro sledování stavu myši a ujistěte se, že <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> metoda vybarví stav správný přepínač.</span><span class="sxs-lookup"><span data-stu-id="c1667-117">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>, and <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> methods to track the state of the mouse and ensure that the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method paints the correct option-button state.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]  
  
### <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a><span data-ttu-id="c1667-118">Zakázání možností na podnabídky, pokud není vybrané nadřazené položky</span><span class="sxs-lookup"><span data-stu-id="c1667-118">To disable options on a submenu when the parent item is not selected</span></span>  
  
1.  <span data-ttu-id="c1667-119">Přepsání <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> vlastnost tak, aby položka bude deaktivovaná, pokud má nadřazenou položku s oběma <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> hodnotu `true` a <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> hodnotu `false`.</span><span class="sxs-lookup"><span data-stu-id="c1667-119">Override the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that the item is disabled when it has a parent item with both a <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> value of `true` and a <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> value of `false`.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]  
  
2.  <span data-ttu-id="c1667-120">Přepsání <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> metoda přihlásit k odběru <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> událostí nadřazené položky.</span><span class="sxs-lookup"><span data-stu-id="c1667-120">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> method to subscribe to the <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event of the parent item.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]  
  
3.  <span data-ttu-id="c1667-121">V obslužné rutiny pro nadřazené položky <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> událostí, zneplatnit položka k aktualizaci zobrazení s novou povoleném stavu.</span><span class="sxs-lookup"><span data-stu-id="c1667-121">In the handler for the parent-item <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event, invalidate the item to update the display with the new enabled state.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]  
  
## <a name="example"></a><span data-ttu-id="c1667-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="c1667-122">Example</span></span>  
 <span data-ttu-id="c1667-123">Následující příklad kódu poskytuje kompletní `ToolStripRadioButtonMenuItem` třída a <xref:System.Windows.Forms.Form> třídy a `Program` třída k předvedení chování možnost tlačítko.</span><span class="sxs-lookup"><span data-stu-id="c1667-123">The following code example provides the complete `ToolStripRadioButtonMenuItem` class, and a <xref:System.Windows.Forms.Form> class and `Program` class to demonstrate the option-button behavior.</span></span>  
  
 [!code-csharp[ToolStripRadioButtonMenuItem#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
 [!code-vb[ToolStripRadioButtonMenuItem#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c1667-124">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="c1667-124">Compiling the Code</span></span>  
 <span data-ttu-id="c1667-125">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="c1667-125">This example requires:</span></span>  
  
-   <span data-ttu-id="c1667-126">Odkazy na systém, System.Drawing a System.Windows.Forms sestavení.</span><span class="sxs-lookup"><span data-stu-id="c1667-126">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1667-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="c1667-127">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.RadioButtonRenderer>  
 [<span data-ttu-id="c1667-128">Ovládací prvek MenuStrip</span><span class="sxs-lookup"><span data-stu-id="c1667-128">MenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)  
 [<span data-ttu-id="c1667-129">Postupy: Implementace vlastního prvku ToolStripRenderer</span><span class="sxs-lookup"><span data-stu-id="c1667-129">How to: Implement a Custom ToolStripRenderer</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-custom-toolstriprenderer.md)
