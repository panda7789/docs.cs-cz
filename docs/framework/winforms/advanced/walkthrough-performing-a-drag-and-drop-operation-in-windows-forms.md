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
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a>Návod: Provádění operace přetažení v modelu Windows Forms
K provádění operací přetažení v rámci aplikací pro systém Windows je nutné zpracovat řady událostí, zejména <xref:System.Windows.Forms.Control.DragEnter>události, <xref:System.Windows.Forms.Control.DragLeave>a <xref:System.Windows.Forms.Control.DragDrop> . Při práci s informacemi dostupnými v argumentech událostí těchto událostí můžete snadno usnadnit operace přetažení.  
  
## <a name="dragging-data"></a>Přetahování dat  
 Všechny operace přetažení začínají přetahováním. Funkce, která povoluje shromažďování dat, když je zahájeno přetahování, je <xref:System.Windows.Forms.Control.DoDragDrop%2A> implementována v metodě.  
  
 V následujícím příkladu <xref:System.Windows.Forms.Control.MouseDown> se událost používá ke spuštění operace přetažení, protože se jedná o nejoblíbenější (většina akcí přetažení začíná tlačítkem myši). Mějte ale na paměti, že k zahájení postupu přetažení se dá použít jakákoli událost.  
  
> [!NOTE]
> Některé ovládací prvky mají vlastní události specifické pro přetahování. Ovládací prvky <xref:System.Windows.Forms.TreeView> amají<xref:System.Windows.Forms.TreeView.ItemDrag>napříkladudálost. <xref:System.Windows.Forms.ListView>  
  
#### <a name="to-start-a-drag-operation"></a>Spuštění operace přetažení  
  
1. V případě ovládacího prvku, kde bude zahájeno přetahování, `DoDragDrop` použijte metodu k nastavení přetažení dat a povoleného přetahování efektů. <xref:System.Windows.Forms.Control.MouseDown> Další informace naleznete v tématu <xref:System.Windows.Forms.DragEventArgs.Data%2A> a <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.  
  
     Následující příklad ukazuje, jak iniciovat operaci přetažení. Ovládací prvek, kde je <xref:System.Windows.Forms.Button> zahájeno přetažení, je ovládací prvek, přetažená data jsou řetězcem <xref:System.Windows.Forms.Control.Text%2A> představujícím <xref:System.Windows.Forms.Button> vlastnost ovládacího prvku a povolené účinky jsou buď zkopírovány nebo přesunuty.  
  
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
    > Všechna data lze použít jako parametr v `DoDragDrop` metodě; v předchozím příkladu se použila <xref:System.Windows.Forms.Control.Text%2A> vlastnost <xref:System.Windows.Forms.Button> ovládacího prvku (místo hardwarového kódování hodnoty nebo načítání dat z datové sady), protože vlastnost se vztahuje k umístění, ze kterého se přetahuje <xref:System.Windows.Forms.Button> (ovládací prvek) Pamatujte na to, že do aplikací založených na systému Windows zařadíte operace přetažení myší.  
  
 Zatímco je aktivní operace přetažení, můžete <xref:System.Windows.Forms.Control.QueryContinueDrag> událost zpracovat, což znamená, že se zobrazí výzva k zadání oprávnění systému, aby bylo možné pokračovat v operaci přetažení. Při zpracování této metody je také vhodným bodem pro volání metod, které budou mít vliv na operaci přetažení, jako je například rozbalení <xref:System.Windows.Forms.TreeNode> <xref:System.Windows.Forms.TreeView> ovládacího prvku, když se ukazatel myši nachází na pozadí.  
  
## <a name="dropping-data"></a>Vyřazení dat  
 Jakmile začnete přetahovat data z umístění ve formuláři nebo ovládacím prvku Windows, budete ho přirozeně chtít umístit jinam. Kurzor se změní, když přeskočí oblast formuláře nebo ovládacího prvku, který je správně nakonfigurován pro vyřazení dat. Jakékoli oblasti v rámci formuláře nebo ovládacího prvku systému Windows lze použít pro příjem zahozených dat <xref:System.Windows.Forms.Control.AllowDrop%2A> nastavením vlastnosti a <xref:System.Windows.Forms.Control.DragEnter> zpracováním <xref:System.Windows.Forms.Control.DragDrop> událostí a.  
  
#### <a name="to-perform-a-drop"></a>Provedení přetažení  
  
1. <xref:System.Windows.Forms.Control.AllowDrop%2A> Nastavte vlastnost na hodnotu true.  
  
2. V případě ovládacího prvku, kde dojde k vyřazení, se ujistěte, že přetažená data jsou přijatelného typu (v tomto <xref:System.Windows.Forms.Control.Text%2A>případě). `DragEnter` Kód pak nastaví efekt, který se stane, když dojde k zapuštění na hodnotu ve <xref:System.Windows.Forms.DragDropEffects> výčtu. Další informace naleznete v tématu <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.  
  
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
    > Můžete definovat <xref:System.Windows.Forms.DataFormats> vlastní objekt zadáním vlastního objektu <xref:System.Object> jako parametru <xref:System.Windows.Forms.DataObject.SetData%2A> metody. Ujistěte se, že v takovém případě je zadaný objekt serializovatelný. Další informace naleznete v tématu <xref:System.Runtime.Serialization.ISerializable>.  
  
3. V případě ovládacího prvku, kde dojde k vyřazení, <xref:System.Windows.Forms.DataObject.GetData%2A> použijte metodu pro načtení přetažených dat. <xref:System.Windows.Forms.Control.DragDrop> Další informace naleznete v tématu <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.  
  
     V následujícím <xref:System.Windows.Forms.TextBox> příkladu je ovládací prvek přetažen do (kde dojde k přetažení). Kód nastaví <xref:System.Windows.Forms.Control.Text%2A> vlastnost <xref:System.Windows.Forms.TextBox> ovládacího prvku na hodnotu přetažená na data.  
  
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
    > Kromě toho můžete s <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> vlastností pracovat, takže když v závislosti na klíčích, které se během operace přetažení přetáhnete, dojde k určitým dopadům (například na standardu zkopírovat přetažená data při stisknutí klávesy CTRL).  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Přidat data do schránky](how-to-add-data-to-the-clipboard.md)
- [Postupy: Načtení dat ze schránky](how-to-retrieve-data-from-the-clipboard.md)
- [Operace přetažení a podpora schránky](drag-and-drop-operations-and-clipboard-support.md)
