---
title: Přidávání a odebírání položek z ovládacího prvku ComboBox, ListBox nebo CheckedListBox
ms.date: 03/30/2017
description: Naučte se, jak přidat a odebrat model Windows Forms ovládací prvky ComboBox, ListBox a CheckedListBox jednoduše a bez vazby dat.
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
ms.openlocfilehash: f3701257bbe410bf03c4c21700705e87b581bf2e
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904439"
---
# <a name="how-to-add-and-remove-items-from-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="12b17-103">Postupy: Přidání a odebrání položek z ovládacích prvků Windows Forms ComboBox, ListBox nebo CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="12b17-103">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="12b17-104">Položky lze přidat do model Windows Forms pole se seznamem, seznam nebo zaškrtnuté pole se seznamem, protože tyto ovládací prvky lze svázat s nejrůznějšími zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="12b17-104">Items can be added to a Windows Forms combo box, list box, or checked list box in a variety of ways, because these controls can be bound to a variety of data sources.</span></span> <span data-ttu-id="12b17-105">Toto téma však ukazuje nejjednodušší metodu a nevyžaduje žádnou datovou vazbu.</span><span class="sxs-lookup"><span data-stu-id="12b17-105">However, this topic demonstrates the simplest method and requires no data binding.</span></span> <span data-ttu-id="12b17-106">Zobrazené položky jsou obvykle řetězce; lze však použít libovolný objekt.</span><span class="sxs-lookup"><span data-stu-id="12b17-106">The items displayed are usually strings; however, any object can be used.</span></span> <span data-ttu-id="12b17-107">Text zobrazený v ovládacím prvku je hodnota vrácená `ToString` metodou objektu.</span><span class="sxs-lookup"><span data-stu-id="12b17-107">The text that is displayed in the control is the value returned by the object's `ToString` method.</span></span>  
  
### <a name="to-add-items"></a><span data-ttu-id="12b17-108">Přidání položek</span><span class="sxs-lookup"><span data-stu-id="12b17-108">To add items</span></span>  
  
1. <span data-ttu-id="12b17-109">Přidejte řetězec nebo objekt do seznamu pomocí `Add` metody `ObjectCollection` třídy.</span><span class="sxs-lookup"><span data-stu-id="12b17-109">Add the string or object to the list by using the `Add` method of the `ObjectCollection` class.</span></span> <span data-ttu-id="12b17-110">Na kolekci se odkazuje pomocí `Items` vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="12b17-110">The collection is referenced using the `Items` property:</span></span>  
  
    ```vb  
    ComboBox1.Items.Add("Tokyo")  
    ```  
  
    ```csharp  
    comboBox1.Items.Add("Tokyo");  
    ```  
  
    ```cpp  
    comboBox1->Items->Add("Tokyo");  
    ```  
  
     - <span data-ttu-id="12b17-111">ani</span><span class="sxs-lookup"><span data-stu-id="12b17-111">or -</span></span>  
  
2. <span data-ttu-id="12b17-112">Vložte řetězec nebo objekt v požadovaném místě v seznamu pomocí `Insert` metody:</span><span class="sxs-lookup"><span data-stu-id="12b17-112">Insert the string or object at the desired point in the list with the `Insert` method:</span></span>  
  
    ```vb  
    CheckedListBox1.Items.Insert(0, "Copenhagen")  
    ```  
  
    ```csharp  
    checkedListBox1.Items.Insert(0, "Copenhagen");  
    ```  
  
    ```cpp  
    checkedListBox1->Items->Insert(0, "Copenhagen");  
    ```  
  
     - <span data-ttu-id="12b17-113">ani</span><span class="sxs-lookup"><span data-stu-id="12b17-113">or -</span></span>  
  
3. <span data-ttu-id="12b17-114">Přiřaďte celému poli `Items` kolekci:</span><span class="sxs-lookup"><span data-stu-id="12b17-114">Assign an entire array to the `Items` collection:</span></span>  
  
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
  
### <a name="to-remove-an-item"></a><span data-ttu-id="12b17-115">Odebrání položky</span><span class="sxs-lookup"><span data-stu-id="12b17-115">To remove an item</span></span>  
  
1. <span data-ttu-id="12b17-116">`Remove` `RemoveAt` Chcete-li odstranit položky, zavolejte metodu or.</span><span class="sxs-lookup"><span data-stu-id="12b17-116">Call the `Remove` or `RemoveAt` method to delete items.</span></span>  
  
     <span data-ttu-id="12b17-117">`Remove`má jeden argument, který určuje položku, která se má odebrat.`RemoveAt`</span><span class="sxs-lookup"><span data-stu-id="12b17-117">`Remove` has one argument that specifies the item to remove.`RemoveAt`</span></span> <span data-ttu-id="12b17-118">Odebere položku se zadaným indexovým číslem.</span><span class="sxs-lookup"><span data-stu-id="12b17-118">removes the item with the specified index number.</span></span>  
  
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
  
### <a name="to-remove-all-items"></a><span data-ttu-id="12b17-119">Odebrání všech položek</span><span class="sxs-lookup"><span data-stu-id="12b17-119">To remove all items</span></span>  
  
1. <span data-ttu-id="12b17-120">Zavolejte `Clear` metodu pro odebrání všech položek z kolekce:</span><span class="sxs-lookup"><span data-stu-id="12b17-120">Call the `Clear` method to remove all items from the collection:</span></span>  
  
    ```vb  
    ListBox1.Items.Clear()  
    ```  
  
    ```csharp  
    listBox1.Items.Clear();  
    ```  
  
    ```cpp  
    listBox1->Items->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="12b17-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="12b17-121">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms.CheckedListBox>
- [<span data-ttu-id="12b17-122">Postupy: Řazení obsahu ovládacího prvku Windows Forms ComboBox, ListBox nebo CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="12b17-122">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [<span data-ttu-id="12b17-123">Kdy použít prvek Windows Forms ComboBox místo prvku ListBox</span><span class="sxs-lookup"><span data-stu-id="12b17-123">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [<span data-ttu-id="12b17-124">Ovládací prvky Windows Forms používané k výpisu možností</span><span class="sxs-lookup"><span data-stu-id="12b17-124">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
