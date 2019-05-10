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
ms.openlocfilehash: 82d75559260292476d81e4440280efb46bfd86c9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64613022"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control"></a><span data-ttu-id="ba5cb-102">Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="ba5cb-102">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>
<span data-ttu-id="ba5cb-103"><xref:System.Windows.Forms.TableLayoutPanel> Podporuje ovládací prvek <xref:System.Windows.Forms.Control.Anchor%2A> a <xref:System.Windows.Forms.Control.Dock%2A> vlastnosti v jeho podřízených ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="ba5cb-103">The <xref:System.Windows.Forms.TableLayoutPanel> control supports the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties in its child controls.</span></span>  
  
### <a name="to-align-a-child-control-in-a-tablelayoutpanel-cell"></a><span data-ttu-id="ba5cb-104">Chcete-li zarovnat podřízeného ovládacího prvku v buňce kontejneru TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="ba5cb-104">To align a child control in a TableLayoutPanel cell</span></span>  
  
1. <span data-ttu-id="ba5cb-105">Vytvoření <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="ba5cb-105">Create a <xref:System.Windows.Forms.TableLayoutPanel> control on your form.</span></span>  
  
2. <span data-ttu-id="ba5cb-106">Nastavte hodnotu <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> a <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> vlastností **1**.</span><span class="sxs-lookup"><span data-stu-id="ba5cb-106">Set the value of the <xref:System.Windows.Forms.TableLayoutPanel> control's <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> and <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> properties to **1**.</span></span>  
  
3. <span data-ttu-id="ba5cb-107">Vytvoření <xref:System.Windows.Forms.Button> v ovládacím prvku <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ba5cb-107">Create a <xref:System.Windows.Forms.Button> control in the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="ba5cb-108"><xref:System.Windows.Forms.Button> Zabírá levém horním rohu buňky.</span><span class="sxs-lookup"><span data-stu-id="ba5cb-108">The <xref:System.Windows.Forms.Button> occupies the upper-left corner of the cell.</span></span>  
  
4. <span data-ttu-id="ba5cb-109">Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Left`.</span><span class="sxs-lookup"><span data-stu-id="ba5cb-109">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left`.</span></span> <span data-ttu-id="ba5cb-110"><xref:System.Windows.Forms.Button> Ovládacího prvku přesune na bylo v souladu s levého ohraničení buňky.</span><span class="sxs-lookup"><span data-stu-id="ba5cb-110">The <xref:System.Windows.Forms.Button> control moves to align with the left border of the cell.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ba5cb-111">Toto chování se liší od chování další ovládací prvky kontejneru.</span><span class="sxs-lookup"><span data-stu-id="ba5cb-111">This behavior differs from the behavior of other container controls.</span></span> <span data-ttu-id="ba5cb-112">V další ovládací prvky kontejneru podřízený ovládací prvek nepřesouvá při <xref:System.Windows.Forms.Control.Anchor%2A> je vlastnost nastavena a vzdálenost mezi ukotvené ovládacího prvku a hranice nadřazeného kontejneru je stanovena v době <xref:System.Windows.Forms.Control.Anchor%2A> je nastavena.</span><span class="sxs-lookup"><span data-stu-id="ba5cb-112">In other container controls, the child control does not move when the <xref:System.Windows.Forms.Control.Anchor%2A> property is set, and the distance between the anchored control and the parent container's boundary is fixed at the time the <xref:System.Windows.Forms.Control.Anchor%2A> property is set.</span></span>  
  
5. <span data-ttu-id="ba5cb-113">Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Top, Left`.</span><span class="sxs-lookup"><span data-stu-id="ba5cb-113">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Left`.</span></span> <span data-ttu-id="ba5cb-114"><xref:System.Windows.Forms.Button> Ovládacího prvku přesune tak, aby obsadily levého horního rohu buňky.</span><span class="sxs-lookup"><span data-stu-id="ba5cb-114">The <xref:System.Windows.Forms.Button> control moves to occupy the top-left corner of the cell.</span></span>  
  
