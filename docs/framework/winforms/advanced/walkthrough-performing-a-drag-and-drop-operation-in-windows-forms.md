---
title: 'Návod: Provedení operace přetažení myší'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: b5e4bf753733cb9bd010672f40e8fbeb0cf036bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182447"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a><span data-ttu-id="2eeed-102">Návod: Provádění operace přetažení ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2eeed-102">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>
<span data-ttu-id="2eeed-103">Chcete-li provádět operace přetažení v aplikacích založených na systému Windows, <xref:System.Windows.Forms.Control.DragLeave>je <xref:System.Windows.Forms.Control.DragDrop> nutné zpracovat řadu událostí, zejména <xref:System.Windows.Forms.Control.DragEnter>aplikace , a události.</span><span class="sxs-lookup"><span data-stu-id="2eeed-103">To perform drag-and-drop operations within Windows-based applications you must handle a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span> <span data-ttu-id="2eeed-104">Při práci s informacemi dostupnými v argumentech události těchto událostí můžete snadno usnadnit operace přetažení myší.</span><span class="sxs-lookup"><span data-stu-id="2eeed-104">By working with the information available in the event arguments of these events, you can easily facilitate drag-and-drop operations.</span></span>  
  
## <a name="dragging-data"></a><span data-ttu-id="2eeed-105">Přetažení dat</span><span class="sxs-lookup"><span data-stu-id="2eeed-105">Dragging Data</span></span>  
 <span data-ttu-id="2eeed-106">Všechny operace přetažení začínají přetažením.</span><span class="sxs-lookup"><span data-stu-id="2eeed-106">All drag-and-drop operations begin with dragging.</span></span> <span data-ttu-id="2eeed-107">Funkce umožňující shromažďování dat při přetahování začíná je <xref:System.Windows.Forms.Control.DoDragDrop%2A> implementována v metodě.</span><span class="sxs-lookup"><span data-stu-id="2eeed-107">The functionality to enable data to be collected when dragging begins is implemented in the <xref:System.Windows.Forms.Control.DoDragDrop%2A> method.</span></span>  
  
 <span data-ttu-id="2eeed-108">V následujícím příkladu <xref:System.Windows.Forms.Control.MouseDown> se událost používá ke spuštění operace přetažení, protože je nejintuitivnější (většina akcí přetažení začíná stlačeným tlačítkem myši).</span><span class="sxs-lookup"><span data-stu-id="2eeed-108">In the following example, the <xref:System.Windows.Forms.Control.MouseDown> event is used to start the drag operation because it is the most intuitive (most drag-and-drop actions begin with the mouse button being depressed).</span></span> <span data-ttu-id="2eeed-109">Mějte však na paměti, že všechny události lze použít k zahájení a přetažení postup.</span><span class="sxs-lookup"><span data-stu-id="2eeed-109">However, remember that any event could be used to initiate a drag-and-drop procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2eeed-110">Některé ovládací prvky mají vlastní události specifické pro přetažení.</span><span class="sxs-lookup"><span data-stu-id="2eeed-110">Certain controls have custom drag-specific events.</span></span> <span data-ttu-id="2eeed-111">Ovládací <xref:System.Windows.Forms.ListView> <xref:System.Windows.Forms.TreeView> prvky a, například mají <xref:System.Windows.Forms.TreeView.ItemDrag> událost.</span><span class="sxs-lookup"><span data-stu-id="2eeed-111">The <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls, for example, have an <xref:System.Windows.Forms.TreeView.ItemDrag> event.</span></span>  
  
#### <a name="to-start-a-drag-operation"></a><span data-ttu-id="2eeed-112">Spuštění operace přetažení</span><span class="sxs-lookup"><span data-stu-id="2eeed-112">To start a drag operation</span></span>  
  
