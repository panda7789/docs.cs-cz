---
title: Výkon zobrazení dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 90820e49-9d46-41f6-9a3d-6c0741bbd8eb
ms.openlocfilehash: f0a85232b753eed891cded4b0fb1154269b30dc9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61606941"
---
# <a name="dataview-performance"></a><span data-ttu-id="9f63f-102">Výkon zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="9f63f-102">DataView Performance</span></span>
<span data-ttu-id="9f63f-103">Toto téma popisuje použití přinese zlepšení výkonu <xref:System.Data.DataView.Find%2A> a <xref:System.Data.DataView.FindRows%2A> metody <xref:System.Data.DataView> třídy a ukládání do mezipaměti <xref:System.Data.DataView> ve webové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9f63f-103">This topic discusses the performance benefits of using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView> class, and of caching a <xref:System.Data.DataView> in a Web application.</span></span>  
  
## <a name="find-and-findrows"></a><span data-ttu-id="9f63f-104">Najít a FindRows</span><span class="sxs-lookup"><span data-stu-id="9f63f-104">Find and FindRows</span></span>  
 <span data-ttu-id="9f63f-105"><xref:System.Data.DataView> Vytvoří index.</span><span class="sxs-lookup"><span data-stu-id="9f63f-105"><xref:System.Data.DataView> constructs an index.</span></span> <span data-ttu-id="9f63f-106">Index obsahuje klíče vytvořené z jednoho nebo více sloupců v tabulce nebo zobrazení.</span><span class="sxs-lookup"><span data-stu-id="9f63f-106">An index contains keys built from one or more columns in the table or view.</span></span> <span data-ttu-id="9f63f-107">Tyto klíče jsou uložené ve struktuře, která umožňuje <xref:System.Data.DataView> najít řádek nebo řádky, které jsou spojené s klíčovými hodnotami rychle a efektivně.</span><span class="sxs-lookup"><span data-stu-id="9f63f-107">These keys are stored in a structure that enables the <xref:System.Data.DataView> to find the row or rows associated with the key values quickly and efficiently.</span></span> <span data-ttu-id="9f63f-108">Operace, které používají index, jako je například filtrování a řazení, naleznete v tématu zvýšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="9f63f-108">Operations that use the index, such as filtering and sorting, see significant performance increases.</span></span> <span data-ttu-id="9f63f-109">Index <xref:System.Data.DataView> tvoříme tak i v případě <xref:System.Data.DataView> se vytvoří a při řazení nebo filtrování informace změněny.</span><span class="sxs-lookup"><span data-stu-id="9f63f-109">The index for a <xref:System.Data.DataView> is built both when the <xref:System.Data.DataView> is created and when any of the sorting or filtering information is modified.</span></span> <span data-ttu-id="9f63f-110">Vytváření <xref:System.Data.DataView> a nastavení řazení nebo filtrování informací později způsobí indexu, který má být sestaven alespoň dvakrát: až při <xref:System.Data.DataView> je vytvořen, a znovu když některé vlastnosti řazení nebo filtrování se upraví.</span><span class="sxs-lookup"><span data-stu-id="9f63f-110">Creating a <xref:System.Data.DataView> and then setting the sorting or filtering information later causes the index to be built at least twice: once when the <xref:System.Data.DataView> is created, and again when any of the sort or filter properties are modified.</span></span> <span data-ttu-id="9f63f-111">Další informace o filtrování a řazení ovládacími <xref:System.Data.DataView>, naleznete v tématu [filtrování se zobrazením dat](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md) a [řazení se zobrazením dat](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="9f63f-111">For more information about filtering and sorting with <xref:System.Data.DataView>, see [Filtering with DataView](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md) and [Sorting with DataView](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md).</span></span>  
  
 <span data-ttu-id="9f63f-112">Pokud chcete vrátit výsledky konkrétní dotaz na data, jako proti poskytující dynamické zobrazení podmnožinu dat, můžete použít <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> metody <xref:System.Data.DataView>, místo nastavení <xref:System.Data.DataView.RowFilter%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9f63f-112">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, you can use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>, rather than setting the <xref:System.Data.DataView.RowFilter%2A> property.</span></span> <span data-ttu-id="9f63f-113"><xref:System.Data.DataView.RowFilter%2A> Vlastnost je nejvhodnější v aplikace vázané na data kde vázaného ovládacího prvku zobrazí filtrované výsledky.</span><span class="sxs-lookup"><span data-stu-id="9f63f-113">The <xref:System.Data.DataView.RowFilter%2A> property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="9f63f-114">Nastavení <xref:System.Data.DataView.RowFilter%2A> vlastnost znovu sestaví index pro data, přidání režie pro vaši aplikaci a snížit výkon.</span><span class="sxs-lookup"><span data-stu-id="9f63f-114">Setting the <xref:System.Data.DataView.RowFilter%2A> property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="9f63f-115"><xref:System.Data.DataView.Find%2A> a <xref:System.Data.DataView.FindRows%2A> metody používat aktuální index bez nutnosti index znovu sestavit.</span><span class="sxs-lookup"><span data-stu-id="9f63f-115">The <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods use the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="9f63f-116">Pokud se chystáte zavolat <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> pouze jednou, měli byste použít stávající <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="9f63f-116">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> only once, then you should use the existing <xref:System.Data.DataView>.</span></span> <span data-ttu-id="9f63f-117">Pokud se chystáte zavolat <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> více než jednou, měli byste vytvořit nový <xref:System.Data.DataView> znovu sestavovat index pro sloupec, který chcete vyhledat a následně zavolat <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="9f63f-117">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> multiple times, you should create a new <xref:System.Data.DataView> to rebuild the index on the column you want to search on, and then call the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods.</span></span> <span data-ttu-id="9f63f-118">Další informace o <xref:System.Data.DataView.Find%2A> a <xref:System.Data.DataView.FindRows%2A> metody, naleznete v tématu [vyhledání řádků](../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).</span><span class="sxs-lookup"><span data-stu-id="9f63f-118">For more information about the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods, see [Finding Rows](../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).</span></span>  
  
 <span data-ttu-id="9f63f-119">V následujícím příkladu <xref:System.Data.DataView.Find%2A> metody k vyhledání kontakt s příjmení "Zhu".</span><span class="sxs-lookup"><span data-stu-id="9f63f-119">The following example uses the <xref:System.Data.DataView.Find%2A> method to find a contact with the last name "Zhu".</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryorderbyfind)]
 [!code-vb[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryorderbyfind)]  
  
 <span data-ttu-id="9f63f-120">V následujícím příkladu <xref:System.Data.DataView.FindRows%2A> metody k vyhledání všech červená barva produktů.</span><span class="sxs-lookup"><span data-stu-id="9f63f-120">The following example uses the <xref:System.Data.DataView.FindRows%2A> method to find all the red colored products.</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryfindrows)]
 [!code-vb[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryfindrows)]  
  
