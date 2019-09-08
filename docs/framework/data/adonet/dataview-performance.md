---
title: Výkon zobrazení dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 90820e49-9d46-41f6-9a3d-6c0741bbd8eb
ms.openlocfilehash: 51ea09965c423f04c220260248c3501e061820cb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784137"
---
# <a name="dataview-performance"></a><span data-ttu-id="c6b93-102">Výkon zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="c6b93-102">DataView Performance</span></span>
<span data-ttu-id="c6b93-103">Toto téma popisuje výkonnostní <xref:System.Data.DataView.Find%2A> výhody použití metod <xref:System.Data.DataView> a <xref:System.Data.DataView.FindRows%2A> třídy a ukládání do mezipaměti <xref:System.Data.DataView> ve webové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c6b93-103">This topic discusses the performance benefits of using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView> class, and of caching a <xref:System.Data.DataView> in a Web application.</span></span>  
  
## <a name="find-and-findrows"></a><span data-ttu-id="c6b93-104">Najít a FindRows</span><span class="sxs-lookup"><span data-stu-id="c6b93-104">Find and FindRows</span></span>  
 <span data-ttu-id="c6b93-105"><xref:System.Data.DataView>vytvoří index.</span><span class="sxs-lookup"><span data-stu-id="c6b93-105"><xref:System.Data.DataView> constructs an index.</span></span> <span data-ttu-id="c6b93-106">Index obsahuje klíče sestavené z jednoho nebo více sloupců v tabulce nebo zobrazení.</span><span class="sxs-lookup"><span data-stu-id="c6b93-106">An index contains keys built from one or more columns in the table or view.</span></span> <span data-ttu-id="c6b93-107">Tyto klíče jsou uloženy ve struktuře, která umožňuje <xref:System.Data.DataView> , aby bylo možné najít řádek nebo řádky přidružené k hodnotám klíčů rychle a efektivně.</span><span class="sxs-lookup"><span data-stu-id="c6b93-107">These keys are stored in a structure that enables the <xref:System.Data.DataView> to find the row or rows associated with the key values quickly and efficiently.</span></span> <span data-ttu-id="c6b93-108">Operace, které používají index, jako je filtrování a třídění, se zvyšují z hlediska zvýšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="c6b93-108">Operations that use the index, such as filtering and sorting, see significant performance increases.</span></span> <span data-ttu-id="c6b93-109">Index pro <xref:System.Data.DataView> je sestaven <xref:System.Data.DataView> při vytvoření a při změně jakékoli informace o řazení nebo filtrování.</span><span class="sxs-lookup"><span data-stu-id="c6b93-109">The index for a <xref:System.Data.DataView> is built both when the <xref:System.Data.DataView> is created and when any of the sorting or filtering information is modified.</span></span> <span data-ttu-id="c6b93-110">Vytvoření a nastavení informací o řazení nebo filtrování později způsobí, že se index sestaví alespoň dvakrát: Jakmile <xref:System.Data.DataView> se vytvoří, a znovu, když se změní kterákoli z vlastností řazení nebo filtru. <xref:System.Data.DataView></span><span class="sxs-lookup"><span data-stu-id="c6b93-110">Creating a <xref:System.Data.DataView> and then setting the sorting or filtering information later causes the index to be built at least twice: once when the <xref:System.Data.DataView> is created, and again when any of the sort or filter properties are modified.</span></span> <span data-ttu-id="c6b93-111">Další informace o filtrování a řazení pomocí <xref:System.Data.DataView>nástroje naleznete v tématu [filtrování pomocí zobrazení dat](filtering-with-dataview-linq-to-dataset.md) a [řazení pomocí objektu DataView](sorting-with-dataview-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="c6b93-111">For more information about filtering and sorting with <xref:System.Data.DataView>, see [Filtering with DataView](filtering-with-dataview-linq-to-dataset.md) and [Sorting with DataView](sorting-with-dataview-linq-to-dataset.md).</span></span>  
  
 <span data-ttu-id="c6b93-112">Pokud chcete vrátit výsledky konkrétního dotazu na data, na rozdíl od poskytnutí dynamického zobrazení podmnožiny dat, můžete <xref:System.Data.DataView.Find%2A> místo nastavení <xref:System.Data.DataView.RowFilter%2A> vlastnosti použít metody <xref:System.Data.DataView>nebo <xref:System.Data.DataView.FindRows%2A> .</span><span class="sxs-lookup"><span data-stu-id="c6b93-112">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, you can use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>, rather than setting the <xref:System.Data.DataView.RowFilter%2A> property.</span></span> <span data-ttu-id="c6b93-113">Tato <xref:System.Data.DataView.RowFilter%2A> vlastnost se nejlépe používá v aplikaci vázané na data, kde vázaný ovládací prvek zobrazuje filtrované výsledky.</span><span class="sxs-lookup"><span data-stu-id="c6b93-113">The <xref:System.Data.DataView.RowFilter%2A> property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="c6b93-114"><xref:System.Data.DataView.RowFilter%2A> Nastavením vlastnosti se znovu sestaví index dat, zvýší se režie do vaší aplikace a zmenší se výkon.</span><span class="sxs-lookup"><span data-stu-id="c6b93-114">Setting the <xref:System.Data.DataView.RowFilter%2A> property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="c6b93-115">Metody <xref:System.Data.DataView.Find%2A> a<xref:System.Data.DataView.FindRows%2A> používají aktuální index, aniž by bylo nutné znovu sestavit index.</span><span class="sxs-lookup"><span data-stu-id="c6b93-115">The <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods use the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="c6b93-116">Pokud budete volat <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> pouze jednou, měli byste použít stávající <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="c6b93-116">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> only once, then you should use the existing <xref:System.Data.DataView>.</span></span> <span data-ttu-id="c6b93-117">Pokud se chystáte zavolat <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> víckrát, měli byste vytvořit nový <xref:System.Data.DataView> , chcete-li znovu sestavit index ve sloupci, který chcete vyhledat, a pak zavolat <xref:System.Data.DataView.Find%2A> metody nebo <xref:System.Data.DataView.FindRows%2A> .</span><span class="sxs-lookup"><span data-stu-id="c6b93-117">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> multiple times, you should create a new <xref:System.Data.DataView> to rebuild the index on the column you want to search on, and then call the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods.</span></span> <span data-ttu-id="c6b93-118">Další informace o <xref:System.Data.DataView.Find%2A> metodách a <xref:System.Data.DataView.FindRows%2A> naleznete v tématu [Vyhledání řádků](./dataset-datatable-dataview/finding-rows.md).</span><span class="sxs-lookup"><span data-stu-id="c6b93-118">For more information about the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods, see [Finding Rows](./dataset-datatable-dataview/finding-rows.md).</span></span>  
  
 <span data-ttu-id="c6b93-119">Následující příklad používá <xref:System.Data.DataView.Find%2A> metodu k vyhledání kontaktu s posledním názvem "Zhu".</span><span class="sxs-lookup"><span data-stu-id="c6b93-119">The following example uses the <xref:System.Data.DataView.Find%2A> method to find a contact with the last name "Zhu".</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryorderbyfind)]
 [!code-vb[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryorderbyfind)]  
  
 <span data-ttu-id="c6b93-120">Následující příklad používá <xref:System.Data.DataView.FindRows%2A> metodu k vyhledání všech červených barevných produktů.</span><span class="sxs-lookup"><span data-stu-id="c6b93-120">The following example uses the <xref:System.Data.DataView.FindRows%2A> method to find all the red colored products.</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryfindrows)]
 [!code-vb[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryfindrows)]  
  
