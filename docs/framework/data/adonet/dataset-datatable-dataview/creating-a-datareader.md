---
title: Vytvoření čtečky dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: cb39ead1fe15e3bfcf67370e4675dcae3bbf9801
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203893"
---
# <a name="creating-a-datareader"></a><span data-ttu-id="c7ae4-102">Vytvoření čtečky dat</span><span class="sxs-lookup"><span data-stu-id="c7ae4-102">Creating a DataReader</span></span>
<span data-ttu-id="c7ae4-103"><xref:System.Data.DataTable> <xref:System.Data.DataSet.Tables%2A> Třídy a <xref:System.Data.DataSet>mají metodu<xref:System.Data.DataTable.CreateDataReader%2A> , která vrací<xref:System.Data.DataSet> obsah nebo obsah kolekce objektu jako jednu nebo více sad výsledků pouze pro čtení, které jsou jen pro čtení. <xref:System.Data.DataTable></span><span class="sxs-lookup"><span data-stu-id="c7ae4-103">The <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes have a <xref:System.Data.DataTable.CreateDataReader%2A> method that returns the contents of the <xref:System.Data.DataTable> or the contents of the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Tables%2A> collection as one or more read-only, forward-only result sets.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7ae4-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="c7ae4-104">Example</span></span>  
 <span data-ttu-id="c7ae4-105">Následující Konzolová aplikace vytvoří <xref:System.Data.DataTable> instanci.</span><span class="sxs-lookup"><span data-stu-id="c7ae4-105">The following console application creates a <xref:System.Data.DataTable> instance.</span></span> <span data-ttu-id="c7ae4-106">Příklad předává vyplněný <xref:System.Data.DataTable> postup, který <xref:System.Data.DataTable.CreateDataReader%2A> volá metodu, která prochází výsledky obsaženými v <xref:System.Data.DataTableReader>.</span><span class="sxs-lookup"><span data-stu-id="c7ae4-106">The example then passes the filled <xref:System.Data.DataTable> to a procedure that calls the <xref:System.Data.DataTable.CreateDataReader%2A> method, which iterates through the results contained within the <xref:System.Data.DataTableReader>.</span></span>  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 <span data-ttu-id="c7ae4-107">V příkladu se zobrazí následující výstup v okně konzoly:</span><span class="sxs-lookup"><span data-stu-id="c7ae4-107">The example displays the following output in the console window:</span></span>  
  
```  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a><span data-ttu-id="c7ae4-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c7ae4-108">See also</span></span>

- <xref:System.Data.DataTable.CreateDataReader%2A>
- <xref:System.Data.DataSet.CreateDataReader%2A>
- [<span data-ttu-id="c7ae4-109">Čtečky datových tabulek</span><span class="sxs-lookup"><span data-stu-id="c7ae4-109">DataTableReaders</span></span>](datatablereaders.md)
- [<span data-ttu-id="c7ae4-110">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="c7ae4-110">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
