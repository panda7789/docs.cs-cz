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
ms.openlocfilehash: f7551f28d07c9517865f60af99954eb40e57daa2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61747391"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a>Návod: Provádění operace přetažení v modelu Windows Forms
K provádění operací přetažení myší v rámci aplikace pro systém Windows je třeba ošetřit řadu událostí, zejména <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, a <xref:System.Windows.Forms.Control.DragDrop> události. Při práci s informacemi, které jsou k dispozici události argumenty tyto události, můžete snadno usnadnění operace přetažení myší.  
  
## <a name="dragging-data"></a>Přetažení dat  
 Všechny operace přetažení myší začínat přetažení. Funkce, které umožňují data shromažďovat, přetažením začíná je implementována v <xref:System.Windows.Forms.Control.DoDragDrop%2A> metody.  
  
 V následujícím příkladu <xref:System.Windows.Forms.Control.MouseDown> událostí se používá ke spuštění operace přetažení, protože je nejvíce intuitivní (většinu akcí a přetahování začínat tlačítko myši stisknuté se). Nezapomeňte však, že všechny události se používal k zahájení proceduru přetahování myší.  
  
> [!NOTE]
>  Některé ovládací prvky mají vlastní události specifické pro přetažení. <xref:System.Windows.Forms.ListView> a <xref:System.Windows.Forms.TreeView> ovládacích prvků, třeba mít <xref:System.Windows.Forms.TreeView.ItemDrag> událostí.  
  
#### <a name="to-start-a-drag-operation"></a>Pokud chcete spustit operaci přetažení  
  
1. V <xref:System.Windows.Forms.Control.MouseDown> události pro ovládací prvek ve kterém se začne přetahování, použijte `DoDragDrop` bude mít metody nastavte data, která mají být kvůli usnadnění použití vypsány a povoleným efektem přetažení. Další informace naleznete v tématu <xref:System.Windows.Forms.DragEventArgs.Data%2A> a <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.  
  
     Následující příklad ukazuje, jak k zahájení operace přetažení. Ovládací prvek, kde začíná přetahování <xref:System.Windows.Forms.Button> ovládacího prvku, data jsou kvůli usnadnění použití vypsány je řetězec představující <xref:System.Windows.Forms.Control.Text%2A> vlastnost <xref:System.Windows.Forms.Button> ovládacího prvku a povolené efekty jsou kopírování nebo přesunutí.  
  
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
    >  Všechna data, můžete použít jako parametr v `DoDragDrop` metody; v příkladu výše, <xref:System.Windows.Forms.Control.Text%2A> vlastnost <xref:System.Windows.Forms.Button> ovládací prvek byl použit (místo pevného kódování hodnotu nebo načítání dat z datové sady) vzhledem k tomu, že byla vlastnosti související s přetažen z umístění ( <xref:System.Windows.Forms.Button> ovládací prvek). Mějte na paměti jako začlenit operací přetažení myší do vaší aplikace pro systém Windows.  
  
 Během operace přetažení je v platnosti, můžete zpracovávat <xref:System.Windows.Forms.Control.QueryContinueDrag> událost, která "požádá oprávnění" systému pokračovat v provádění operace přetažení. Při zpracování této metody, je také odpovídajícím bodě si můžete volat metody, které budou mít vliv na operace přetažení, například rozšíření <xref:System.Windows.Forms.TreeNode> v <xref:System.Windows.Forms.TreeView> ovládací prvek, když se ukazatelem přejde nad ním.  
  
## <a name="dropping-data"></a>Vyřazení dat  
 Po zahájení přetáhnete data z umístění na Windows formulář nebo ovládací prvek se přirozeně chcete vyřadit někde. Při překročí určitou oblast formuláře nebo ovládací prvek, který je správně nakonfigurovaný pro odstranění dat se změní kurzor. Všechny oblasti v rámci ovládacího prvku formuláře Windows nebo můžete provést tak, aby přijímal vynechaných dat tím, že nastavíte <xref:System.Windows.Forms.Control.AllowDrop%2A> vlastnost a zpracování <xref:System.Windows.Forms.Control.DragEnter> a <xref:System.Windows.Forms.Control.DragDrop> události.  
  
#### <a name="to-perform-a-drop"></a>K provedení přetažení  
  
1. Nastavte <xref:System.Windows.Forms.Control.AllowDrop%2A> vlastnost na hodnotu true.  
  
2. V `DragEnter` události pro ovládací prvek, pokud dojde k rozevírací nabídku, ujistěte se, že data jsou kvůli usnadnění použití vypsány přijatelné typ (v tomto případě <xref:System.Windows.Forms.Control.Text%2A>). Kód poté nastaví efekt, který se stane, když rozevírací dojde k hodnotě ve <xref:System.Windows.Forms.DragDropEffects> výčtu. Další informace naleznete v tématu <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.  
  
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
    >  Můžete definovat vlastní <xref:System.Windows.Forms.DataFormats> tak, že zadáte jako vlastní objekt <xref:System.Object> parametr <xref:System.Windows.Forms.DataObject.SetData%2A> metody. Ujistěte se, když to, že je zadaný objekt serializovatelný. Další informace naleznete v tématu <xref:System.Runtime.Serialization.ISerializable>.  
  
3. V <xref:System.Windows.Forms.Control.DragDrop> události pro ovládací prvek rozevírací kde dojde, použijte <xref:System.Windows.Forms.DataObject.GetData%2A> metodu pro načtení dat se přetáhnout. Další informace naleznete v tématu <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.  
  
     V následujícím příkladu <xref:System.Windows.Forms.TextBox> ovládací prvek je ovládací prvek přetažen (ve kterém bude každý rozevírací). Nastaví kód <xref:System.Windows.Forms.Control.Text%2A> vlastnost <xref:System.Windows.Forms.TextBox> řídit rovna data jsou kvůli usnadnění použití vypsány.  
  
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
    >  Kromě toho můžete pracovat <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> určité účinkům dochází vlastnost, takže v závislosti na klíče stisknuté během operace přetažení myší, (například je standardní kopírování Přetahované dat při stisknutí klávesy CTRL).  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Přidání dat do schránky.](how-to-add-data-to-the-clipboard.md)
- [Postupy: Načtení dat ze schránky](how-to-retrieve-data-from-the-clipboard.md)
- [Operace přetažení a podpora schránky](drag-and-drop-operations-and-clipboard-support.md)
