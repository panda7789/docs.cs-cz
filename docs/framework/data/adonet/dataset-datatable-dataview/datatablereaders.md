---
title: DataTableReaders
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: a790335a25327563e3dab6093449345b99afd048
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607862"
---
# <a name="datatablereaders"></a><span data-ttu-id="834b2-102">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="834b2-102">DataTableReaders</span></span>
<span data-ttu-id="834b2-103"><xref:System.Data.DataTableReader> Představuje obsah <xref:System.Data.DataTable> nebo <xref:System.Data.DataSet> ve formě nejmíň jeden výsledek jen pro čtení, dopředné nastaví.</span><span class="sxs-lookup"><span data-stu-id="834b2-103">The <xref:System.Data.DataTableReader> presents the contents of a <xref:System.Data.DataTable> or a <xref:System.Data.DataSet> in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="834b2-104">Při vytváření **třída DataTableReader** z **DataTable**, výsledná **třída DataTableReader** objekt obsahuje sadu s stejná data jako jeden výsledek  **Objekt DataTable** ze které byla vytvořena, s výjimkou všechny řádky, které jsou označené jako odstraněný.</span><span class="sxs-lookup"><span data-stu-id="834b2-104">When you create a **DataTableReader** from a **DataTable**, the resulting **DataTableReader** object contains one result set with the same data as the **DataTable** from which it was created, except for any rows that have been marked as deleted.</span></span> <span data-ttu-id="834b2-105">Sloupce se zobrazí ve stejném pořadí jako původní **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="834b2-105">The columns appear in the same order as in the original **DataTable**.</span></span>  
  
 <span data-ttu-id="834b2-106">A **třída DataTableReader** může obsahovat více sad výsledků dotazu, pokud byl vytvořen voláním <xref:System.Data.DataSet.CreateDataReader%2A>.</span><span class="sxs-lookup"><span data-stu-id="834b2-106">A **DataTableReader** may contain multiple result sets if it was created by calling <xref:System.Data.DataSet.CreateDataReader%2A>.</span></span> <span data-ttu-id="834b2-107">Výsledky jsou ve stejném pořadí jako **DataTables** v **datovou sadu** objektu <xref:System.Data.DataSet.Tables%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="834b2-107">The results are in the same order as the **DataTables** in the **DataSet** object's <xref:System.Data.DataSet.Tables%2A> collection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="834b2-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="834b2-108">In This Section</span></span>  
 [<span data-ttu-id="834b2-109">Vytvoření čtečky dat</span><span class="sxs-lookup"><span data-stu-id="834b2-109">Creating a DataReader</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datareader.md)  
 <span data-ttu-id="834b2-110">Popisuje, jak vytvořit **třída DataTableReader** objektu.</span><span class="sxs-lookup"><span data-stu-id="834b2-110">Discusses how to create a **DataTableReader** object.</span></span>  
  
 [<span data-ttu-id="834b2-111">Navigace v datových tabulkách</span><span class="sxs-lookup"><span data-stu-id="834b2-111">Navigating DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datatables.md)  
 <span data-ttu-id="834b2-112">Popisuje použití **čtení** metoda procházejte obsah **třída DataTableReader**.</span><span class="sxs-lookup"><span data-stu-id="834b2-112">Describes the use of the **Read** method to move through the contents of a **DataTableReader**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="834b2-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="834b2-113">See also</span></span>

- [<span data-ttu-id="834b2-114">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="834b2-114">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="834b2-115">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="834b2-115">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
