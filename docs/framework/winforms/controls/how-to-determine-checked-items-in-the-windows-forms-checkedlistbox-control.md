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
ms.openlocfilehash: 10793053934dce0bb83113004a79f1c265f5f267
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59316567"
---
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a><span data-ttu-id="4d5b3-102">Postupy: Určení zaškrtnutých položek v ovládacím prvku Windows Forms CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="4d5b3-102">How to: Determine Checked Items in the Windows Forms CheckedListBox Control</span></span>
<span data-ttu-id="4d5b3-103">Při zobrazení dat ve Windows Forms <xref:System.Windows.Forms.CheckedListBox> ovládacího prvku, můžete buď iterovat uložených v kolekci <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> vlastnost nebo kroku pomocí seznamu <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> metodou ke zjištění, které položky jsou kontrolovány.</span><span class="sxs-lookup"><span data-stu-id="4d5b3-103">When presenting data in a Windows Forms <xref:System.Windows.Forms.CheckedListBox> control, you can either iterate through the collection stored in the <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> property, or step through the list using the <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> method to determine which items are checked.</span></span> <span data-ttu-id="4d5b3-104"><xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> Metoda přijímá číslo indexu položky jako svůj argument a vrátí `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="4d5b3-104">The <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> method takes an item index number as its argument and returns `true` or `false`.</span></span> <span data-ttu-id="4d5b3-105">Rozporu s dalo očekávat <xref:System.Windows.Forms.ListBox.SelectedItems%2A> a <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> vlastnosti neurčují položky, které zjišťována; určují, které položky jsou zvýrazněné.</span><span class="sxs-lookup"><span data-stu-id="4d5b3-105">Contrary to what you might expect, the <xref:System.Windows.Forms.ListBox.SelectedItems%2A> and <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> properties do not determine which items are checked; they determine which items are highlighted.</span></span>  
  
### <a name="to-determine-checked-items-in-a-checkedlistbox-control"></a><span data-ttu-id="4d5b3-106">K určení zaškrtnutých položek v ovládacím prvku CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="4d5b3-106">To determine checked items in a CheckedListBox control</span></span>  
  
1. <span data-ttu-id="4d5b3-107">Iterovat přes <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> kolekce, počínaje 0, protože kolekce je založený na nule.</span><span class="sxs-lookup"><span data-stu-id="4d5b3-107">Iterate through the <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> collection, starting at 0 since the collection is zero-based.</span></span> <span data-ttu-id="4d5b3-108">Všimněte si, že tato metoda získáte počet položek v seznamu zaškrtnutých položek není celkový přehled.</span><span class="sxs-lookup"><span data-stu-id="4d5b3-108">Note that this method will give you the item number in the list of checked items, not the overall list.</span></span> <span data-ttu-id="4d5b3-109">Takže pokud není zaškrtnuto políčko na první položku v seznamu a je druhá položka zaškrtnuta, následující kód zobrazí text jako "zaškrtnutá položka 1 = MyListItem2".</span><span class="sxs-lookup"><span data-stu-id="4d5b3-109">So if the first item in the list is not checked and the second item is checked, the code below will display text like "Checked Item 1 = MyListItem2".</span></span>  
  
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
       for(int x = 0; x < checkedListBox1.CheckedItems.Count ; x++)  
       {  
          s = s + "Checked Item " + (x+1).ToString() + " = " + checkedListBox1.CheckedItems[x].ToString() + "\n";  
       }  
       MessageBox.Show(s);  
    }  
    ```  
  
    ```cpp  
    // Determine if there are any items checked.  
    if(checkedListBox1->CheckedItems->Count != 0)  
    {  
       // If so, loop through all checked items and print results.  
       String ^ s = "";  
       for(int x = 0; x < checkedListBox1->CheckedItems->Count; x++)  
       {  
          s = String::Concat(s, "Checked Item ", (x+1).ToString(),  
             " = ", checkedListBox1->CheckedItems[x]->ToString(),  
             "\n");  
       }  
       MessageBox::Show(s);  
    }  
    ```  
  
     - <span data-ttu-id="4d5b3-110">nebo –</span><span class="sxs-lookup"><span data-stu-id="4d5b3-110">or -</span></span>  
  
2. <span data-ttu-id="4d5b3-111">Projít <xref:System.Windows.Forms.CheckedListBox.Items%2A> kolekce, protože kolekce je založený na nule, začínajícím hodnotou 0 a volání <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> metoda pro každou položku.</span><span class="sxs-lookup"><span data-stu-id="4d5b3-111">Step through the <xref:System.Windows.Forms.CheckedListBox.Items%2A> collection, starting at 0 since the collection is zero-based, and call the <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> method for each item.</span></span> <span data-ttu-id="4d5b3-112">Všimněte si, že tato metoda získáte počet položek v seznamu celkové, pokud první položku v seznamu není zaškrtnuto a druhá položka je zaškrtnuto, zobrazí něco jako "položka 2 = MyListItem2".</span><span class="sxs-lookup"><span data-stu-id="4d5b3-112">Note that this method will give you the item number in the overall list, so if the first item in the list is not checked and the second item is checked, it will display something like "Item 2 = MyListItem2".</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4d5b3-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d5b3-113">See also</span></span>

- [<span data-ttu-id="4d5b3-114">Ovládací prvky Windows Forms používané k výpisu možností</span><span class="sxs-lookup"><span data-stu-id="4d5b3-114">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
