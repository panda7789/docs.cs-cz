---
title: Řazení pomocí zobrazení dat (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885b3b7b-51c1-42b3-bb29-b925f4f69a6f
ms.openlocfilehash: 481a56f923c4218cd8689c578ce990785aee0ab3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782720"
---
# <a name="sorting-with-dataview-linq-to-dataset"></a>Řazení pomocí zobrazení dat (LINQ to DataSet)
Možnost řadit data na základě určitých kritérií a potom data prezentovat klientovi prostřednictvím ovládacího prvku uživatelského rozhraní je důležitým aspektem datových vazeb. <xref:System.Data.DataView>nabízí několik způsobů řazení dat a vrácení řádků dat seřazených podle konkrétních kritérií řazení. Kromě funkcí <xref:System.Data.DataView> řazení založených na řetězci vám také umožní používat [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] výrazy pro kritéria řazení. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]výrazy umožňují mnohem složitější a výkonné operace řazení než řazení založené na řetězci. Toto téma popisuje oba přístupy k řazení pomocí <xref:System.Data.DataView>.  
  
## <a name="creating-dataview-from-a-query-with-sorting-information"></a>Vytvoření objektu DataView z dotazu s informacemi o řazení  
 <xref:System.Data.DataView> Objekt lze vytvořit z LINQ to DataSetho dotazu. <xref:System.Linq.Enumerable.OrderBy%2A>Pokud tento dotaz obsahuje klauzuli, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.ThenBy%2A>nebo <xref:System.Linq.Enumerable.ThenByDescending%2A> , <xref:System.Data.DataView>jsou výrazy v těchto klauzulích použity jako základ pro řazení dat v. Například pokud dotaz obsahuje `Order By…`klauzule a `Then By…` , výsledná <xref:System.Data.DataView> data budou řadit podle obou zadaných sloupců.  
  
 Řazení založené na výrazu nabízí výkonnější a složitější řazení než zjednodušené řazení založené na řetězcích. Všimněte si, že řazení založené na řetězcích a výrazech se vzájemně vylučují. Pokud je založen <xref:System.Data.DataView.Sort%2A> na typu <xref:System.Data.DataView> String po vytvoření z dotazu, filtr založený na výrazu odvozený z dotazu je vymazán a nemůže být resetován.  
  
 Index pro <xref:System.Data.DataView> je sestaven <xref:System.Data.DataView> při vytvoření a při změně jakékoli informace o řazení nebo filtrování. Dosáhnete nejlepšího výkonu tím, že zadáte kritéria řazení v LINQ to DataSet dotaz, <xref:System.Data.DataView> ze kterého se vytvoří, a neupravují informace o řazení později. Další informace najdete v tématu [výkon objektu DataView](dataview-performance.md).  
  
> [!NOTE]
> Ve většině případů výrazy použité pro řazení by neměly mít vedlejší účinky a musí být deterministické. Výrazy by neměly obsahovat ani žádnou logiku, která závisí na nastaveném počtu spuštění, protože operace řazení mohou být provedeny libovolným počtem opakování.  
  
### <a name="example"></a>Příklad  
 Následující příklad vyhledá tabulku SalesOrderHeader a seřadí vrácené řádky podle data objednávky; Vytvoří z tohoto dotazu a váže <xref:System.Data.DataView> <xref:System.Windows.Forms.BindingSource>na. <xref:System.Data.DataView>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby)]  
  
### <a name="example"></a>Příklad  
 Následující příklad dotazuje tabulku SalesOrderHeader a objedná vrácený řádek podle celkové dlužné částky; Vytvoří z tohoto dotazu a váže <xref:System.Data.DataView> <xref:System.Windows.Forms.BindingSource>na. <xref:System.Data.DataView>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby2)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby2)]  
  
### <a name="example"></a>Příklad  
 V následujícím příkladu se dotazuje na tabulku SalesOrderDetail a objednávky vrácených řádků podle množství objednávek a pak podle ID prodejní objednávky. Vytvoří z tohoto dotazu a váže <xref:System.Data.DataView> <xref:System.Windows.Forms.BindingSource>na. <xref:System.Data.DataView>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderbythenby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderbythenby)]  
  
## <a name="using-the-string-based-sort-property"></a>Použití vlastnosti řazení založené na řetězci  
 Funkce řazení založené na řetězcích <xref:System.Data.DataView> stále funguje s LINQ to DataSet. Po vytvoření z LINQ to DataSetho dotazu můžete <xref:System.Data.DataView.Sort%2A> použít vlastnost k <xref:System.Data.DataView>nastavení řazení v. <xref:System.Data.DataView>  
  
 Funkce řazení založené na řetězci a na základě výrazů se vzájemně vylučují. Nastavením vlastnosti se zruší řazení založené na výrazu zděděné z dotazu <xref:System.Data.DataView> , ze kterého byl vytvořen. <xref:System.Data.DataView.Sort%2A>  
  
 Další informace o filtrování na základě <xref:System.Data.DataView.Sort%2A> řetězců najdete v tématu [řazení a filtrování dat](./dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
### <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Data.DataView> z tabulky kontaktů a seřadí řádky podle příjmení v sestupném pořadí a křestní jméno ve vzestupném pořadí:  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
### <a name="example"></a>Příklad  
 Následující příklad vyhledá v tabulce kontaktů poslední názvy začínající písmenem "S".  A je vytvořen z tohoto dotazu a svázán <xref:System.Windows.Forms.BindingSource> s objektem. <xref:System.Data.DataView>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="clearing-the-sort"></a>Mazání řazení  
 Informace <xref:System.Data.DataView> o řazení lze po nastavení <xref:System.Data.DataView.Sort%2A> pomocí vlastnosti vymazat. Existují dva způsoby, jak vymazat informace o řazení v <xref:System.Data.DataView>nástroji:  
  
- Nastavte <xref:System.Data.DataView.Sort%2A> vlastnost `null`.  
  
- <xref:System.Data.DataView.Sort%2A> Nastavte vlastnost na prázdný řetězec.  
  
### <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Data.DataView> z dotazu a vymaže řazení <xref:System.Data.DataView.Sort%2A> nastavením vlastnosti na prázdný řetězec:  
  
 [!code-csharp[DP DataView Samples#LDVClearSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort)]
 [!code-vb[DP DataView Samples#LDVClearSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort)]  
  
### <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Data.DataView> z tabulky kontaktů a <xref:System.Data.DataView.Sort%2A> nastaví vlastnost na hodnotu seřadit podle příjmení v sestupném pořadí. Informace o řazení se pak vymažou <xref:System.Data.DataView.Sort%2A> nastavením vlastnosti na: `null`  
  
 [!code-csharp[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort2)]
 [!code-vb[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort2)]  
  
## <a name="see-also"></a>Viz také:

- [Datová vazba a LINQ to DataSet](data-binding-and-linq-to-dataset.md)
- [Filtrování se zobrazením dat](filtering-with-dataview-linq-to-dataset.md)
- [Řazení dat](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb546145(v=vs.120))
