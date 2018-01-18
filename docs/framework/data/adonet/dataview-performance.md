---
title: "Zobrazení dat výkonu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 90820e49-9d46-41f6-9a3d-6c0741bbd8eb
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 0858dec79f17906647a3244eb1686e91e53ac48d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="dataview-performance"></a><span data-ttu-id="06637-102">Zobrazení dat výkonu</span><span class="sxs-lookup"><span data-stu-id="06637-102">DataView Performance</span></span>
<span data-ttu-id="06637-103">Toto téma popisuje výhody výkonu pomocí <xref:System.Data.DataView.Find%2A> a <xref:System.Data.DataView.FindRows%2A> metody <xref:System.Data.DataView> třída a ukládání do mezipaměti <xref:System.Data.DataView> ve webové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="06637-103">This topic discusses the performance benefits of using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView> class, and of caching a <xref:System.Data.DataView> in a Web application.</span></span>  
  
## <a name="find-and-findrows"></a><span data-ttu-id="06637-104">Najít a FindRows</span><span class="sxs-lookup"><span data-stu-id="06637-104">Find and FindRows</span></span>  
 <span data-ttu-id="06637-105"><xref:System.Data.DataView>Vytvoří index.</span><span class="sxs-lookup"><span data-stu-id="06637-105"><xref:System.Data.DataView> constructs an index.</span></span> <span data-ttu-id="06637-106">Index obsahuje klíče ze jeden nebo více sloupců v tabulce nebo zobrazení.</span><span class="sxs-lookup"><span data-stu-id="06637-106">An index contains keys built from one or more columns in the table or view.</span></span> <span data-ttu-id="06637-107">Tyto klíče jsou uložené ve struktuře, která umožňuje <xref:System.Data.DataView> k vyhledání řádků přidružené hodnoty klíče rychle a efektivně či řádku.</span><span class="sxs-lookup"><span data-stu-id="06637-107">These keys are stored in a structure that enables the <xref:System.Data.DataView> to find the row or rows associated with the key values quickly and efficiently.</span></span> <span data-ttu-id="06637-108">Operace, které používají index, jako je například filtrování a řazení, najdete v části signifcant zvyšuje výkon.</span><span class="sxs-lookup"><span data-stu-id="06637-108">Operations that use the index, such as filtering and sorting, see signifcant performance increases.</span></span> <span data-ttu-id="06637-109">Index <xref:System.Data.DataView> vychází i v případě <xref:System.Data.DataView> je vytvořena a při řazení nebo filtrování je upravit informace.</span><span class="sxs-lookup"><span data-stu-id="06637-109">The index for a <xref:System.Data.DataView> is built both when the <xref:System.Data.DataView> is created and when any of the sorting or filtering information is modified.</span></span> <span data-ttu-id="06637-110">Vytváření <xref:System.Data.DataView> a následně nastavení toto řazení nebo filtrování informace později způsobí index, který má být sestaven alespoň dvakrát: Jakmile při <xref:System.Data.DataView> je vytvořen, a znovu jakékoli vlastnosti řazení nebo filtrování jsou změny.</span><span class="sxs-lookup"><span data-stu-id="06637-110">Creating a <xref:System.Data.DataView> and then setting the sorting or filtering information later causes the index to be built at least twice: once when the <xref:System.Data.DataView> is created, and again when any of the sort or filter properties are modified.</span></span> <span data-ttu-id="06637-111">Další informace o filtrování a řazení s <xref:System.Data.DataView>, najdete v části [filtrování s DataView](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md) a [řazení s DataView](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="06637-111">For more information about filtering and sorting with <xref:System.Data.DataView>, see [Filtering with DataView](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md) and [Sorting with DataView](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md).</span></span>  
  
 <span data-ttu-id="06637-112">Pokud chcete výsledky konkrétní dotaz na data, oproti Pokud dynamické zobrazení podmnožinu dat, můžete použít <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> metody <xref:System.Data.DataView>, nikoli nastavení <xref:System.Data.DataView.RowFilter%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="06637-112">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, you can use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>, rather than setting the <xref:System.Data.DataView.RowFilter%2A> property.</span></span> <span data-ttu-id="06637-113"><xref:System.Data.DataView.RowFilter%2A> Vlastnost nejlépe slouží v aplikaci vázané na data kde připojeného ovládacího prvku zobrazí filtrované výsledky.</span><span class="sxs-lookup"><span data-stu-id="06637-113">The <xref:System.Data.DataView.RowFilter%2A> property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="06637-114">Nastavení <xref:System.Data.DataView.RowFilter%2A> vlastnost znovu sestaví index pro data, přidávání režie k vaší aplikaci a snížení výkonu.</span><span class="sxs-lookup"><span data-stu-id="06637-114">Setting the <xref:System.Data.DataView.RowFilter%2A> property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="06637-115"><xref:System.Data.DataView.Find%2A> a <xref:System.Data.DataView.FindRows%2A> metody použití aktuální index bez nutnosti znovu sestavit index.</span><span class="sxs-lookup"><span data-stu-id="06637-115">The <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods use the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="06637-116">Pokud chcete volat <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> pouze jednou, měli byste použít stávající <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="06637-116">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> only once, then you should use the existing <xref:System.Data.DataView>.</span></span> <span data-ttu-id="06637-117">Pokud chcete volat <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> vícekrát, měli byste vytvořit nový <xref:System.Data.DataView> znovu sestavit index na sloupci, kterou chcete hledat na a pak zavolají <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="06637-117">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> multiple times, you should create a new <xref:System.Data.DataView> to rebuild the index on the column you want to search on, and then call the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods.</span></span> <span data-ttu-id="06637-118">Další informace o <xref:System.Data.DataView.Find%2A> a <xref:System.Data.DataView.FindRows%2A> metody, najdete v části [hledání řádky](../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).</span><span class="sxs-lookup"><span data-stu-id="06637-118">For more information about the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods, see [Finding Rows](../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).</span></span>  
  
 <span data-ttu-id="06637-119">Následující příklad používá <xref:System.Data.DataView.Find%2A> metody k vyhledání kontakt s příjmení "Zhu".</span><span class="sxs-lookup"><span data-stu-id="06637-119">The following example uses the <xref:System.Data.DataView.Find%2A> method to find a contact with the last name "Zhu".</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryorderbyfind)]
 [!code-vb[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryorderbyfind)]  
  
 <span data-ttu-id="06637-120">Následující příklad používá <xref:System.Data.DataView.FindRows%2A> metody k vyhledání všech red barevné produkty.</span><span class="sxs-lookup"><span data-stu-id="06637-120">The following example uses the <xref:System.Data.DataView.FindRows%2A> method to find all the red colored products.</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryfindrows)]
 [!code-vb[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryfindrows)]  
  
