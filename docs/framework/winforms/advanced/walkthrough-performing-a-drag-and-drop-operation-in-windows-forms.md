---
title: 'Návod: Provádění operace přetažení ve Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: 6c78a06e37de491e95d56d29c9d2f3e60b88e8ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529451"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a><span data-ttu-id="8e595-102">Návod: Provádění operace přetažení ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8e595-102">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>
<span data-ttu-id="8e595-103">K provádění operací přetažení myší v rámci aplikace pro systém Windows je nutné zpracovat řadu událostí, zejména <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, a <xref:System.Windows.Forms.Control.DragDrop> události.</span><span class="sxs-lookup"><span data-stu-id="8e595-103">To perform drag-and-drop operations within Windows-based applications you must handle a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span> <span data-ttu-id="8e595-104">Ve spolupráci s informací, které jsou k dispozici události argumenty tyto události, můžete snadno usnadnění operací přetažení myší.</span><span class="sxs-lookup"><span data-stu-id="8e595-104">By working with the information available in the event arguments of these events, you can easily facilitate drag-and-drop operations.</span></span>  
  
## <a name="dragging-data"></a><span data-ttu-id="8e595-105">Přetahování dat</span><span class="sxs-lookup"><span data-stu-id="8e595-105">Dragging Data</span></span>  
 <span data-ttu-id="8e595-106">Všechny operace přetažení myší začínat přetahování.</span><span class="sxs-lookup"><span data-stu-id="8e595-106">All drag-and-drop operations begin with dragging.</span></span> <span data-ttu-id="8e595-107">Funkci, která umožní při přetahování začne shromažďovat data je implementována ve <xref:System.Windows.Forms.Control.DoDragDrop%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="8e595-107">The functionality to enable data to be collected when dragging begins is implemented in the <xref:System.Windows.Forms.Control.DoDragDrop%2A> method.</span></span>  
  
 <span data-ttu-id="8e595-108">V následujícím příkladu <xref:System.Windows.Forms.Control.MouseDown> událostí se používá ke spuštění operaci přetažení, protože je nejvíce intuitivní (většinu akcí a přetažení začínat tlačítko myši stisknuté probíhá).</span><span class="sxs-lookup"><span data-stu-id="8e595-108">In the following example, the <xref:System.Windows.Forms.Control.MouseDown> event is used to start the drag operation because it is the most intuitive (most drag-and-drop actions begin with the mouse button being depressed).</span></span> <span data-ttu-id="8e595-109">Nezapomeňte však, že všechny události by bylo možné zahájit přetažení myší řízení.</span><span class="sxs-lookup"><span data-stu-id="8e595-109">However, remember that any event could be used to initiate a drag-and-drop procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e595-110">Některé ovládací prvky mít vlastní události specifické pro přetažení.</span><span class="sxs-lookup"><span data-stu-id="8e595-110">Certain controls have custom drag-specific events.</span></span> <span data-ttu-id="8e595-111"><xref:System.Windows.Forms.ListView> a <xref:System.Windows.Forms.TreeView> ovládacích prvků, je třeba mít <xref:System.Windows.Forms.TreeView.ItemDrag> událostí.</span><span class="sxs-lookup"><span data-stu-id="8e595-111">The <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls, for example, have an <xref:System.Windows.Forms.TreeView.ItemDrag> event.</span></span>  
  
#### <a name="to-start-a-drag-operation"></a><span data-ttu-id="8e595-112">Spusťte operaci přetažení</span><span class="sxs-lookup"><span data-stu-id="8e595-112">To start a drag operation</span></span>  
  
