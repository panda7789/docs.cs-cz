---
title: 'Návod: Provádění operace přetažení v modelu Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: cda3e87a4b0eb680d374eb0419a6b6b3157dc4a7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957126"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a><span data-ttu-id="9c599-102">Návod: Provádění operace přetažení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9c599-102">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>
<span data-ttu-id="9c599-103">K provádění operací přetažení v rámci aplikací pro systém Windows je nutné zpracovat řady událostí, zejména <xref:System.Windows.Forms.Control.DragEnter>události, <xref:System.Windows.Forms.Control.DragLeave>a <xref:System.Windows.Forms.Control.DragDrop> .</span><span class="sxs-lookup"><span data-stu-id="9c599-103">To perform drag-and-drop operations within Windows-based applications you must handle a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span> <span data-ttu-id="9c599-104">Při práci s informacemi dostupnými v argumentech událostí těchto událostí můžete snadno usnadnit operace přetažení.</span><span class="sxs-lookup"><span data-stu-id="9c599-104">By working with the information available in the event arguments of these events, you can easily facilitate drag-and-drop operations.</span></span>  
  
## <a name="dragging-data"></a><span data-ttu-id="9c599-105">Přetahování dat</span><span class="sxs-lookup"><span data-stu-id="9c599-105">Dragging Data</span></span>  
 <span data-ttu-id="9c599-106">Všechny operace přetažení začínají přetahováním.</span><span class="sxs-lookup"><span data-stu-id="9c599-106">All drag-and-drop operations begin with dragging.</span></span> <span data-ttu-id="9c599-107">Funkce, která povoluje shromažďování dat, když je zahájeno přetahování, je <xref:System.Windows.Forms.Control.DoDragDrop%2A> implementována v metodě.</span><span class="sxs-lookup"><span data-stu-id="9c599-107">The functionality to enable data to be collected when dragging begins is implemented in the <xref:System.Windows.Forms.Control.DoDragDrop%2A> method.</span></span>  
  
 <span data-ttu-id="9c599-108">V následujícím příkladu <xref:System.Windows.Forms.Control.MouseDown> se událost používá ke spuštění operace přetažení, protože se jedná o nejoblíbenější (většina akcí přetažení začíná tlačítkem myši).</span><span class="sxs-lookup"><span data-stu-id="9c599-108">In the following example, the <xref:System.Windows.Forms.Control.MouseDown> event is used to start the drag operation because it is the most intuitive (most drag-and-drop actions begin with the mouse button being depressed).</span></span> <span data-ttu-id="9c599-109">Mějte ale na paměti, že k zahájení postupu přetažení se dá použít jakákoli událost.</span><span class="sxs-lookup"><span data-stu-id="9c599-109">However, remember that any event could be used to initiate a drag-and-drop procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9c599-110">Některé ovládací prvky mají vlastní události specifické pro přetahování.</span><span class="sxs-lookup"><span data-stu-id="9c599-110">Certain controls have custom drag-specific events.</span></span> <span data-ttu-id="9c599-111">Ovládací prvky <xref:System.Windows.Forms.TreeView> amají<xref:System.Windows.Forms.TreeView.ItemDrag>napříkladudálost. <xref:System.Windows.Forms.ListView></span><span class="sxs-lookup"><span data-stu-id="9c599-111">The <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls, for example, have an <xref:System.Windows.Forms.TreeView.ItemDrag> event.</span></span>  
  
#### <a name="to-start-a-drag-operation"></a><span data-ttu-id="9c599-112">Spuštění operace přetažení</span><span class="sxs-lookup"><span data-stu-id="9c599-112">To start a drag operation</span></span>  
  
