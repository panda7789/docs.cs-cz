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
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a>Návod: Provádění operace přetažení ve Windows Forms
K provádění operací přetažení myší v rámci aplikace pro systém Windows je nutné zpracovat řadu událostí, zejména <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, a <xref:System.Windows.Forms.Control.DragDrop> události. Ve spolupráci s informací, které jsou k dispozici události argumenty tyto události, můžete snadno usnadnění operací přetažení myší.  
  
## <a name="dragging-data"></a>Přetahování dat  
 Všechny operace přetažení myší začínat přetahování. Funkci, která umožní při přetahování začne shromažďovat data je implementována ve <xref:System.Windows.Forms.Control.DoDragDrop%2A> metoda.  
  
 V následujícím příkladu <xref:System.Windows.Forms.Control.MouseDown> událostí se používá ke spuštění operaci přetažení, protože je nejvíce intuitivní (většinu akcí a přetažení začínat tlačítko myši stisknuté probíhá). Nezapomeňte však, že všechny události by bylo možné zahájit přetažení myší řízení.  
  
> [!NOTE]
>  Některé ovládací prvky mít vlastní události specifické pro přetažení. <xref:System.Windows.Forms.ListView> a <xref:System.Windows.Forms.TreeView> ovládacích prvků, je třeba mít <xref:System.Windows.Forms.TreeView.ItemDrag> událostí.  
  
#### <a name="to-start-a-drag-operation"></a>Spusťte operaci přetažení  
  
1.  V <xref:System.Windows.Forms.Control.MouseDown> událostí pro ovládací prvek, kde bude zahájena přetažení, použijte `DoDragDrop` bude mít metodu a nastavit data, která mají být přetažen a povoleným efektem přetahování. Další informace naleznete v tématu <xref:System.Windows.Forms.DragEventArgs.Data%2A> a <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.  
  
     Následující příklad ukazuje, jak zahájit operaci přetažení. Ovládací prvek, kde začíná přetáhněte je <xref:System.Windows.Forms.Button> řízení, data přetažen je řetězec představující <xref:System.Windows.Forms.Control.Text%2A> vlastnost <xref:System.Windows.Forms.Button> řízení a povolených důsledky jsou kopírování nebo přesunutí.  
  
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
    >  Žádná data lze použít jako parametr v `DoDragDrop` metoda; v příkladu nahoře, <xref:System.Windows.Forms.Control.Text%2A> vlastnost <xref:System.Windows.Forms.Button> řízení byl použit (místo pevně kódováno hodnotu nebo načítání dat z datové sady) vzhledem k tomu, že byla vlastnosti související s přetažení z umístění ( <xref:System.Windows.Forms.Button> řízení). Mějte to na paměti, jak začlenit operací přetažení myší do vaší aplikace pro systém Windows.  
  
 Během operace přetažení, může zpracovat <xref:System.Windows.Forms.Control.QueryContinueDrag> událost, která "požádá oprávnění" systému do pokračovat v provádění operace přetažení. Při zpracování této metody, je také vhodné bod pro volání metody, které bude mít vliv na operace přetažení, jako je například rozšíření <xref:System.Windows.Forms.TreeNode> v <xref:System.Windows.Forms.TreeView> řízení, když ukazatel myši nad jeho.  
  
## <a name="dropping-data"></a>Vyřazení dat  
 Po zahájení přetahování data z umístění ve formuláři Windows nebo ovládací prvek, samozřejmě můžete někde ho vyřadit. Kurzor se změní, když ji oblasti formuláře nebo ovládací prvek, který je správně nakonfigurováno pro vyřazení dat překračuje. Všechny oblasti v rámci formuláře Windows nebo řízení můžete provést tak, aby přijímal vynechaných data podle nastavení <xref:System.Windows.Forms.Control.AllowDrop%2A> vlastnost a zpracování <xref:System.Windows.Forms.Control.DragEnter> a <xref:System.Windows.Forms.Control.DragDrop> události.  
  
#### <a name="to-perform-a-drop"></a>K provedení pokles  
  
1.  Nastavte <xref:System.Windows.Forms.Control.AllowDrop%2A> vlastnost na hodnotu true.  
  
2.  V `DragEnter` událostí pro ovládací prvek, kde bude probíhat rozevíracího, zajistěte, aby byla data přetažen přijatelné typu (v tomto případě <xref:System.Windows.Forms.Control.Text%2A>). Kód pak nastaví o tom, že se stane, když dojde k rozevíracího na hodnotu v <xref:System.Windows.Forms.DragDropEffects> výčtu. Další informace naleznete v tématu <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.  
  
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
    >  Můžete definovat vlastní <xref:System.Windows.Forms.DataFormats> zadáním vlastního objektu jako <xref:System.Object> parametr <xref:System.Windows.Forms.DataObject.SetData%2A> metoda. Třeba, aby, pokud to, zda je zadaný objekt serializable. Další informace naleznete v tématu <xref:System.Runtime.Serialization.ISerializable>.  
  
3.  V <xref:System.Windows.Forms.Control.DragDrop> událostí pro ovládací prvek rozevírací kde bude probíhat, použijte <xref:System.Windows.Forms.DataObject.GetData%2A> metoda pro načtení dat přetažen. Další informace naleznete v tématu <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.  
  
     V příkladu níže <xref:System.Windows.Forms.TextBox> prvek je ovládací prvek tažením (kde bude probíhat rozevíracího). Nastaví kód <xref:System.Windows.Forms.Control.Text%2A> vlastnost <xref:System.Windows.Forms.TextBox> řízení rovna přetažen data.  
  
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
    >  Kromě toho můžete pracovat <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> určité účinky dojít vlastnost tak, aby v závislosti na klíče stisknuté během operace přetahování myší, (například je standardní ke zkopírování taženou dat po stisknutí klávesy CTRL).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Přidání dat do schránky](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 [Postupy: Načtení dat ze schránky](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 [Operace přetažení a podpora schránky](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)