6. <span data-ttu-id="ba5cb-115">Opakováním kroku 5 s hodnotou `Top, Right` přesunout <xref:System.Windows.Forms.Button> ovládacího prvku na pravém horním rohu buňky.</span><span class="sxs-lookup"><span data-stu-id="ba5cb-115">Repeat step 5 with a value of `Top, Right` to move the <xref:System.Windows.Forms.Button> control to the top-right corner of the cell.</span></span> <span data-ttu-id="ba5cb-116">Opakování s hodnotami `Bottom, Left` a `Bottom, Right`.</span><span class="sxs-lookup"><span data-stu-id="ba5cb-116">Repeat with values of `Bottom, Left` and `Bottom, Right`.</span></span>  
  
### <a name="to-stretch-a-child-control-in-a-tablelayoutpanel-cell"></a><span data-ttu-id="ba5cb-117">Roztáhnout podřízeného ovládacího prvku v buňce kontejneru TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="ba5cb-117">To stretch a child control in a TableLayoutPanel cell</span></span>  
  
1. <span data-ttu-id="ba5cb-118">Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Left, Right`.</span><span class="sxs-lookup"><span data-stu-id="ba5cb-118">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left, Right`.</span></span> <span data-ttu-id="ba5cb-119"><xref:System.Windows.Forms.Button> Změně velikosti ovládacího prvku k roztahování v buňce.</span><span class="sxs-lookup"><span data-stu-id="ba5cb-119">The <xref:System.Windows.Forms.Button> control is resized to stretch across the cell.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ba5cb-120">Toto chování se liší od chování další ovládací prvky kontejneru.</span><span class="sxs-lookup"><span data-stu-id="ba5cb-120">This behavior differs from the behavior of other container controls.</span></span> <span data-ttu-id="ba5cb-121">V další ovládací prvky kontejneru podřízený ovládací prvek není při změně velikosti <xref:System.Windows.Forms.Control.Anchor%2A> je nastavena na `Left, Right` nebo `Top, Bottom`.</span><span class="sxs-lookup"><span data-stu-id="ba5cb-121">In other container controls, the child control is not resized when the <xref:System.Windows.Forms.Control.Anchor%2A> property is set to `Left, Right` or `Top, Bottom`.</span></span>  
  
2. <span data-ttu-id="ba5cb-122">Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Top, Bottom`.</span><span class="sxs-lookup"><span data-stu-id="ba5cb-122">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Bottom`.</span></span> <span data-ttu-id="ba5cb-123"><xref:System.Windows.Forms.Button> Změně velikosti ovládacího prvku k roztahování shora dolů buňce.</span><span class="sxs-lookup"><span data-stu-id="ba5cb-123">The <xref:System.Windows.Forms.Button> control is resized to stretch from the top to the bottom of the cell.</span></span>  
  
3. <span data-ttu-id="ba5cb-124">Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Top, Bottom, Left, Right`.</span><span class="sxs-lookup"><span data-stu-id="ba5cb-124">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Bottom, Left, Right`.</span></span> <span data-ttu-id="ba5cb-125"><xref:System.Windows.Forms.Button> Změně velikosti ovládacího prvku tak, aby vyplnil buňku.</span><span class="sxs-lookup"><span data-stu-id="ba5cb-125">The <xref:System.Windows.Forms.Button> control is resized to fill the cell.</span></span>  
  
4. <span data-ttu-id="ba5cb-126">Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `None`.</span><span class="sxs-lookup"><span data-stu-id="ba5cb-126">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `None`.</span></span> <span data-ttu-id="ba5cb-127"><xref:System.Windows.Forms.Button> Změně velikosti nebo na střed v buňce ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ba5cb-127">The <xref:System.Windows.Forms.Button> control is resized and centered in the cell.</span></span>  
  
