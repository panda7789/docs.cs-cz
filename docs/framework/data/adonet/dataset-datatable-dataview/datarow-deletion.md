---
title: Odstranění DataRow
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
ms.openlocfilehash: 128c41e1906b17e7f42458e8a5f1b3d3ec9cc449
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757512"
---
# <a name="datarow-deletion"></a><span data-ttu-id="73752-102">Odstranění DataRow</span><span class="sxs-lookup"><span data-stu-id="73752-102">DataRow Deletion</span></span>
<span data-ttu-id="73752-103">Existují dvě metody, které můžete použít k odstranění <xref:System.Data.DataRow> objektu z <xref:System.Data.DataTable> objektu: **odebrat** metodu <xref:System.Data.DataRowCollection> objekt a <xref:System.Data.DataRow.Delete%2A> metodu **DataRow**objektu.</span><span class="sxs-lookup"><span data-stu-id="73752-103">There are two methods you can use to delete a <xref:System.Data.DataRow> object from a <xref:System.Data.DataTable> object: the **Remove** method of the <xref:System.Data.DataRowCollection> object, and the <xref:System.Data.DataRow.Delete%2A> method of the **DataRow** object.</span></span> <span data-ttu-id="73752-104">Zatímco <xref:System.Data.DataRowCollection.Remove%2A> metoda odstranění **DataRow** z **kolekci DataRowCollection**, <xref:System.Data.DataRow.Delete%2A> metoda pouze označí řádek pro odstranění.</span><span class="sxs-lookup"><span data-stu-id="73752-104">Whereas the <xref:System.Data.DataRowCollection.Remove%2A> method deletes a **DataRow** from the **DataRowCollection**, the <xref:System.Data.DataRow.Delete%2A> method only marks the row for deletion.</span></span> <span data-ttu-id="73752-105">Skutečné odebrání nastane, když aplikace volá **metoda AcceptChanges** metoda.</span><span class="sxs-lookup"><span data-stu-id="73752-105">The actual removal occurs when the application calls the **AcceptChanges** method.</span></span> <span data-ttu-id="73752-106">Pomocí <xref:System.Data.DataRow.Delete%2A>, můžete programově zkontrolovat řádky jsou označena pro odstranění před skutečného odstranění.</span><span class="sxs-lookup"><span data-stu-id="73752-106">By using <xref:System.Data.DataRow.Delete%2A>, you can programmatically check which rows are marked for deletion before actually removing them.</span></span> <span data-ttu-id="73752-107">Když řádek je označena pro odstranění, jeho <xref:System.Data.DataRow.RowState%2A> je nastavena na <xref:System.Data.DataRow.Delete%2A>.</span><span class="sxs-lookup"><span data-stu-id="73752-107">When a row is marked for deletion, its <xref:System.Data.DataRow.RowState%2A> property is set to <xref:System.Data.DataRow.Delete%2A>.</span></span>  
  
 <span data-ttu-id="73752-108">Ani <xref:System.Data.DataRow.Delete%2A> ani <xref:System.Data.DataRowCollection.Remove%2A> by měla být volána v smyčka typu foreach při iterace v rámci <xref:System.Data.DataRowCollection> objektu.</span><span class="sxs-lookup"><span data-stu-id="73752-108">Neither <xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> should be called in a foreach loop while iterating through a <xref:System.Data.DataRowCollection> object.</span></span> <span data-ttu-id="73752-109"><xref:System.Data.DataRow.Delete%2A> ani <xref:System.Data.DataRowCollection.Remove%2A> změnit stav kolekce.</span><span class="sxs-lookup"><span data-stu-id="73752-109"><xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> modify the state of the collection.</span></span>  
  
 <span data-ttu-id="73752-110">Při použití <xref:System.Data.DataSet> nebo **DataTable** ve spojení s **DataAdapter** a zdroje relačních dat, použijte **odstranit** metodu  **DataRow** odebrat řádek.</span><span class="sxs-lookup"><span data-stu-id="73752-110">When using a <xref:System.Data.DataSet> or **DataTable** in conjunction with a **DataAdapter** and a relational data source, use the **Delete** method of the **DataRow** to remove the row.</span></span> <span data-ttu-id="73752-111">**Odstranit** metoda řádek označí jako **odstraněné** v **datovou sadu** nebo **DataTable** ale nedojde k jeho odebrání.</span><span class="sxs-lookup"><span data-stu-id="73752-111">The **Delete** method marks the row as **Deleted** in the **DataSet** or **DataTable** but does not remove it.</span></span> <span data-ttu-id="73752-112">Místo toho, když **DataAdapter** zaznamená řádek označený jako **odstraněné**, se provede jeho **DeleteCommand** metoda k odstranění řádku ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="73752-112">Instead, when the **DataAdapter** encounters a row marked as **Deleted**, it executes its **DeleteCommand** method to delete the row at the data source.</span></span> <span data-ttu-id="73752-113">Řádek se dá pak trvale odebrat pomocí **metoda AcceptChanges** metoda.</span><span class="sxs-lookup"><span data-stu-id="73752-113">The row can then be permanently removed using the **AcceptChanges** method.</span></span> <span data-ttu-id="73752-114">Pokud používáte **odebrat** k odstranění řádku, řádku je zcela odeberou z tabulky, ale **DataAdapter** řádek ve zdroji dat se neodstraní.</span><span class="sxs-lookup"><span data-stu-id="73752-114">If you use **Remove** to delete the row, the row is removed entirely from the table, but the **DataAdapter** will not delete the row at the data source.</span></span>  
  
 <span data-ttu-id="73752-115">**Odebrat** metodu **kolekci DataRowCollection** trvá **DataRow** jako argument a odebere ji z kolekce, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="73752-115">The **Remove** method of the **DataRowCollection** takes a **DataRow** as an argument and removes it from the collection, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 <span data-ttu-id="73752-116">Naproti tomu následující příklad ukazuje, jak volat **odstranit** metodu **DataRow** změnit jeho **RowState** k **odstraněné** .</span><span class="sxs-lookup"><span data-stu-id="73752-116">In contrast, the following example demonstrates how to call the **Delete** method on a **DataRow** to change its **RowState** to **Deleted**.</span></span>  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 <span data-ttu-id="73752-117">Pokud řádek je označena pro odstranění a volání **metoda AcceptChanges** metodu **DataTable** objektu řádek je odebrán z **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="73752-117">If a row is marked for deletion and you call the **AcceptChanges** method of the **DataTable** object, the row is removed from the **DataTable**.</span></span> <span data-ttu-id="73752-118">Naproti tomu při volání **RejectChanges**, **RowState** řádku přejde do stavu, který byl před označit jako **odstraněné**.</span><span class="sxs-lookup"><span data-stu-id="73752-118">In contrast, if you call **RejectChanges**, the **RowState** of the row reverts to what it was before being marked as **Deleted**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="73752-119">Pokud **RowState** z **DataRow** je **Added**, znamená ho právě byl přidán do tabulky, a pak je označen jako **odstraněné**, je Odebere z tabulky.</span><span class="sxs-lookup"><span data-stu-id="73752-119">If the **RowState** of a **DataRow** is **Added**, meaning it has just been added to the table, and it is then marked as **Deleted**, it is removed from the table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73752-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="73752-120">See Also</span></span>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataRowCollection>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="73752-121">Manipulace s daty v datové tabulce</span><span class="sxs-lookup"><span data-stu-id="73752-121">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="73752-122">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="73752-122">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
