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
# <a name="how-to-add-and-remove-items-from-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="28d50-102">Postupy: Přidání a odebrání položek z ovládacích prvků Windows Forms ComboBox, ListBox nebo CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="28d50-102">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="28d50-103">Položky lze přidat do model Windows Forms pole se seznamem, seznam nebo zaškrtnuté pole se seznamem, protože tyto ovládací prvky lze svázat s nejrůznějšími zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="28d50-103">Items can be added to a Windows Forms combo box, list box, or checked list box in a variety of ways, because these controls can be bound to a variety of data sources.</span></span> <span data-ttu-id="28d50-104">Toto téma však ukazuje nejjednodušší metodu a nevyžaduje žádnou datovou vazbu.</span><span class="sxs-lookup"><span data-stu-id="28d50-104">However, this topic demonstrates the simplest method and requires no data binding.</span></span> <span data-ttu-id="28d50-105">Zobrazené položky jsou obvykle řetězce; lze však použít libovolný objekt.</span><span class="sxs-lookup"><span data-stu-id="28d50-105">The items displayed are usually strings; however, any object can be used.</span></span> <span data-ttu-id="28d50-106">Text zobrazený v ovládacím prvku je hodnota vrácená metodou `ToString` objektu.</span><span class="sxs-lookup"><span data-stu-id="28d50-106">The text that is displayed in the control is the value returned by the object's `ToString` method.</span></span>  
  
### <a name="to-add-items"></a><span data-ttu-id="28d50-107">Přidání položek</span><span class="sxs-lookup"><span data-stu-id="28d50-107">To add items</span></span>  
  
1. <span data-ttu-id="28d50-108">Přidejte řetězec nebo objekt do seznamu pomocí metody `Add` třídy `ObjectCollection`.</span><span class="sxs-lookup"><span data-stu-id="28d50-108">Add the string or object to the list by using the `Add` method of the `ObjectCollection` class.</span></span> <span data-ttu-id="28d50-109">Na kolekci se odkazuje pomocí vlastnosti `Items`:</span><span class="sxs-lookup"><span data-stu-id="28d50-109">The collection is referenced using the `Items` property:</span></span>  
  
    ```vb  
    ComboBox1.Items.Add("Tokyo")  
    ```  
  
    ```csharp  
    comboBox1.Items.Add("Tokyo");  
    ```  
  
    ```cpp  
    comboBox1->Items->Add("Tokyo");  
    ```  
  
     - <span data-ttu-id="28d50-110">nebo –</span><span class="sxs-lookup"><span data-stu-id="28d50-110">or -</span></span>  
  
2. <span data-ttu-id="28d50-111">Do požadovaného bodu v seznamu vložte řetězec nebo objekt pomocí metody `Insert`:</span><span class="sxs-lookup"><span data-stu-id="28d50-111">Insert the string or object at the desired point in the list with the `Insert` method:</span></span>  
  
    ```vb  
    CheckedListBox1.Items.Insert(0, "Copenhagen")  
    ```  
  
    ```csharp  
    checkedListBox1.Items.Insert(0, "Copenhagen");  
    ```  
  
    ```cpp  
    checkedListBox1->Items->Insert(0, "Copenhagen");  
    ```  
  
     - <span data-ttu-id="28d50-112">nebo –</span><span class="sxs-lookup"><span data-stu-id="28d50-112">or -</span></span>  
  
3. <span data-ttu-id="28d50-113">Přiřaďte celému poli kolekci `Items`:</span><span class="sxs-lookup"><span data-stu-id="28d50-113">Assign an entire array to the `Items` collection:</span></span>  
  
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
  
### <a name="to-remove-an-item"></a><span data-ttu-id="28d50-114">Odebrání položky</span><span class="sxs-lookup"><span data-stu-id="28d50-114">To remove an item</span></span>  
  
1. <span data-ttu-id="28d50-115">Chcete-li odstranit položky, zavolejte metodu `Remove` nebo `RemoveAt`.</span><span class="sxs-lookup"><span data-stu-id="28d50-115">Call the `Remove` or `RemoveAt` method to delete items.</span></span>  
  
     <span data-ttu-id="28d50-116">`Remove` má jeden argument, který určuje položku, která se má odebrat.`RemoveAt`</span><span class="sxs-lookup"><span data-stu-id="28d50-116">`Remove` has one argument that specifies the item to remove.`RemoveAt`</span></span> <span data-ttu-id="28d50-117">Odebere položku se zadaným indexovým číslem.</span><span class="sxs-lookup"><span data-stu-id="28d50-117">removes the item with the specified index number.</span></span>  
  
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
  
### <a name="to-remove-all-items"></a><span data-ttu-id="28d50-118">Odebrání všech položek</span><span class="sxs-lookup"><span data-stu-id="28d50-118">To remove all items</span></span>  
  
1. <span data-ttu-id="28d50-119">Chcete-li odebrat všechny položky z kolekce, zavolejte metodu `Clear`:</span><span class="sxs-lookup"><span data-stu-id="28d50-119">Call the `Clear` method to remove all items from the collection:</span></span>  
  
    ```vb  
    ListBox1.Items.Clear()  
    ```  
  
    ```csharp  
    listBox1.Items.Clear();  
    ```  
  
    ```cpp  
    listBox1->Items->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="28d50-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="28d50-120">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms.CheckedListBox>
- [<span data-ttu-id="28d50-121">Postupy: Řazení obsahu ovládacího prvku ComboBox, ListBox nebo CheckedListBox z Windows Forms</span><span class="sxs-lookup"><span data-stu-id="28d50-121">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [<span data-ttu-id="28d50-122">Kdy použít prvek Windows Forms ComboBox místo prvku ListBox</span><span class="sxs-lookup"><span data-stu-id="28d50-122">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [<span data-ttu-id="28d50-123">Ovládací prvky Windows Forms používané k výpisu možností</span><span class="sxs-lookup"><span data-stu-id="28d50-123">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
