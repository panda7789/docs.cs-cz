---
title: Vytvoření objektu DataView (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76057508-e12d-4779-a707-06a4c2568acf
ms.openlocfilehash: 3f53c9889e1fdae6c582e8d4a17f640e425e6594
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734432"
---
# <a name="creating-a-dataview-object-linq-to-dataset"></a>Vytvoření objektu DataView (LINQ to DataSet)
Existují dva způsoby, jak vytvořit <xref:System.Data.DataView> v [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kontextu. Můžete vytvořit <xref:System.Data.DataView> z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotaz nad <xref:System.Data.DataTable>, nebo si můžete vytvořit z typovaného nebo netypové <xref:System.Data.DataTable>. V obou případech můžete vytvořit <xref:System.Data.DataView> pomocí jedné z <xref:System.Data.DataTableExtensions.AsDataView%2A> rozšiřující metody; <xref:System.Data.DataView> není přímo constructible v [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kontextu.  
  
 Po <xref:System.Data.DataView> byl vytvořen, můžete svázat ovládací prvek uživatelského rozhraní ve formulářové aplikaci Windows nebo aplikace ASP.NET, nebo změnit filtrování a řazení nastavení.  
  
 <xref:System.Data.DataView> Vytvoří index, který výrazně zvyšuje výkon operací, které můžete použít index, jako je například filtrování a řazení. Index <xref:System.Data.DataView> tvoříme tak i v případě <xref:System.Data.DataView> se vytvoří a při řazení nebo filtrování informace změněny. Vytváření <xref:System.Data.DataView> a nastavení řazení nebo filtrování informací později způsobí indexu, který má být sestaven alespoň dvakrát: až při <xref:System.Data.DataView> je vytvořen, a znovu když některé vlastnosti řazení nebo filtrování se upraví.  
  
 Další informace o filtrování a řazení ovládacími <xref:System.Data.DataView>, naleznete v tématu [filtrování se zobrazením dat](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md) a [řazení se zobrazením dat](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md).  
  
## <a name="creating-dataview-from-a-linq-to-dataset-query"></a>Vytváření zobrazení dat z LINQ k datové sadě dotazu  
 A <xref:System.Data.DataView> objekt můžete vytvořit z výsledků [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotaz, kde jsou výsledky projekci <xref:System.Data.DataRow> objekty. Nově vytvořený <xref:System.Data.DataView> dědí filtrování a řazení informace z dotazu je vytvořen z.  
  
> [!NOTE]
>  Výrazy použité pro filtrování a řazení ve většině případů by neměl mít vedlejší účinky a musí být deterministický. Výrazů nesmí obsahovat žádný logiku, která závisí na stanovený počet spuštění, řazení a filtrování operací může být spuštěn libovolný počet pokusů.  
  
 Vytváření <xref:System.Data.DataView> z dotazu, který vrátí anonymní typy nebo dotazy, které provádějí operace spojení se nepodporuje.  
  
 Jsou podporovány pouze následující operátory dotazu v dotazu použít k vytvoření <xref:System.Data.DataView>:  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.Cast%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.OrderBy%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.OrderByDescending%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.Select%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.ThenBy%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.ThenByDescending%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.Where%2A>  
  
 Všimněte si, že <xref:System.Data.DataView> je vytvořený z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotaz <xref:System.Data.EnumerableRowCollectionExtensions.Select%2A> metoda musí být finální metodou volána v dotazu. To je ukázáno v následujícím příkladu, který vytvoří <xref:System.Data.DataView> online objednávek, seřazené podle dlužná částka:  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquery1)]
 [!code-vb[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquery1)]  
  
 Můžete také použít řetězec podle <xref:System.Data.DataView.RowFilter%2A> a <xref:System.Data.DataView.Sort%2A> vlastností pro filtrování a řazení <xref:System.Data.DataView> po vytvoření z dotazu. Všimněte si, že touto akcí vymažete, řazení a filtrování informací zděděno z dotazu. Následující příklad vytvoří <xref:System.Data.DataView> z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotaz, který filtruje podle příjmení, které začínají na ". Založené na řetězci <xref:System.Data.DataView.Sort%2A> je nastavena na řazení podle příjmení ve vzestupném pořadí a pak křestní jména v sestupném pořadí:  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="creating-a-dataview-from-a-datatable"></a>Vytvoření zobrazení dat z objektu DataTable  
 Kromě vytváří z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazu, <xref:System.Data.DataView> objekt můžete vytvořit z <xref:System.Data.DataTable> pomocí <xref:System.Data.DataTableExtensions.AsDataView%2A> metoda.  
  
 Následující příklad vytvoří <xref:System.Data.DataView> z podrobnosti prodejní objednávky tabulky a nastaví jej jako zdroj dat <xref:System.Windows.Forms.BindingSource> objektu. Tento objekt funguje jako proxy pro <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromtable)]
 [!code-vb[DP DataView Samples#CreateLDVFromTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromtable)]  
  
 Filtrování a řazení lze nastavit na <xref:System.Data.DataView> po vytvoření z <xref:System.Data.DataTable>. Následující příklad vytvoří <xref:System.Data.DataView> z tabulky Kontakt a nastaví <xref:System.Data.DataView.Sort%2A> vlastnost řazení podle příjmení ve vzestupném pořadí a pak křestní jména v sestupném pořadí:  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
 Však dojde ke ztrátě výkonu, která se dodává s nastavením <xref:System.Data.DataView.RowFilter%2A> nebo <xref:System.Data.DataView.Sort%2A> vlastnost po <xref:System.Data.DataView> byla vytvořena z dotazu, protože <xref:System.Data.DataView> vytvoří index pro podporu operace filtrování a řazení. Nastavení <xref:System.Data.DataView.RowFilter%2A> nebo <xref:System.Data.DataView.Sort%2A> vlastnost znovu sestaví index pro data, přidání režie pro vaši aplikaci a snížit výkon. Pokud je to možné, je lepší zadejte filtrování a řazení informace při prvním vytvoření <xref:System.Data.DataView> a neměli upravovat později.  
  
## <a name="see-also"></a>Viz také:
- [Datová vazba a LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
- [Filtrování se zobrazením dat](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)
- [Řazení se zobrazením dat](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)