1. <span data-ttu-id="2eeed-113">V <xref:System.Windows.Forms.Control.MouseDown> případě ovládacího prvku, kde bude `DoDragDrop` přetahování zahájeno, použijte metodu k nastavení dat, která mají být přetažena, a bude mít povolený efekt přetažení.</span><span class="sxs-lookup"><span data-stu-id="2eeed-113">In the <xref:System.Windows.Forms.Control.MouseDown> event for the control where the drag will begin, use the `DoDragDrop` method to set the data to be dragged and the allowed effect dragging will have.</span></span> <span data-ttu-id="2eeed-114">Další informace naleznete v tématech <xref:System.Windows.Forms.DragEventArgs.Data%2A> a <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span><span class="sxs-lookup"><span data-stu-id="2eeed-114">For more information, see <xref:System.Windows.Forms.DragEventArgs.Data%2A> and <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span></span>  
  
     <span data-ttu-id="2eeed-115">Následující příklad ukazuje, jak zahájit operaci přetažení.</span><span class="sxs-lookup"><span data-stu-id="2eeed-115">The following example shows how to initiate a drag operation.</span></span> <span data-ttu-id="2eeed-116">Ovládací prvek, kde začíná <xref:System.Windows.Forms.Button> přetažení je ovládací prvek, přetahovaná <xref:System.Windows.Forms.Control.Text%2A> data <xref:System.Windows.Forms.Button> je řetězec představující vlastnost ovládacího prvku a povolené efekty jsou buď kopírování nebo přesunutí.</span><span class="sxs-lookup"><span data-stu-id="2eeed-116">The control where the drag begins is a <xref:System.Windows.Forms.Button> control, the data being dragged is the string representing the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control, and the allowed effects are either copying or moving.</span></span>  
  
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
    > <span data-ttu-id="2eeed-117">Jako parametr v metodě `DoDragDrop` lze použít libovolná data; ve výše uvedeném <xref:System.Windows.Forms.Control.Text%2A> příkladu <xref:System.Windows.Forms.Button> byla použita vlastnost ovládacího prvku (spíše než pevné kódování hodnoty nebo načítání dat z datové <xref:System.Windows.Forms.Button> sady), protože vlastnost souvisela s umístěním přetahovaným z (ovládací prvek).</span><span class="sxs-lookup"><span data-stu-id="2eeed-117">Any data can be used as a parameter in the `DoDragDrop` method; in the example above, the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control was used (rather than hard-coding a value or retrieving data from a dataset) because the property was related to the location being dragged from (the <xref:System.Windows.Forms.Button> control).</span></span> <span data-ttu-id="2eeed-118">Mějte to na paměti při zapracování operací přetažení do aplikací založených na systému Windows.</span><span class="sxs-lookup"><span data-stu-id="2eeed-118">Keep this in mind as you incorporate drag-and-drop operations into your Windows-based applications.</span></span>  
  
 <span data-ttu-id="2eeed-119">Během operace přetažení můžete zpracovat <xref:System.Windows.Forms.Control.QueryContinueDrag> událost, která "požádá o oprávnění" systému, aby mohla pokračovat v operaci přetažení.</span><span class="sxs-lookup"><span data-stu-id="2eeed-119">While a drag operation is in effect, you can handle the <xref:System.Windows.Forms.Control.QueryContinueDrag> event, which "asks permission" of the system to continue the drag operation.</span></span> <span data-ttu-id="2eeed-120">Při zpracování této metody je také vhodný bod pro volání metod, které budou mít vliv <xref:System.Windows.Forms.TreeNode> na <xref:System.Windows.Forms.TreeView> operaci přetažení, jako je například rozbalení v ovládacím prvku, když kurzor najedou nad ním.</span><span class="sxs-lookup"><span data-stu-id="2eeed-120">When handling this method, it is also the appropriate point for you to call methods that will have an effect on the drag operation, such as expanding a <xref:System.Windows.Forms.TreeNode> in a <xref:System.Windows.Forms.TreeView> control when the cursor hovers over it.</span></span>  
  
## <a name="dropping-data"></a><span data-ttu-id="2eeed-121">Zrušení dat</span><span class="sxs-lookup"><span data-stu-id="2eeed-121">Dropping Data</span></span>  
 <span data-ttu-id="2eeed-122">Jakmile začnete přetahovat data z umístění ve formuláři nebo ovládacím prvku systému Windows, budete je přirozeně chtít někam upustit.</span><span class="sxs-lookup"><span data-stu-id="2eeed-122">Once you have begun dragging data from a location on a Windows Form or control, you will naturally want to drop it somewhere.</span></span> <span data-ttu-id="2eeed-123">Kurzor se změní, když překročí oblast formuláře nebo ovládacího prvku, který je správně nakonfigurován pro vyřazování dat.</span><span class="sxs-lookup"><span data-stu-id="2eeed-123">The cursor will change when it crosses an area of a form or control that is correctly configured for dropping data.</span></span> <span data-ttu-id="2eeed-124">Libovolná oblast ve formuláři systému Windows nebo ovládací <xref:System.Windows.Forms.Control.AllowDrop%2A> prvek lze <xref:System.Windows.Forms.Control.DragEnter> <xref:System.Windows.Forms.Control.DragDrop> provést přijímat vynecháná data nastavením vlastnosti a zpracování a události.</span><span class="sxs-lookup"><span data-stu-id="2eeed-124">Any area within a Windows Form or control can be made to accept dropped data by setting the <xref:System.Windows.Forms.Control.AllowDrop%2A> property and handling the <xref:System.Windows.Forms.Control.DragEnter> and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
#### <a name="to-perform-a-drop"></a><span data-ttu-id="2eeed-125">Provedení poklesu</span><span class="sxs-lookup"><span data-stu-id="2eeed-125">To perform a drop</span></span>  
  
1. <span data-ttu-id="2eeed-126">Nastavte <xref:System.Windows.Forms.Control.AllowDrop%2A> vlastnost na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="2eeed-126">Set the <xref:System.Windows.Forms.Control.AllowDrop%2A> property to true.</span></span>  
  
