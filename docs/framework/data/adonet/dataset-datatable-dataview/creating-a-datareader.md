---
title: Vytvoření čtečky dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: 79cb2ce7ffae81aeba9aaca557e37ba566a8370c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784763"
---
# <a name="creating-a-datareader"></a><span data-ttu-id="3ec70-102">Vytvoření čtečky dat</span><span class="sxs-lookup"><span data-stu-id="3ec70-102">Creating a DataReader</span></span>
<span data-ttu-id="3ec70-103"><xref:System.Data.DataTable> <xref:System.Data.DataSet.Tables%2A> Třídy a <xref:System.Data.DataSet>mají metodu<xref:System.Data.DataTable.CreateDataReader%2A> , která vrací<xref:System.Data.DataSet> obsah nebo obsah kolekce objektu jako jednu nebo více sad výsledků pouze pro čtení, které jsou jen pro čtení. <xref:System.Data.DataTable></span><span class="sxs-lookup"><span data-stu-id="3ec70-103">The <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes have a <xref:System.Data.DataTable.CreateDataReader%2A> method that returns the contents of the <xref:System.Data.DataTable> or the contents of the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Tables%2A> collection as one or more read-only, forward-only result sets.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ec70-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="3ec70-104">Example</span></span>  
 <span data-ttu-id="3ec70-105">Následující Konzolová aplikace vytvoří <xref:System.Data.DataTable> instanci.</span><span class="sxs-lookup"><span data-stu-id="3ec70-105">The following console application creates a <xref:System.Data.DataTable> instance.</span></span> <span data-ttu-id="3ec70-106">Příklad předává vyplněný <xref:System.Data.DataTable> postup, který <xref:System.Data.DataTable.CreateDataReader%2A> volá metodu, která prochází výsledky obsaženými v <xref:System.Data.DataTableReader>.</span><span class="sxs-lookup"><span data-stu-id="3ec70-106">The example then passes the filled <xref:System.Data.DataTable> to a procedure that calls the <xref:System.Data.DataTable.CreateDataReader%2A> method, which iterates through the results contained within the <xref:System.Data.DataTableReader>.</span></span>  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 <span data-ttu-id="3ec70-107">V příkladu se zobrazí následující výstup v okně konzoly:</span><span class="sxs-lookup"><span data-stu-id="3ec70-107">The example displays the following output in the console window:</span></span>  
  
```  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a><span data-ttu-id="3ec70-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3ec70-108">See also</span></span>

- <xref:System.Data.DataTable.CreateDataReader%2A>
- <xref:System.Data.DataSet.CreateDataReader%2A>
- [<span data-ttu-id="3ec70-109">Čtečky datových tabulek</span><span class="sxs-lookup"><span data-stu-id="3ec70-109">DataTableReaders</span></span>](datatablereaders.md)
- [<span data-ttu-id="3ec70-110">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3ec70-110">ADO.NET Overview</span></span>](../ado-net-overview.md)
