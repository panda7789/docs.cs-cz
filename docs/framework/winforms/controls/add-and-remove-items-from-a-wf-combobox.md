---
title: 'Postupy: Přidání a odebrání položek z ovládacích prvků Windows Forms ComboBox, ListBox nebo CheckedListBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- combo boxes [Windows Forms], adding items
- list boxes [Windows Forms], removing items
- ComboBox control [Windows Forms], adding and removing items
- ListBox control [Windows Forms], adding and removing items
- list boxes [Windows Forms], adding items
- combo boxes [Windows Forms], removing items
- CheckedListBox control [Windows Forms], adding and removing items
ms.assetid: 7224c8d2-4118-443e-ae1e-d7c17d1e69ee
ms.openlocfilehash: bd6614c76c63a44a7367ac7c7113c4db260c9a02
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322729"
---
# <a name="how-to-add-and-remove-items-from-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>Postupy: Přidání a odebrání položek z ovládacích prvků Windows Forms ComboBox, ListBox nebo CheckedListBox
Položky lze přidat do pole se seznamem Windows Forms, pole se seznamem, nebo zkontrolovat mnoha různými způsoby, pole se seznamem, protože tyto ovládací prvky mohou být vázány na širokou škálu zdrojů dat. Toto téma však ukazuje nejjednodušší způsob a vyžaduje žádné datové vazby. Zobrazení položek jsou obvykle řetězce; však můžete použít libovolný objekt. Text, který se zobrazí v ovládacím prvku je hodnotu vrácenou objektu `ToString` metody.  
  
### <a name="to-add-items"></a>Chcete-li přidat položky  
  
1. Přidání řetězec nebo objekt, do seznamu s použitím `Add` metodu `ObjectCollection` třídy. Kolekce odkazuje pomocí `Items` vlastnost:  
  
    ```vb  
    ComboBox1.Items.Add("Tokyo")  
    ```  
  
    ```csharp  
    comboBox1.Items.Add("Tokyo");  
    ```  
  
    ```cpp  
    comboBox1->Items->Add("Tokyo");  
    ```  
  
     - nebo –  
  
2. Vložit řetězec nebo objekt na požadované místo v seznamu se `Insert` metody:  
  
    ```vb  
    CheckedListBox1.Items.Insert(0, "Copenhagen")  
    ```  
  
    ```csharp  
    checkedListBox1.Items.Insert(0, "Copenhagen");  
    ```  
  
    ```cpp  
    checkedListBox1->Items->Insert(0, "Copenhagen");  
    ```  
  
     - nebo –  
  
3. Přiřadit celého pole na `Items` kolekce:  
  
    ```vb  
    Dim ItemObject(9) As System.Object  
    Dim i As Integer  
       For i = 0 To 9  
       ItemObject(i) = "Item" & i  
    Next i  
    ListBox1.Items.AddRange(ItemObject)  
    ```  
  
    ```csharp  
    System.Object[] ItemObject = new System.Object[10];  
    for (int i = 0; i <= 9; i++)  
    {  
       ItemObject[i] = "Item" + i;  
    }  
    listBox1.Items.AddRange(ItemObject);  
    ```  
  
    ```cpp  
    Array<System::Object^>^ ItemObject = gcnew Array<System::Object^>(10);  
    for (int i = 0; i <= 9; i++)  
    {  
       ItemObject[i] = String::Concat("Item", i.ToString());  
    }  
    listBox1->Items->AddRange(ItemObject);  
    ```  
  
### <a name="to-remove-an-item"></a>Chcete-li odebrat položku  
  
1. Volání `Remove` nebo `RemoveAt` metoda odstraňovat položky.  
  
     `Remove` má jeden argument, který obsahuje položky, které chcete odebrat.`RemoveAt` Odebere položku se zadané číslo indexu.  
  
    ```vb  
    ' To remove item with index 0:  
    ComboBox1.Items.RemoveAt(0)  
    ' To remove currently selected item:  
    ComboBox1.Items.Remove(ComboBox1.SelectedItem)  
    ' To remove "Tokyo" item:  
    ComboBox1.Items.Remove("Tokyo")  
    ```  
  
    ```csharp  
    // To remove item with index 0:  
    comboBox1.Items.RemoveAt(0);  
    // To remove currently selected item:  
    comboBox1.Items.Remove(comboBox1.SelectedItem);  
    // To remove "Tokyo" item:  
    comboBox1.Items.Remove("Tokyo");  
    ```  
  
    ```cpp  
    // To remove item with index 0:  
    comboBox1->Items->RemoveAt(0);  
    // To remove currently selected item:  
    comboBox1->Items->Remove(comboBox1->SelectedItem);  
    // To remove "Tokyo" item:  
    comboBox1->Items->Remove("Tokyo");  
    ```  
  
### <a name="to-remove-all-items"></a>Chcete-li odebrat všechny položky  
  
1. Volání `Clear` metoda odebrat všechny položky z kolekce:  
  
    ```vb  
    ListBox1.Items.Clear()  
    ```  
  
    ```csharp  
    listBox1.Items.Clear();  
    ```  
  
    ```cpp  
    listBox1->Items->Clear();  
    ```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms.CheckedListBox>
- [Postupy: Řazení obsahu ovládacího prvku Windows Forms ComboBox, ListBox nebo CheckedListBox](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [Kdy použít prvek Windows Forms ComboBox místo prvku ListBox](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [Ovládací prvky Windows Forms používané k výpisu možností](windows-forms-controls-used-to-list-options.md)
