---
title: Řazení se zobrazením dat (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885b3b7b-51c1-42b3-bb29-b925f4f69a6f
ms.openlocfilehash: 9f69b64088093bbdd46239a26f16aeea50b6dee7
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44177752"
---
# <a name="sorting-with-dataview-linq-to-dataset"></a>Řazení se zobrazením dat (LINQ to DataSet)
Možnost řadit data podle určitých kritérií a potom prezentovat data do klienta prostřednictvím ovládacího prvku uživatelského rozhraní je důležitou součástí datové vazby. <xref:System.Data.DataView> poskytuje několik způsobů, jak řadit data a vrátí řádky dat, které jsou seřazené podle konkrétní kritéria řazení. Kromě jeho založené na řetězci možnosti, řazení <xref:System.Data.DataView> také umožňuje používat [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] výrazy řazení kritérií. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] výrazy umožňují mnohem komplexnější a výkonné operace řazení než založené na řetězci řazení. Toto téma popisuje oba přístupy k řazení pomocí <xref:System.Data.DataView>.  
  
## <a name="creating-dataview-from-a-query-with-sorting-information"></a>Vytváření zobrazení dat z dotazu s řazením informace  
 A <xref:System.Data.DataView> objekt můžete vytvořit z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazu. Pokud tento dotaz obsahuje <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.ThenBy%2A>, nebo <xref:System.Linq.Enumerable.ThenByDescending%2A> výrazy v těchto klauzulí jsou použity jako základ pro řazení dat v klauzuli <xref:System.Data.DataView>. Například, pokud dotaz obsahuje `Order By…`a `Then By…` klauzule, výsledná <xref:System.Data.DataView> by order oba sloupce zadaná data.  
  
 Řazení podle výrazu nabízí výkonnější a komplexní řazení než založené na řetězci řazení jednodušší. Všimněte si, že založených na řetězec a výraz řazení se vzájemně vylučují. Pokud založené na řetězci <xref:System.Data.DataView.Sort%2A> se nastaví po <xref:System.Data.DataView> je vytvořen z dotazu, založené na výrazu filtru odvodit z dotazu je vymazána a nelze jej obnovit.  
  
 Index <xref:System.Data.DataView> tvoříme tak i v případě <xref:System.Data.DataView> se vytvoří a při řazení nebo filtrování informace změněny. Získání nejlepšího výkonu dosáhnete zadáním kritérií pro řazení [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotaz, který <xref:System.Data.DataView> je vytvořený z a místo abyste upravili řazení informace později. Další informace najdete v tématu [výkon zobrazení dat](../../../../docs/framework/data/adonet/dataview-performance.md).  
  
> [!NOTE]
>  Výrazy použité pro řazení ve většině případů by neměl mít vedlejší účinky a musí být deterministický. Výrazů nesmí obsahovat žádný logiku, která závisí na stanovený počet spuštění, protože operace řazení může být spuštěn libovolný počet pokusů.  
  
### <a name="example"></a>Příklad  
 V následujícím příkladu dotazuje tabulku SalesOrderHeader a řadí vrácené řádky podle pořadí date. vytvoří <xref:System.Data.DataView> z dotazu; a vytvoří vazbu <xref:System.Data.DataView> k <xref:System.Windows.Forms.BindingSource>.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby)]  
  
### <a name="example"></a>Příklad  
 V následujícím příkladu dotazuje tabulku SalesOrderHeader a řadí podle celková částka splatná; vrácený řádek vytvoří <xref:System.Data.DataView> z dotazu; a vytvoří vazbu <xref:System.Data.DataView> k <xref:System.Windows.Forms.BindingSource>.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby2)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby2)]  
  
### <a name="example"></a>Příklad  
 V následujícím příkladu dotazuje tabulku Podrobnosti prodejní objednávky a řadí vrácené řádky podle množství objednávky a pak podle ID prodejní objednávky; vytvoří <xref:System.Data.DataView> z dotazu; a vytvoří vazbu <xref:System.Data.DataView> k <xref:System.Windows.Forms.BindingSource>.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderbythenby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderbythenby)]  
  
## <a name="using-the-string-based-sort-property"></a>Pomocí vlastnosti založené na řetězci řazení  
 Založené na řetězci řazení funkce <xref:System.Data.DataView> stále funguje s [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. Po <xref:System.Data.DataView> byl vytvořen z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazu, můžete použít <xref:System.Data.DataView.Sort%2A> vlastnost pro nastavení řazení na <xref:System.Data.DataView>.  
  
 Založené na řetězci a založené na výrazu funkce řazení se vzájemně vylučují. Nastavení <xref:System.Data.DataView.Sort%2A> vlastnost vymaže výrazu podle řazení zděděno z dotazu, který <xref:System.Data.DataView> byl vytvořen z.  
  
 Další informace o založené na řetězci <xref:System.Data.DataView.Sort%2A> filtrování, najdete v článku [řazení a filtrování dat](../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
### <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Data.DataView> z kontaktu tabulky a řádky jsou řazeny podle příjmení v sestupném pořadí a pak ve vzestupném pořadí křestní jméno:  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
### <a name="example"></a>Příklad  
 V následujícím příkladu se dotazuje tabulky Kontakt pro poslední názvy, které začínají písmenem "S".  A <xref:System.Data.DataView> je vytvořena z dotazu a vázán na <xref:System.Windows.Forms.BindingSource> objektu.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="clearing-the-sort"></a>Vymazání řazení  
 Řazení informace o <xref:System.Data.DataView> můžete vymazat, jakmile byla nastavena, pomocí <xref:System.Data.DataView.Sort%2A> vlastnost. Existují dva způsoby, jak vymazat řazení informace v <xref:System.Data.DataView>:  
  
-   Nastavte <xref:System.Data.DataView.Sort%2A> vlastnost `null`.  
  
-   Nastavte <xref:System.Data.DataView.Sort%2A> vlastnost na prázdný řetězec.  
  
### <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Data.DataView> z dotazu a vymaže řazení tak, že nastavíte <xref:System.Data.DataView.Sort%2A> vlastnost na prázdný řetězec:  
  
 [!code-csharp[DP DataView Samples#LDVClearSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort)]
 [!code-vb[DP DataView Samples#LDVClearSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort)]  
  
### <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Data.DataView> z tabulky Kontakt a nastaví <xref:System.Data.DataView.Sort%2A> vlastnost řazení podle jména v sestupném pořadí. Informace o řazení je potom vymazána tak, že nastavíte <xref:System.Data.DataView.Sort%2A> vlastnost `null`:  
  
 [!code-csharp[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort2)]
 [!code-vb[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort2)]  
  
## <a name="see-also"></a>Viz také  
 [Datová vazba a LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)  
 [Filtrování se zobrazením dat](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)  
 [Řazení dat](https://msdn.microsoft.com/library/6d76e2d7-b418-49b5-ac78-2bcd61169c48)
