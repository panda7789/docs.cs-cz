---
title: Vytvoření datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
ms.openlocfilehash: 19badb009ebe95c52ab1dbbaef96f280c769553b
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205153"
---
# <a name="creating-a-dataset"></a><span data-ttu-id="596a8-102">Vytvoření datové sady</span><span class="sxs-lookup"><span data-stu-id="596a8-102">Creating a DataSet</span></span>
<span data-ttu-id="596a8-103">Vytvoříte instanci <xref:System.Data.DataSet> <xref:System.Data.DataSet> voláním konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="596a8-103">You create an instance of a <xref:System.Data.DataSet> by calling the <xref:System.Data.DataSet> constructor.</span></span> <span data-ttu-id="596a8-104">Volitelně můžete zadat argument name.</span><span class="sxs-lookup"><span data-stu-id="596a8-104">Optionally specify a name argument.</span></span> <span data-ttu-id="596a8-105">Pokud neurčíte název pro <xref:System.Data.DataSet>, název je nastaven na "NewDataSet".</span><span class="sxs-lookup"><span data-stu-id="596a8-105">If you do not specify a name for the <xref:System.Data.DataSet>, the name is set to "NewDataSet".</span></span>  
  
 <span data-ttu-id="596a8-106">Můžete také vytvořit novou <xref:System.Data.DataSet> na základě existujícího. <xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="596a8-106">You can also create a new <xref:System.Data.DataSet> based on an existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="596a8-107"><xref:System.Data.DataSet> Nový může být přesná kopie stávajícího <xref:System.Data.DataSet> <xref:System.Data.DataSet> ; klon, který kopíruje relační strukturu nebo schéma, ale neobsahuje žádná data z existujících <xref:System.Data.DataSet>nebo podmnožinu <xref:System.Data.DataSet>, obsahuje pouze upravené řádky z existující <xref:System.Data.DataSet> <xref:System.Data.DataSet.GetChanges%2A> pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="596a8-107">The new <xref:System.Data.DataSet> can be an exact copy of the existing <xref:System.Data.DataSet>; a clone of the <xref:System.Data.DataSet> that copies the relational structure or schema but that does not contain any of the data from the existing <xref:System.Data.DataSet>; or a subset of the <xref:System.Data.DataSet>, containing only the modified rows from the existing <xref:System.Data.DataSet> using the <xref:System.Data.DataSet.GetChanges%2A> method.</span></span> <span data-ttu-id="596a8-108">Další informace najdete v tématu [kopírování obsahu datové sady](copying-dataset-contents.md).</span><span class="sxs-lookup"><span data-stu-id="596a8-108">For more information, see [Copying DataSet Contents](copying-dataset-contents.md).</span></span>  
  
 <span data-ttu-id="596a8-109">Následující příklad kódu ukazuje, jak vytvořit instanci <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="596a8-109">The following code example demonstrates how to construct an instance of a <xref:System.Data.DataSet>.</span></span>  
  
```vb  
Dim customerOrders As DataSet = New DataSet("CustomerOrders")  
```  
  
```csharp  
DataSet customerOrders = new DataSet("CustomerOrders");  
```  
  
## <a name="see-also"></a><span data-ttu-id="596a8-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="596a8-110">See also</span></span>

- [<span data-ttu-id="596a8-111">Naplnění datové sady z adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="596a8-111">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)
- [<span data-ttu-id="596a8-112">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="596a8-112">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="596a8-113">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="596a8-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
