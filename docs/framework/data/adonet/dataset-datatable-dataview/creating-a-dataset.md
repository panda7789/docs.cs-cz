---
title: Vytvoření datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
ms.openlocfilehash: d496167b7bce31491402414c43ae0bcdee423b89
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786503"
---
# <a name="creating-a-dataset"></a><span data-ttu-id="f69fe-102">Vytvoření datové sady</span><span class="sxs-lookup"><span data-stu-id="f69fe-102">Creating a DataSet</span></span>
<span data-ttu-id="f69fe-103">Vytvoříte instanci <xref:System.Data.DataSet> <xref:System.Data.DataSet> voláním konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="f69fe-103">You create an instance of a <xref:System.Data.DataSet> by calling the <xref:System.Data.DataSet> constructor.</span></span> <span data-ttu-id="f69fe-104">Volitelně můžete zadat argument name.</span><span class="sxs-lookup"><span data-stu-id="f69fe-104">Optionally specify a name argument.</span></span> <span data-ttu-id="f69fe-105">Pokud neurčíte název pro <xref:System.Data.DataSet>, název je nastaven na "NewDataSet".</span><span class="sxs-lookup"><span data-stu-id="f69fe-105">If you do not specify a name for the <xref:System.Data.DataSet>, the name is set to "NewDataSet".</span></span>  
  
 <span data-ttu-id="f69fe-106">Můžete také vytvořit novou <xref:System.Data.DataSet> na základě existujícího. <xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="f69fe-106">You can also create a new <xref:System.Data.DataSet> based on an existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="f69fe-107"><xref:System.Data.DataSet> Nový může být přesná kopie stávajícího <xref:System.Data.DataSet> <xref:System.Data.DataSet> ; klon, který kopíruje relační strukturu nebo schéma, ale neobsahuje žádná data z existujících <xref:System.Data.DataSet>nebo podmnožinu <xref:System.Data.DataSet>, obsahuje pouze upravené řádky z existující <xref:System.Data.DataSet> <xref:System.Data.DataSet.GetChanges%2A> pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="f69fe-107">The new <xref:System.Data.DataSet> can be an exact copy of the existing <xref:System.Data.DataSet>; a clone of the <xref:System.Data.DataSet> that copies the relational structure or schema but that does not contain any of the data from the existing <xref:System.Data.DataSet>; or a subset of the <xref:System.Data.DataSet>, containing only the modified rows from the existing <xref:System.Data.DataSet> using the <xref:System.Data.DataSet.GetChanges%2A> method.</span></span> <span data-ttu-id="f69fe-108">Další informace najdete v tématu [kopírování obsahu datové sady](copying-dataset-contents.md).</span><span class="sxs-lookup"><span data-stu-id="f69fe-108">For more information, see [Copying DataSet Contents](copying-dataset-contents.md).</span></span>  
  
 <span data-ttu-id="f69fe-109">Následující příklad kódu ukazuje, jak vytvořit instanci <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="f69fe-109">The following code example demonstrates how to construct an instance of a <xref:System.Data.DataSet>.</span></span>  
  
```vb  
Dim customerOrders As DataSet = New DataSet("CustomerOrders")  
```  
  
```csharp  
DataSet customerOrders = new DataSet("CustomerOrders");  
```  
  
## <a name="see-also"></a><span data-ttu-id="f69fe-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f69fe-110">See also</span></span>

- [<span data-ttu-id="f69fe-111">Naplnění datové sady z adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="f69fe-111">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)
- [<span data-ttu-id="f69fe-112">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="f69fe-112">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="f69fe-113">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f69fe-113">ADO.NET Overview</span></span>](../ado-net-overview.md)