1. <span data-ttu-id="9c599-113">V případě ovládacího prvku, kde bude zahájeno přetahování, `DoDragDrop` použijte metodu k nastavení přetažení dat a povoleného přetahování efektů. <xref:System.Windows.Forms.Control.MouseDown></span><span class="sxs-lookup"><span data-stu-id="9c599-113">In the <xref:System.Windows.Forms.Control.MouseDown> event for the control where the drag will begin, use the `DoDragDrop` method to set the data to be dragged and the allowed effect dragging will have.</span></span> <span data-ttu-id="9c599-114">Další informace naleznete v tématu <xref:System.Windows.Forms.DragEventArgs.Data%2A> a <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span><span class="sxs-lookup"><span data-stu-id="9c599-114">For more information, see <xref:System.Windows.Forms.DragEventArgs.Data%2A> and <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span></span>  
  
     <span data-ttu-id="9c599-115">Následující příklad ukazuje, jak iniciovat operaci přetažení.</span><span class="sxs-lookup"><span data-stu-id="9c599-115">The following example shows how to initiate a drag operation.</span></span> <span data-ttu-id="9c599-116">Ovládací prvek, kde je <xref:System.Windows.Forms.Button> zahájeno přetažení, je ovládací prvek, přetažená data jsou řetězcem <xref:System.Windows.Forms.Control.Text%2A> představujícím <xref:System.Windows.Forms.Button> vlastnost ovládacího prvku a povolené účinky jsou buď zkopírovány nebo přesunuty.</span><span class="sxs-lookup"><span data-stu-id="9c599-116">The control where the drag begins is a <xref:System.Windows.Forms.Button> control, the data being dragged is the string representing the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control, and the allowed effects are either copying or moving.</span></span>  
  
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
    > <span data-ttu-id="9c599-117">Všechna data lze použít jako parametr v `DoDragDrop` metodě; v předchozím příkladu se použila <xref:System.Windows.Forms.Control.Text%2A> vlastnost <xref:System.Windows.Forms.Button> ovládacího prvku (místo hardwarového kódování hodnoty nebo načítání dat z datové sady), protože vlastnost se vztahuje k umístění, ze kterého se přetahuje <xref:System.Windows.Forms.Button> (ovládací prvek)</span><span class="sxs-lookup"><span data-stu-id="9c599-117">Any data can be used as a parameter in the `DoDragDrop` method; in the example above, the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control was used (rather than hard-coding a value or retrieving data from a dataset) because the property was related to the location being dragged from (the <xref:System.Windows.Forms.Button> control).</span></span> <span data-ttu-id="9c599-118">Pamatujte na to, že do aplikací založených na systému Windows zařadíte operace přetažení myší.</span><span class="sxs-lookup"><span data-stu-id="9c599-118">Keep this in mind as you incorporate drag-and-drop operations into your Windows-based applications.</span></span>  
  
 <span data-ttu-id="9c599-119">Zatímco je aktivní operace přetažení, můžete <xref:System.Windows.Forms.Control.QueryContinueDrag> událost zpracovat, což znamená, že se zobrazí výzva k zadání oprávnění systému, aby bylo možné pokračovat v operaci přetažení.</span><span class="sxs-lookup"><span data-stu-id="9c599-119">While a drag operation is in effect, you can handle the <xref:System.Windows.Forms.Control.QueryContinueDrag> event, which "asks permission" of the system to continue the drag operation.</span></span> <span data-ttu-id="9c599-120">Při zpracování této metody je také vhodným bodem pro volání metod, které budou mít vliv na operaci přetažení, jako je například rozbalení <xref:System.Windows.Forms.TreeNode> <xref:System.Windows.Forms.TreeView> ovládacího prvku, když se ukazatel myši nachází na pozadí.</span><span class="sxs-lookup"><span data-stu-id="9c599-120">When handling this method, it is also the appropriate point for you to call methods that will have an effect on the drag operation, such as expanding a <xref:System.Windows.Forms.TreeNode> in a <xref:System.Windows.Forms.TreeView> control when the cursor hovers over it.</span></span>  
  
## <a name="dropping-data"></a><span data-ttu-id="9c599-121">Vyřazení dat</span><span class="sxs-lookup"><span data-stu-id="9c599-121">Dropping Data</span></span>  
 <span data-ttu-id="9c599-122">Jakmile začnete přetahovat data z umístění ve formuláři nebo ovládacím prvku Windows, budete ho přirozeně chtít umístit jinam.</span><span class="sxs-lookup"><span data-stu-id="9c599-122">Once you have begun dragging data from a location on a Windows Form or control, you will naturally want to drop it somewhere.</span></span> <span data-ttu-id="9c599-123">Kurzor se změní, když přeskočí oblast formuláře nebo ovládacího prvku, který je správně nakonfigurován pro vyřazení dat.</span><span class="sxs-lookup"><span data-stu-id="9c599-123">The cursor will change when it crosses an area of a form or control that is correctly configured for dropping data.</span></span> <span data-ttu-id="9c599-124">Jakékoli oblasti v rámci formuláře nebo ovládacího prvku systému Windows lze použít pro příjem zahozených dat <xref:System.Windows.Forms.Control.AllowDrop%2A> nastavením vlastnosti a <xref:System.Windows.Forms.Control.DragEnter> zpracováním <xref:System.Windows.Forms.Control.DragDrop> událostí a.</span><span class="sxs-lookup"><span data-stu-id="9c599-124">Any area within a Windows Form or control can be made to accept dropped data by setting the <xref:System.Windows.Forms.Control.AllowDrop%2A> property and handling the <xref:System.Windows.Forms.Control.DragEnter> and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
#### <a name="to-perform-a-drop"></a><span data-ttu-id="9c599-125">Provedení přetažení</span><span class="sxs-lookup"><span data-stu-id="9c599-125">To perform a drop</span></span>  
  
1. <span data-ttu-id="9c599-126"><xref:System.Windows.Forms.Control.AllowDrop%2A> Nastavte vlastnost na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="9c599-126">Set the <xref:System.Windows.Forms.Control.AllowDrop%2A> property to true.</span></span>  
  
