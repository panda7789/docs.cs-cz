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
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a>Návod: Provádění operace přetažení ve Windows Forms
Chcete-li provádět operace přetažení v aplikacích založených na systému Windows, <xref:System.Windows.Forms.Control.DragLeave>je <xref:System.Windows.Forms.Control.DragDrop> nutné zpracovat řadu událostí, zejména <xref:System.Windows.Forms.Control.DragEnter>aplikace , a události. Při práci s informacemi dostupnými v argumentech události těchto událostí můžete snadno usnadnit operace přetažení myší.  
  
## <a name="dragging-data"></a>Přetažení dat  
 Všechny operace přetažení začínají přetažením. Funkce umožňující shromažďování dat při přetahování začíná je <xref:System.Windows.Forms.Control.DoDragDrop%2A> implementována v metodě.  
  
 V následujícím příkladu <xref:System.Windows.Forms.Control.MouseDown> se událost používá ke spuštění operace přetažení, protože je nejintuitivnější (většina akcí přetažení začíná stlačeným tlačítkem myši). Mějte však na paměti, že všechny události lze použít k zahájení a přetažení postup.  
  
> [!NOTE]
> Některé ovládací prvky mají vlastní události specifické pro přetažení. Ovládací <xref:System.Windows.Forms.ListView> <xref:System.Windows.Forms.TreeView> prvky a, například mají <xref:System.Windows.Forms.TreeView.ItemDrag> událost.  
  
#### <a name="to-start-a-drag-operation"></a>Spuštění operace přetažení  
  
1. V <xref:System.Windows.Forms.Control.MouseDown> případě ovládacího prvku, kde bude `DoDragDrop` přetahování zahájeno, použijte metodu k nastavení dat, která mají být přetažena, a bude mít povolený efekt přetažení. Další informace naleznete v tématech <xref:System.Windows.Forms.DragEventArgs.Data%2A> a <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.  
  
     Následující příklad ukazuje, jak zahájit operaci přetažení. Ovládací prvek, kde začíná <xref:System.Windows.Forms.Button> přetažení je ovládací prvek, přetahovaná <xref:System.Windows.Forms.Control.Text%2A> data <xref:System.Windows.Forms.Button> je řetězec představující vlastnost ovládacího prvku a povolené efekty jsou buď kopírování nebo přesunutí.  
  
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
    > Jako parametr v metodě `DoDragDrop` lze použít libovolná data; ve výše uvedeném <xref:System.Windows.Forms.Control.Text%2A> příkladu <xref:System.Windows.Forms.Button> byla použita vlastnost ovládacího prvku (spíše než pevné kódování hodnoty nebo načítání dat z datové <xref:System.Windows.Forms.Button> sady), protože vlastnost souvisela s umístěním přetahovaným z (ovládací prvek). Mějte to na paměti při zapracování operací přetažení do aplikací založených na systému Windows.  
  
 Během operace přetažení můžete zpracovat <xref:System.Windows.Forms.Control.QueryContinueDrag> událost, která "požádá o oprávnění" systému, aby mohla pokračovat v operaci přetažení. Při zpracování této metody je také vhodný bod pro volání metod, které budou mít vliv <xref:System.Windows.Forms.TreeNode> na <xref:System.Windows.Forms.TreeView> operaci přetažení, jako je například rozbalení v ovládacím prvku, když kurzor najedou nad ním.  
  
## <a name="dropping-data"></a>Zrušení dat  
 Jakmile začnete přetahovat data z umístění ve formuláři nebo ovládacím prvku systému Windows, budete je přirozeně chtít někam upustit. Kurzor se změní, když překročí oblast formuláře nebo ovládacího prvku, který je správně nakonfigurován pro vyřazování dat. Libovolná oblast ve formuláři systému Windows nebo ovládací <xref:System.Windows.Forms.Control.AllowDrop%2A> prvek lze <xref:System.Windows.Forms.Control.DragEnter> <xref:System.Windows.Forms.Control.DragDrop> provést přijímat vynecháná data nastavením vlastnosti a zpracování a události.  
  
#### <a name="to-perform-a-drop"></a>Provedení poklesu  
  
1. Nastavte <xref:System.Windows.Forms.Control.AllowDrop%2A> vlastnost na hodnotu true.  
  
2. V `DragEnter` případě ovládacího prvku, kde dojde k přetažení, ujistěte se, že přetahovaná data jsou přijatelného typu (v tomto případě <xref:System.Windows.Forms.Control.Text%2A>). Kód pak nastaví efekt, který se stane, když <xref:System.Windows.Forms.DragDropEffects> dojde k poklesu na hodnotu ve výčtu. Další informace naleznete v tématu <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.  
  
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
    > Můžete definovat vlastní <xref:System.Windows.Forms.DataFormats> zadáním vlastního objektu <xref:System.Object> jako <xref:System.Windows.Forms.DataObject.SetData%2A> parametr metody. Ujistěte se, že při tomto, že zadaný objekt je serializovatelný. Další informace naleznete v tématu <xref:System.Runtime.Serialization.ISerializable>.  
  
3. V <xref:System.Windows.Forms.Control.DragDrop> případě ovládacího prvku, kde dojde <xref:System.Windows.Forms.DataObject.GetData%2A> k přetažení, použijte metodu k načtení přetahovaných dat. Další informace naleznete v tématu <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.  
  
     V níže uvedeném <xref:System.Windows.Forms.TextBox> příkladu je ovládací prvek přetahovaný do (kde dojde k přetažení). Kód nastaví <xref:System.Windows.Forms.Control.Text%2A> vlastnost <xref:System.Windows.Forms.TextBox> ovládacího prvku rovná data přetahovaná.  
  
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
    > Kromě toho můžete pracovat <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> s vlastností, takže v závislosti na klávesách stisknutých během operace přetažení dochází k určitým efektům (například kopírování přetažených dat při stisknutí klávesy CTRL).  
  
## <a name="see-also"></a>Viz také

- [Postupy: Přidání dat do schránky](how-to-add-data-to-the-clipboard.md)
- [Postupy: Načtení dat ze schránky](how-to-retrieve-data-from-the-clipboard.md)
- [Operace přetažení a podpora schránky](drag-and-drop-operations-and-clipboard-support.md)
