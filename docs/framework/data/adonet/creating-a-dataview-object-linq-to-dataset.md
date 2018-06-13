---
title: Vytvoření objektu DataView (LINQ na DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76057508-e12d-4779-a707-06a4c2568acf
ms.openlocfilehash: ee4005d6f7d8899b19b2bcc5c62501570165f03e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759176"
---
# <a name="creating-a-dataview-object-linq-to-dataset"></a>Vytvoření objektu DataView (LINQ na DataSet)
Existují dva způsoby, jak vytvořit <xref:System.Data.DataView> v [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kontextu. Můžete vytvořit <xref:System.Data.DataView> z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotaz přes <xref:System.Data.DataTable>, nebo si můžete vytvořit z představuje zadaný nebo beztypové <xref:System.Data.DataTable>. V obou případech můžete vytvořit <xref:System.Data.DataView> pomocí jedné z <xref:System.Data.DataTableExtensions.AsDataView%2A> rozšiřující metody; <xref:System.Data.DataView> není zkonstruovatelný přímo v [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kontextu.  
  
 Po <xref:System.Data.DataView> byl vytvořen, můžete svázat do ovládacího prvku uživatelského rozhraní v aplikaci Windows forms nebo aplikace ASP.NET, nebo změnit filtrování a řazení nastavení.  
  
 <xref:System.Data.DataView> Vytvoří index, který výrazně zvyšuje výkon operací, které mohou používat index, jako je například filtrování a řazení. Index <xref:System.Data.DataView> vychází i v případě <xref:System.Data.DataView> je vytvořena a při řazení nebo filtrování je upravit informace. Vytváření <xref:System.Data.DataView> a následně nastavení toto řazení nebo filtrování informace později způsobí index, který má být sestaven alespoň dvakrát: Jakmile při <xref:System.Data.DataView> je vytvořen, a znovu jakékoli vlastnosti řazení nebo filtrování jsou změny.  
  
 Další informace o filtrování a řazení s <xref:System.Data.DataView>, najdete v části [filtrování s DataView](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md) a [řazení s DataView](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md).  
  
## <a name="creating-dataview-from-a-linq-to-dataset-query"></a>Vytváření zobrazení dat z LINQ dotaz datové sady  
 A <xref:System.Data.DataView> objekt můžete vytvořit z výsledků [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotaz, kde jsou výsledky projekci <xref:System.Data.DataRow> objekty. Nově vytvořený <xref:System.Data.DataView> dědí filtrování a řazení informace z je vytvořený z dotazu.  
  
> [!NOTE]
>  Výrazy použité pro filtrování a řazení ve většině případů by neměl mít vedlejší efekty a musí být deterministický. Výrazy nesmí obsahovat žádný logiky, která závisí na se stanoveným počtem spuštěních, jak může být řazení a filtrování operací provést jakékoli stanovený počet.  
  
 Vytváření <xref:System.Data.DataView> z dotaz, který vrátí anonymní typy nebo dotazy, které provádějí operace spojení není podporován.  
  
 Jsou podporovány pouze následující operátory dotazu v dotazu použít k vytvoření <xref:System.Data.DataView>:  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.Cast%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.OrderBy%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.OrderByDescending%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.Select%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.ThenBy%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.ThenByDescending%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.Where%2A>  
  
 Všimněte si, že pokud <xref:System.Data.DataView> je vytvořený z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotaz <xref:System.Data.EnumerableRowCollectionExtensions.Select%2A> metoda musí být poslední metodu volat v dotazu. To je znázorněno v následujícím příkladu, který vytvoří <xref:System.Data.DataView> online objednávek seřazený podle celkové termínu:  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquery1)]
 [!code-vb[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquery1)]  
  
 Můžete taky základě řetězec <xref:System.Data.DataView.RowFilter%2A> a <xref:System.Data.DataView.Sort%2A> vlastnosti k filtrování a řazení <xref:System.Data.DataView> po vytvoření z dotazu. Všimněte si, že tato akce vymaže toto řazení a filtrování informace zděděno z dotazu. Následující příklad vytvoří <xref:System.Data.DataView> z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotaz, který filtruje poslední názvy, které začínají je ". Řetězec základě <xref:System.Data.DataView.Sort%2A> je nastavena na seřadit příjmení ve vzestupném pořadí a potom první názvy v sestupném pořadí:  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="creating-a-dataview-from-a-datatable"></a>Vytváření v zobrazení DataView z DataTable  
 Kromě vytvářený z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazu, <xref:System.Data.DataView> objekt můžete vytvořit z <xref:System.Data.DataTable> pomocí <xref:System.Data.DataTableExtensions.AsDataView%2A> metoda.  
  
 Následující příklad vytvoří <xref:System.Data.DataView> z podrobnosti prodejní objednávky tabulky a nastaví jej jako zdroj dat <xref:System.Windows.Forms.BindingSource> objektu. Tento objekt funguje jako proxy pro <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromtable)]
 [!code-vb[DP DataView Samples#CreateLDVFromTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromtable)]  
  
 Filtrování a řazení lze nastavit u <xref:System.Data.DataView> po vytvoření z <xref:System.Data.DataTable>. Následující příklad vytvoří <xref:System.Data.DataView> z tabulky Kontakt a nastaví <xref:System.Data.DataView.Sort%2A> vlastnost, která má seřadit příjmení ve vzestupném pořadí a potom první názvy v sestupném pořadí:  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
 Však dojde ke ztrátě výkonu, která se dodává s nastavením <xref:System.Data.DataView.RowFilter%2A> nebo <xref:System.Data.DataView.Sort%2A> vlastnost po <xref:System.Data.DataView> byl vytvořen z dotazu, protože <xref:System.Data.DataView> vytvoří index pro podporu filtrování a řazení. Nastavení <xref:System.Data.DataView.RowFilter%2A> nebo <xref:System.Data.DataView.Sort%2A> vlastnost znovu sestaví index pro data, přidávání režie k vaší aplikaci a snížení výkonu. Pokud je to možné, je lepší zadejte filtrování a řazení informace při prvním vytváření <xref:System.Data.DataView> a neměli upravovat ji později.  
  
## <a name="see-also"></a>Viz také  
 [Datová vazba a LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)  
 [Filtrování se zobrazením dat](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)  
 [Řazení se zobrazením dat](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)
