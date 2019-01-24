---
title: Odstranění datového řádku
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
ms.openlocfilehash: 69bdf4d23463cc07259a2b1de6b9efaa78f0f0de
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54593755"
---
# <a name="datarow-deletion"></a><span data-ttu-id="309f3-102">Odstranění datového řádku</span><span class="sxs-lookup"><span data-stu-id="309f3-102">DataRow Deletion</span></span>
<span data-ttu-id="309f3-103">Existují dvě metody, které slouží k odstranění <xref:System.Data.DataRow> objektu z <xref:System.Data.DataTable> objektu: **odebrat** metodu <xref:System.Data.DataRowCollection> objektu a <xref:System.Data.DataRow.Delete%2A> metodu **DataRow**objektu.</span><span class="sxs-lookup"><span data-stu-id="309f3-103">There are two methods you can use to delete a <xref:System.Data.DataRow> object from a <xref:System.Data.DataTable> object: the **Remove** method of the <xref:System.Data.DataRowCollection> object, and the <xref:System.Data.DataRow.Delete%2A> method of the **DataRow** object.</span></span> <span data-ttu-id="309f3-104">Vzhledem k tomu <xref:System.Data.DataRowCollection.Remove%2A> metoda odstraní **DataRow** z **kolekci DataRowCollection**, <xref:System.Data.DataRow.Delete%2A> metoda pouze označuje řádek pro odstranění.</span><span class="sxs-lookup"><span data-stu-id="309f3-104">Whereas the <xref:System.Data.DataRowCollection.Remove%2A> method deletes a **DataRow** from the **DataRowCollection**, the <xref:System.Data.DataRow.Delete%2A> method only marks the row for deletion.</span></span> <span data-ttu-id="309f3-105">Skutečné odebrání dochází, když aplikace volá **metoda AcceptChanges** metody.</span><span class="sxs-lookup"><span data-stu-id="309f3-105">The actual removal occurs when the application calls the **AcceptChanges** method.</span></span> <span data-ttu-id="309f3-106">S použitím <xref:System.Data.DataRow.Delete%2A>, můžete prostřednictvím kódu programu zkontrolovat, které řádky jsou označená k odstranění předtím než je ve skutečnosti odeberete.</span><span class="sxs-lookup"><span data-stu-id="309f3-106">By using <xref:System.Data.DataRow.Delete%2A>, you can programmatically check which rows are marked for deletion before actually removing them.</span></span> <span data-ttu-id="309f3-107">Pokud je řádek označený k odstranění, jeho <xref:System.Data.DataRow.RowState%2A> je nastavena na <xref:System.Data.DataRow.Delete%2A>.</span><span class="sxs-lookup"><span data-stu-id="309f3-107">When a row is marked for deletion, its <xref:System.Data.DataRow.RowState%2A> property is set to <xref:System.Data.DataRow.Delete%2A>.</span></span>  
  
 <span data-ttu-id="309f3-108">Ani <xref:System.Data.DataRow.Delete%2A> ani <xref:System.Data.DataRowCollection.Remove%2A> by měla být volána ve smyčce foreach během iterace <xref:System.Data.DataRowCollection> objektu.</span><span class="sxs-lookup"><span data-stu-id="309f3-108">Neither <xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> should be called in a foreach loop while iterating through a <xref:System.Data.DataRowCollection> object.</span></span> <span data-ttu-id="309f3-109"><xref:System.Data.DataRow.Delete%2A> ani <xref:System.Data.DataRowCollection.Remove%2A> upravují stav kolekce.</span><span class="sxs-lookup"><span data-stu-id="309f3-109"><xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> modify the state of the collection.</span></span>  
  
 <span data-ttu-id="309f3-110">Při použití <xref:System.Data.DataSet> nebo **DataTable** ve spojení s **DataAdapter** a zdroje relačních dat, použijte **odstranit** metodu  **Objekt DataRow** odebrat řádek.</span><span class="sxs-lookup"><span data-stu-id="309f3-110">When using a <xref:System.Data.DataSet> or **DataTable** in conjunction with a **DataAdapter** and a relational data source, use the **Delete** method of the **DataRow** to remove the row.</span></span> <span data-ttu-id="309f3-111">**Odstranit** metoda řádek bude označen jako **odstraněné** v **datovou sadu** nebo **DataTable** , ale neodstraní ho.</span><span class="sxs-lookup"><span data-stu-id="309f3-111">The **Delete** method marks the row as **Deleted** in the **DataSet** or **DataTable** but does not remove it.</span></span> <span data-ttu-id="309f3-112">Místo toho, když **DataAdapter** zaznamená řádek označený jako **odstraněné**, se provede jeho **událost DeleteCommand** metoda odstraňte řádek ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="309f3-112">Instead, when the **DataAdapter** encounters a row marked as **Deleted**, it executes its **DeleteCommand** method to delete the row at the data source.</span></span> <span data-ttu-id="309f3-113">Na řádku můžete poté trvale odebrány **metoda AcceptChanges** metody.</span><span class="sxs-lookup"><span data-stu-id="309f3-113">The row can then be permanently removed using the **AcceptChanges** method.</span></span> <span data-ttu-id="309f3-114">Pokud používáte **odebrat** odstranění řádku, řádku je zcela odeberou z tabulky, ale **DataAdapter** nedojde k odstranění řádků ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="309f3-114">If you use **Remove** to delete the row, the row is removed entirely from the table, but the **DataAdapter** will not delete the row at the data source.</span></span>  
  
 <span data-ttu-id="309f3-115">**Odebrat** metodu **kolekci DataRowCollection** přijímá **DataRow** jako argument a odebere ji z kolekce, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="309f3-115">The **Remove** method of the **DataRowCollection** takes a **DataRow** as an argument and removes it from the collection, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 <span data-ttu-id="309f3-116">Naproti tomu následující příklad ukazuje, jak volat **odstranit** metodu na **DataRow** změnit jeho **RowState** k **odstraněné** .</span><span class="sxs-lookup"><span data-stu-id="309f3-116">In contrast, the following example demonstrates how to call the **Delete** method on a **DataRow** to change its **RowState** to **Deleted**.</span></span>  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 <span data-ttu-id="309f3-117">Pokud je řádek označený k odstranění a zavoláte **metoda AcceptChanges** metodu **DataTable** objekt řádku je odebrán z **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="309f3-117">If a row is marked for deletion and you call the **AcceptChanges** method of the **DataTable** object, the row is removed from the **DataTable**.</span></span> <span data-ttu-id="309f3-118">Naopak pokud zavoláte **RejectChanges**, **RowState** řádku, který se vrátí do byl před jako **odstraněné**.</span><span class="sxs-lookup"><span data-stu-id="309f3-118">In contrast, if you call **RejectChanges**, the **RowState** of the row reverts to what it was before being marked as **Deleted**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="309f3-119">Pokud **RowState** z **DataRow** je **přidané**, znamená to zrovna došlo k přidání do tabulky a pak je označen jako **odstraněné**, je odebrat z tabulky.</span><span class="sxs-lookup"><span data-stu-id="309f3-119">If the **RowState** of a **DataRow** is **Added**, meaning it has just been added to the table, and it is then marked as **Deleted**, it is removed from the table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="309f3-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="309f3-120">See also</span></span>
- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="309f3-121">Manipulace s daty v datové tabulce</span><span class="sxs-lookup"><span data-stu-id="309f3-121">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="309f3-122">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="309f3-122">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