## <a name="aspnet"></a><span data-ttu-id="06637-121">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="06637-121">ASP.NET</span></span>  
 <span data-ttu-id="06637-122">Technologie ASP.NET má mechanismus ukládání do mezipaměti, která umožňuje ukládat objekty, které vyžadují rozsáhlé serveru zdrojů pro vytvoření v paměti.</span><span class="sxs-lookup"><span data-stu-id="06637-122">ASP.NET has a caching mechanism that allows you to store objects that require extensive server resources to create in memory.</span></span> <span data-ttu-id="06637-123">Ukládání do mezipaměti tyto typy prostředků může výrazně zlepšit výkon aplikace.</span><span class="sxs-lookup"><span data-stu-id="06637-123">Caching these types of resources can significantly improve the performance of your application.</span></span> <span data-ttu-id="06637-124">Ukládání do mezipaměti je implementované <xref:System.Web.Caching.Cache> třídy s instancemi mezipaměti, které jsou soukromé pro každou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="06637-124">Caching is implemented by the <xref:System.Web.Caching.Cache> class, with cache instances that are private to each application.</span></span> <span data-ttu-id="06637-125">Vzhledem k tomu, že vytvoření nové <xref:System.Data.DataView> objekt může být náročné, můžete chtít použít funkce ve webových aplikacích mezipaměti, aby <xref:System.Data.DataView> není nutné znovu sestavit pokaždé, když se aktualizují webové stránky.</span><span class="sxs-lookup"><span data-stu-id="06637-125">Because creating a new <xref:System.Data.DataView> object can be resource intensive, you might want to use this caching functionality in Web applications so that the <xref:System.Data.DataView> does not have to be rebuilt every time the Web page is refreshed.</span></span>  
  
 <span data-ttu-id="06637-126">V následujícím příkladu <xref:System.Data.DataView> se uloží do mezipaměti, takže není nutné data znovu seřadit při aktualizaci stránky.</span><span class="sxs-lookup"><span data-stu-id="06637-126">In the following example, the <xref:System.Data.DataView> is cached so that the data does not have to be re-sorted when the page is refreshed.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="06637-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="06637-127">See Also</span></span>  
 [<span data-ttu-id="06637-128">Datová vazba a LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="06637-128">Data Binding and LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
