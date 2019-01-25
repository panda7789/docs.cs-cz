---
title: 'Postupy: Změna rozložení ovládacího prvku DataRepeater (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, changing layout style
- DataRepeater, changing orientation
ms.assetid: 33aa8fd5-ac63-4bd0-ba13-8c2ab17e7824
ms.openlocfilehash: 3389daa6383444b48faab4c5383b281e44349bce
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625598"
---
# <a name="how-to-change-the-layout-of-a-datarepeater-control-visual-studio"></a><span data-ttu-id="9133c-102">Postupy: Změna rozložení ovládacího prvku DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="9133c-102">How to: Change the Layout of a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="9133c-103"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Ovládací prvek lze zobrazit ve svislé (položky posunout svisle) nebo vodorovně (posunutí položky vodorovně) orientace.</span><span class="sxs-lookup"><span data-stu-id="9133c-103">The <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control can be displayed in either a vertical (items scroll vertically) or horizontal (items scroll horizontally) orientation.</span></span> <span data-ttu-id="9133c-104">Orientace v době návrhu nebo za běhu můžete změnit tak, že změníte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9133c-104">You can change the orientation at design time or at run time by changing the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property.</span></span> <span data-ttu-id="9133c-105">Pokud změníte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> vlastnost v době běhu, můžete také změnit velikost <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> a přemístění podřízené ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="9133c-105">If you change the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property at run time, you may also want to resize the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> and reposition the child controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9133c-106">Pokud umístění ovládacích prvků na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> za běhu, je potřeba volat <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> metody na začátek a konec bloku kódu, který přemístí ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="9133c-106">If you reposition controls on the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> at run time, you will need to call the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> and <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> methods at the beginning and end of the code block that repositions the controls.</span></span>  
  
### <a name="to-change-the-layout-at-design-time"></a><span data-ttu-id="9133c-107">Chcete-li změnit rozložení v době návrhu</span><span class="sxs-lookup"><span data-stu-id="9133c-107">To change the layout at design time</span></span>  
  
1.  <span data-ttu-id="9133c-108">V Návrháři formulářů Windows, vyberte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9133c-108">In the Windows Forms Designer, select the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9133c-109">Je nutné vybrat vnější okraj <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku v dolní oblasti ovládacího prvku, ne v horním rohu klikněte na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> oblasti.</span><span class="sxs-lookup"><span data-stu-id="9133c-109">You must select the outer border of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control by clicking in the lower region of the control, not in the upper <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> region.</span></span>  
  
2.  <span data-ttu-id="9133c-110">V okně Vlastnosti nastavte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> vlastnost buď <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> nebo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>.</span><span class="sxs-lookup"><span data-stu-id="9133c-110">In the Properties window, set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property to either <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> or <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>.</span></span>  
  
### <a name="to-change-the-layout-at-run-time"></a><span data-ttu-id="9133c-111">Chcete-li změnit rozložení v době běhu</span><span class="sxs-lookup"><span data-stu-id="9133c-111">To change the layout at run time</span></span>  
  
1.  <span data-ttu-id="9133c-112">Přidejte následující kód k tlačítka nebo nabídka `Click` obslužné rutiny události:</span><span class="sxs-lookup"><span data-stu-id="9133c-112">Add the following code to a button or menu `Click` event handler:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.vb)]  
  
2.  <span data-ttu-id="9133c-113">Ve většině případů budete chtít přidat kód, který se zobrazí v oddíle Příklad pro změnu velikosti podobný <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> a změna uspořádání ovládacích prvků podle nového orientace.</span><span class="sxs-lookup"><span data-stu-id="9133c-113">In most cases, you will want to add code similar to that shown in the Example section to resize the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> and rearrange controls to fit the new orientation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9133c-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="9133c-114">Example</span></span>  
 <span data-ttu-id="9133c-115">Následující příklad ukazuje, jak reagovat na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyleChanged> události v obslužné rutině události.</span><span class="sxs-lookup"><span data-stu-id="9133c-115">The following example shows how to respond to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyleChanged> event in an event handler.</span></span> <span data-ttu-id="9133c-116">Tento příklad vyžaduje, abyste měli <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládací prvek s názvem `DataRepeater1` na formuláři a že jeho <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> obsahovat dva <xref:System.Windows.Forms.TextBox> ovládací prvky s názvem `TextBox1` a `TextBox2`.</span><span class="sxs-lookup"><span data-stu-id="9133c-116">This example requires that you have a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control named `DataRepeater1` on a form and that its <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> contain two <xref:System.Windows.Forms.TextBox> controls named `TextBox1` and `TextBox2`.</span></span>  
  
 [!code-csharp[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.cs)]
 [!code-vb[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9133c-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9133c-117">See also</span></span>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A>
- [<span data-ttu-id="9133c-118">Úvod do ovládacího prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="9133c-118">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="9133c-119">Řešení potíží s ovládacím prvkem DataRepeater</span><span class="sxs-lookup"><span data-stu-id="9133c-119">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="9133c-120">Postupy: Změna vzhledu ovládacího prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="9133c-120">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
