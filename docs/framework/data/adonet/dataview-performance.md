---
title: Zobrazení dat výkonu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 90820e49-9d46-41f6-9a3d-6c0741bbd8eb
ms.openlocfilehash: df7c5525738d23a1489bfeec75d2c6b1dbd29e94
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32762777"
---
# <a name="dataview-performance"></a>Zobrazení dat výkonu
Toto téma popisuje výhody výkonu pomocí <xref:System.Data.DataView.Find%2A> a <xref:System.Data.DataView.FindRows%2A> metody <xref:System.Data.DataView> třída a ukládání do mezipaměti <xref:System.Data.DataView> ve webové aplikaci.  
  
## <a name="find-and-findrows"></a>Najít a FindRows  
 <xref:System.Data.DataView> Vytvoří index. Index obsahuje klíče ze jeden nebo více sloupců v tabulce nebo zobrazení. Tyto klíče jsou uložené ve struktuře, která umožňuje <xref:System.Data.DataView> k vyhledání řádků přidružené hodnoty klíče rychle a efektivně či řádku. Operace, které používají index, jako je například filtrování a řazení, najdete v části signifcant zvyšuje výkon. Index <xref:System.Data.DataView> vychází i v případě <xref:System.Data.DataView> je vytvořena a při řazení nebo filtrování je upravit informace. Vytváření <xref:System.Data.DataView> a následně nastavení toto řazení nebo filtrování informace později způsobí index, který má být sestaven alespoň dvakrát: Jakmile při <xref:System.Data.DataView> je vytvořen, a znovu jakékoli vlastnosti řazení nebo filtrování jsou změny. Další informace o filtrování a řazení s <xref:System.Data.DataView>, najdete v části [filtrování s DataView](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md) a [řazení s DataView](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md).  
  
 Pokud chcete výsledky konkrétní dotaz na data, oproti Pokud dynamické zobrazení podmnožinu dat, můžete použít <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> metody <xref:System.Data.DataView>, nikoli nastavení <xref:System.Data.DataView.RowFilter%2A> vlastnost. <xref:System.Data.DataView.RowFilter%2A> Vlastnost nejlépe slouží v aplikaci vázané na data kde připojeného ovládacího prvku zobrazí filtrované výsledky. Nastavení <xref:System.Data.DataView.RowFilter%2A> vlastnost znovu sestaví index pro data, přidávání režie k vaší aplikaci a snížení výkonu. <xref:System.Data.DataView.Find%2A> a <xref:System.Data.DataView.FindRows%2A> metody použití aktuální index bez nutnosti znovu sestavit index. Pokud chcete volat <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> pouze jednou, měli byste použít stávající <xref:System.Data.DataView>. Pokud chcete volat <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> vícekrát, měli byste vytvořit nový <xref:System.Data.DataView> znovu sestavit index na sloupci, kterou chcete hledat na a pak zavolají <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> metody. Další informace o <xref:System.Data.DataView.Find%2A> a <xref:System.Data.DataView.FindRows%2A> metody, najdete v části [hledání řádky](../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).  
  
 Následující příklad používá <xref:System.Data.DataView.Find%2A> metody k vyhledání kontakt s příjmení "Zhu".  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryorderbyfind)]
 [!code-vb[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryorderbyfind)]  
  
 Následující příklad používá <xref:System.Data.DataView.FindRows%2A> metody k vyhledání všech red barevné produkty.  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryfindrows)]
 [!code-vb[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryfindrows)]  
  
## <a name="aspnet"></a>ASP.NET  
 Technologie ASP.NET má mechanismus ukládání do mezipaměti, která umožňuje ukládat objekty, které vyžadují rozsáhlé serveru zdrojů pro vytvoření v paměti. Ukládání do mezipaměti tyto typy prostředků může výrazně zlepšit výkon aplikace. Ukládání do mezipaměti je implementované <xref:System.Web.Caching.Cache> třídy s instancemi mezipaměti, které jsou soukromé pro každou aplikaci. Vzhledem k tomu, že vytvoření nové <xref:System.Data.DataView> objekt může být náročné, můžete chtít použít funkce ve webových aplikacích mezipaměti, aby <xref:System.Data.DataView> není nutné znovu sestavit pokaždé, když se aktualizují webové stránky.  
  
 V následujícím příkladu <xref:System.Data.DataView> se uloží do mezipaměti, takže není nutné data znovu seřadit při aktualizaci stránky.  
  
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
 [Datová vazba a LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
