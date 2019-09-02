---
title: Úpravy zobrazení dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
ms.openlocfilehash: 0b2bfd1b0490572e78c8ce365491a8d48db87684
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204574"
---
# <a name="modifying-dataviews"></a><span data-ttu-id="0caa3-102">Úpravy zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="0caa3-102">Modifying DataViews</span></span>
<span data-ttu-id="0caa3-103">Pomocí <xref:System.Data.DataView> můžete přidat, odstranit nebo upravit řádky dat v podkladové tabulce.</span><span class="sxs-lookup"><span data-stu-id="0caa3-103">You can use the <xref:System.Data.DataView> to add, delete, or modify rows of data in the underlying table.</span></span> <span data-ttu-id="0caa3-104">Možnost použít zobrazení **DataView** ke změně dat v podkladové tabulce je ovládána nastavením jedné ze tří logických vlastností objektu **DataView**.</span><span class="sxs-lookup"><span data-stu-id="0caa3-104">The ability to use the **DataView** to modify data in the underlying table is controlled by setting one of three Boolean properties of the **DataView**.</span></span> <span data-ttu-id="0caa3-105">Tyto vlastnosti jsou <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A>a <xref:System.Data.DataView.AllowDelete%2A>.</span><span class="sxs-lookup"><span data-stu-id="0caa3-105">These properties are <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A>, and <xref:System.Data.DataView.AllowDelete%2A>.</span></span> <span data-ttu-id="0caa3-106">Ve výchozím nastavení jsou nastaveny na **hodnotu true** .</span><span class="sxs-lookup"><span data-stu-id="0caa3-106">They are set to **true** by default.</span></span>  
  
 <span data-ttu-id="0caa3-107">Pokud má AllowNew **hodnotu true**, <xref:System.Data.DataView.AddNew%2A> můžete k vytvoření nové <xref:System.Data.DataRowView>použít metodu zobrazení **DataView** .</span><span class="sxs-lookup"><span data-stu-id="0caa3-107">If **AllowNew** is **true**, you can use the <xref:System.Data.DataView.AddNew%2A> method of the **DataView** to create a new <xref:System.Data.DataRowView>.</span></span> <span data-ttu-id="0caa3-108">Všimněte si, že nový řádek není ve skutečnosti přidán do <xref:System.Data.DataTable> podkladu <xref:System.Data.DataRowView.EndEdit%2A> , dokud nebude volána metoda **DataRowView** .</span><span class="sxs-lookup"><span data-stu-id="0caa3-108">Note that a new row is not actually added to the underlying <xref:System.Data.DataTable> until the <xref:System.Data.DataRowView.EndEdit%2A> method of the **DataRowView** is called.</span></span> <span data-ttu-id="0caa3-109">Pokud je volána MetodaDataRowView,novýřádekje<xref:System.Data.DataRowView.CancelEdit%2A> zahozen.</span><span class="sxs-lookup"><span data-stu-id="0caa3-109">If the <xref:System.Data.DataRowView.CancelEdit%2A> method of the **DataRowView** is called, the new row is discarded.</span></span> <span data-ttu-id="0caa3-110">Všimněte si také, že v jednu chvíli můžete upravovat jenom jeden **DataRowView** .</span><span class="sxs-lookup"><span data-stu-id="0caa3-110">Note also that you can edit only one **DataRowView** at a time.</span></span> <span data-ttu-id="0caa3-111">Pokud zavoláte metodu **AddNew** nebo **metody BeginEdit** **DataRowView** , zatímco existuje řádek, který čeká na vyřízení, **metodu EndEdit volat** se implicitně volá na nevyřízeném řádku.</span><span class="sxs-lookup"><span data-stu-id="0caa3-111">If you call the **AddNew** or **BeginEdit** method of the **DataRowView** while a pending row exists, **EndEdit** is implicitly called on the pending row.</span></span> <span data-ttu-id="0caa3-112">Při volání **metodu EndEdit volat** jsou změny použity v podkladovém **objektu DataTable** a lze je později potvrdit nebo odmítat pomocí metod **AcceptChanges** nebo **RejectChanges** **objektu DataTable**, **datové sady**nebo  **Objekt DataRow**</span><span class="sxs-lookup"><span data-stu-id="0caa3-112">When **EndEdit** is called, the changes are applied to the underlying **DataTable** and can later be committed or rejected using the **AcceptChanges** or **RejectChanges** methods of the **DataTable**, **DataSet**, or **DataRow** object.</span></span> <span data-ttu-id="0caa3-113">Pokud je AllowNew **false**, je vyvolána výjimka, pokud zavoláte metodu **AddNew** objektu **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="0caa3-113">If **AllowNew** is **false**, an exception is thrown if you call the **AddNew** method of the **DataRowView**.</span></span>  
  
 <span data-ttu-id="0caa3-114">Pokud má AllowEdit **hodnotu true**, můžete upravit obsah objektu **DataRow** prostřednictvím rozhraní **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="0caa3-114">If **AllowEdit** is **true**, you can modify the contents of a **DataRow** via the **DataRowView**.</span></span> <span data-ttu-id="0caa3-115">Změny v podkladovém řádku můžete potvrdit pomocí **DataRowView. metodu EndEdit volat** nebo změny zamítnout pomocí **DataRowView. CancelEdit**.</span><span class="sxs-lookup"><span data-stu-id="0caa3-115">You can confirm changes to the underlying row using **DataRowView.EndEdit** or reject the changes using **DataRowView.CancelEdit**.</span></span> <span data-ttu-id="0caa3-116">Všimněte si, že v jednu chvíli lze upravovat pouze jeden řádek.</span><span class="sxs-lookup"><span data-stu-id="0caa3-116">Note that only one row can be edited at a time.</span></span> <span data-ttu-id="0caa3-117">Pokud zavoláte metody **AddNew** nebo **metody BeginEdit** **DataRowView** , zatímco existuje řádek, který čeká na vyřízení, **metodu EndEdit volat** je implicitně voláno na nevyřízeném řádku.</span><span class="sxs-lookup"><span data-stu-id="0caa3-117">If you call the **AddNew** or **BeginEdit** methods of the **DataRowView** while a pending row exists, **EndEdit** is implicitly called on the pending row.</span></span> <span data-ttu-id="0caa3-118">Když se zavolá **metodu EndEdit volat** , navrhované změny se umístí do **aktuální** verze řádku podkladového objektu **DataRow** a dají se později potvrdit nebo odmítat pomocí metod **AcceptChanges nebo RejectChanges. DataTable**, **DataSet**nebo objekt **DataRow** .</span><span class="sxs-lookup"><span data-stu-id="0caa3-118">When **EndEdit** is called, proposed changes are placed in the **Current** row version of the underlying **DataRow** and can later be committed or rejected using the **AcceptChanges** or **RejectChanges** methods of the **DataTable**, **DataSet**, or **DataRow** object.</span></span> <span data-ttu-id="0caa3-119">Pokud je AllowEdit **false**, je vyvolána výjimka, pokud se pokusíte změnit hodnotu v zobrazení **DataView**.</span><span class="sxs-lookup"><span data-stu-id="0caa3-119">If **AllowEdit** is **false**, an exception is thrown if you attempt to modify a value in the **DataView**.</span></span>  
  
 <span data-ttu-id="0caa3-120">Pokud je upravován existující **DataRowView** , budou události podkladového **objektu DataTable** stále vyvolány navrhovanými změnami.</span><span class="sxs-lookup"><span data-stu-id="0caa3-120">When an existing **DataRowView** is being edited, events of the underlying **DataTable** will still be raised with the proposed changes.</span></span> <span data-ttu-id="0caa3-121">Všimněte si, že pokud **voláte metodu EndEdit volat** nebo **CancelEdit** v podkladovém objektu **DataRow**, budou se nedokončené změny použít nebo zrušeny bez ohledu na to, zda je na **DataRowView**voláno **metodu EndEdit volat** nebo **CancelEdit** .</span><span class="sxs-lookup"><span data-stu-id="0caa3-121">Note that if you call **EndEdit** or **CancelEdit** on the underlying **DataRow**, pending changes will be applied or canceled regardless of whether **EndEdit** or **CancelEdit** is called on the **DataRowView**.</span></span>  
  
 <span data-ttu-id="0caa3-122">Pokud má AllowDelete **hodnotu true**, můžete odstranit řádky z objektu **DataView** pomocí metody **Delete** objektu **DataView** nebo **DataRowView** a řádky jsou odstraněny z podkladového objektu **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="0caa3-122">If **AllowDelete** is **true**, you can delete rows from the **DataView** by using the **Delete** method of the **DataView** or **DataRowView** object, and the rows are deleted from the underlying **DataTable**.</span></span> <span data-ttu-id="0caa3-123">Odstranění později můžete potvrdit nebo odmítnout pomocí příkazu **AcceptChanges** nebo **RejectChanges** v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="0caa3-123">You can later commit or reject the deletes using **AcceptChanges** or **RejectChanges** respectively.</span></span> <span data-ttu-id="0caa3-124">Pokud je AllowDelete **false**, je vyvolána výjimka, pokud zavoláte metodu **Delete** objektu **DataView** nebo **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="0caa3-124">If **AllowDelete** is **false**, an exception is thrown if you call the **Delete** method of the **DataView** or **DataRowView**.</span></span>  
  
 <span data-ttu-id="0caa3-125">Následující příklad kódu deaktivuje použití objektu **DataView** k odstranění řádků a přidá nový řádek do podkladové tabulky pomocí objektu **DataView**.</span><span class="sxs-lookup"><span data-stu-id="0caa3-125">The following code example disables using the **DataView** to delete rows  and adds a new row to the underlying table using the **DataView**.</span></span>  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custView As DataView = custTable.DefaultView  
custView.Sort = "CompanyName"  
  
custView.AllowDelete = False  
  
Dim newDRV As DataRowView = custView.AddNew()  
newDRV("CustomerID") = "ABCDE"  
newDRV("CompanyName") = "ABC Products"  
newDRV.EndEdit()  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
DataView custView = custTable.DefaultView;  
custView.Sort = "CompanyName";  
  
custView.AllowDelete = false;  
  
DataRowView newDRV = custView.AddNew();  
newDRV["CustomerID"] = "ABCDE";  
newDRV["CompanyName"] = "ABC Products";  
newDRV.EndEdit();  
```  
  
## <a name="see-also"></a><span data-ttu-id="0caa3-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0caa3-126">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [<span data-ttu-id="0caa3-127">Zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="0caa3-127">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="0caa3-128">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="0caa3-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
