---
title: Vytvoření datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
ms.openlocfilehash: 43e2f7a1892459ca96d44350431935493b596a60
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509548"
---
# <a name="creating-a-dataset"></a><span data-ttu-id="0f789-102">Vytvoření datové sady</span><span class="sxs-lookup"><span data-stu-id="0f789-102">Creating a DataSet</span></span>
<span data-ttu-id="0f789-103">Vytvoření instance <xref:System.Data.DataSet> voláním <xref:System.Data.DataSet> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="0f789-103">You create an instance of a <xref:System.Data.DataSet> by calling the <xref:System.Data.DataSet> constructor.</span></span> <span data-ttu-id="0f789-104">Volitelně můžete zadáte název argumentu.</span><span class="sxs-lookup"><span data-stu-id="0f789-104">Optionally specify a name argument.</span></span> <span data-ttu-id="0f789-105">Pokud nezadáte název <xref:System.Data.DataSet>, je název nastavený na "NewDataSet".</span><span class="sxs-lookup"><span data-stu-id="0f789-105">If you do not specify a name for the <xref:System.Data.DataSet>, the name is set to "NewDataSet".</span></span>  
  
 <span data-ttu-id="0f789-106">Můžete také vytvořit novou <xref:System.Data.DataSet> založené na existujícím <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="0f789-106">You can also create a new <xref:System.Data.DataSet> based on an existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="0f789-107">Nové <xref:System.Data.DataSet> může být přesnou kopii existující <xref:System.Data.DataSet>; klon <xref:System.Data.DataSet> , která kopíruje relační struktury nebo schématu, ale která neobsahuje žádný dat z existující <xref:System.Data.DataSet>; nebo podmnožinu <xref:System.Data.DataSet>, obsahující jenom změněné řádky z existující <xref:System.Data.DataSet> pomocí <xref:System.Data.DataSet.GetChanges%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="0f789-107">The new <xref:System.Data.DataSet> can be an exact copy of the existing <xref:System.Data.DataSet>; a clone of the <xref:System.Data.DataSet> that copies the relational structure or schema but that does not contain any of the data from the existing <xref:System.Data.DataSet>; or a subset of the <xref:System.Data.DataSet>, containing only the modified rows from the existing <xref:System.Data.DataSet> using the <xref:System.Data.DataSet.GetChanges%2A> method.</span></span> <span data-ttu-id="0f789-108">Další informace najdete v tématu [kopírování obsahu datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md).</span><span class="sxs-lookup"><span data-stu-id="0f789-108">For more information, see [Copying DataSet Contents](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md).</span></span>  
  
 <span data-ttu-id="0f789-109">Následující příklad kódu ukazuje, jak vytvořit instanci <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="0f789-109">The following code example demonstrates how to construct an instance of a <xref:System.Data.DataSet>.</span></span>  
  
```vb  
Dim customerOrders As DataSet = New DataSet("CustomerOrders")  
```  
  
```csharp  
DataSet customerOrders = new DataSet("CustomerOrders");  
```  
  
## <a name="see-also"></a><span data-ttu-id="0f789-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="0f789-110">See Also</span></span>  
 [<span data-ttu-id="0f789-111">Naplnění datové sady z adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="0f789-111">Populating a DataSet from a DataAdapter</span></span>](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 [<span data-ttu-id="0f789-112">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="0f789-112">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="0f789-113">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="0f789-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
