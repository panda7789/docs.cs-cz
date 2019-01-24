---
title: Výkon zobrazení dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 90820e49-9d46-41f6-9a3d-6c0741bbd8eb
ms.openlocfilehash: 1384103f6ca35bab02280e6019d717a5d2f333cc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684720"
---
# <a name="dataview-performance"></a>Výkon zobrazení dat
Toto téma popisuje použití přinese zlepšení výkonu <xref:System.Data.DataView.Find%2A> a <xref:System.Data.DataView.FindRows%2A> metody <xref:System.Data.DataView> třídy a ukládání do mezipaměti <xref:System.Data.DataView> ve webové aplikaci.  
  
## <a name="find-and-findrows"></a>Najít a FindRows  
 <xref:System.Data.DataView> Vytvoří index. Index obsahuje klíče vytvořené z jednoho nebo více sloupců v tabulce nebo zobrazení. Tyto klíče jsou uložené ve struktuře, která umožňuje <xref:System.Data.DataView> najít řádek nebo řádky, které jsou spojené s klíčovými hodnotami rychle a efektivně. Operace, které používají index, jako je například filtrování a řazení, naleznete v tématu zvýšení výkonu. Index <xref:System.Data.DataView> tvoříme tak i v případě <xref:System.Data.DataView> se vytvoří a při řazení nebo filtrování informace změněny. Vytváření <xref:System.Data.DataView> a nastavení řazení nebo filtrování informací později způsobí indexu, který má být sestaven alespoň dvakrát: až při <xref:System.Data.DataView> je vytvořen, a znovu když některé vlastnosti řazení nebo filtrování se upraví. Další informace o filtrování a řazení ovládacími <xref:System.Data.DataView>, naleznete v tématu [filtrování se zobrazením dat](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md) a [řazení se zobrazením dat](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md).  
  
 Pokud chcete vrátit výsledky konkrétní dotaz na data, jako proti poskytující dynamické zobrazení podmnožinu dat, můžete použít <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> metody <xref:System.Data.DataView>, místo nastavení <xref:System.Data.DataView.RowFilter%2A> vlastnost. <xref:System.Data.DataView.RowFilter%2A> Vlastnost je nejvhodnější v aplikace vázané na data kde vázaného ovládacího prvku zobrazí filtrované výsledky. Nastavení <xref:System.Data.DataView.RowFilter%2A> vlastnost znovu sestaví index pro data, přidání režie pro vaši aplikaci a snížit výkon. <xref:System.Data.DataView.Find%2A> a <xref:System.Data.DataView.FindRows%2A> metody používat aktuální index bez nutnosti index znovu sestavit. Pokud se chystáte zavolat <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> pouze jednou, měli byste použít stávající <xref:System.Data.DataView>. Pokud se chystáte zavolat <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> více než jednou, měli byste vytvořit nový <xref:System.Data.DataView> znovu sestavovat index pro sloupec, který chcete vyhledat a následně zavolat <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> metody. Další informace o <xref:System.Data.DataView.Find%2A> a <xref:System.Data.DataView.FindRows%2A> metody, naleznete v tématu [vyhledání řádků](../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).  
  
 V následujícím příkladu <xref:System.Data.DataView.Find%2A> metody k vyhledání kontakt s příjmení "Zhu".  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryorderbyfind)]
 [!code-vb[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryorderbyfind)]  
  
 V následujícím příkladu <xref:System.Data.DataView.FindRows%2A> metody k vyhledání všech červená barva produktů.  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryfindrows)]
 [!code-vb[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryfindrows)]  
  
## <a name="aspnet"></a>ASP.NET  
 Technologie ASP.NET obsahuje mechanismus ukládání do mezipaměti, která umožňuje ukládat objekty, které vyžadují rozsáhlé server prostředky pro vytvoření v paměti. Ukládání do mezipaměti těchto typů prostředků může výrazně zlepšit výkon aplikace. Ukládání do mezipaměti je implementovaných <xref:System.Web.Caching.Cache> třídy s instancí mezipaměti, které jsou privátní pro danou aplikaci. Vzhledem k tomu, že vytvoření nového <xref:System.Data.DataView> objekt může být náročné, můžete chtít použít funkce ve webových aplikacích mezipaměti tak, aby <xref:System.Data.DataView> není nutné znovu sestavit pokaždé, když se aktualizuje webové stránky.  
  
 V následujícím příkladu <xref:System.Data.DataView> se uloží do mezipaměti, takže není nutné data znovu seřadit při obnovení stránky.  
  
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
- [Datová vazba a LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