2. <span data-ttu-id="2eeed-127">V `DragEnter` případě ovládacího prvku, kde dojde k přetažení, ujistěte se, že přetahovaná data jsou přijatelného typu (v tomto případě <xref:System.Windows.Forms.Control.Text%2A>).</span><span class="sxs-lookup"><span data-stu-id="2eeed-127">In the `DragEnter` event for the control where the drop will occur, ensure that the data being dragged is of an acceptable type (in this case, <xref:System.Windows.Forms.Control.Text%2A>).</span></span> <span data-ttu-id="2eeed-128">Kód pak nastaví efekt, který se stane, když <xref:System.Windows.Forms.DragDropEffects> dojde k poklesu na hodnotu ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="2eeed-128">The code then sets the effect that will happen when the drop occurs to a value in the <xref:System.Windows.Forms.DragDropEffects> enumeration.</span></span> <span data-ttu-id="2eeed-129">Další informace naleznete v tématu <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span><span class="sxs-lookup"><span data-stu-id="2eeed-129">For more information, see <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span></span>  
  
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
    > <span data-ttu-id="2eeed-130">Můžete definovat vlastní <xref:System.Windows.Forms.DataFormats> zadáním vlastního objektu <xref:System.Object> jako <xref:System.Windows.Forms.DataObject.SetData%2A> parametr metody.</span><span class="sxs-lookup"><span data-stu-id="2eeed-130">You can define your own <xref:System.Windows.Forms.DataFormats> by specifying your own object as the <xref:System.Object> parameter of the <xref:System.Windows.Forms.DataObject.SetData%2A> method.</span></span> <span data-ttu-id="2eeed-131">Ujistěte se, že při tomto, že zadaný objekt je serializovatelný.</span><span class="sxs-lookup"><span data-stu-id="2eeed-131">Be sure, when doing this, that the object specified is serializable.</span></span> <span data-ttu-id="2eeed-132">Další informace naleznete v tématu <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="2eeed-132">For more information, see <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
3. <span data-ttu-id="2eeed-133">V <xref:System.Windows.Forms.Control.DragDrop> případě ovládacího prvku, kde dojde <xref:System.Windows.Forms.DataObject.GetData%2A> k přetažení, použijte metodu k načtení přetahovaných dat.</span><span class="sxs-lookup"><span data-stu-id="2eeed-133">In the <xref:System.Windows.Forms.Control.DragDrop> event for the control where the drop will occur, use the <xref:System.Windows.Forms.DataObject.GetData%2A> method to retrieve the data being dragged.</span></span> <span data-ttu-id="2eeed-134">Další informace naleznete v tématu <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span><span class="sxs-lookup"><span data-stu-id="2eeed-134">For more information, see <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span></span>  
  
     <span data-ttu-id="2eeed-135">V níže uvedeném <xref:System.Windows.Forms.TextBox> příkladu je ovládací prvek přetahovaný do (kde dojde k přetažení).</span><span class="sxs-lookup"><span data-stu-id="2eeed-135">In the example below, a <xref:System.Windows.Forms.TextBox> control is the control being dragged to (where the drop will occur).</span></span> <span data-ttu-id="2eeed-136">Kód nastaví <xref:System.Windows.Forms.Control.Text%2A> vlastnost <xref:System.Windows.Forms.TextBox> ovládacího prvku rovná data přetahovaná.</span><span class="sxs-lookup"><span data-stu-id="2eeed-136">The code sets the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.TextBox> control equal to the data being dragged.</span></span>  
  
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
    > <span data-ttu-id="2eeed-137">Kromě toho můžete pracovat <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> s vlastností, takže v závislosti na klávesách stisknutých během operace přetažení dochází k určitým efektům (například kopírování přetažených dat při stisknutí klávesy CTRL).</span><span class="sxs-lookup"><span data-stu-id="2eeed-137">Additionally, you can work with the <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> property, so that, depending on keys depressed during the drag-and-drop operation, certain effects occur (for example, it is standard to copy the dragged data when the CTRL key is pressed).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2eeed-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="2eeed-138">See also</span></span>

- [<span data-ttu-id="2eeed-139">Postupy: Přidání dat do schránky</span><span class="sxs-lookup"><span data-stu-id="2eeed-139">How to: Add Data to the Clipboard</span></span>](how-to-add-data-to-the-clipboard.md)
- [<span data-ttu-id="2eeed-140">Postupy: Načtení dat ze schránky</span><span class="sxs-lookup"><span data-stu-id="2eeed-140">How to: Retrieve Data from the Clipboard</span></span>](how-to-retrieve-data-from-the-clipboard.md)
- [<span data-ttu-id="2eeed-141">Operace přetažení a podpora schránky</span><span class="sxs-lookup"><span data-stu-id="2eeed-141">Drag-and-Drop Operations and Clipboard Support</span></span>](drag-and-drop-operations-and-clipboard-support.md)
