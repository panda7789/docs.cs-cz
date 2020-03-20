---
title: Výkon zobrazení dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 90820e49-9d46-41f6-9a3d-6c0741bbd8eb
ms.openlocfilehash: 7c81619bf4ac6ed084ea63349345dbf3b7f139b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150685"
---
# <a name="dataview-performance"></a><span data-ttu-id="ad370-102">Výkon zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="ad370-102">DataView Performance</span></span>
<span data-ttu-id="ad370-103">Toto téma popisuje výhody výkonu <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> použití a <xref:System.Data.DataView> metody třídy a <xref:System.Data.DataView> ukládání do mezipaměti ve webové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ad370-103">This topic discusses the performance benefits of using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView> class, and of caching a <xref:System.Data.DataView> in a Web application.</span></span>  
  
## <a name="find-and-findrows"></a><span data-ttu-id="ad370-104">Najít a najít řádky</span><span class="sxs-lookup"><span data-stu-id="ad370-104">Find and FindRows</span></span>  
 <span data-ttu-id="ad370-105"><xref:System.Data.DataView>vytvoří index.</span><span class="sxs-lookup"><span data-stu-id="ad370-105"><xref:System.Data.DataView> constructs an index.</span></span> <span data-ttu-id="ad370-106">Index obsahuje klíče vytvořené z jednoho nebo více sloupců v tabulce nebo zobrazení.</span><span class="sxs-lookup"><span data-stu-id="ad370-106">An index contains keys built from one or more columns in the table or view.</span></span> <span data-ttu-id="ad370-107">Tyto klíče jsou uloženy ve <xref:System.Data.DataView> struktuře, která umožňuje najít řádek nebo řádky spojené s hodnotami klíče rychle a efektivně.</span><span class="sxs-lookup"><span data-stu-id="ad370-107">These keys are stored in a structure that enables the <xref:System.Data.DataView> to find the row or rows associated with the key values quickly and efficiently.</span></span> <span data-ttu-id="ad370-108">Operace, které používají index, jako je například filtrování a řazení, viz významné zvýšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="ad370-108">Operations that use the index, such as filtering and sorting, see significant performance increases.</span></span> <span data-ttu-id="ad370-109">Index pro <xref:System.Data.DataView> je vytvořen při <xref:System.Data.DataView> vytvoření a při změně některé informace o řazení nebo filtrování.</span><span class="sxs-lookup"><span data-stu-id="ad370-109">The index for a <xref:System.Data.DataView> is built both when the <xref:System.Data.DataView> is created and when any of the sorting or filtering information is modified.</span></span> <span data-ttu-id="ad370-110">Vytvoření <xref:System.Data.DataView> a potom nastavení řazení nebo filtrování informace později způsobí, že index, <xref:System.Data.DataView> který má být sestaven alespoň dvakrát: jednou při vytvoření a znovu při změně některé ho řazení nebo vlastnosti filtru.</span><span class="sxs-lookup"><span data-stu-id="ad370-110">Creating a <xref:System.Data.DataView> and then setting the sorting or filtering information later causes the index to be built at least twice: once when the <xref:System.Data.DataView> is created, and again when any of the sort or filter properties are modified.</span></span> <span data-ttu-id="ad370-111">Další informace o filtrování a <xref:System.Data.DataView>řazení pomocí najdete v [tématu Filtrování pomocí zobrazení dat](filtering-with-dataview-linq-to-dataset.md) a řazení pomocí zobrazení [dat](sorting-with-dataview-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="ad370-111">For more information about filtering and sorting with <xref:System.Data.DataView>, see [Filtering with DataView](filtering-with-dataview-linq-to-dataset.md) and [Sorting with DataView](sorting-with-dataview-linq-to-dataset.md).</span></span>  
  
 <span data-ttu-id="ad370-112">Chcete-li vrátit výsledky určitého dotazu na data, na rozdíl od poskytování dynamické zobrazení podmnožiny <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> dat, <xref:System.Data.DataView>můžete použít nebo <xref:System.Data.DataView.RowFilter%2A> metody , spíše než nastavení vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ad370-112">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, you can use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>, rather than setting the <xref:System.Data.DataView.RowFilter%2A> property.</span></span> <span data-ttu-id="ad370-113">Vlastnost <xref:System.Data.DataView.RowFilter%2A> se nejlépe používá v aplikaci vázané na data, kde vázaný ovládací prvek zobrazuje filtrované výsledky.</span><span class="sxs-lookup"><span data-stu-id="ad370-113">The <xref:System.Data.DataView.RowFilter%2A> property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="ad370-114">Nastavení <xref:System.Data.DataView.RowFilter%2A> vlastnosti znovu vytvoří index pro data, přidání režie do aplikace a snížení výkonu.</span><span class="sxs-lookup"><span data-stu-id="ad370-114">Setting the <xref:System.Data.DataView.RowFilter%2A> property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="ad370-115">Metody <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> a používají aktuální index bez nutnosti znovu sestavit index.</span><span class="sxs-lookup"><span data-stu-id="ad370-115">The <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods use the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="ad370-116">Pokud se chystáte <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> volat, nebo pouze jednou, <xref:System.Data.DataView>pak byste měli použít stávající .</span><span class="sxs-lookup"><span data-stu-id="ad370-116">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> only once, then you should use the existing <xref:System.Data.DataView>.</span></span> <span data-ttu-id="ad370-117">Pokud se chystáte <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> volat nebo vícekrát, <xref:System.Data.DataView> měli byste vytvořit nový znovu sestavit index na sloupec, který chcete hledat na a pak volat <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ad370-117">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> multiple times, you should create a new <xref:System.Data.DataView> to rebuild the index on the column you want to search on, and then call the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods.</span></span> <span data-ttu-id="ad370-118">Další informace o <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> metodách a naleznete v tématu [Hledání řádků](./dataset-datatable-dataview/finding-rows.md).</span><span class="sxs-lookup"><span data-stu-id="ad370-118">For more information about the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods, see [Finding Rows](./dataset-datatable-dataview/finding-rows.md).</span></span>  
  
 <span data-ttu-id="ad370-119">Následující příklad používá <xref:System.Data.DataView.Find%2A> metodu k nalezení kontaktu s příjmením "Zhu".</span><span class="sxs-lookup"><span data-stu-id="ad370-119">The following example uses the <xref:System.Data.DataView.Find%2A> method to find a contact with the last name "Zhu".</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryorderbyfind)]
 [!code-vb[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryorderbyfind)]  
  
 <span data-ttu-id="ad370-120">Následující příklad používá <xref:System.Data.DataView.FindRows%2A> metodu k vyhledání všech produktů červené barvy.</span><span class="sxs-lookup"><span data-stu-id="ad370-120">The following example uses the <xref:System.Data.DataView.FindRows%2A> method to find all the red colored products.</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryfindrows)]
 [!code-vb[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryfindrows)]  
  
