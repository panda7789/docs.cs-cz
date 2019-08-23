---
title: 'Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.AnchorDock
helpviewer_keywords:
- layout [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
- TableLayoutPanel control [Windows Forms], child controls
ms.assetid: 0d267c35-25f1-49b8-8976-c64e8f0ddc0b
ms.openlocfilehash: 0e565b56c31d0776f6e89bbbe0b0681ae184758e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922824"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control"></a><span data-ttu-id="c610c-102">Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="c610c-102">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>
<span data-ttu-id="c610c-103">Ovládací prvek podporuje vlastnosti <xref:System.Windows.Forms.Control.Dock%2A> a v jeho podřízených ovládacích prvcích. <xref:System.Windows.Forms.Control.Anchor%2A> <xref:System.Windows.Forms.TableLayoutPanel></span><span class="sxs-lookup"><span data-stu-id="c610c-103">The <xref:System.Windows.Forms.TableLayoutPanel> control supports the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties in its child controls.</span></span>  
  
### <a name="to-align-a-child-control-in-a-tablelayoutpanel-cell"></a><span data-ttu-id="c610c-104">Zarovnání podřízeného ovládacího prvku v buňce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="c610c-104">To align a child control in a TableLayoutPanel cell</span></span>  
  
1. <span data-ttu-id="c610c-105">Vytvořte na formuláři ovládací prvek. <xref:System.Windows.Forms.TableLayoutPanel></span><span class="sxs-lookup"><span data-stu-id="c610c-105">Create a <xref:System.Windows.Forms.TableLayoutPanel> control on your form.</span></span>  
  
2. <span data-ttu-id="c610c-106">Nastavte hodnotu <xref:System.Windows.Forms.TableLayoutPanel> <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> ovládacího prvku a vlastnosti na **1.** <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A></span><span class="sxs-lookup"><span data-stu-id="c610c-106">Set the value of the <xref:System.Windows.Forms.TableLayoutPanel> control's <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> and <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> properties to **1**.</span></span>  
  
3. <span data-ttu-id="c610c-107">Vytvoří ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> v ovládacím prvku. <xref:System.Windows.Forms.Button></span><span class="sxs-lookup"><span data-stu-id="c610c-107">Create a <xref:System.Windows.Forms.Button> control in the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="c610c-108"><xref:System.Windows.Forms.Button> Zabírá levý horní roh buňky.</span><span class="sxs-lookup"><span data-stu-id="c610c-108">The <xref:System.Windows.Forms.Button> occupies the upper-left corner of the cell.</span></span>  
  
4. <span data-ttu-id="c610c-109">Změňte hodnotu <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Anchor%2A> vlastnosti ovládacího prvku na `Left`.</span><span class="sxs-lookup"><span data-stu-id="c610c-109">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left`.</span></span> <span data-ttu-id="c610c-110"><xref:System.Windows.Forms.Button> Ovládací prvek se přesune k zarovnání s levým ohraničením buňky.</span><span class="sxs-lookup"><span data-stu-id="c610c-110">The <xref:System.Windows.Forms.Button> control moves to align with the left border of the cell.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c610c-111">Toto chování se liší od chování jiných ovládacích prvků kontejneru.</span><span class="sxs-lookup"><span data-stu-id="c610c-111">This behavior differs from the behavior of other container controls.</span></span> <span data-ttu-id="c610c-112">V jiných ovládacích prvcích kontejneru se podřízený ovládací prvek nepřesouvá, když <xref:System.Windows.Forms.Control.Anchor%2A> je nastavena vlastnost a vzdálenost mezi ukotveným ovládacím prvkem a hranicí nadřazeného kontejneru je pevně nastavená v době, kdy <xref:System.Windows.Forms.Control.Anchor%2A> je vlastnost nastavena.</span><span class="sxs-lookup"><span data-stu-id="c610c-112">In other container controls, the child control does not move when the <xref:System.Windows.Forms.Control.Anchor%2A> property is set, and the distance between the anchored control and the parent container's boundary is fixed at the time the <xref:System.Windows.Forms.Control.Anchor%2A> property is set.</span></span>  
  
5. <span data-ttu-id="c610c-113">Změňte hodnotu <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Anchor%2A> vlastnosti ovládacího prvku na `Top, Left`.</span><span class="sxs-lookup"><span data-stu-id="c610c-113">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Left`.</span></span> <span data-ttu-id="c610c-114"><xref:System.Windows.Forms.Button> Ovládací prvek se přesune, aby vybíral levý horní roh buňky.</span><span class="sxs-lookup"><span data-stu-id="c610c-114">The <xref:System.Windows.Forms.Button> control moves to occupy the top-left corner of the cell.</span></span>  
  
6. <span data-ttu-id="c610c-115">Opakujte krok 5 s hodnotou `Top, Right` pro <xref:System.Windows.Forms.Button> přesunutí ovládacího prvku do pravého horního rohu buňky.</span><span class="sxs-lookup"><span data-stu-id="c610c-115">Repeat step 5 with a value of `Top, Right` to move the <xref:System.Windows.Forms.Button> control to the top-right corner of the cell.</span></span> <span data-ttu-id="c610c-116">Opakujte s hodnotami `Bottom, Left` a `Bottom, Right`.</span><span class="sxs-lookup"><span data-stu-id="c610c-116">Repeat with values of `Bottom, Left` and `Bottom, Right`.</span></span>  
  
### <a name="to-stretch-a-child-control-in-a-tablelayoutpanel-cell"></a><span data-ttu-id="c610c-117">Roztažení podřízeného ovládacího prvku v buňce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="c610c-117">To stretch a child control in a TableLayoutPanel cell</span></span>  
  
1. <span data-ttu-id="c610c-118">Změňte hodnotu <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Anchor%2A> vlastnosti ovládacího prvku na `Left, Right`.</span><span class="sxs-lookup"><span data-stu-id="c610c-118">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left, Right`.</span></span> <span data-ttu-id="c610c-119">Velikost <xref:System.Windows.Forms.Button> ovládacího prvku se změní tak, aby se roztáhla napříč buňkou.</span><span class="sxs-lookup"><span data-stu-id="c610c-119">The <xref:System.Windows.Forms.Button> control is resized to stretch across the cell.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c610c-120">Toto chování se liší od chování jiných ovládacích prvků kontejneru.</span><span class="sxs-lookup"><span data-stu-id="c610c-120">This behavior differs from the behavior of other container controls.</span></span> <span data-ttu-id="c610c-121">V jiných ovládacích prvcích kontejneru není podřízený ovládací prvek změněna velikost, pokud <xref:System.Windows.Forms.Control.Anchor%2A> je vlastnost nastavena na `Left, Right` nebo `Top, Bottom`.</span><span class="sxs-lookup"><span data-stu-id="c610c-121">In other container controls, the child control is not resized when the <xref:System.Windows.Forms.Control.Anchor%2A> property is set to `Left, Right` or `Top, Bottom`.</span></span>  
  
2. <span data-ttu-id="c610c-122">Změňte hodnotu <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Anchor%2A> vlastnosti ovládacího prvku na `Top, Bottom`.</span><span class="sxs-lookup"><span data-stu-id="c610c-122">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Bottom`.</span></span> <span data-ttu-id="c610c-123">Velikost <xref:System.Windows.Forms.Button> ovládacího prvku se změní tak, aby se natáhla shora dolů v dolní části buňky.</span><span class="sxs-lookup"><span data-stu-id="c610c-123">The <xref:System.Windows.Forms.Button> control is resized to stretch from the top to the bottom of the cell.</span></span>  
  
3. <span data-ttu-id="c610c-124">Změňte hodnotu <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Anchor%2A> vlastnosti ovládacího prvku na `Top, Bottom, Left, Right`.</span><span class="sxs-lookup"><span data-stu-id="c610c-124">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Bottom, Left, Right`.</span></span> <span data-ttu-id="c610c-125">Velikost <xref:System.Windows.Forms.Button> ovládacího prvku se změní tak, aby se vyplnila buňka.</span><span class="sxs-lookup"><span data-stu-id="c610c-125">The <xref:System.Windows.Forms.Button> control is resized to fill the cell.</span></span>  
  
4. <span data-ttu-id="c610c-126">Změňte hodnotu <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Anchor%2A> vlastnosti ovládacího prvku na `None`.</span><span class="sxs-lookup"><span data-stu-id="c610c-126">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `None`.</span></span> <span data-ttu-id="c610c-127">Velikost <xref:System.Windows.Forms.Button> ovládacího prvku se změní na střed v buňce.</span><span class="sxs-lookup"><span data-stu-id="c610c-127">The <xref:System.Windows.Forms.Button> control is resized and centered in the cell.</span></span>  
  
5. <span data-ttu-id="c610c-128">Změňte hodnotu <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Dock%2A> vlastnosti ovládacího prvku na <xref:System.Windows.Forms.DockStyle.Left>.</span><span class="sxs-lookup"><span data-stu-id="c610c-128">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Left>.</span></span> <span data-ttu-id="c610c-129"><xref:System.Windows.Forms.Button> Ovládací prvek se přesune k zarovnání s levým ohraničením buňky.</span><span class="sxs-lookup"><span data-stu-id="c610c-129">The <xref:System.Windows.Forms.Button> control moves to align with the left border of the cell.</span></span> <span data-ttu-id="c610c-130"><xref:System.Windows.Forms.Button> Ovládací prvek si zachová šířku, ale jeho výška se změní tak, aby se buňka vyplnila svisle.</span><span class="sxs-lookup"><span data-stu-id="c610c-130">The <xref:System.Windows.Forms.Button> control retains its width, but its height is resized to fill the cell vertically.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c610c-131">Jedná se o stejné chování, ke kterému dochází v jiných ovládacích prvcích kontejneru.</span><span class="sxs-lookup"><span data-stu-id="c610c-131">This is the same behavior that occurs in other container controls.</span></span>  
  
6. <span data-ttu-id="c610c-132">Změňte hodnotu <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Dock%2A> vlastnosti ovládacího prvku na <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="c610c-132">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span> <span data-ttu-id="c610c-133">Velikost <xref:System.Windows.Forms.Button> ovládacího prvku se změní tak, aby se vyplnila buňka.</span><span class="sxs-lookup"><span data-stu-id="c610c-133">The <xref:System.Windows.Forms.Button> control is resized to fill the cell.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c610c-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="c610c-134">Example</span></span>  
 <span data-ttu-id="c610c-135">Následující ilustrace znázorňuje pět tlačítek ukotvených v pěti samostatných <xref:System.Windows.Forms.TableLayoutPanel> buňkách.</span><span class="sxs-lookup"><span data-stu-id="c610c-135">The following illustration shows five buttons anchored in five separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="c610c-136">![Ukotvení kontejneru TableLayoutPanel](./media/vs-tlpanchor.gif "VS_TLPanchor")</span><span class="sxs-lookup"><span data-stu-id="c610c-136">![TableLayoutPanel Anchoring](./media/vs-tlpanchor.gif "VS_TLPanchor")</span></span>  
  
 <span data-ttu-id="c610c-137">Následující ilustrace znázorňuje čtyři tlačítka ukotvená v rozích čtyř samostatných <xref:System.Windows.Forms.TableLayoutPanel> buněk.</span><span class="sxs-lookup"><span data-stu-id="c610c-137">The following illustration shows four buttons anchored in the corners of four separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="c610c-138">![Ukotvení kontejneru TableLayoutPanel](./media/vs-tlpanchor2.gif "VS_TLPanchor2")</span><span class="sxs-lookup"><span data-stu-id="c610c-138">![TableLayoutPanel Anchoring](./media/vs-tlpanchor2.gif "VS_TLPanchor2")</span></span>  
  
 <span data-ttu-id="c610c-139">Následující ilustrace znázorňuje tři tlačítka roztažená ukotvením ve třech samostatných <xref:System.Windows.Forms.TableLayoutPanel> buňkách.</span><span class="sxs-lookup"><span data-stu-id="c610c-139">The following illustration shows three buttons stretched by anchoring in three separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="c610c-140">![Ukotvení kontejneru TableLayoutPanel](./media/vs-tlpanchor3.gif "VS_TLPAnchor3")</span><span class="sxs-lookup"><span data-stu-id="c610c-140">![TableLayoutPanel Anchoring](./media/vs-tlpanchor3.gif "VS_TLPAnchor3")</span></span>  
  
 <span data-ttu-id="c610c-141">Následující příklad kódu ukazuje všechny kombinace <xref:System.Windows.Forms.Control.Anchor%2A> hodnot <xref:System.Windows.Forms.Button> vlastností ovládacího prvku v <xref:System.Windows.Forms.TableLayoutPanel> ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="c610c-141">The following code example demonstrates all the combinations of <xref:System.Windows.Forms.Control.Anchor%2A> property values for a <xref:System.Windows.Forms.Button> control in a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/CS/TlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/VB/TlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c610c-142">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="c610c-142">Compiling the Code</span></span>  
 <span data-ttu-id="c610c-143">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="c610c-143">This example requires:</span></span>  
  
- <span data-ttu-id="c610c-144">Odkazy na sestavení System, System. data, System. Drawing a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="c610c-144">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c610c-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c610c-145">See also</span></span>

- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="c610c-146">Ovládací prvek TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="c610c-146">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)
