---
title: 'Návod: provedení operace přetažení'
description: Naučte se, jak provést operaci přetažení v model Windows Forms tím, že zpracujete řadu událostí, zejména události DragEnter, DragLeave a DragDrop.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: 83bfda875e2fdec3981bbcb8f8f7be00db342440
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325817"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a>Návod: Provádění operace přetažení ve Windows Forms
K provádění operací přetažení v rámci aplikací pro systém Windows je nutné zpracovat řady událostí, zejména <xref:System.Windows.Forms.Control.DragEnter> <xref:System.Windows.Forms.Control.DragLeave> události, a <xref:System.Windows.Forms.Control.DragDrop> . Při práci s informacemi dostupnými v argumentech událostí těchto událostí můžete snadno usnadnit operace přetažení.  
  
## <a name="dragging-data"></a>Přetahování dat  
 Všechny operace přetažení začínají přetahováním. Funkce, která povoluje shromažďování dat, když je zahájeno přetahování, je implementována v <xref:System.Windows.Forms.Control.DoDragDrop%2A> metodě.  
  
 V následujícím příkladu se <xref:System.Windows.Forms.Control.MouseDown> událost používá ke spuštění operace přetažení, protože se jedná o nejoblíbenější (většina akcí přetažení začíná tlačítkem myši). Mějte ale na paměti, že k zahájení postupu přetažení se dá použít jakákoli událost.  
  
> [!NOTE]
> Některé ovládací prvky mají vlastní události specifické pro přetahování. <xref:System.Windows.Forms.ListView> <xref:System.Windows.Forms.TreeView> Ovládací prvky a mají například <xref:System.Windows.Forms.TreeView.ItemDrag> událost.  
  
#### <a name="to-start-a-drag-operation"></a>Spuštění operace přetažení  
  
1. V <xref:System.Windows.Forms.Control.MouseDown> případě ovládacího prvku, kde bude zahájeno přetahování, použijte `DoDragDrop` metodu k nastavení přetažení dat a povoleného přetahování efektů. Další informace naleznete v tématech <xref:System.Windows.Forms.DragEventArgs.Data%2A> a <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.  
  
     Následující příklad ukazuje, jak iniciovat operaci přetažení. Ovládací prvek, kde je zahájeno přetažení <xref:System.Windows.Forms.Button> , je ovládací prvek, přetažená data jsou řetězcem představujícím <xref:System.Windows.Forms.Control.Text%2A> vlastnost <xref:System.Windows.Forms.Button> ovládacího prvku a povolené účinky jsou buď zkopírovány nebo přesunuty.  
  
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
    > Všechna data lze použít jako parametr v `DoDragDrop` metodě; v předchozím příkladu se <xref:System.Windows.Forms.Control.Text%2A> <xref:System.Windows.Forms.Button> použila vlastnost ovládacího prvku (místo hardwarového kódování hodnoty nebo načítání dat z datové sady), protože vlastnost se vztahuje k umístění, ze kterého se přetahuje ( <xref:System.Windows.Forms.Button> ovládací prvek). Pamatujte na to, že do aplikací založených na systému Windows zařadíte operace přetažení myší.  
  
 Zatímco je aktivní operace přetažení, můžete <xref:System.Windows.Forms.Control.QueryContinueDrag> událost zpracovat, což znamená, že se zobrazí výzva k zadání oprávnění systému, aby bylo možné pokračovat v operaci přetažení. Při zpracování této metody je také vhodným bodem pro volání metod, které budou mít vliv na operaci přetažení, jako je například rozbalení <xref:System.Windows.Forms.TreeNode> ovládacího prvku, když se ukazatel myši nachází na pozadí <xref:System.Windows.Forms.TreeView> .  
  
## <a name="dropping-data"></a>Vyřazení dat  
 Jakmile začnete přetahovat data z umístění ve formuláři nebo ovládacím prvku Windows, budete ho přirozeně chtít umístit jinam. Kurzor se změní, když přeskočí oblast formuláře nebo ovládacího prvku, který je správně nakonfigurován pro vyřazení dat. Jakékoli oblasti v rámci formuláře nebo ovládacího prvku systému Windows lze použít pro příjem zahozených dat nastavením <xref:System.Windows.Forms.Control.AllowDrop%2A> vlastnosti a zpracováním <xref:System.Windows.Forms.Control.DragEnter> <xref:System.Windows.Forms.Control.DragDrop> událostí a.  
  
#### <a name="to-perform-a-drop"></a>Provedení přetažení  
  
1. Nastavte <xref:System.Windows.Forms.Control.AllowDrop%2A> vlastnost na hodnotu true.  
  
2. V `DragEnter` případě ovládacího prvku, kde dojde k vyřazení, se ujistěte, že přetažená data jsou přijatelného typu (v tomto případě <xref:System.Windows.Forms.Control.Text%2A> ). Kód pak nastaví efekt, který se stane, když dojde k zapuštění na hodnotu ve <xref:System.Windows.Forms.DragDropEffects> výčtu. Další informace naleznete v tématu <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.  
  
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
    > Můžete definovat vlastní <xref:System.Windows.Forms.DataFormats> objekt zadáním vlastního objektu jako <xref:System.Object> parametru <xref:System.Windows.Forms.DataObject.SetData%2A> metody. Ujistěte se, že v takovém případě je zadaný objekt serializovatelný. Další informace naleznete v tématu <xref:System.Runtime.Serialization.ISerializable>.  
  
3. V <xref:System.Windows.Forms.Control.DragDrop> případě ovládacího prvku, kde dojde k vyřazení, použijte <xref:System.Windows.Forms.DataObject.GetData%2A> metodu pro načtení přetažených dat. Další informace naleznete v tématu <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.  
  
     V následujícím příkladu <xref:System.Windows.Forms.TextBox> je ovládací prvek přetažen do (kde dojde k přetažení). Kód nastaví <xref:System.Windows.Forms.Control.Text%2A> vlastnost <xref:System.Windows.Forms.TextBox> ovládacího prvku na hodnotu přetažená na data.  
  
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
  
## <a name="see-also"></a>Viz také

- [Postupy: Přidání dat do schránky](how-to-add-data-to-the-clipboard.md)
- [Postupy: Načtení dat ze schránky](how-to-retrieve-data-from-the-clipboard.md)
- [Operace přetažení a podpora schránky](drag-and-drop-operations-and-clipboard-support.md)
