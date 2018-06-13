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
ms.openlocfilehash: f9319ffe5e9c4f06565648565ce21dec6fc672f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527184"
---
# <a name="how-to-add-and-remove-items-from-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="82473-102">Postupy: Přidání a odebrání položek z ovládacích prvků Windows Forms ComboBox, ListBox nebo CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="82473-102">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="82473-103">Položky lze přidat do Windows Forms pole se seznamem pole se seznamem, nebo zaškrtnutí pole se seznamem v mnoha různými způsoby, protože tyto ovládací prvky mohou být vázány na celou řadu zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="82473-103">Items can be added to a Windows Forms combo box, list box, or checked list box in a variety of ways, because these controls can be bound to a variety of data sources.</span></span> <span data-ttu-id="82473-104">Toto téma však představuje nejjednodušší způsob a vyžaduje žádná vazba na data.</span><span class="sxs-lookup"><span data-stu-id="82473-104">However, this topic demonstrates the simplest method and requires no data binding.</span></span> <span data-ttu-id="82473-105">Položky zobrazené jsou obvykle řetězce; lze však použít libovolného objektu.</span><span class="sxs-lookup"><span data-stu-id="82473-105">The items displayed are usually strings; however, any object can be used.</span></span> <span data-ttu-id="82473-106">Text, který se zobrazí v ovládacím prvku je hodnoty vrácené objektu `ToString` metoda.</span><span class="sxs-lookup"><span data-stu-id="82473-106">The text that is displayed in the control is the value returned by the object's `ToString` method.</span></span>  
  
### <a name="to-add-items"></a><span data-ttu-id="82473-107">K přidávání položek</span><span class="sxs-lookup"><span data-stu-id="82473-107">To add items</span></span>  
  
1.  <span data-ttu-id="82473-108">Přidejte řetězec nebo objekt do seznamu pomocí `Add` metodu `ObjectCollection` třída.</span><span class="sxs-lookup"><span data-stu-id="82473-108">Add the string or object to the list by using the `Add` method of the `ObjectCollection` class.</span></span> <span data-ttu-id="82473-109">Kolekce odkazuje pomocí `Items` vlastnost:</span><span class="sxs-lookup"><span data-stu-id="82473-109">The collection is referenced using the `Items` property:</span></span>  
  
    ```vb  
    ComboBox1.Items.Add("Tokyo")  
    ```  
  
    ```csharp  
    comboBox1.Items.Add("Tokyo");  
    ```  
  
    ```cpp  
    comboBox1->Items->Add("Tokyo");  
    ```  
  
     - <span data-ttu-id="82473-110">nebo –</span><span class="sxs-lookup"><span data-stu-id="82473-110">or -</span></span>  
  
2.  <span data-ttu-id="82473-111">Vložte řetězec nebo objekt na požadované místo v seznamu pomocí `Insert` metoda:</span><span class="sxs-lookup"><span data-stu-id="82473-111">Insert the string or object at the desired point in the list with the `Insert` method:</span></span>  
  
    ```vb  
    CheckedListBox1.Items.Insert(0, "Copenhagen")  
    ```  
  
    ```csharp  
    checkedListBox1.Items.Insert(0, "Copenhagen");  
    ```  
  
    ```cpp  
    checkedListBox1->Items->Insert(0, "Copenhagen");  
    ```  
  
     - <span data-ttu-id="82473-112">nebo –</span><span class="sxs-lookup"><span data-stu-id="82473-112">or -</span></span>  
  
3.  <span data-ttu-id="82473-113">Přiřadit celé pole na `Items` kolekce:</span><span class="sxs-lookup"><span data-stu-id="82473-113">Assign an entire array to the `Items` collection:</span></span>  
  
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
  
### <a name="to-remove-an-item"></a><span data-ttu-id="82473-114">Pokud chcete odebrat položku</span><span class="sxs-lookup"><span data-stu-id="82473-114">To remove an item</span></span>  
  
1.  <span data-ttu-id="82473-115">Volání `Remove` nebo `RemoveAt` metoda odstranit položky.</span><span class="sxs-lookup"><span data-stu-id="82473-115">Call the `Remove` or `RemoveAt` method to delete items.</span></span>  
  
     <span data-ttu-id="82473-116">`Remove` má jeden argument, který určuje položka pro odstranění.`RemoveAt`</span><span class="sxs-lookup"><span data-stu-id="82473-116">`Remove` has one argument that specifies the item to remove.`RemoveAt`</span></span> <span data-ttu-id="82473-117">Odebere položku se zadané číslo indexu.</span><span class="sxs-lookup"><span data-stu-id="82473-117">removes the item with the specified index number.</span></span>  
  
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
  
### <a name="to-remove-all-items"></a><span data-ttu-id="82473-118">Chcete-li odebrat všechny položky</span><span class="sxs-lookup"><span data-stu-id="82473-118">To remove all items</span></span>  
  
1.  <span data-ttu-id="82473-119">Volání `Clear` metoda odebrat všechny položky z kolekce:</span><span class="sxs-lookup"><span data-stu-id="82473-119">Call the `Clear` method to remove all items from the collection:</span></span>  
  
    ```vb  
    ListBox1.Items.Clear()  
    ```  
  
    ```csharp  
    listBox1.Items.Clear();  
    ```  
  
    ```cpp  
    listBox1->Items->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="82473-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="82473-120">See Also</span></span>  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 <xref:System.Windows.Forms.CheckedListBox>  
 [<span data-ttu-id="82473-121">Postupy: Řazení obsahu ovládacího prvku ComboBox, ListBox nebo CheckedListBox z Windows Forms</span><span class="sxs-lookup"><span data-stu-id="82473-121">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)  
 [<span data-ttu-id="82473-122">Kdy použít prvek Windows Forms ComboBox místo prvku ListBox</span><span class="sxs-lookup"><span data-stu-id="82473-122">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)  
 [<span data-ttu-id="82473-123">Ovládací prvky Windows Forms používané k výpisu možností</span><span class="sxs-lookup"><span data-stu-id="82473-123">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
