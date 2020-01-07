---
title: Řazení pomocí zobrazení dat (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885b3b7b-51c1-42b3-bb29-b925f4f69a6f
ms.openlocfilehash: 2998de7dee34f9b5410bfe53988e0b7cfa797784
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634752"
---
# <a name="sorting-with-dataview-linq-to-dataset"></a>Řazení pomocí zobrazení dat (LINQ to DataSet)
Možnost řadit data na základě určitých kritérií a potom data prezentovat klientovi prostřednictvím ovládacího prvku uživatelského rozhraní je důležitým aspektem datových vazeb. <xref:System.Data.DataView> poskytuje několik způsobů řazení dat a vrácení řádků dat seřazených podle konkrétních kritérií řazení. Kromě funkcí řazení založených na řetězcích, <xref:System.Data.DataView> také umožňuje používat výrazy LINQ (Language-Integrated Query) pro kritéria řazení. Výrazy LINQ umožňují mnohem složitější a výkonné operace řazení než řazení založené na řetězci. Toto téma popisuje oba přístupy k řazení pomocí <xref:System.Data.DataView>.  
  
## <a name="creating-dataview-from-a-query-with-sorting-information"></a>Vytvoření objektu DataView z dotazu s informacemi o řazení  
 Objekt <xref:System.Data.DataView> lze vytvořit z dotazu LINQ to DataSet. Pokud tento dotaz obsahuje klauzuli <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.ThenBy%2A>nebo <xref:System.Linq.Enumerable.ThenByDescending%2A>, výrazy v těchto klauzulích se používají jako základ pro řazení dat v <xref:System.Data.DataView>. Pokud například dotaz obsahuje klauzule `Order By…`a `Then By…`, výsledná <xref:System.Data.DataView> budou data seřadit podle obou zadaných sloupců.  
  
 Řazení založené na výrazu nabízí výkonnější a složitější řazení než zjednodušené řazení založené na řetězcích. Všimněte si, že řazení založené na řetězcích a výrazech se vzájemně vylučují. Pokud je <xref:System.Data.DataView.Sort%2A> založené na řetězci nastaveno po vytvoření <xref:System.Data.DataView> z dotazu, filtr založený na výrazu odvozený z dotazu je vymazán a nelze jej resetovat.  
  
 Index pro <xref:System.Data.DataView> je sestaven při vytvoření <xref:System.Data.DataView> a při změně jakékoli informace o řazení nebo filtrování. Dosáhnete nejlepšího výkonu tím, že zadáte kritéria řazení v LINQ to DataSet dotaz, ze kterého se <xref:System.Data.DataView> vytvoří, a neupravují informace o řazení později. Další informace najdete v tématu [výkon objektu DataView](dataview-performance.md).  
  
> [!NOTE]
> Ve většině případů výrazy použité pro řazení by neměly mít vedlejší účinky a musí být deterministické. Výrazy by neměly obsahovat ani žádnou logiku, která závisí na nastaveném počtu spuštění, protože operace řazení mohou být provedeny libovolným počtem opakování.  
  
### <a name="example"></a>Příklad  
 Následující příklad vyhledá tabulku SalesOrderHeader a seřadí vrácené řádky podle data objednávky; Vytvoří z tohoto dotazu <xref:System.Data.DataView>. a váže <xref:System.Data.DataView> k <xref:System.Windows.Forms.BindingSource>.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby)]  
  
### <a name="example"></a>Příklad  
 Následující příklad dotazuje tabulku SalesOrderHeader a objedná vrácený řádek podle celkové dlužné částky; Vytvoří z tohoto dotazu <xref:System.Data.DataView>. a váže <xref:System.Data.DataView> k <xref:System.Windows.Forms.BindingSource>.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby2)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby2)]  
  
### <a name="example"></a>Příklad  
 V následujícím příkladu se dotazuje na tabulku SalesOrderDetail a objednávky vrácených řádků podle množství objednávek a pak podle ID prodejní objednávky. Vytvoří z tohoto dotazu <xref:System.Data.DataView>. a váže <xref:System.Data.DataView> k <xref:System.Windows.Forms.BindingSource>.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderbythenby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderbythenby)]  
  
## <a name="using-the-string-based-sort-property"></a>Použití vlastnosti řazení založené na řetězci  
 Funkce řazení na základě řetězců <xref:System.Data.DataView> stále pracuje s LINQ to DataSet. Po vytvoření <xref:System.Data.DataView> z dotazu LINQ to DataSet můžete použít vlastnost <xref:System.Data.DataView.Sort%2A> k nastavení řazení pro <xref:System.Data.DataView>.  
  
 Funkce řazení založené na řetězci a na základě výrazů se vzájemně vylučují. Nastavením vlastnosti <xref:System.Data.DataView.Sort%2A> se zruší řazení založené na výrazu děděné z dotazu, ze kterého byla vytvořena <xref:System.Data.DataView>.  
  
 Další informace o filtrování <xref:System.Data.DataView.Sort%2A> založeném na řetězcích naleznete v tématu [řazení a filtrování dat](./dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
### <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Data.DataView> z tabulky Contact a seřadí řádky podle příjmení v sestupném pořadí a křestní jméno ve vzestupném pořadí:  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
### <a name="example"></a>Příklad  
 Následující příklad vyhledá v tabulce kontaktů poslední názvy začínající písmenem "S".  Z tohoto dotazu je vytvořen <xref:System.Data.DataView> a svázán s objektem <xref:System.Windows.Forms.BindingSource>.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="clearing-the-sort"></a>Mazání řazení  
 Informace o řazení u <xref:System.Data.DataView> lze vymazat poté, co byly nastaveny pomocí vlastnosti <xref:System.Data.DataView.Sort%2A>. Existují dva způsoby, jak vymazat informace o řazení v <xref:System.Data.DataView>:  
  
- Nastavte <xref:System.Data.DataView.Sort%2A> vlastnost `null`.  
  
- Vlastnost <xref:System.Data.DataView.Sort%2A> nastavte na prázdný řetězec.  
  
### <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Data.DataView> z dotazu a vymaže řazení nastavením vlastnosti <xref:System.Data.DataView.Sort%2A> na prázdný řetězec:  
  
 [!code-csharp[DP DataView Samples#LDVClearSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort)]
 [!code-vb[DP DataView Samples#LDVClearSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort)]  
  
### <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Data.DataView> z tabulky kontaktů a nastaví vlastnost <xref:System.Data.DataView.Sort%2A> tak, aby se seřadila podle příjmení v sestupném pořadí. Informace o řazení se pak vymažou nastavením vlastnosti <xref:System.Data.DataView.Sort%2A> na `null`:  
  
 [!code-csharp[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort2)]
 [!code-vb[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort2)]  
  
## <a name="see-also"></a>Viz také:

- [Datová vazba a LINQ to DataSet](data-binding-and-linq-to-dataset.md)
- [Filtrování se zobrazením dat](filtering-with-dataview-linq-to-dataset.md)
- [Řazení dat](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb546145(v=vs.120))
