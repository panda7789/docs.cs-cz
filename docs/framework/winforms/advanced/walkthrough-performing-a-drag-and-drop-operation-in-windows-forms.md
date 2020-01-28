---
title: 'Návod: provedení operace přetažení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: 265e6d4f9e3370d28a18b86dea983bb0b556be41
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746790"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a>Návod: Provádění operace přetažení ve Windows Forms
K provádění operací přetažení v rámci aplikací pro Windows musíte zpracovat řadu událostí, zejména <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>a <xref:System.Windows.Forms.Control.DragDrop>ch událostí. Při práci s informacemi dostupnými v argumentech událostí těchto událostí můžete snadno usnadnit operace přetažení.  
  
## <a name="dragging-data"></a>Přetahování dat  
 Všechny operace přetažení začínají přetahováním. Funkce, která umožňuje shromažďování dat, když je zahájeno přetahování, je implementována v metodě <xref:System.Windows.Forms.Control.DoDragDrop%2A>.  
  
 V následujícím příkladu se událost <xref:System.Windows.Forms.Control.MouseDown> používá ke spuštění operace přetažení, protože se jedná o nejoblíbenější (většina akcí přetažení začíná tlačítkem myši). Mějte ale na paměti, že k zahájení postupu přetažení se dá použít jakákoli událost.  
  
> [!NOTE]
> Některé ovládací prvky mají vlastní události specifické pro přetahování. Ovládací prvky <xref:System.Windows.Forms.ListView> a <xref:System.Windows.Forms.TreeView> například mají událost <xref:System.Windows.Forms.TreeView.ItemDrag>.  
  
#### <a name="to-start-a-drag-operation"></a>Spuštění operace přetažení  
  
1. V události <xref:System.Windows.Forms.Control.MouseDown> ovládacího prvku, kde začne přetahování, použijte metodu `DoDragDrop` k nastavení přetáhnutí dat a povolené přetahování efektů. Další informace naleznete v tématu <xref:System.Windows.Forms.DragEventArgs.Data%2A> a <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.  
  
     Následující příklad ukazuje, jak iniciovat operaci přetažení. Ovládací prvek, kde je zahájeno přetažení, je ovládací prvek <xref:System.Windows.Forms.Button>, přetažená data jsou řetězcem představujícím vlastnost <xref:System.Windows.Forms.Control.Text%2A> ovládacího prvku <xref:System.Windows.Forms.Button> a povolené účinky jsou buď zkopírovány nebo přesunuty.  
  
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
    > Všechna data lze použít jako parametr v metodě `DoDragDrop`; v předchozím příkladu se použila vlastnost <xref:System.Windows.Forms.Control.Text%2A> ovládacího prvku <xref:System.Windows.Forms.Button> (namísto hardwarového kódování hodnoty nebo načítání dat z datové sady), protože vlastnost se vztahuje k umístění, ze kterého se přetahuje (ovládací prvek <xref:System.Windows.Forms.Button>). Pamatujte na to, že do aplikací založených na systému Windows zařadíte operace přetažení myší.  
  
 Zatímco je aktivní operace přetažení, můžete zpracovat událost <xref:System.Windows.Forms.Control.QueryContinueDrag>, která v systému vyzve oprávnění, aby pokračovala v operaci přetažení. Při zpracování této metody je také vhodným bodem pro volání metod, které budou mít vliv na operaci přetažení, jako je například rozbalení <xref:System.Windows.Forms.TreeNode> v ovládacím prvku <xref:System.Windows.Forms.TreeView>, když se ukazatel myši nachází nad ním.  
  
## <a name="dropping-data"></a>Vyřazení dat  
 Jakmile začnete přetahovat data z umístění ve formuláři nebo ovládacím prvku Windows, budete ho přirozeně chtít umístit jinam. Kurzor se změní, když přeskočí oblast formuláře nebo ovládacího prvku, který je správně nakonfigurován pro vyřazení dat. Všechny oblasti v rámci formuláře nebo ovládacího prvku Windows lze použít pro příjem zahozených dat nastavením vlastnosti <xref:System.Windows.Forms.Control.AllowDrop%2A> a zpracováním událostí <xref:System.Windows.Forms.Control.DragEnter> a <xref:System.Windows.Forms.Control.DragDrop>.  
  
#### <a name="to-perform-a-drop"></a>Provedení přetažení  
  
1. Vlastnost <xref:System.Windows.Forms.Control.AllowDrop%2A> nastavte na hodnotu true.  
  
2. V události `DragEnter` pro ovládací prvek, kde dojde k vyřazení, se ujistěte, že přetažená data jsou přijatelného typu (v tomto případě <xref:System.Windows.Forms.Control.Text%2A>). Kód pak nastaví efekt, který se stane, když dojde k zapuštění na hodnotu ve výčtu <xref:System.Windows.Forms.DragDropEffects>. Další informace najdete v tématu <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.  
  
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
    > Vlastní <xref:System.Windows.Forms.DataFormats> můžete definovat zadáním vlastního objektu jako parametru <xref:System.Object> metody <xref:System.Windows.Forms.DataObject.SetData%2A>. Ujistěte se, že v takovém případě je zadaný objekt serializovatelný. Další informace najdete v tématu <xref:System.Runtime.Serialization.ISerializable>.  
  
3. V události <xref:System.Windows.Forms.Control.DragDrop> ovládacího prvku, kde dojde k vyřazení, použijte metodu <xref:System.Windows.Forms.DataObject.GetData%2A> k načtení přetažených dat. Další informace najdete v tématu <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.  
  
     V následujícím příkladu je ovládací prvek <xref:System.Windows.Forms.TextBox> přetažen do (kde dojde k přetažení). Kód nastaví vlastnost <xref:System.Windows.Forms.Control.Text%2A> ovládacího prvku <xref:System.Windows.Forms.TextBox>, která se rovná přetahování dat.  
  
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
    > Kromě toho můžete pracovat s vlastností <xref:System.Windows.Forms.DragEventArgs.KeyState%2A>, takže v závislosti na stisknutých klávesách během operace přetažení se vyskytnou určité účinky (například je standardně kopírovat přetažená data při stisknutí klávesy CTRL).  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Přidání dat do schránky](how-to-add-data-to-the-clipboard.md)
- [Postupy: Načtení dat ze schránky](how-to-retrieve-data-from-the-clipboard.md)
- [Operace přetažení a podpora schránky](drag-and-drop-operations-and-clipboard-support.md)
