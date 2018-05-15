---
title: Navigace DataTables
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
ms.openlocfilehash: 3bd10694512e828354254588361cc009aac6602f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="navigating-datatables"></a><span data-ttu-id="f651e-102">Navigace DataTables</span><span class="sxs-lookup"><span data-stu-id="f651e-102">Navigating DataTables</span></span>
<span data-ttu-id="f651e-103"><xref:System.Data.DataTableReader> Získává obsah jedné nebo více <xref:System.Data.DataTable> objekty ve formě jednoho nebo více sad výsledků dotazu jen pro čtení, pouze pro předávání.</span><span class="sxs-lookup"><span data-stu-id="f651e-103">The <xref:System.Data.DataTableReader> obtains the contents of one or more <xref:System.Data.DataTable> objects in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="f651e-104">A <xref:System.Data.DataTableReader> může obsahovat více sad výsledků dotazu, pokud je vytvořen pomocí <xref:System.Data.DataSet.CreateDataReader%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="f651e-104">A <xref:System.Data.DataTableReader> may contain multiple result sets if it is created by using the <xref:System.Data.DataSet.CreateDataReader%2A> method.</span></span> <span data-ttu-id="f651e-105">Pokud je více než jednu sadu výsledků <xref:System.Data.DataTableReader.NextResult%2A> metoda Posune kurzor na další sadu výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="f651e-105">When there is more than one result set, the <xref:System.Data.DataTableReader.NextResult%2A> method advances the cursor to the next result set.</span></span> <span data-ttu-id="f651e-106">Toto je pouze pro předávání procesu.</span><span class="sxs-lookup"><span data-stu-id="f651e-106">This is a forward-only process.</span></span> <span data-ttu-id="f651e-107">Není možné vrátit k předchozí sadu výsledků.</span><span class="sxs-lookup"><span data-stu-id="f651e-107">It is not possible to return to a previous result set.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f651e-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="f651e-108">Example</span></span>  
 <span data-ttu-id="f651e-109">V následujícím příkladu `TestConstructor` metoda vytvoří dvě <xref:System.Data.DataTable> instance.</span><span class="sxs-lookup"><span data-stu-id="f651e-109">In the following example, the `TestConstructor` method creates two <xref:System.Data.DataTable> instances.</span></span> <span data-ttu-id="f651e-110">K prokázání tohoto konstruktoru pro <xref:System.Data.DataTableReader> třída, ukázka vytvoří novou **třída DataTableReader** podle pole, které obsahuje dvě **DataTables**a provede jednoduchá operace Tisk obsahu z první málo sloupců do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="f651e-110">In order to demonstrate this constructor for the <xref:System.Data.DataTableReader> class, the sample creates a new **DataTableReader** based on an array that contains the two **DataTables**, and performs a simple operation, printing the contents from the first few columns to the console window.</span></span>  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f651e-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="f651e-111">See Also</span></span>  
 [<span data-ttu-id="f651e-112">Čtečky datových tabulek</span><span class="sxs-lookup"><span data-stu-id="f651e-112">DataTableReaders</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 [<span data-ttu-id="f651e-113">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="f651e-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
