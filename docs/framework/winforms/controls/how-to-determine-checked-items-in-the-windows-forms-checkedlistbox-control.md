---
title: 'Postupy: Určení zaškrtnutých položek v ovládacím prvku Windows Forms CheckedListBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- check boxes [Windows Forms], determining checked state
- CheckedListBox control [Windows Forms], determining checked state
ms.assetid: 178b477d-27c9-489c-8914-44a9623a4d41
ms.openlocfilehash: 98b4ef7c4ac73e1560bd5c68f22898e46585d082
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531011"
---
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a><span data-ttu-id="cb91a-102">Postupy: Určení zaškrtnutých položek v ovládacím prvku Windows Forms CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="cb91a-102">How to: Determine Checked Items in the Windows Forms CheckedListBox Control</span></span>
<span data-ttu-id="cb91a-103">Při zobrazení dat uložených v systému Windows Forms <xref:System.Windows.Forms.CheckedListBox> ovládací prvek, můžete buď iterovat uložené v kolekci <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> vlastnost, nebo krok prostřednictvím seznamu <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> metoda k určení, které položky se kontroluje.</span><span class="sxs-lookup"><span data-stu-id="cb91a-103">When presenting data in a Windows Forms <xref:System.Windows.Forms.CheckedListBox> control, you can either iterate through the collection stored in the <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> property, or step through the list using the <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> method to determine which items are checked.</span></span> <span data-ttu-id="cb91a-104"><xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> Metoda přebírá číslo indexu položky jako její argument a vrátí `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="cb91a-104">The <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> method takes an item index number as its argument and returns `true` or `false`.</span></span> <span data-ttu-id="cb91a-105">Na rozdíl od mohou očekávat <xref:System.Windows.Forms.ListBox.SelectedItems%2A> a <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> vlastnosti není určeno, které položky se kontroluje; určují, které položky se zvýrazněnou.</span><span class="sxs-lookup"><span data-stu-id="cb91a-105">Contrary to what you might expect, the <xref:System.Windows.Forms.ListBox.SelectedItems%2A> and <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> properties do not determine which items are checked; they determine which items are highlighted.</span></span>  
  
### <a name="to-determine-checked-items-in-a-checkedlistbox-control"></a><span data-ttu-id="cb91a-106">K určení zaškrtnutých položek v ovládacím prvku CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="cb91a-106">To determine checked items in a CheckedListBox control</span></span>  
  
1.  <span data-ttu-id="cb91a-107">Iterace <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> kolekce, začínající na 0, protože kolekce je počítáno od nuly.</span><span class="sxs-lookup"><span data-stu-id="cb91a-107">Iterate through the <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> collection, starting at 0 since the collection is zero-based.</span></span> <span data-ttu-id="cb91a-108">Všimněte si, že tato metoda vám poskytne počet položek v seznamu zkontrolovat položky, ne celkový seznam.</span><span class="sxs-lookup"><span data-stu-id="cb91a-108">Note that this method will give you the item number in the list of checked items, not the overall list.</span></span> <span data-ttu-id="cb91a-109">Takže pokud není zaškrtnuta možnost první položky v seznamu a druhá položka je zaškrtnuta, následující kód zobrazí text jako "zaškrtnuté položky 1 = MyListItem2".</span><span class="sxs-lookup"><span data-stu-id="cb91a-109">So if the first item in the list is not checked and the second item is checked, the code below will display text like "Checked Item 1 = MyListItem2".</span></span>  
  
    ```vb  
    ' Determine if there are any items checked.  
    If CheckedListBox1.CheckedItems.Count <> 0 Then  
       ' If so, loop through all checked items and print results.  
       Dim x As Integer  
       Dim s As String = ""  
       For x = 0 To CheckedListBox1.CheckedItems.Count - 1  
          s = s & "Checked Item " & (x + 1).ToString & " = " & CheckedListBox1.CheckedItems(x).ToString & ControlChars.CrLf  
       Next x  
       MessageBox.Show(s)  
    End If  
    ```  
  
    ```csharp  
    // Determine if there are any items checked.  
    if(checkedListBox1.CheckedItems.Count != 0)  
    {  
       // If so, loop through all checked items and print results.  
       string s = "";  
       for(int x = 0; x <= checkedListBox1.CheckedItems.Count - 1 ; x++)  
       {  
          s = s + "Checked Item " + (x+1).ToString() + " = " + checkedListBox1.CheckedItems[x].ToString() + "\n";  
       }  
    MessageBox.Show (s);  
    }  
    ```  
  
    ```cpp  
    // Determine if there are any items checked.  
    if(checkedListBox1->CheckedItems->Count != 0)  
    {  
       // If so, loop through all checked items and print results.  
       String ^ s = "";  
       for(int x = 0; x <= checkedListBox1->CheckedItems->Count - 1; x++)  
       {  
          s = String::Concat(s, "Checked Item ", (x+1).ToString(),  
             " = ", checkedListBox1->CheckedItems[x]->ToString(),  
             "\n");  
       }  
       MessageBox::Show(s);  
    }  
    ```  
  
     - <span data-ttu-id="cb91a-110">nebo –</span><span class="sxs-lookup"><span data-stu-id="cb91a-110">or -</span></span>  
  
2.  <span data-ttu-id="cb91a-111">Jednotlivé kroky <xref:System.Windows.Forms.CheckedListBox.Items%2A> kolekce začínající na 0, protože kolekce je počítáno od nuly a volání <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> metoda pro každou položku.</span><span class="sxs-lookup"><span data-stu-id="cb91a-111">Step through the <xref:System.Windows.Forms.CheckedListBox.Items%2A> collection, starting at 0 since the collection is zero-based, and call the <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> method for each item.</span></span> <span data-ttu-id="cb91a-112">Všimněte si, že tato metoda vám poskytne počet položek v seznamu celkové, pokud první položku v seznamu nastavení není kontrolován a druhá položka je zaškrtnuta možnost zobrazí něco jako "položka 2 = MyListItem2".</span><span class="sxs-lookup"><span data-stu-id="cb91a-112">Note that this method will give you the item number in the overall list, so if the first item in the list is not checked and the second item is checked, it will display something like "Item 2 = MyListItem2".</span></span>  
  
    ```vb  
    Dim i As Integer  
    Dim s As String  
    s = "Checked Items:" & ControlChars.CrLf  
    For i = 0 To (CheckedListBox1.Items.Count - 1)  
       If CheckedListBox1.GetItemChecked(i) = True Then  
          s = s & "Item " & (i + 1).ToString & " = " & CheckedListBox1.Items(i).ToString & ControlChars.CrLf  
       End If  
    Next  
    MessageBox.Show(s)  
    ```  
  
    ```csharp  
    int i;  
    string s;   
    s = "Checked items:\n" ;  
    for (i = 0; i <= (checkedListBox1.Items.Count-1); i++)  
    {  
       if (checkedListBox1.GetItemChecked(i))  
       {  
          s = s + "Item " + (i+1).ToString() + " = " + checkedListBox1.Items[i].ToString() + "\n";  
       }  
    }  
    MessageBox.Show (s);  
    ```  
  
    ```cpp  
    int i;  
    String ^ s;   
    s = "Checked items:\n" ;  
    for (i = 0; i <= (checkedListBox1->Items->Count-1); i++)  
    {  
       if (checkedListBox1->GetItemChecked(i))  
       {  
          s = String::Concat(s, "Item ", (i+1).ToString(), " = ",  
             checkedListBox1->Item[i]->ToString(), "\n");  
       }  
    }  
    MessageBox::Show(s);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="cb91a-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="cb91a-113">See Also</span></span>  
 [<span data-ttu-id="cb91a-114">Ovládací prvky Windows Forms používané k výpisu možností</span><span class="sxs-lookup"><span data-stu-id="cb91a-114">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
