---
title: "Postupy: Přístup ke konkrétním položkám v ovládacím prvku Windows Forms ComboBox, ListBox nebo CheckedListBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ComboBox control [Windows Forms], accessing items
- ListBox control [Windows Forms], returning item information
- list boxes [Windows Forms], accessing items
- ListBox control [Windows Forms], accessing items
- combo boxes [Windows Forms], accessing items
- CheckedListBox control [Windows Forms], accessing items
ms.assetid: 1216742f-bcf9-4ff8-8a62-d7c9053c2b96
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4ddcf6941f90556db26e2945c6b4460dfa585dbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-specific-items-in-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="caf87-102">Postupy: Přístup ke konkrétním položkám v ovládacím prvku Windows Forms ComboBox, ListBox nebo CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="caf87-102">How to: Access Specific Items in a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="caf87-103">Přístup ke konkrétní položky ve Windows Forms – pole se seznamem, seznamu nebo pole se seznamem zaškrtnuté je nezbytné úlohy.</span><span class="sxs-lookup"><span data-stu-id="caf87-103">Accessing specific items in a Windows Forms combo box, list box, or checked list box is an essential task.</span></span> <span data-ttu-id="caf87-104">Umožňuje programu určit, co je v seznamu, na dané pozici.</span><span class="sxs-lookup"><span data-stu-id="caf87-104">It enables you to programmatically determine what is in a list, at any given position.</span></span>  
  
### <a name="to-access-a-specific-item"></a><span data-ttu-id="caf87-105">Pro přístup k určité položce</span><span class="sxs-lookup"><span data-stu-id="caf87-105">To access a specific item</span></span>  
  
1.  <span data-ttu-id="caf87-106">Dotaz `Items` kolekce s použitím indexu konkrétní položky:</span><span class="sxs-lookup"><span data-stu-id="caf87-106">Query the `Items` collection using the index of the specific item:</span></span>  
  
    ```vb  
    Private Function GetItemText(i As Integer) As String  
       ' Return the text of the item using the index:  
       Return ComboBox1.Items(i).ToString  
    End Function  
    ```  
  
    ```csharp  
    private string GetItemText(int i)  
    {  
       // Return the text of the item using the index:  
       return (comboBox1.Items[i].ToString());  
    }  
    ```  
  
    ```cpp  
    private:  
       String^ GetItemText(int i)  
       {  
          // Return the text of the item using the index:  
          return (comboBox1->Items->Item[i]->ToString());  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="caf87-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="caf87-107">See Also</span></span>  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 <xref:System.Windows.Forms.CheckedListBox>  
 [<span data-ttu-id="caf87-108">Windows Forms – ovládací prvky používané k výpisu možností</span><span class="sxs-lookup"><span data-stu-id="caf87-108">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