1.  <span data-ttu-id="8e595-113">V <xref:System.Windows.Forms.Control.MouseDown> událostí pro ovládací prvek, kde bude zahájena přetažení, použijte `DoDragDrop` bude mít metodu a nastavit data, která mají být přetažen a povoleným efektem přetahování.</span><span class="sxs-lookup"><span data-stu-id="8e595-113">In the <xref:System.Windows.Forms.Control.MouseDown> event for the control where the drag will begin, use the `DoDragDrop` method to set the data to be dragged and the allowed effect dragging will have.</span></span> <span data-ttu-id="8e595-114">Další informace naleznete v tématu <xref:System.Windows.Forms.DragEventArgs.Data%2A> a <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span><span class="sxs-lookup"><span data-stu-id="8e595-114">For more information, see <xref:System.Windows.Forms.DragEventArgs.Data%2A> and <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span></span>  
  
     <span data-ttu-id="8e595-115">Následující příklad ukazuje, jak zahájit operaci přetažení.</span><span class="sxs-lookup"><span data-stu-id="8e595-115">The following example shows how to initiate a drag operation.</span></span> <span data-ttu-id="8e595-116">Ovládací prvek, kde začíná přetáhněte je <xref:System.Windows.Forms.Button> řízení, data přetažen je řetězec představující <xref:System.Windows.Forms.Control.Text%2A> vlastnost <xref:System.Windows.Forms.Button> řízení a povolených důsledky jsou kopírování nebo přesunutí.</span><span class="sxs-lookup"><span data-stu-id="8e595-116">The control where the drag begins is a <xref:System.Windows.Forms.Button> control, the data being dragged is the string representing the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control, and the allowed effects are either copying or moving.</span></span>  
  
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
    >  <span data-ttu-id="8e595-117">Žádná data lze použít jako parametr v `DoDragDrop` metoda; v příkladu nahoře, <xref:System.Windows.Forms.Control.Text%2A> vlastnost <xref:System.Windows.Forms.Button> řízení byl použit (místo pevně kódováno hodnotu nebo načítání dat z datové sady) vzhledem k tomu, že byla vlastnosti související s přetažení z umístění ( <xref:System.Windows.Forms.Button> řízení).</span><span class="sxs-lookup"><span data-stu-id="8e595-117">Any data can be used as a parameter in the `DoDragDrop` method; in the example above, the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control was used (rather than hard-coding a value or retrieving data from a dataset) because the property was related to the location being dragged from (the <xref:System.Windows.Forms.Button> control).</span></span> <span data-ttu-id="8e595-118">Mějte to na paměti, jak začlenit operací přetažení myší do vaší aplikace pro systém Windows.</span><span class="sxs-lookup"><span data-stu-id="8e595-118">Keep this in mind as you incorporate drag-and-drop operations into your Windows-based applications.</span></span>  
  
 <span data-ttu-id="8e595-119">Během operace přetažení, může zpracovat <xref:System.Windows.Forms.Control.QueryContinueDrag> událost, která "požádá oprávnění" systému do pokračovat v provádění operace přetažení.</span><span class="sxs-lookup"><span data-stu-id="8e595-119">While a drag operation is in effect, you can handle the <xref:System.Windows.Forms.Control.QueryContinueDrag> event, which "asks permission" of the system to continue the drag operation.</span></span> <span data-ttu-id="8e595-120">Při zpracování této metody, je také vhodné bod pro volání metody, které bude mít vliv na operace přetažení, jako je například rozšíření <xref:System.Windows.Forms.TreeNode> v <xref:System.Windows.Forms.TreeView> řízení, když ukazatel myši nad jeho.</span><span class="sxs-lookup"><span data-stu-id="8e595-120">When handling this method, it is also the appropriate point for you to call methods that will have an effect on the drag operation, such as expanding a <xref:System.Windows.Forms.TreeNode> in a <xref:System.Windows.Forms.TreeView> control when the cursor hovers over it.</span></span>  
  
## <a name="dropping-data"></a><span data-ttu-id="8e595-121">Vyřazení dat</span><span class="sxs-lookup"><span data-stu-id="8e595-121">Dropping Data</span></span>  
 <span data-ttu-id="8e595-122">Po zahájení přetahování data z umístění ve formuláři Windows nebo ovládací prvek, samozřejmě můžete někde ho vyřadit.</span><span class="sxs-lookup"><span data-stu-id="8e595-122">Once you have begun dragging data from a location on a Windows Form or control, you will naturally want to drop it somewhere.</span></span> <span data-ttu-id="8e595-123">Kurzor se změní, když ji oblasti formuláře nebo ovládací prvek, který je správně nakonfigurováno pro vyřazení dat překračuje.</span><span class="sxs-lookup"><span data-stu-id="8e595-123">The cursor will change when it crosses an area of a form or control that is correctly configured for dropping data.</span></span> <span data-ttu-id="8e595-124">Všechny oblasti v rámci formuláře Windows nebo řízení můžete provést tak, aby přijímal vynechaných data podle nastavení <xref:System.Windows.Forms.Control.AllowDrop%2A> vlastnost a zpracování <xref:System.Windows.Forms.Control.DragEnter> a <xref:System.Windows.Forms.Control.DragDrop> události.</span><span class="sxs-lookup"><span data-stu-id="8e595-124">Any area within a Windows Form or control can be made to accept dropped data by setting the <xref:System.Windows.Forms.Control.AllowDrop%2A> property and handling the <xref:System.Windows.Forms.Control.DragEnter> and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
#### <a name="to-perform-a-drop"></a><span data-ttu-id="8e595-125">K provedení pokles</span><span class="sxs-lookup"><span data-stu-id="8e595-125">To perform a drop</span></span>  
  
1.  <span data-ttu-id="8e595-126">Nastavte <xref:System.Windows.Forms.Control.AllowDrop%2A> vlastnost na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="8e595-126">Set the <xref:System.Windows.Forms.Control.AllowDrop%2A> property to true.</span></span>  
  
