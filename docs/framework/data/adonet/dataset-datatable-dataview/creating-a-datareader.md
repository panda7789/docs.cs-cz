---
title: Vytvoření čtečky dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: 696eb4dfc334390e1968dd317d441f3c987a1f77
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040112"
---
# <a name="creating-a-datareader"></a><span data-ttu-id="e1d2b-102">Vytvoření čtečky dat</span><span class="sxs-lookup"><span data-stu-id="e1d2b-102">Creating a DataReader</span></span>
<span data-ttu-id="e1d2b-103">Třídy <xref:System.Data.DataTable> a <xref:System.Data.DataSet> mají metodu <xref:System.Data.DataTable.CreateDataReader%2A>, která vrací obsah <xref:System.Data.DataTable> nebo obsah <xref:System.Data.DataSet> kolekce objektu <xref:System.Data.DataSet.Tables%2A> jako jednu nebo více sad výsledků, které jsou jen pro čtení a pouze pro čtení.</span><span class="sxs-lookup"><span data-stu-id="e1d2b-103">The <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes have a <xref:System.Data.DataTable.CreateDataReader%2A> method that returns the contents of the <xref:System.Data.DataTable> or the contents of the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Tables%2A> collection as one or more read-only, forward-only result sets.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1d2b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="e1d2b-104">Example</span></span>  
 <span data-ttu-id="e1d2b-105">Následující Konzolová aplikace vytvoří instanci <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="e1d2b-105">The following console application creates a <xref:System.Data.DataTable> instance.</span></span> <span data-ttu-id="e1d2b-106">Příklad předává vyplněný <xref:System.Data.DataTable> proceduře, která volá metodu <xref:System.Data.DataTable.CreateDataReader%2A>, která prochází výsledky obsaženými v <xref:System.Data.DataTableReader>.</span><span class="sxs-lookup"><span data-stu-id="e1d2b-106">The example then passes the filled <xref:System.Data.DataTable> to a procedure that calls the <xref:System.Data.DataTable.CreateDataReader%2A> method, which iterates through the results contained within the <xref:System.Data.DataTableReader>.</span></span>  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 <span data-ttu-id="e1d2b-107">V příkladu se zobrazí následující výstup v okně konzoly:</span><span class="sxs-lookup"><span data-stu-id="e1d2b-107">The example displays the following output in the console window:</span></span>  
  
```output  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a><span data-ttu-id="e1d2b-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e1d2b-108">See also</span></span>

- <xref:System.Data.DataTable.CreateDataReader%2A>
- <xref:System.Data.DataSet.CreateDataReader%2A>
- [<span data-ttu-id="e1d2b-109">Čtečky datových tabulek</span><span class="sxs-lookup"><span data-stu-id="e1d2b-109">DataTableReaders</span></span>](datatablereaders.md)
- [<span data-ttu-id="e1d2b-110">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e1d2b-110">ADO.NET Overview</span></span>](../ado-net-overview.md)
