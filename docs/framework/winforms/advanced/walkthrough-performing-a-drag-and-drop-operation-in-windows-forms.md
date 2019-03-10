---
title: 'Návod: Operace a přetažení ve Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: 664c78ce3fff9651acf6ad720360cdb077f23108
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715240"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a><span data-ttu-id="5226b-102">Návod: Operace a přetažení ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5226b-102">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>
<span data-ttu-id="5226b-103">K provádění operací přetažení myší v rámci aplikace pro systém Windows je třeba ošetřit řadu událostí, zejména <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, a <xref:System.Windows.Forms.Control.DragDrop> události.</span><span class="sxs-lookup"><span data-stu-id="5226b-103">To perform drag-and-drop operations within Windows-based applications you must handle a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span> <span data-ttu-id="5226b-104">Při práci s informacemi, které jsou k dispozici události argumenty tyto události, můžete snadno usnadnění operace přetažení myší.</span><span class="sxs-lookup"><span data-stu-id="5226b-104">By working with the information available in the event arguments of these events, you can easily facilitate drag-and-drop operations.</span></span>  
  
## <a name="dragging-data"></a><span data-ttu-id="5226b-105">Přetažení dat</span><span class="sxs-lookup"><span data-stu-id="5226b-105">Dragging Data</span></span>  
 <span data-ttu-id="5226b-106">Všechny operace přetažení myší začínat přetažení.</span><span class="sxs-lookup"><span data-stu-id="5226b-106">All drag-and-drop operations begin with dragging.</span></span> <span data-ttu-id="5226b-107">Funkce, které umožňují data shromažďovat, přetažením začíná je implementována v <xref:System.Windows.Forms.Control.DoDragDrop%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5226b-107">The functionality to enable data to be collected when dragging begins is implemented in the <xref:System.Windows.Forms.Control.DoDragDrop%2A> method.</span></span>  
  
 <span data-ttu-id="5226b-108">V následujícím příkladu <xref:System.Windows.Forms.Control.MouseDown> událostí se používá ke spuštění operace přetažení, protože je nejvíce intuitivní (většinu akcí a přetahování začínat tlačítko myši stisknuté se).</span><span class="sxs-lookup"><span data-stu-id="5226b-108">In the following example, the <xref:System.Windows.Forms.Control.MouseDown> event is used to start the drag operation because it is the most intuitive (most drag-and-drop actions begin with the mouse button being depressed).</span></span> <span data-ttu-id="5226b-109">Nezapomeňte však, že všechny události se používal k zahájení proceduru přetahování myší.</span><span class="sxs-lookup"><span data-stu-id="5226b-109">However, remember that any event could be used to initiate a drag-and-drop procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5226b-110">Některé ovládací prvky mají vlastní události specifické pro přetažení.</span><span class="sxs-lookup"><span data-stu-id="5226b-110">Certain controls have custom drag-specific events.</span></span> <span data-ttu-id="5226b-111"><xref:System.Windows.Forms.ListView> a <xref:System.Windows.Forms.TreeView> ovládacích prvků, třeba mít <xref:System.Windows.Forms.TreeView.ItemDrag> událostí.</span><span class="sxs-lookup"><span data-stu-id="5226b-111">The <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls, for example, have an <xref:System.Windows.Forms.TreeView.ItemDrag> event.</span></span>  
  
#### <a name="to-start-a-drag-operation"></a><span data-ttu-id="5226b-112">Pokud chcete spustit operaci přetažení</span><span class="sxs-lookup"><span data-stu-id="5226b-112">To start a drag operation</span></span>  
  
