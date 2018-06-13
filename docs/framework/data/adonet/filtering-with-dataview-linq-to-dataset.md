---
title: Filtrování s DataView (LINQ na DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5632d74a-ff53-4ea7-9fe7-4a148eeb1c68
ms.openlocfilehash: b457eb925f636656455ef8f3f02f9d2a78558325
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766098"
---
# <a name="filtering-with-dataview-linq-to-dataset"></a>Filtrování s DataView (LINQ na DataSet)
Možnost filtrování dat pomocí konkrétních kritérií a potom prezentovat data ke klientovi pomocí ovládacího prvku uživatelského rozhraní je důležitým aspektem datové vazby. <xref:System.Data.DataView> poskytuje několik způsobů, jak filtrovat data a vrátit podmnožiny dat řádků kritéria filtru konkrétní schůzku. Kromě základě řetězec možností filtrování <xref:System.Data.DataView> taky poskytuje možnost používat [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] výrazy pro kritéria filtrování. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] výrazy umožňují mnohem složitější a výkonné filtrování operací než filtrování založené na řetězec.  
  
 Existují dva způsoby pro filtrování dat pomocí <xref:System.Data.DataView>:  
  
-   Vytvoření <xref:System.Data.DataView> z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazu místo, kde klauzule.  
  
-   Použít existující, založené na řetězcích Filtrování možností <xref:System.Data.DataView>.  
  
## <a name="creating-dataview-from-a-query-with-filtering-information"></a>Vytváření zobrazení dat z dotazu s informacemi o filtrování  
 A <xref:System.Data.DataView> objekt můžete vytvořit z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazu. Pokud tento dotaz obsahuje `Where` klauzuli <xref:System.Data.DataView> je vytvořena s filtrování informace z dotazu. Výraz v `Where` klauzule slouží k určení, které řádky dat budou zahrnuty do <xref:System.Data.DataView>, a slouží jako základ pro filtr.  
  
 Filtry založené na výrazu nabízí výkonný a komplexní filtrování než jednodušší filtry založené na řetězec. Filtry založené na řetězcích a založené na výrazu se vzájemně vylučují. Když základě řetězec <xref:System.Data.DataView.RowFilter%2A> se nastaví po <xref:System.Data.DataView> je vytvořený z dotazu, výraz se vymaže na základě filtru odvodit z dotazu.  
  
> [!NOTE]
>  Výrazy použité k filtrování ve většině případů by neměl mít vedlejší efekty a musí být deterministický. Výrazy nesmí obsahovat žádný logiky, která závisí na se stanoveným počtem spuštěních, protože může být filtrování operací provést jakékoli stanovený počet.  
  
### <a name="example"></a>Příklad  
 Následující příklad dotazuje tabulku Podrobnosti prodejní objednávky pro objednávky s množstvím větší než 2 a menší než 6; vytvoří <xref:System.Data.DataView> z tohoto dotazu; a váže <xref:System.Data.DataView> k <xref:System.Windows.Forms.BindingSource>:  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhere](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhere)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhere](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhere)]  
  
### <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Data.DataView> z dotazu pro objednávky dává za 6 červen 2001:  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhere3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhere3)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhere3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhere3)]  
  
### <a name="example"></a>Příklad  
 Filtrování může být spojen s řazení. Následující příklad vytvoří <xref:System.Data.DataView> z dotazu pro kontakty jehož poslední název začněte s "S" a seřazené podle příjmení a potom křestní jméno:  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhereOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhereorderbythenby)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhereOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhereorderbythenby)]  
  
