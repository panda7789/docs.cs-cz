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
# <a name="dataview-performance"></a>Výkon zobrazení dat
Toto téma popisuje výkonnostní <xref:System.Data.DataView.Find%2A> výhody použití metod <xref:System.Data.DataView> a <xref:System.Data.DataView.FindRows%2A> třídy a ukládání do mezipaměti <xref:System.Data.DataView> ve webové aplikaci.  
  
## <a name="find-and-findrows"></a>Najít a FindRows  
 <xref:System.Data.DataView>vytvoří index. Index obsahuje klíče sestavené z jednoho nebo více sloupců v tabulce nebo zobrazení. Tyto klíče jsou uloženy ve struktuře, která umožňuje <xref:System.Data.DataView> , aby bylo možné najít řádek nebo řádky přidružené k hodnotám klíčů rychle a efektivně. Operace, které používají index, jako je filtrování a třídění, se zvyšují z hlediska zvýšení výkonu. Index pro <xref:System.Data.DataView> je sestaven <xref:System.Data.DataView> při vytvoření a při změně jakékoli informace o řazení nebo filtrování. Vytvoření a nastavení informací o řazení nebo filtrování později způsobí, že se index sestaví alespoň dvakrát: Jakmile <xref:System.Data.DataView> se vytvoří, a znovu, když se změní kterákoli z vlastností řazení nebo filtru. <xref:System.Data.DataView> Další informace o filtrování a řazení pomocí <xref:System.Data.DataView>nástroje naleznete v tématu [filtrování pomocí zobrazení dat](filtering-with-dataview-linq-to-dataset.md) a [řazení pomocí objektu DataView](sorting-with-dataview-linq-to-dataset.md).  
  
 Pokud chcete vrátit výsledky konkrétního dotazu na data, na rozdíl od poskytnutí dynamického zobrazení podmnožiny dat, můžete <xref:System.Data.DataView.Find%2A> místo nastavení <xref:System.Data.DataView.RowFilter%2A> vlastnosti použít metody <xref:System.Data.DataView>nebo <xref:System.Data.DataView.FindRows%2A> . Tato <xref:System.Data.DataView.RowFilter%2A> vlastnost se nejlépe používá v aplikaci vázané na data, kde vázaný ovládací prvek zobrazuje filtrované výsledky. <xref:System.Data.DataView.RowFilter%2A> Nastavením vlastnosti se znovu sestaví index dat, zvýší se režie do vaší aplikace a zmenší se výkon. Metody <xref:System.Data.DataView.Find%2A> a<xref:System.Data.DataView.FindRows%2A> používají aktuální index, aniž by bylo nutné znovu sestavit index. Pokud budete volat <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> pouze jednou, měli byste použít stávající <xref:System.Data.DataView>. Pokud se chystáte zavolat <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> víckrát, měli byste vytvořit nový <xref:System.Data.DataView> , chcete-li znovu sestavit index ve sloupci, který chcete vyhledat, a pak zavolat <xref:System.Data.DataView.Find%2A> metody nebo <xref:System.Data.DataView.FindRows%2A> . Další informace o <xref:System.Data.DataView.Find%2A> metodách a <xref:System.Data.DataView.FindRows%2A> naleznete v tématu [Vyhledání řádků](./dataset-datatable-dataview/finding-rows.md).  
  
 Následující příklad používá <xref:System.Data.DataView.Find%2A> metodu k vyhledání kontaktu s posledním názvem "Zhu".  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryorderbyfind)]
 [!code-vb[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryorderbyfind)]  
  
 Následující příklad používá <xref:System.Data.DataView.FindRows%2A> metodu k vyhledání všech červených barevných produktů.  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryfindrows)]
 [!code-vb[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryfindrows)]  
  
## <a name="aspnet"></a>ASP.NET  
 ASP.NET má mechanismus ukládání do mezipaměti, který umožňuje ukládat objekty, které vyžadují rozsáhlé serverové prostředky k vytvoření v paměti. Ukládání těchto typů prostředků do mezipaměti může významně zlepšit výkon aplikace. Ukládání do mezipaměti je implementováno <xref:System.Web.Caching.Cache> třídou, s instancemi mezipaměti, které jsou pro každou aplikaci privátní. Vzhledem k tomu, <xref:System.Data.DataView> že vytvoření nového objektu může být náročné na prostředky, můžete použít tuto funkci ukládání do mezipaměti ve webových aplikacích <xref:System.Data.DataView> , aby se při každém obnovení webové stránky nemuselo znovu vytvářet.  
  
 V následujícím příkladu <xref:System.Data.DataView> je uložen do mezipaměti, aby se data po obnovení stránky nemusela znovu řadit.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Datová vazba a LINQ to DataSet](data-binding-and-linq-to-dataset.md)
