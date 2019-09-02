---
title: Odstranění datového řádku
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
ms.openlocfilehash: 46109ee1781b8b509df87b4203c51a55b9f596ae
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205102"
---
# <a name="datarow-deletion"></a><span data-ttu-id="cd8ff-102">Odstranění datového řádku</span><span class="sxs-lookup"><span data-stu-id="cd8ff-102">DataRow Deletion</span></span>
<span data-ttu-id="cd8ff-103">Existují dvě metody, které <xref:System.Data.DataRow> lze použít k odstranění objektu <xref:System.Data.DataTable> z objektu: <xref:System.Data.DataRow.Delete%2A> metodu <xref:System.Data.DataRowCollection> **Remove** objektu a metodu objektu **DataRow** .</span><span class="sxs-lookup"><span data-stu-id="cd8ff-103">There are two methods you can use to delete a <xref:System.Data.DataRow> object from a <xref:System.Data.DataTable> object: the **Remove** method of the <xref:System.Data.DataRowCollection> object, and the <xref:System.Data.DataRow.Delete%2A> method of the **DataRow** object.</span></span> <span data-ttu-id="cd8ff-104">Zatímco metoda odstraní **objekt DataRow** z **kolekci DataRowCollection**, <xref:System.Data.DataRow.Delete%2A> metoda označí řádek pouze pro odstranění. <xref:System.Data.DataRowCollection.Remove%2A></span><span class="sxs-lookup"><span data-stu-id="cd8ff-104">Whereas the <xref:System.Data.DataRowCollection.Remove%2A> method deletes a **DataRow** from the **DataRowCollection**, the <xref:System.Data.DataRow.Delete%2A> method only marks the row for deletion.</span></span> <span data-ttu-id="cd8ff-105">Ke skutečnému odebrání dojde, když aplikace zavolá metodu **AcceptChanges** .</span><span class="sxs-lookup"><span data-stu-id="cd8ff-105">The actual removal occurs when the application calls the **AcceptChanges** method.</span></span> <span data-ttu-id="cd8ff-106">Pomocí nástroje <xref:System.Data.DataRow.Delete%2A>můžete programově ověřit, které řádky jsou označené k odstranění, než je skutečně odeberete.</span><span class="sxs-lookup"><span data-stu-id="cd8ff-106">By using <xref:System.Data.DataRow.Delete%2A>, you can programmatically check which rows are marked for deletion before actually removing them.</span></span> <span data-ttu-id="cd8ff-107">Když je řádek označený k odstranění, jeho <xref:System.Data.DataRow.RowState%2A> vlastnost je nastavena na. <xref:System.Data.DataRow.Delete%2A></span><span class="sxs-lookup"><span data-stu-id="cd8ff-107">When a row is marked for deletion, its <xref:System.Data.DataRow.RowState%2A> property is set to <xref:System.Data.DataRow.Delete%2A>.</span></span>  
  
 <span data-ttu-id="cd8ff-108">Ani ani <xref:System.Data.DataRowCollection.Remove%2A> by neměl být volán ve <xref:System.Data.DataRowCollection> smyčce foreach při iteraci objektu. <xref:System.Data.DataRow.Delete%2A></span><span class="sxs-lookup"><span data-stu-id="cd8ff-108">Neither <xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> should be called in a foreach loop while iterating through a <xref:System.Data.DataRowCollection> object.</span></span> <span data-ttu-id="cd8ff-109"><xref:System.Data.DataRow.Delete%2A>ani <xref:System.Data.DataRowCollection.Remove%2A> nezmění stav kolekce.</span><span class="sxs-lookup"><span data-stu-id="cd8ff-109"><xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> modify the state of the collection.</span></span>  
  
 <span data-ttu-id="cd8ff-110"><xref:System.Data.DataSet> Při použití objektu nebo **DataTable** ve spojení s **metodou DataAdapter** a relačním zdrojem dat odeberte řádek pomocí metody **Delete** objektu **DataRow** .</span><span class="sxs-lookup"><span data-stu-id="cd8ff-110">When using a <xref:System.Data.DataSet> or **DataTable** in conjunction with a **DataAdapter** and a relational data source, use the **Delete** method of the **DataRow** to remove the row.</span></span> <span data-ttu-id="cd8ff-111">Metoda **Delete** označí řádek jako **Odstraněný** v **datové sadě** nebo **DataTable** , ale neodebere jej.</span><span class="sxs-lookup"><span data-stu-id="cd8ff-111">The **Delete** method marks the row as **Deleted** in the **DataSet** or **DataTable** but does not remove it.</span></span> <span data-ttu-id="cd8ff-112">Místo toho, když modul **DataAdapter** nalezne řádek označený jako **Odstraněný**, provede jeho metodu **DeleteCommand** k odstranění řádku ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="cd8ff-112">Instead, when the **DataAdapter** encounters a row marked as **Deleted**, it executes its **DeleteCommand** method to delete the row at the data source.</span></span> <span data-ttu-id="cd8ff-113">Řádek je pak možné trvale odebrat pomocí metody **AcceptChanges** .</span><span class="sxs-lookup"><span data-stu-id="cd8ff-113">The row can then be permanently removed using the **AcceptChanges** method.</span></span> <span data-ttu-id="cd8ff-114">Použijete-li příkaz **Remove** k odstranění řádku, řádek bude z tabulky zcela odebrán, ale objekt **DataAdapter** neodstraní řádek ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="cd8ff-114">If you use **Remove** to delete the row, the row is removed entirely from the table, but the **DataAdapter** will not delete the row at the data source.</span></span>  
  
 <span data-ttu-id="cd8ff-115">Metoda **Remove** **kolekci DataRowCollection** přebírá **objekt DataRow** jako argument a odebírá jej z kolekce, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="cd8ff-115">The **Remove** method of the **DataRowCollection** takes a **DataRow** as an argument and removes it from the collection, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 <span data-ttu-id="cd8ff-116">Naopak následující příklad ukazuje, jak zavolat metodu **Delete** na **objekt DataRow** , aby změnila její **RowState** na hodnotu **Deleted**.</span><span class="sxs-lookup"><span data-stu-id="cd8ff-116">In contrast, the following example demonstrates how to call the **Delete** method on a **DataRow** to change its **RowState** to **Deleted**.</span></span>  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 <span data-ttu-id="cd8ff-117">Pokud je řádek označen pro odstranění a zavoláte metodu **AcceptChanges** objektu **DataTable** , řádek je odebrán z **objektu DataTable**.</span><span class="sxs-lookup"><span data-stu-id="cd8ff-117">If a row is marked for deletion and you call the **AcceptChanges** method of the **DataTable** object, the row is removed from the **DataTable**.</span></span> <span data-ttu-id="cd8ff-118">Naopak pokud voláte **RejectChanges**, **RowState** řádku se vrátí k tomu, co bylo předtím označeno jako odstraněné.</span><span class="sxs-lookup"><span data-stu-id="cd8ff-118">In contrast, if you call **RejectChanges**, the **RowState** of the row reverts to what it was before being marked as **Deleted**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cd8ff-119">Pokud se **přidá** **RowState** objektu **DataRow** , znamená to, že se právě přidal do tabulky a pak je označený jako **Odstraněný**, odebere se z tabulky.</span><span class="sxs-lookup"><span data-stu-id="cd8ff-119">If the **RowState** of a **DataRow** is **Added**, meaning it has just been added to the table, and it is then marked as **Deleted**, it is removed from the table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd8ff-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cd8ff-120">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="cd8ff-121">Manipulace s daty v datové tabulce</span><span class="sxs-lookup"><span data-stu-id="cd8ff-121">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="cd8ff-122">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="cd8ff-122">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