2. <span data-ttu-id="9c599-127">V případě ovládacího prvku, kde dojde k vyřazení, se ujistěte, že přetažená data jsou přijatelného typu (v tomto <xref:System.Windows.Forms.Control.Text%2A>případě). `DragEnter`</span><span class="sxs-lookup"><span data-stu-id="9c599-127">In the `DragEnter` event for the control where the drop will occur, ensure that the data being dragged is of an acceptable type (in this case, <xref:System.Windows.Forms.Control.Text%2A>).</span></span> <span data-ttu-id="9c599-128">Kód pak nastaví efekt, který se stane, když dojde k zapuštění na hodnotu ve <xref:System.Windows.Forms.DragDropEffects> výčtu.</span><span class="sxs-lookup"><span data-stu-id="9c599-128">The code then sets the effect that will happen when the drop occurs to a value in the <xref:System.Windows.Forms.DragDropEffects> enumeration.</span></span> <span data-ttu-id="9c599-129">Další informace naleznete v tématu <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span><span class="sxs-lookup"><span data-stu-id="9c599-129">For more information, see <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span></span>  
  
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
    > <span data-ttu-id="9c599-130">Můžete definovat <xref:System.Windows.Forms.DataFormats> vlastní objekt zadáním vlastního objektu <xref:System.Object> jako parametru <xref:System.Windows.Forms.DataObject.SetData%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="9c599-130">You can define your own <xref:System.Windows.Forms.DataFormats> by specifying your own object as the <xref:System.Object> parameter of the <xref:System.Windows.Forms.DataObject.SetData%2A> method.</span></span> <span data-ttu-id="9c599-131">Ujistěte se, že v takovém případě je zadaný objekt serializovatelný.</span><span class="sxs-lookup"><span data-stu-id="9c599-131">Be sure, when doing this, that the object specified is serializable.</span></span> <span data-ttu-id="9c599-132">Další informace naleznete v tématu <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="9c599-132">For more information, see <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
3. <span data-ttu-id="9c599-133">V případě ovládacího prvku, kde dojde k vyřazení, <xref:System.Windows.Forms.DataObject.GetData%2A> použijte metodu pro načtení přetažených dat. <xref:System.Windows.Forms.Control.DragDrop></span><span class="sxs-lookup"><span data-stu-id="9c599-133">In the <xref:System.Windows.Forms.Control.DragDrop> event for the control where the drop will occur, use the <xref:System.Windows.Forms.DataObject.GetData%2A> method to retrieve the data being dragged.</span></span> <span data-ttu-id="9c599-134">Další informace naleznete v tématu <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span><span class="sxs-lookup"><span data-stu-id="9c599-134">For more information, see <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span></span>  
  
     <span data-ttu-id="9c599-135">V následujícím <xref:System.Windows.Forms.TextBox> příkladu je ovládací prvek přetažen do (kde dojde k přetažení).</span><span class="sxs-lookup"><span data-stu-id="9c599-135">In the example below, a <xref:System.Windows.Forms.TextBox> control is the control being dragged to (where the drop will occur).</span></span> <span data-ttu-id="9c599-136">Kód nastaví <xref:System.Windows.Forms.Control.Text%2A> vlastnost <xref:System.Windows.Forms.TextBox> ovládacího prvku na hodnotu přetažená na data.</span><span class="sxs-lookup"><span data-stu-id="9c599-136">The code sets the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.TextBox> control equal to the data being dragged.</span></span>  
  
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
    > <span data-ttu-id="9c599-137">Kromě toho můžete s <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> vlastností pracovat, takže když v závislosti na klíčích, které se během operace přetažení přetáhnete, dojde k určitým dopadům (například na standardu zkopírovat přetažená data při stisknutí klávesy CTRL).</span><span class="sxs-lookup"><span data-stu-id="9c599-137">Additionally, you can work with the <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> property, so that, depending on keys depressed during the drag-and-drop operation, certain effects occur (for example, it is standard to copy the dragged data when the CTRL key is pressed).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c599-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9c599-138">See also</span></span>

- [<span data-ttu-id="9c599-139">Postupy: Přidat data do schránky</span><span class="sxs-lookup"><span data-stu-id="9c599-139">How to: Add Data to the Clipboard</span></span>](how-to-add-data-to-the-clipboard.md)
- [<span data-ttu-id="9c599-140">Postupy: Načtení dat ze schránky</span><span class="sxs-lookup"><span data-stu-id="9c599-140">How to: Retrieve Data from the Clipboard</span></span>](how-to-retrieve-data-from-the-clipboard.md)
- [<span data-ttu-id="9c599-141">Operace přetažení a podpora schránky</span><span class="sxs-lookup"><span data-stu-id="9c599-141">Drag-and-Drop Operations and Clipboard Support</span></span>](drag-and-drop-operations-and-clipboard-support.md)