## <a name="aspnet"></a><span data-ttu-id="c6b93-121">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c6b93-121">ASP.NET</span></span>  
 <span data-ttu-id="c6b93-122">ASP.NET má mechanismus ukládání do mezipaměti, který umožňuje ukládat objekty, které vyžadují rozsáhlé serverové prostředky k vytvoření v paměti.</span><span class="sxs-lookup"><span data-stu-id="c6b93-122">ASP.NET has a caching mechanism that allows you to store objects that require extensive server resources to create in memory.</span></span> <span data-ttu-id="c6b93-123">Ukládání těchto typů prostředků do mezipaměti může významně zlepšit výkon aplikace.</span><span class="sxs-lookup"><span data-stu-id="c6b93-123">Caching these types of resources can significantly improve the performance of your application.</span></span> <span data-ttu-id="c6b93-124">Ukládání do mezipaměti je implementováno <xref:System.Web.Caching.Cache> třídou, s instancemi mezipaměti, které jsou pro každou aplikaci privátní.</span><span class="sxs-lookup"><span data-stu-id="c6b93-124">Caching is implemented by the <xref:System.Web.Caching.Cache> class, with cache instances that are private to each application.</span></span> <span data-ttu-id="c6b93-125">Vzhledem k tomu, <xref:System.Data.DataView> že vytvoření nového objektu může být náročné na prostředky, můžete použít tuto funkci ukládání do mezipaměti ve webových aplikacích <xref:System.Data.DataView> , aby se při každém obnovení webové stránky nemuselo znovu vytvářet.</span><span class="sxs-lookup"><span data-stu-id="c6b93-125">Because creating a new <xref:System.Data.DataView> object can be resource intensive, you might want to use this caching functionality in Web applications so that the <xref:System.Data.DataView> does not have to be rebuilt every time the Web page is refreshed.</span></span>  
  
 <span data-ttu-id="c6b93-126">V následujícím příkladu <xref:System.Data.DataView> je uložen do mezipaměti, aby se data po obnovení stránky nemusela znovu řadit.</span><span class="sxs-lookup"><span data-stu-id="c6b93-126">In the following example, the <xref:System.Data.DataView> is cached so that the data does not have to be re-sorted when the page is refreshed.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c6b93-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6b93-127">See also</span></span>

- [<span data-ttu-id="c6b93-128">Datová vazba a LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="c6b93-128">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)
