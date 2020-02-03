---
title: Přidávání a odebírání položek z ovládacího prvku ComboBox, ListBox nebo CheckedListBox
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
ms.openlocfilehash: 3a83d98af42386b566b4af7bc11ff383dea8fd6b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746305"
---
# <a name="how-to-add-and-remove-items-from-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>Postupy: Přidání a odebrání položek z ovládacích prvků Windows Forms ComboBox, ListBox nebo CheckedListBox
Položky lze přidat do model Windows Forms pole se seznamem, seznam nebo zaškrtnuté pole se seznamem, protože tyto ovládací prvky lze svázat s nejrůznějšími zdroji dat. Toto téma však ukazuje nejjednodušší metodu a nevyžaduje žádnou datovou vazbu. Zobrazené položky jsou obvykle řetězce; lze však použít libovolný objekt. Text zobrazený v ovládacím prvku je hodnota vrácená metodou `ToString` objektu.  
  
### <a name="to-add-items"></a>Přidání položek  
  
1. Přidejte řetězec nebo objekt do seznamu pomocí metody `Add` třídy `ObjectCollection`. Na kolekci se odkazuje pomocí vlastnosti `Items`:  
  
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
  
2. Do požadovaného bodu v seznamu vložte řetězec nebo objekt pomocí metody `Insert`:  
  
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
  
3. Přiřaďte celému poli kolekci `Items`:  
  
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
  
### <a name="to-remove-an-item"></a>Odebrání položky  
  
1. Chcete-li odstranit položky, zavolejte metodu `Remove` nebo `RemoveAt`.  
  
     `Remove` má jeden argument, který určuje položku, která se má odebrat.`RemoveAt` Odebere položku se zadaným indexovým číslem.  
  
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
  
### <a name="to-remove-all-items"></a>Odebrání všech položek  
  
1. Chcete-li odebrat všechny položky z kolekce, zavolejte metodu `Clear`:  
  
    ```vb  
    ListBox1.Items.Clear()  
    ```  
  
    ```csharp  
    listBox1.Items.Clear();  
    ```  
  
    ```cpp  
    listBox1->Items->Clear();  
    ```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms.CheckedListBox>
- [Postupy: Řazení obsahu ovládacího prvku ComboBox, ListBox nebo CheckedListBox z Windows Forms](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [Kdy použít prvek Windows Forms ComboBox místo prvku ListBox](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [Ovládací prvky Windows Forms používané k výpisu možností](windows-forms-controls-used-to-list-options.md)
