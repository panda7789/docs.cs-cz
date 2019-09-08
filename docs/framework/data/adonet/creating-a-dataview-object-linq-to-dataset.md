---
title: Vytvoření objektu DataView (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76057508-e12d-4779-a707-06a4c2568acf
ms.openlocfilehash: 054898a3520cbc2b607fc26b94b72b9896ad9c71
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786681"
---
# <a name="creating-a-dataview-object-linq-to-dataset"></a>Vytvoření objektu DataView (LINQ to DataSet)
Existují dva způsoby, jak vytvořit <xref:System.Data.DataView> v kontextu LINQ to DataSet. Můžete vytvořit <xref:System.Data.DataView> dotaz <xref:System.Data.DataTable>z LINQ to DataSet nebo ho můžete vytvořit ze zadaného nebo netypového <xref:System.Data.DataTable>typu. V obou případech vytvoříte <xref:System.Data.DataView> pomocí jedné <xref:System.Data.DataTableExtensions.AsDataView%2A> z rozšiřujících metod; <xref:System.Data.DataView> není přímo constructible v kontextu LINQ to DataSet.  
  
 <xref:System.Data.DataView> Po vytvoření je můžete navazovat na ovládací prvek uživatelského rozhraní v aplikaci Windows Forms nebo v aplikaci ASP.NET nebo změnit nastavení filtrování a řazení.  
  
 <xref:System.Data.DataView>vytvoří index, který významně zvyšuje výkon operací, které mohou používat index, jako je například filtrování a řazení. Index pro <xref:System.Data.DataView> je sestaven <xref:System.Data.DataView> při vytvoření a při změně jakékoli informace o řazení nebo filtrování. Vytvoření a nastavení informací o řazení nebo filtrování později způsobí, že se index sestaví alespoň dvakrát: Jakmile <xref:System.Data.DataView> se vytvoří, a znovu, když se změní kterákoli z vlastností řazení nebo filtru. <xref:System.Data.DataView>  
  
 Další informace o filtrování a řazení pomocí <xref:System.Data.DataView>nástroje naleznete v tématu [filtrování pomocí zobrazení dat](filtering-with-dataview-linq-to-dataset.md) a [řazení pomocí objektu DataView](sorting-with-dataview-linq-to-dataset.md).  
  
## <a name="creating-dataview-from-a-linq-to-dataset-query"></a>Vytvoření objektu DataView z LINQ to DataSetho dotazu  
 Objekt lze vytvořit z výsledků LINQ to DataSet dotaz, kde jsou výsledky <xref:System.Data.DataRow> projekcí objektů. <xref:System.Data.DataView> Nově vytvořená <xref:System.Data.DataView> metoda zdědí informace o filtrování a řazení z dotazu, ze kterého je vytvořena.  
  
> [!NOTE]
> Ve většině případů výrazy používané pro filtrování a řazení by neměly mít vedlejší účinky a musí být deterministické. Výrazy by neměly obsahovat ani žádnou logiku, která závisí na nastaveném počtu spuštění, protože operace řazení a filtrování se můžou provádět několikrát.  
  
 <xref:System.Data.DataView> Vytvoření z dotazu, který vrátí anonymní typy nebo dotazy, které provádějí operace JOIN, není podporováno.  
  
 V dotazu, který slouží k vytvoření <xref:System.Data.DataView>, jsou podporovány pouze následující operátory dotazu:  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.Cast%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.OrderBy%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.OrderByDescending%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.Select%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.ThenBy%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.ThenByDescending%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.Where%2A>  
  
 Všimněte si, že <xref:System.Data.DataView> když je vytvořen z LINQ to DataSet dotaz, <xref:System.Data.EnumerableRowCollectionExtensions.Select%2A> Metoda musí být poslední metodou volanou v dotazu. To je znázorněno v následujícím příkladu, který vytváří <xref:System.Data.DataView> online objednávky seřazené podle celkové splatnosti:  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquery1)]
 [!code-vb[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquery1)]  
  
 Můžete také použít řetězcové <xref:System.Data.DataView.RowFilter%2A> a <xref:System.Data.DataView.Sort%2A> vlastnosti <xref:System.Data.DataView> pro filtrování a řazení po jeho vytvoření z dotazu. Všimněte si, že tato akce vymaže informace o řazení a filtrování děděné z dotazu. Následující příklad vytvoří <xref:System.Data.DataView> z LINQ to DataSet dotaz, který filtruje podle příjmení, které začínají na ' '. Vlastnost založená <xref:System.Data.DataView.Sort%2A> na řetězci je nastavena na hodnotu seřadit podle příjmení ve vzestupném pořadí a pak křestní jména v sestupném pořadí:  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="creating-a-dataview-from-a-datatable"></a>Vytvoření zobrazení dat z DataTable  
 Kromě vytvoření z LINQ to DataSetho dotazu <xref:System.Data.DataView> lze objekt vytvořit <xref:System.Data.DataTable> pomocí <xref:System.Data.DataTableExtensions.AsDataView%2A> metody.  
  
 Následující příklad vytvoří <xref:System.Data.DataView> z tabulky SalesOrderDetail a nastaví ji jako zdroj <xref:System.Windows.Forms.BindingSource> dat objektu. Tento objekt funguje jako proxy server pro <xref:System.Windows.Forms.DataGridView> ovládací prvek.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromtable)]
 [!code-vb[DP DataView Samples#CreateLDVFromTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromtable)]  
  
 Filtrování a řazení lze nastavit na <xref:System.Data.DataView> základě toho, jak bylo vytvořeno <xref:System.Data.DataTable>z. Následující příklad vytvoří <xref:System.Data.DataView> z tabulky kontaktů a <xref:System.Data.DataView.Sort%2A> nastaví vlastnost pro řazení podle příjmení ve vzestupném pořadí a pak křestní jména v sestupném pořadí:  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
 Nicméně dojde ke ztrátě výkonu, která se <xref:System.Data.DataView.RowFilter%2A> dodává s nastavením vlastnosti nebo <xref:System.Data.DataView.Sort%2A> po <xref:System.Data.DataView> vytvoření z dotazu, protože <xref:System.Data.DataView> sestaví index pro podporu operací filtrování a řazení. <xref:System.Data.DataView.RowFilter%2A> Nastavení nebo <xref:System.Data.DataView.Sort%2A> vlastnost znovu sestaví index pro data, zvyšuje režii aplikace a snižuje výkon. Pokud je to možné, je lepší určit informace o filtrování a řazení při prvním vytvoření <xref:System.Data.DataView> a vyhnout se jeho úpravám.  
  
## <a name="see-also"></a>Viz také:

- [Datová vazba a LINQ to DataSet](data-binding-and-linq-to-dataset.md)
- [Filtrování se zobrazením dat](filtering-with-dataview-linq-to-dataset.md)
- [Řazení se zobrazením dat](sorting-with-dataview-linq-to-dataset.md)