5. <span data-ttu-id="ba5cb-128">Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Left>.</span><span class="sxs-lookup"><span data-stu-id="ba5cb-128">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Left>.</span></span> <span data-ttu-id="ba5cb-129"><xref:System.Windows.Forms.Button> Ovládacího prvku přesune na bylo v souladu s levého ohraničení buňky.</span><span class="sxs-lookup"><span data-stu-id="ba5cb-129">The <xref:System.Windows.Forms.Button> control moves to align with the left border of the cell.</span></span> <span data-ttu-id="ba5cb-130"><xref:System.Windows.Forms.Button> Uchovává šířku ovládacího prvku, ale jeho výška svou velikost tak, aby vyplnil buňky svisle.</span><span class="sxs-lookup"><span data-stu-id="ba5cb-130">The <xref:System.Windows.Forms.Button> control retains its width, but its height is resized to fill the cell vertically.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ba5cb-131">Toto je stejné chování, který se nachází v jiné ovládací prvky kontejneru.</span><span class="sxs-lookup"><span data-stu-id="ba5cb-131">This is the same behavior that occurs in other container controls.</span></span>  
  
6. <span data-ttu-id="ba5cb-132">Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="ba5cb-132">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span> <span data-ttu-id="ba5cb-133"><xref:System.Windows.Forms.Button> Změně velikosti ovládacího prvku tak, aby vyplnil buňku.</span><span class="sxs-lookup"><span data-stu-id="ba5cb-133">The <xref:System.Windows.Forms.Button> control is resized to fill the cell.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba5cb-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="ba5cb-134">Example</span></span>  
 <span data-ttu-id="ba5cb-135">Následující obrázek znázorňuje pět tlačítek ukotvené pět samostatné <xref:System.Windows.Forms.TableLayoutPanel> buňky.</span><span class="sxs-lookup"><span data-stu-id="ba5cb-135">The following illustration shows five buttons anchored in five separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="ba5cb-136">![Kontejner TableLayoutPanel ukotvení](./media/vs-tlpanchor.gif "VS_TLPanchor")</span><span class="sxs-lookup"><span data-stu-id="ba5cb-136">![TableLayoutPanel Anchoring](./media/vs-tlpanchor.gif "VS_TLPanchor")</span></span>  
  
 <span data-ttu-id="ba5cb-137">Následující obrázek znázorňuje čtyři tlačítka ukotvené v rozích čtyři samostatné <xref:System.Windows.Forms.TableLayoutPanel> buňky.</span><span class="sxs-lookup"><span data-stu-id="ba5cb-137">The following illustration shows four buttons anchored in the corners of four separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="ba5cb-138">![Kontejner TableLayoutPanel ukotvení](./media/vs-tlpanchor2.gif "VS_TLPanchor2")</span><span class="sxs-lookup"><span data-stu-id="ba5cb-138">![TableLayoutPanel Anchoring](./media/vs-tlpanchor2.gif "VS_TLPanchor2")</span></span>  
  
 <span data-ttu-id="ba5cb-139">Následující obrázek znázorňuje tři tlačítka roztažená podle ukotvení tři samostatné <xref:System.Windows.Forms.TableLayoutPanel> buňky.</span><span class="sxs-lookup"><span data-stu-id="ba5cb-139">The following illustration shows three buttons stretched by anchoring in three separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="ba5cb-140">![Kontejner TableLayoutPanel ukotvení](./media/vs-tlpanchor3.gif "VS_TLPAnchor3")</span><span class="sxs-lookup"><span data-stu-id="ba5cb-140">![TableLayoutPanel Anchoring](./media/vs-tlpanchor3.gif "VS_TLPAnchor3")</span></span>  
  
 <span data-ttu-id="ba5cb-141">Následující příklad kódu ukazuje všechny kombinace <xref:System.Windows.Forms.Control.Anchor%2A> hodnot vlastností pro <xref:System.Windows.Forms.Button> v ovládacím prvku <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ba5cb-141">The following code example demonstrates all the combinations of <xref:System.Windows.Forms.Control.Anchor%2A> property values for a <xref:System.Windows.Forms.Button> control in a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/CS/TlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/VB/TlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ba5cb-142">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ba5cb-142">Compiling the Code</span></span>  
 <span data-ttu-id="ba5cb-143">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="ba5cb-143">This example requires:</span></span>  
  
- <span data-ttu-id="ba5cb-144">Odkazy na sestavení systému, System.Data, System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="ba5cb-144">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="ba5cb-145">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="ba5cb-145">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="ba5cb-146">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="ba5cb-146">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba5cb-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ba5cb-147">See also</span></span>

- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="ba5cb-148">Ovládací prvek TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="ba5cb-148">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)
