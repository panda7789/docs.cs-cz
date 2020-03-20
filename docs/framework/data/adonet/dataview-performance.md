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
# <a name="dataview-performance"></a>Výkon zobrazení dat
Toto téma popisuje výhody výkonu <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> použití a <xref:System.Data.DataView> metody třídy a <xref:System.Data.DataView> ukládání do mezipaměti ve webové aplikaci.  
  
## <a name="find-and-findrows"></a>Najít a najít řádky  
 <xref:System.Data.DataView>vytvoří index. Index obsahuje klíče vytvořené z jednoho nebo více sloupců v tabulce nebo zobrazení. Tyto klíče jsou uloženy ve <xref:System.Data.DataView> struktuře, která umožňuje najít řádek nebo řádky spojené s hodnotami klíče rychle a efektivně. Operace, které používají index, jako je například filtrování a řazení, viz významné zvýšení výkonu. Index pro <xref:System.Data.DataView> je vytvořen při <xref:System.Data.DataView> vytvoření a při změně některé informace o řazení nebo filtrování. Vytvoření <xref:System.Data.DataView> a potom nastavení řazení nebo filtrování informace později způsobí, že index, <xref:System.Data.DataView> který má být sestaven alespoň dvakrát: jednou při vytvoření a znovu při změně některé ho řazení nebo vlastnosti filtru. Další informace o filtrování a <xref:System.Data.DataView>řazení pomocí najdete v [tématu Filtrování pomocí zobrazení dat](filtering-with-dataview-linq-to-dataset.md) a řazení pomocí zobrazení [dat](sorting-with-dataview-linq-to-dataset.md).  
  
 Chcete-li vrátit výsledky určitého dotazu na data, na rozdíl od poskytování dynamické zobrazení podmnožiny <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> dat, <xref:System.Data.DataView>můžete použít nebo <xref:System.Data.DataView.RowFilter%2A> metody , spíše než nastavení vlastnosti. Vlastnost <xref:System.Data.DataView.RowFilter%2A> se nejlépe používá v aplikaci vázané na data, kde vázaný ovládací prvek zobrazuje filtrované výsledky. Nastavení <xref:System.Data.DataView.RowFilter%2A> vlastnosti znovu vytvoří index pro data, přidání režie do aplikace a snížení výkonu. Metody <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> a používají aktuální index bez nutnosti znovu sestavit index. Pokud se chystáte <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> volat, nebo pouze jednou, <xref:System.Data.DataView>pak byste měli použít stávající . Pokud se chystáte <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> volat nebo vícekrát, <xref:System.Data.DataView> měli byste vytvořit nový znovu sestavit index na sloupec, který chcete hledat na a pak volat <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> metody. Další informace o <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> metodách a naleznete v tématu [Hledání řádků](./dataset-datatable-dataview/finding-rows.md).  
  
 Následující příklad používá <xref:System.Data.DataView.Find%2A> metodu k nalezení kontaktu s příjmením "Zhu".  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryorderbyfind)]
 [!code-vb[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryorderbyfind)]  
  
 Následující příklad používá <xref:System.Data.DataView.FindRows%2A> metodu k vyhledání všech produktů červené barvy.  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryfindrows)]
 [!code-vb[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryfindrows)]  
  
## <a name="aspnet"></a>ASP.NET  
 ASP.NET má mechanismus ukládání do mezipaměti, který umožňuje ukládat objekty, které vyžadují rozsáhlé prostředky serveru k vytvoření v paměti. Ukládání těchto typů prostředků do mezipaměti může výrazně zlepšit výkon aplikace. Ukládání do mezipaměti <xref:System.Web.Caching.Cache> je implementováno třídou, s instancemi mezipaměti, které jsou soukromé pro každou aplikaci. Vzhledem k <xref:System.Data.DataView> tomu, že vytvoření nového objektu může být náročné na prostředky, můžete tuto funkci ukládání do mezipaměti použít ve webových aplikacích, <xref:System.Data.DataView> aby nebylo nutné znovu sestavit webovou stránku při každé aktualizaci webové stránky.  
  
 V následujícím příkladu <xref:System.Data.DataView> je uložena do mezipaměti tak, aby data nemusí být znovu seřazeny při aktualizaci stránky.  
  
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
  
## <a name="see-also"></a>Viz také

- [Datová vazba a LINQ to DataSet](data-binding-and-linq-to-dataset.md)
