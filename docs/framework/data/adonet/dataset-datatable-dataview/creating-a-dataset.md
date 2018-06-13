---
title: Vytvoření datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
ms.openlocfilehash: 3c48b430b1a087a79db37398b2c68014b8077c55
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755962"
---
# <a name="creating-a-dataset"></a><span data-ttu-id="b70eb-102">Vytvoření datové sady</span><span class="sxs-lookup"><span data-stu-id="b70eb-102">Creating a DataSet</span></span>
<span data-ttu-id="b70eb-103">Vytvoření instance <xref:System.Data.DataSet> voláním <xref:System.Data.DataSet> konstruktor.</span><span class="sxs-lookup"><span data-stu-id="b70eb-103">You create an instance of a <xref:System.Data.DataSet> by calling the <xref:System.Data.DataSet> constructor.</span></span> <span data-ttu-id="b70eb-104">Volitelně můžete zadáte název argument.</span><span class="sxs-lookup"><span data-stu-id="b70eb-104">Optionally specify a name argument.</span></span> <span data-ttu-id="b70eb-105">Pokud nezadáte název <xref:System.Data.DataSet>, název nastavena na "NewDataSet".</span><span class="sxs-lookup"><span data-stu-id="b70eb-105">If you do not specify a name for the <xref:System.Data.DataSet>, the name is set to "NewDataSet".</span></span>  
  
 <span data-ttu-id="b70eb-106">Můžete také vytvořit novou <xref:System.Data.DataSet> na základě existujícího <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="b70eb-106">You can also create a new <xref:System.Data.DataSet> based on an existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="b70eb-107">Nové <xref:System.Data.DataSet> lze přesnou kopii existující <xref:System.Data.DataSet>; klon <xref:System.Data.DataSet> který zkopíruje relační struktury nebo schématu, ale který neobsahuje žádná data z existující <xref:System.Data.DataSet>; nebo podmnožinu <xref:System.Data.DataSet>, obsahující pouze změněné řádky z existující <xref:System.Data.DataSet> pomocí <xref:System.Data.DataSet.GetChanges%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="b70eb-107">The new <xref:System.Data.DataSet> can be an exact copy of the existing <xref:System.Data.DataSet>; a clone of the <xref:System.Data.DataSet> that copies the relational structure or schema but that does not contain any of the data from the existing <xref:System.Data.DataSet>; or a subset of the <xref:System.Data.DataSet>, containing only the modified rows from the existing <xref:System.Data.DataSet> using the <xref:System.Data.DataSet.GetChanges%2A> method.</span></span> <span data-ttu-id="b70eb-108">Další informace najdete v tématu [kopírování obsahu datovou sadu](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md).</span><span class="sxs-lookup"><span data-stu-id="b70eb-108">For more information, see [Copying DataSet Contents](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md).</span></span>  
  
 <span data-ttu-id="b70eb-109">Následující příklad kódu ukazuje, jak vytvořit instanci <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="b70eb-109">The following code example demonstrates how to construct an instance of a <xref:System.Data.DataSet>.</span></span>  
  
```vb  
Dim customerOrders As DataSet = New DataSet("CustomerOrders")  
```  
  
```csharp  
DataSet customerOrders = new DataSet("CustomerOrders");  
```  
  
## <a name="see-also"></a><span data-ttu-id="b70eb-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="b70eb-110">See Also</span></span>  
 [<span data-ttu-id="b70eb-111">Naplnění datové sady z adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="b70eb-111">Populating a DataSet from a DataAdapter</span></span>](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 [<span data-ttu-id="b70eb-112">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="b70eb-112">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="b70eb-113">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="b70eb-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
