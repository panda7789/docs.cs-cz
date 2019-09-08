---
title: Navigace v datových tabulkách
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
ms.openlocfilehash: 5008f8397b7d396b14fdfe8e24f1e59785c4319d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785251"
---
# <a name="navigating-datatables"></a><span data-ttu-id="6d8a7-102">Navigace v datových tabulkách</span><span class="sxs-lookup"><span data-stu-id="6d8a7-102">Navigating DataTables</span></span>
<span data-ttu-id="6d8a7-103">Získá obsah jednoho nebo více <xref:System.Data.DataTable> objektů ve formě jedné nebo více sad výsledků pouze pro čtení, které jsou jen pro čtení. <xref:System.Data.DataTableReader></span><span class="sxs-lookup"><span data-stu-id="6d8a7-103">The <xref:System.Data.DataTableReader> obtains the contents of one or more <xref:System.Data.DataTable> objects in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="6d8a7-104">Může obsahovat více sad výsledků, pokud je vytvořen <xref:System.Data.DataSet.CreateDataReader%2A> pomocí metody. <xref:System.Data.DataTableReader></span><span class="sxs-lookup"><span data-stu-id="6d8a7-104">A <xref:System.Data.DataTableReader> may contain multiple result sets if it is created by using the <xref:System.Data.DataSet.CreateDataReader%2A> method.</span></span> <span data-ttu-id="6d8a7-105">Pokud je k dispozici více než jedna sada výsledků <xref:System.Data.DataTableReader.NextResult%2A> , metoda přesune kurzor na další sadu výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="6d8a7-105">When there is more than one result set, the <xref:System.Data.DataTableReader.NextResult%2A> method advances the cursor to the next result set.</span></span> <span data-ttu-id="6d8a7-106">Toto je proces jenom pro přeposílání.</span><span class="sxs-lookup"><span data-stu-id="6d8a7-106">This is a forward-only process.</span></span> <span data-ttu-id="6d8a7-107">Není možné se vrátit k předchozí sadě výsledků.</span><span class="sxs-lookup"><span data-stu-id="6d8a7-107">It is not possible to return to a previous result set.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d8a7-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="6d8a7-108">Example</span></span>  
 <span data-ttu-id="6d8a7-109">V následujícím příkladu `TestConstructor` metoda vytvoří dvě <xref:System.Data.DataTable> instance.</span><span class="sxs-lookup"><span data-stu-id="6d8a7-109">In the following example, the `TestConstructor` method creates two <xref:System.Data.DataTable> instances.</span></span> <span data-ttu-id="6d8a7-110">Aby bylo možné předvést tento konstruktor pro <xref:System.Data.DataTableReader> třídu, ukázka vytvoří novou **třídu DataTableReader** založenou na poli, které obsahuje dvě **tabulky DataTables**a provede jednoduchou operaci, vytištění obsahu z prvních několika. sloupce do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="6d8a7-110">In order to demonstrate this constructor for the <xref:System.Data.DataTableReader> class, the sample creates a new **DataTableReader** based on an array that contains the two **DataTables**, and performs a simple operation, printing the contents from the first few columns to the console window.</span></span>  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6d8a7-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6d8a7-111">See also</span></span>

- [<span data-ttu-id="6d8a7-112">Čtečky datových tabulek</span><span class="sxs-lookup"><span data-stu-id="6d8a7-112">DataTableReaders</span></span>](datatablereaders.md)
- [<span data-ttu-id="6d8a7-113">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6d8a7-113">ADO.NET Overview</span></span>](../ado-net-overview.md)