2.  <span data-ttu-id="8e595-127">V `DragEnter` událostí pro ovládací prvek, kde bude probíhat rozevíracího, zajistěte, aby byla data přetažen přijatelné typu (v tomto případě <xref:System.Windows.Forms.Control.Text%2A>).</span><span class="sxs-lookup"><span data-stu-id="8e595-127">In the `DragEnter` event for the control where the drop will occur, ensure that the data being dragged is of an acceptable type (in this case, <xref:System.Windows.Forms.Control.Text%2A>).</span></span> <span data-ttu-id="8e595-128">Kód pak nastaví o tom, že se stane, když dojde k rozevíracího na hodnotu v <xref:System.Windows.Forms.DragDropEffects> výčtu.</span><span class="sxs-lookup"><span data-stu-id="8e595-128">The code then sets the effect that will happen when the drop occurs to a value in the <xref:System.Windows.Forms.DragDropEffects> enumeration.</span></span> <span data-ttu-id="8e595-129">Další informace naleznete v tématu <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span><span class="sxs-lookup"><span data-stu-id="8e595-129">For more information, see <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span></span>  
  
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
    >  <span data-ttu-id="8e595-130">Můžete definovat vlastní <xref:System.Windows.Forms.DataFormats> zadáním vlastního objektu jako <xref:System.Object> parametr <xref:System.Windows.Forms.DataObject.SetData%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="8e595-130">You can define your own <xref:System.Windows.Forms.DataFormats> by specifying your own object as the <xref:System.Object> parameter of the <xref:System.Windows.Forms.DataObject.SetData%2A> method.</span></span> <span data-ttu-id="8e595-131">Třeba, aby, pokud to, zda je zadaný objekt serializable.</span><span class="sxs-lookup"><span data-stu-id="8e595-131">Be sure, when doing this, that the object specified is serializable.</span></span> <span data-ttu-id="8e595-132">Další informace naleznete v tématu <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="8e595-132">For more information, see <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
3.  <span data-ttu-id="8e595-133">V <xref:System.Windows.Forms.Control.DragDrop> událostí pro ovládací prvek rozevírací kde bude probíhat, použijte <xref:System.Windows.Forms.DataObject.GetData%2A> metoda pro načtení dat přetažen.</span><span class="sxs-lookup"><span data-stu-id="8e595-133">In the <xref:System.Windows.Forms.Control.DragDrop> event for the control where the drop will occur, use the <xref:System.Windows.Forms.DataObject.GetData%2A> method to retrieve the data being dragged.</span></span> <span data-ttu-id="8e595-134">Další informace naleznete v tématu <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span><span class="sxs-lookup"><span data-stu-id="8e595-134">For more information, see <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span></span>  
  
     <span data-ttu-id="8e595-135">V příkladu níže <xref:System.Windows.Forms.TextBox> prvek je ovládací prvek tažením (kde bude probíhat rozevíracího).</span><span class="sxs-lookup"><span data-stu-id="8e595-135">In the example below, a <xref:System.Windows.Forms.TextBox> control is the control being dragged to (where the drop will occur).</span></span> <span data-ttu-id="8e595-136">Nastaví kód <xref:System.Windows.Forms.Control.Text%2A> vlastnost <xref:System.Windows.Forms.TextBox> řízení rovna přetažen data.</span><span class="sxs-lookup"><span data-stu-id="8e595-136">The code sets the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.TextBox> control equal to the data being dragged.</span></span>  
  
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
    >  <span data-ttu-id="8e595-137">Kromě toho můžete pracovat <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> určité účinky dojít vlastnost tak, aby v závislosti na klíče stisknuté během operace přetahování myší, (například je standardní ke zkopírování taženou dat po stisknutí klávesy CTRL).</span><span class="sxs-lookup"><span data-stu-id="8e595-137">Additionally, you can work with the <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> property, so that, depending on keys depressed during the drag-and-drop operation, certain effects occur (for example, it is standard to copy the dragged data when the CTRL key is pressed).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e595-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e595-138">See Also</span></span>  
 [<span data-ttu-id="8e595-139">Postupy: Přidání dat do schránky</span><span class="sxs-lookup"><span data-stu-id="8e595-139">How to: Add Data to the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 [<span data-ttu-id="8e595-140">Postupy: Načtení dat ze schránky</span><span class="sxs-lookup"><span data-stu-id="8e595-140">How to: Retrieve Data from the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 [<span data-ttu-id="8e595-141">Operace přetažení a podpora schránky</span><span class="sxs-lookup"><span data-stu-id="8e595-141">Drag-and-Drop Operations and Clipboard Support</span></span>](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)