1.  <span data-ttu-id="5226b-113">V <xref:System.Windows.Forms.Control.MouseDown> události pro ovládací prvek ve kterém se začne přetahování, použijte `DoDragDrop` bude mít metody nastavte data, která mají být kvůli usnadnění použití vypsány a povoleným efektem přetažení.</span><span class="sxs-lookup"><span data-stu-id="5226b-113">In the <xref:System.Windows.Forms.Control.MouseDown> event for the control where the drag will begin, use the `DoDragDrop` method to set the data to be dragged and the allowed effect dragging will have.</span></span> <span data-ttu-id="5226b-114">Další informace naleznete v tématu <xref:System.Windows.Forms.DragEventArgs.Data%2A> a <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span><span class="sxs-lookup"><span data-stu-id="5226b-114">For more information, see <xref:System.Windows.Forms.DragEventArgs.Data%2A> and <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span></span>  
  
     <span data-ttu-id="5226b-115">Následující příklad ukazuje, jak k zahájení operace přetažení.</span><span class="sxs-lookup"><span data-stu-id="5226b-115">The following example shows how to initiate a drag operation.</span></span> <span data-ttu-id="5226b-116">Ovládací prvek, kde začíná přetahování <xref:System.Windows.Forms.Button> ovládacího prvku, data jsou kvůli usnadnění použití vypsány je řetězec představující <xref:System.Windows.Forms.Control.Text%2A> vlastnost <xref:System.Windows.Forms.Button> ovládacího prvku a povolené efekty jsou kopírování nebo přesunutí.</span><span class="sxs-lookup"><span data-stu-id="5226b-116">The control where the drag begins is a <xref:System.Windows.Forms.Button> control, the data being dragged is the string representing the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control, and the allowed effects are either copying or moving.</span></span>  
  
    ```vb  
    Private Sub Button1_MouseDown(ByVal sender As Object, ByVal e As System.Windows.Forms.MouseEventArgs) Handles Button1.MouseDown  
       Button1.DoDragDrop(Button1.Text, DragDropEffects.Copy Or DragDropEffects.Move)  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_MouseDown(object sender,   
    System.Windows.Forms.MouseEventArgs e)  
    {  
       button1.DoDragDrop(button1.Text, DragDropEffects.Copy |   
          DragDropEffects.Move);  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="5226b-117">Všechna data, můžete použít jako parametr v `DoDragDrop` metody; v příkladu výše, <xref:System.Windows.Forms.Control.Text%2A> vlastnost <xref:System.Windows.Forms.Button> ovládací prvek byl použit (místo pevného kódování hodnotu nebo načítání dat z datové sady) vzhledem k tomu, že byla vlastnosti související s přetažen z umístění ( <xref:System.Windows.Forms.Button> ovládací prvek).</span><span class="sxs-lookup"><span data-stu-id="5226b-117">Any data can be used as a parameter in the `DoDragDrop` method; in the example above, the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control was used (rather than hard-coding a value or retrieving data from a dataset) because the property was related to the location being dragged from (the <xref:System.Windows.Forms.Button> control).</span></span> <span data-ttu-id="5226b-118">Mějte na paměti jako začlenit operací přetažení myší do vaší aplikace pro systém Windows.</span><span class="sxs-lookup"><span data-stu-id="5226b-118">Keep this in mind as you incorporate drag-and-drop operations into your Windows-based applications.</span></span>  
  
 <span data-ttu-id="5226b-119">Během operace přetažení je v platnosti, můžete zpracovávat <xref:System.Windows.Forms.Control.QueryContinueDrag> událost, která "požádá oprávnění" systému pokračovat v provádění operace přetažení.</span><span class="sxs-lookup"><span data-stu-id="5226b-119">While a drag operation is in effect, you can handle the <xref:System.Windows.Forms.Control.QueryContinueDrag> event, which "asks permission" of the system to continue the drag operation.</span></span> <span data-ttu-id="5226b-120">Při zpracování této metody, je také odpovídajícím bodě si můžete volat metody, které budou mít vliv na operace přetažení, například rozšíření <xref:System.Windows.Forms.TreeNode> v <xref:System.Windows.Forms.TreeView> ovládací prvek, když se ukazatelem přejde nad ním.</span><span class="sxs-lookup"><span data-stu-id="5226b-120">When handling this method, it is also the appropriate point for you to call methods that will have an effect on the drag operation, such as expanding a <xref:System.Windows.Forms.TreeNode> in a <xref:System.Windows.Forms.TreeView> control when the cursor hovers over it.</span></span>  
  
## <a name="dropping-data"></a><span data-ttu-id="5226b-121">Vyřazení dat</span><span class="sxs-lookup"><span data-stu-id="5226b-121">Dropping Data</span></span>  
 <span data-ttu-id="5226b-122">Po zahájení přetáhnete data z umístění na Windows formulář nebo ovládací prvek se přirozeně chcete vyřadit někde.</span><span class="sxs-lookup"><span data-stu-id="5226b-122">Once you have begun dragging data from a location on a Windows Form or control, you will naturally want to drop it somewhere.</span></span> <span data-ttu-id="5226b-123">Při překročí určitou oblast formuláře nebo ovládací prvek, který je správně nakonfigurovaný pro odstranění dat se změní kurzor.</span><span class="sxs-lookup"><span data-stu-id="5226b-123">The cursor will change when it crosses an area of a form or control that is correctly configured for dropping data.</span></span> <span data-ttu-id="5226b-124">Všechny oblasti v rámci ovládacího prvku formuláře Windows nebo můžete provést tak, aby přijímal vynechaných dat tím, že nastavíte <xref:System.Windows.Forms.Control.AllowDrop%2A> vlastnost a zpracování <xref:System.Windows.Forms.Control.DragEnter> a <xref:System.Windows.Forms.Control.DragDrop> události.</span><span class="sxs-lookup"><span data-stu-id="5226b-124">Any area within a Windows Form or control can be made to accept dropped data by setting the <xref:System.Windows.Forms.Control.AllowDrop%2A> property and handling the <xref:System.Windows.Forms.Control.DragEnter> and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
#### <a name="to-perform-a-drop"></a><span data-ttu-id="5226b-125">K provedení přetažení</span><span class="sxs-lookup"><span data-stu-id="5226b-125">To perform a drop</span></span>  
  
1.  <span data-ttu-id="5226b-126">Nastavte <xref:System.Windows.Forms.Control.AllowDrop%2A> vlastnost na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="5226b-126">Set the <xref:System.Windows.Forms.Control.AllowDrop%2A> property to true.</span></span>  
  
2.  <span data-ttu-id="5226b-127">V `DragEnter` události pro ovládací prvek, pokud dojde k rozevírací nabídku, ujistěte se, že data jsou kvůli usnadnění použití vypsány přijatelné typ (v tomto případě <xref:System.Windows.Forms.Control.Text%2A>).</span><span class="sxs-lookup"><span data-stu-id="5226b-127">In the `DragEnter` event for the control where the drop will occur, ensure that the data being dragged is of an acceptable type (in this case, <xref:System.Windows.Forms.Control.Text%2A>).</span></span> <span data-ttu-id="5226b-128">Kód poté nastaví efekt, který se stane, když rozevírací dojde k hodnotě ve <xref:System.Windows.Forms.DragDropEffects> výčtu.</span><span class="sxs-lookup"><span data-stu-id="5226b-128">The code then sets the effect that will happen when the drop occurs to a value in the <xref:System.Windows.Forms.DragDropEffects> enumeration.</span></span> <span data-ttu-id="5226b-129">Další informace naleznete v tématu <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span><span class="sxs-lookup"><span data-stu-id="5226b-129">For more information, see <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span></span>  
  
    ```vb  
    Private Sub TextBox1_DragEnter(ByVal sender As Object, ByVal e As System.Windows.Forms.DragEventArgs) Handles TextBox1.DragEnter  
       If (e.Data.GetDataPresent(DataFormats.Text)) Then  
         e.Effect = DragDropEffects.Copy  
       Else  
         e.Effect = DragDropEffects.None  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_DragEnter(object sender,   
    System.Windows.Forms.DragEventArgs e)  
    {  
       if (e.Data.GetDataPresent(DataFormats.Text))   
          e.Effect = DragDropEffects.Copy;  
       else  
          e.Effect = DragDropEffects.None;  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="5226b-130">Můžete definovat vlastní <xref:System.Windows.Forms.DataFormats> tak, že zadáte jako vlastní objekt <xref:System.Object> parametr <xref:System.Windows.Forms.DataObject.SetData%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5226b-130">You can define your own <xref:System.Windows.Forms.DataFormats> by specifying your own object as the <xref:System.Object> parameter of the <xref:System.Windows.Forms.DataObject.SetData%2A> method.</span></span> <span data-ttu-id="5226b-131">Ujistěte se, když to, že je zadaný objekt serializovatelný.</span><span class="sxs-lookup"><span data-stu-id="5226b-131">Be sure, when doing this, that the object specified is serializable.</span></span> <span data-ttu-id="5226b-132">Další informace naleznete v tématu <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="5226b-132">For more information, see <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
3.  <span data-ttu-id="5226b-133">V <xref:System.Windows.Forms.Control.DragDrop> události pro ovládací prvek rozevírací kde dojde, použijte <xref:System.Windows.Forms.DataObject.GetData%2A> metodu pro načtení dat se přetáhnout.</span><span class="sxs-lookup"><span data-stu-id="5226b-133">In the <xref:System.Windows.Forms.Control.DragDrop> event for the control where the drop will occur, use the <xref:System.Windows.Forms.DataObject.GetData%2A> method to retrieve the data being dragged.</span></span> <span data-ttu-id="5226b-134">Další informace naleznete v tématu <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span><span class="sxs-lookup"><span data-stu-id="5226b-134">For more information, see <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span></span>  
  
     <span data-ttu-id="5226b-135">V následujícím příkladu <xref:System.Windows.Forms.TextBox> ovládací prvek je ovládací prvek přetažen (ve kterém bude každý rozevírací).</span><span class="sxs-lookup"><span data-stu-id="5226b-135">In the example below, a <xref:System.Windows.Forms.TextBox> control is the control being dragged to (where the drop will occur).</span></span> <span data-ttu-id="5226b-136">Nastaví kód <xref:System.Windows.Forms.Control.Text%2A> vlastnost <xref:System.Windows.Forms.TextBox> řídit rovna data jsou kvůli usnadnění použití vypsány.</span><span class="sxs-lookup"><span data-stu-id="5226b-136">The code sets the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.TextBox> control equal to the data being dragged.</span></span>  
  
    ```vb  
    Private Sub TextBox1_DragDrop(ByVal sender As Object, ByVal e As System.Windows.Forms.DragEventArgs) Handles TextBox1.DragDrop  
       TextBox1.Text = e.Data.GetData(DataFormats.Text).ToString  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_DragDrop(object sender,   
    System.Windows.Forms.DragEventArgs e)  
    {  
       textBox1.Text = e.Data.GetData(DataFormats.Text).ToString();  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="5226b-137">Kromě toho můžete pracovat <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> určité účinkům dochází vlastnost, takže v závislosti na klíče stisknuté během operace přetažení myší, (například je standardní kopírování Přetahované dat při stisknutí klávesy CTRL).</span><span class="sxs-lookup"><span data-stu-id="5226b-137">Additionally, you can work with the <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> property, so that, depending on keys depressed during the drag-and-drop operation, certain effects occur (for example, it is standard to copy the dragged data when the CTRL key is pressed).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5226b-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5226b-138">See also</span></span>
- [<span data-ttu-id="5226b-139">Postupy: Přidání dat do schránky.</span><span class="sxs-lookup"><span data-stu-id="5226b-139">How to: Add Data to the Clipboard</span></span>](how-to-add-data-to-the-clipboard.md)
- [<span data-ttu-id="5226b-140">Postupy: Načtení dat ze schránky</span><span class="sxs-lookup"><span data-stu-id="5226b-140">How to: Retrieve Data from the Clipboard</span></span>](how-to-retrieve-data-from-the-clipboard.md)
- [<span data-ttu-id="5226b-141">Operace přetažení a podpora schránky</span><span class="sxs-lookup"><span data-stu-id="5226b-141">Drag-and-Drop Operations and Clipboard Support</span></span>](drag-and-drop-operations-and-clipboard-support.md)
