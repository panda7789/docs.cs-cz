---
title: Navigace v datových tabulkách
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
ms.openlocfilehash: f00e2171c1adf4ff99a669085131ebc8d38f7006
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43788607"
---
# <a name="navigating-datatables"></a><span data-ttu-id="910d2-102">Navigace v datových tabulkách</span><span class="sxs-lookup"><span data-stu-id="910d2-102">Navigating DataTables</span></span>
<span data-ttu-id="910d2-103"><xref:System.Data.DataTableReader> Získá obsah jednoho nebo více <xref:System.Data.DataTable> objekty ve formě jednoho nebo více sad výsledků dotazu jen pro čtení, pouze vpřed.</span><span class="sxs-lookup"><span data-stu-id="910d2-103">The <xref:System.Data.DataTableReader> obtains the contents of one or more <xref:System.Data.DataTable> objects in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="910d2-104">A <xref:System.Data.DataTableReader> může obsahovat více sad výsledků dotazu, pokud je vytvořena pomocí <xref:System.Data.DataSet.CreateDataReader%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="910d2-104">A <xref:System.Data.DataTableReader> may contain multiple result sets if it is created by using the <xref:System.Data.DataSet.CreateDataReader%2A> method.</span></span> <span data-ttu-id="910d2-105">Po více než jednu sadu výsledků, <xref:System.Data.DataTableReader.NextResult%2A> metoda Posune kurzor na další sadu výsledků.</span><span class="sxs-lookup"><span data-stu-id="910d2-105">When there is more than one result set, the <xref:System.Data.DataTableReader.NextResult%2A> method advances the cursor to the next result set.</span></span> <span data-ttu-id="910d2-106">Jedná se o proces pouze vpřed.</span><span class="sxs-lookup"><span data-stu-id="910d2-106">This is a forward-only process.</span></span> <span data-ttu-id="910d2-107">Není možné vrátit na předchozí sadu výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="910d2-107">It is not possible to return to a previous result set.</span></span>  
  
## <a name="example"></a><span data-ttu-id="910d2-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="910d2-108">Example</span></span>  
 <span data-ttu-id="910d2-109">V následujícím příkladu `TestConstructor` metoda vytvoří dva <xref:System.Data.DataTable> instancí.</span><span class="sxs-lookup"><span data-stu-id="910d2-109">In the following example, the `TestConstructor` method creates two <xref:System.Data.DataTable> instances.</span></span> <span data-ttu-id="910d2-110">Pro ukázání tento konstruktor pro <xref:System.Data.DataTableReader> třídy, vzorovým kódem se vytvoří nový **třída DataTableReader** na základě pole, která obsahuje dvě **DataTables**a provádí jednoduché operace Tisk obsahu z prvního několik sloupců do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="910d2-110">In order to demonstrate this constructor for the <xref:System.Data.DataTableReader> class, the sample creates a new **DataTableReader** based on an array that contains the two **DataTables**, and performs a simple operation, printing the contents from the first few columns to the console window.</span></span>  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="910d2-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="910d2-111">See Also</span></span>  
 [<span data-ttu-id="910d2-112">Čtečky datových tabulek</span><span class="sxs-lookup"><span data-stu-id="910d2-112">DataTableReaders</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 [<span data-ttu-id="910d2-113">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="910d2-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