## <a name="aspnet"></a><span data-ttu-id="9f63f-121">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9f63f-121">ASP.NET</span></span>  
 <span data-ttu-id="9f63f-122">Technologie ASP.NET obsahuje mechanismus ukládání do mezipaměti, která umožňuje ukládat objekty, které vyžadují rozsáhlé server prostředky pro vytvoření v paměti.</span><span class="sxs-lookup"><span data-stu-id="9f63f-122">ASP.NET has a caching mechanism that allows you to store objects that require extensive server resources to create in memory.</span></span> <span data-ttu-id="9f63f-123">Ukládání do mezipaměti těchto typů prostředků může výrazně zlepšit výkon aplikace.</span><span class="sxs-lookup"><span data-stu-id="9f63f-123">Caching these types of resources can significantly improve the performance of your application.</span></span> <span data-ttu-id="9f63f-124">Ukládání do mezipaměti je implementovaných <xref:System.Web.Caching.Cache> třídy s instancí mezipaměti, které jsou privátní pro danou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9f63f-124">Caching is implemented by the <xref:System.Web.Caching.Cache> class, with cache instances that are private to each application.</span></span> <span data-ttu-id="9f63f-125">Vzhledem k tomu, že vytvoření nového <xref:System.Data.DataView> objekt může být náročné, můžete chtít použít funkce ve webových aplikacích mezipaměti tak, aby <xref:System.Data.DataView> není nutné znovu sestavit pokaždé, když se aktualizuje webové stránky.</span><span class="sxs-lookup"><span data-stu-id="9f63f-125">Because creating a new <xref:System.Data.DataView> object can be resource intensive, you might want to use this caching functionality in Web applications so that the <xref:System.Data.DataView> does not have to be rebuilt every time the Web page is refreshed.</span></span>  
  
 <span data-ttu-id="9f63f-126">V následujícím příkladu <xref:System.Data.DataView> se uloží do mezipaměti, takže není nutné data znovu seřadit při obnovení stránky.</span><span class="sxs-lookup"><span data-stu-id="9f63f-126">In the following example, the <xref:System.Data.DataView> is cached so that the data does not have to be re-sorted when the page is refreshed.</span></span>  
  
```vb  
If (Cache("ordersView") = Nothing) Then  
  
Dim dataSet As New DataSet()  
  
   FillDataSet(dataSet)  
  
   Dim orders As DataTable = dataSet.Tables("SalesOrderHeader")  
  
   Dim query = _  
                    From order In orders.AsEnumerable() _  
                    Where order.Field(Of Boolean)("OnlineOrderFlag") = True _  
                    Order By order.Field(Of Decimal)("TotalDue") _  
                    Select order  
  
   Dim view As DataView = query.AsDataView()  
  
   Cache.Insert("ordersView", view)  
  
End If  
  
Dim ordersView = CType(Cache("ordersView"), DataView)  
  
GridView1.DataSource = ordersView  
GridView1.DataBind()  
```  
  
```csharp  
if (Cache["ordersView"] == null)  
{  
   // Fill the DataSet.                  
   DataSet dataSet = FillDataSet();  
  
   DataTable orders = dataSet.Tables["SalesOrderHeader"];  
  
   EnumerableRowCollection<DataRow> query =  
                        from order in orders.AsEnumerable()  
                        where order.Field<bool>("OnlineOrderFlag") == true  
                        orderby order.Field<decimal>("TotalDue")  
                        select order;  
  
   DataView view = query.AsDataView();  
   Cache.Insert("ordersView", view);  
}  
  
DataView ordersView = (DataView)Cache["ordersView"];  
  
GridView1.DataSource = ordersView;  
GridView1.DataBind();  
```  
  
## <a name="see-also"></a><span data-ttu-id="9f63f-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f63f-127">See also</span></span>

- [<span data-ttu-id="9f63f-128">Datová vazba a LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="9f63f-128">Data Binding and LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