## <a name="aspnet"></a><span data-ttu-id="ad370-121">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ad370-121">ASP.NET</span></span>  
 <span data-ttu-id="ad370-122">ASP.NET má mechanismus ukládání do mezipaměti, který umožňuje ukládat objekty, které vyžadují rozsáhlé prostředky serveru k vytvoření v paměti.</span><span class="sxs-lookup"><span data-stu-id="ad370-122">ASP.NET has a caching mechanism that allows you to store objects that require extensive server resources to create in memory.</span></span> <span data-ttu-id="ad370-123">Ukládání těchto typů prostředků do mezipaměti může výrazně zlepšit výkon aplikace.</span><span class="sxs-lookup"><span data-stu-id="ad370-123">Caching these types of resources can significantly improve the performance of your application.</span></span> <span data-ttu-id="ad370-124">Ukládání do mezipaměti <xref:System.Web.Caching.Cache> je implementováno třídou, s instancemi mezipaměti, které jsou soukromé pro každou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ad370-124">Caching is implemented by the <xref:System.Web.Caching.Cache> class, with cache instances that are private to each application.</span></span> <span data-ttu-id="ad370-125">Vzhledem k <xref:System.Data.DataView> tomu, že vytvoření nového objektu může být náročné na prostředky, můžete tuto funkci ukládání do mezipaměti použít ve webových aplikacích, <xref:System.Data.DataView> aby nebylo nutné znovu sestavit webovou stránku při každé aktualizaci webové stránky.</span><span class="sxs-lookup"><span data-stu-id="ad370-125">Because creating a new <xref:System.Data.DataView> object can be resource intensive, you might want to use this caching functionality in Web applications so that the <xref:System.Data.DataView> does not have to be rebuilt every time the Web page is refreshed.</span></span>  
  
 <span data-ttu-id="ad370-126">V následujícím příkladu <xref:System.Data.DataView> je uložena do mezipaměti tak, aby data nemusí být znovu seřazeny při aktualizaci stránky.</span><span class="sxs-lookup"><span data-stu-id="ad370-126">In the following example, the <xref:System.Data.DataView> is cached so that the data does not have to be re-sorted when the page is refreshed.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ad370-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="ad370-127">See also</span></span>

- [<span data-ttu-id="ad370-128">Datová vazba a LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="ad370-128">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)