### <a name="example"></a>Příklad  
 Následující příklad používá algoritmus SoundEx Najít kontakty, jejichž příjmení je podobná "Zhu". Algoritmus SoundEx je implementovaná v metodě SoundEx.  
  
 [!code-csharp[DP DataView Samples#LDVSoundExFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvsoundexfilter)]
 [!code-vb[DP DataView Samples#LDVSoundExFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvsoundexfilter)]  
  
 SoundEx je výslovnosti algoritmus použít pro indexování názvy zvukovou, jako jsou vyslovováno v angličtině, původně vyvinuté USA Úplné zjišťování kancelář. Vrátí metoda SoundEx čtyři znakové kódu pro název, který se skládá z anglické písmeno, za nímž následuje tří čísel. Písmeno je první písmeno názvu a čísla kódování zbývající souhlásky v názvu. Podobně jako názvy zní sdílet stejný kód SoundEx. Zobrazí se zde SoundEx implementace používá v metodě SoundEx v předchozím příkladu:  
  
 [!code-csharp[DP DataView Samples#SoundEx](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#soundex)]
 [!code-vb[DP DataView Samples#SoundEx](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#soundex)]  
  
## <a name="using-the-rowfilter-property"></a>Pomocí vlastnosti RowFilter  
 Existující založené na řetězcích Filtrování funkce <xref:System.Data.DataView> stále funguje [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kontextu. Další informace o založené na řetězcích <xref:System.Data.DataView.RowFilter%2A> filtrování, najdete v části [řazení a filtrování dat](../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
 Následující příklad vytvoří <xref:System.Data.DataView> z tabulky Kontakt a poté nastaví <xref:System.Data.DataView.RowFilter%2A> vlastnost řádky, kde je poslední jméno kontaktu "Zhu":  
  
 [!code-csharp[DP DataView Samples#LDVRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvrowfilter)]
 [!code-vb[DP DataView Samples#LDVRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvrowfilter)]  
  
 Po <xref:System.Data.DataView> byly vytvořeny z <xref:System.Data.DataTable> nebo [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazu, můžete použít <xref:System.Data.DataView.RowFilter%2A> vlastnosti k určení podmnožiny řádků podle jejich hodnot sloupců. Filtry založené na řetězcích a založené na výrazu se vzájemně vylučují. Nastavení <xref:System.Data.DataView.RowFilter%2A> vlastnost vymaže odvodit z výrazu filtru [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazu a výraz filtru nelze resetovat.  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhereSetRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywheresetrowfilter)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhereSetRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywheresetrowfilter)]  
  
 Pokud chcete výsledky konkrétní dotaz na data, oproti Pokud dynamické zobrazení podmnožinu dat, můžete použít <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> metody <xref:System.Data.DataView>, nikoli nastavení <xref:System.Data.DataView.RowFilter%2A> vlastnost. <xref:System.Data.DataView.RowFilter%2A> Vlastnost nejlépe slouží v aplikaci vázané na data kde připojeného ovládacího prvku zobrazí filtrované výsledky. Nastavení <xref:System.Data.DataView.RowFilter%2A> vlastnost znovu sestaví index pro data, přidávání režie k vaší aplikaci a snížení výkonu. <xref:System.Data.DataView.Find%2A> a <xref:System.Data.DataView.FindRows%2A> metody použití aktuální index bez nutnosti znovu sestavit index. Pokud chcete volat <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> pouze jednou, měli byste použít stávající <xref:System.Data.DataView>. Pokud chcete volat <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> vícekrát, měli byste vytvořit nový <xref:System.Data.DataView> znovu sestavit index na sloupci, kterou chcete hledat na a pak zavolají <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> metody. Další informace o <xref:System.Data.DataView.Find%2A> a <xref:System.Data.DataView.FindRows%2A> najdete v části metody [hledání řádků](../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md) a [zobrazení dat výkonu](../../../../docs/framework/data/adonet/dataview-performance.md).  
  
## <a name="clearing-the-filter"></a>Vymazání filtru  
 Na filtr <xref:System.Data.DataView> lze vymazat po filtrování byla nastavena pomocí <xref:System.Data.DataView.RowFilter%2A> vlastnost. Na filtr <xref:System.Data.DataView> lze vymazat dvěma různými způsoby:  
  
-   Nastavte <xref:System.Data.DataView.RowFilter%2A> vlastnost `null`.  
  
-   Nastavte <xref:System.Data.DataView.RowFilter%2A> vlastnost prázdný řetězec.  
  
### <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Data.DataView> z dotazu a potom vymaže filtr nastavením <xref:System.Data.DataView.RowFilter%2A> vlastnost `null`:  
  
 [!code-csharp[DP DataView Samples#LDVClearRowFilter2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearrowfilter2)]
 [!code-vb[DP DataView Samples#LDVClearRowFilter2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearrowfilter2)]  
  
### <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Data.DataView> z tabulky nastaví <xref:System.Data.DataView.RowFilter%2A> vlastnost a pak vymaže filtr nastavením <xref:System.Data.DataView.RowFilter%2A> vlastnost prázdný řetězec:  
  
 [!code-csharp[DP DataView Samples#LDVClearRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearrowfilter)]
 [!code-vb[DP DataView Samples#LDVClearRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearrowfilter)]  
  
## <a name="see-also"></a>Viz také  
 [Datová vazba a LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)  
 [Řazení se zobrazením dat](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)
