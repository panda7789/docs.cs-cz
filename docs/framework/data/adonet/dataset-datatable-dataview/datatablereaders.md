---
title: DataTableReaders
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: 1559cde9cb786ccb2baf920347064b8b28d472c3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785341"
---
# <a name="datatablereaders"></a><span data-ttu-id="f5325-102">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="f5325-102">DataTableReaders</span></span>
<span data-ttu-id="f5325-103">Zobrazí obsah <xref:System.Data.DataTable> nebo<xref:System.Data.DataSet> ve formě jedné nebo více sad výsledků pouze pro čtení, které jsou jen pro čtení. <xref:System.Data.DataTableReader></span><span class="sxs-lookup"><span data-stu-id="f5325-103">The <xref:System.Data.DataTableReader> presents the contents of a <xref:System.Data.DataTable> or a <xref:System.Data.DataSet> in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="f5325-104">Když vytvoříte **třídu DataTableReader** z **objektu DataTable**, výsledný objekt **DataTableReader** obsahuje jednu sadu výsledků se stejnými daty jako **objekt DataTable** , ze kterého byla vytvořena, s výjimkou řádků, které byly označeny jako odstraňování.</span><span class="sxs-lookup"><span data-stu-id="f5325-104">When you create a **DataTableReader** from a **DataTable**, the resulting **DataTableReader** object contains one result set with the same data as the **DataTable** from which it was created, except for any rows that have been marked as deleted.</span></span> <span data-ttu-id="f5325-105">Sloupce se zobrazí ve stejném pořadí jako v původním **objektu DataTable**.</span><span class="sxs-lookup"><span data-stu-id="f5325-105">The columns appear in the same order as in the original **DataTable**.</span></span>  
  
 <span data-ttu-id="f5325-106">**Třída DataTableReader** může obsahovat více sad výsledků, pokud byla vytvořena voláním <xref:System.Data.DataSet.CreateDataReader%2A>.</span><span class="sxs-lookup"><span data-stu-id="f5325-106">A **DataTableReader** may contain multiple result sets if it was created by calling <xref:System.Data.DataSet.CreateDataReader%2A>.</span></span> <span data-ttu-id="f5325-107">Výsledky jsou ve stejném pořadí jako datové **tabulky** v <xref:System.Data.DataSet.Tables%2A> kolekci objektu **DataSet** .</span><span class="sxs-lookup"><span data-stu-id="f5325-107">The results are in the same order as the **DataTables** in the **DataSet** object's <xref:System.Data.DataSet.Tables%2A> collection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f5325-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f5325-108">In This Section</span></span>  
 [<span data-ttu-id="f5325-109">Vytvoření čtečky dat</span><span class="sxs-lookup"><span data-stu-id="f5325-109">Creating a DataReader</span></span>](creating-a-datareader.md)  
 <span data-ttu-id="f5325-110">Popisuje, jak vytvořit objekt **DataTableReader** .</span><span class="sxs-lookup"><span data-stu-id="f5325-110">Discusses how to create a **DataTableReader** object.</span></span>  
  
 [<span data-ttu-id="f5325-111">Navigace v datových tabulkách</span><span class="sxs-lookup"><span data-stu-id="f5325-111">Navigating DataTables</span></span>](navigating-datatables.md)  
 <span data-ttu-id="f5325-112">Popisuje použití metody **Read** k přesunu obsahu pro **třídu DataTableReader**.</span><span class="sxs-lookup"><span data-stu-id="f5325-112">Describes the use of the **Read** method to move through the contents of a **DataTableReader**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5325-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f5325-113">See also</span></span>

- [<span data-ttu-id="f5325-114">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f5325-114">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="f5325-115">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f5325-115">ADO.NET Overview</span></span>](../ado-net-overview.md)
