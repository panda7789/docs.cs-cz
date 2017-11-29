---
title: DataTableReaders
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ed9094a036262bac2e101e7b4268aac2e66a0d10
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="datatablereaders"></a><span data-ttu-id="c9441-102">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="c9441-102">DataTableReaders</span></span>
<span data-ttu-id="c9441-103"><xref:System.Data.DataTableReader> Uvede obsah <xref:System.Data.DataTable> nebo <xref:System.Data.DataSet> ve formě jednoho nebo více jen pro čtení, dopředné výsledek nastaví.</span><span class="sxs-lookup"><span data-stu-id="c9441-103">The <xref:System.Data.DataTableReader> presents the contents of a <xref:System.Data.DataTable> or a <xref:System.Data.DataSet> in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="c9441-104">Při vytváření **třída DataTableReader** z **DataTable**, výsledná **třída DataTableReader** objekt obsahuje jedna sada výsledků s stejná data jako  **DataTable** ze které byla vytvořena, s výjimkou všechny řádky, které byly označeny jako odstraněný.</span><span class="sxs-lookup"><span data-stu-id="c9441-104">When you create a **DataTableReader** from a **DataTable**, the resulting **DataTableReader** object contains one result set with the same data as the **DataTable** from which it was created, except for any rows that have been marked as deleted.</span></span> <span data-ttu-id="c9441-105">Se sloupce zobrazí ve stejném pořadí jako původní **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="c9441-105">The columns appear in the same order as in the original **DataTable**.</span></span>  
  
 <span data-ttu-id="c9441-106">A **třída DataTableReader** může obsahovat více sad výsledků dotazu, pokud byla vytvořena pomocí volání <xref:System.Data.DataSet.CreateDataReader%2A>.</span><span class="sxs-lookup"><span data-stu-id="c9441-106">A **DataTableReader** may contain multiple result sets if it was created by calling <xref:System.Data.DataSet.CreateDataReader%2A>.</span></span> <span data-ttu-id="c9441-107">Výsledky jsou ve stejném pořadí jako **DataTables** v **datovou sadu** objektu <xref:System.Data.DataSet.Tables%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="c9441-107">The results are in the same order as the **DataTables** in the **DataSet** object's <xref:System.Data.DataSet.Tables%2A> collection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c9441-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c9441-108">In This Section</span></span>  
 [<span data-ttu-id="c9441-109">Vytváření DataReader –</span><span class="sxs-lookup"><span data-stu-id="c9441-109">Creating a DataReader</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datareader.md)  
 <span data-ttu-id="c9441-110">Popisuje, jak vytvořit **třída DataTableReader** objektu.</span><span class="sxs-lookup"><span data-stu-id="c9441-110">Discusses how to create a **DataTableReader** object.</span></span>  
  
 [<span data-ttu-id="c9441-111">Navigace DataTables</span><span class="sxs-lookup"><span data-stu-id="c9441-111">Navigating DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datatables.md)  
 <span data-ttu-id="c9441-112">Popisuje použití **čtení** metoda Chcete-li procházet obsah **třída DataTableReader**.</span><span class="sxs-lookup"><span data-stu-id="c9441-112">Describes the use of the **Read** method to move through the contents of a **DataTableReader**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9441-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="c9441-113">See Also</span></span>  
 [<span data-ttu-id="c9441-114">Načítání a upravovat Data v technologii ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c9441-114">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="c9441-115">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="c9441-115">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
