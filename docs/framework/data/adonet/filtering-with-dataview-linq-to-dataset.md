---
title: Filtrování se zobrazením dat (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5632d74a-ff53-4ea7-9fe7-4a148eeb1c68
ms.openlocfilehash: c4c6c01839294e134b0961059a4c165a67c1ecf9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516730"
---
# <a name="filtering-with-dataview-linq-to-dataset"></a>Filtrování se zobrazením dat (LINQ to DataSet)
Možnost filtrovat data s využitím určitých kritérií a potom prezentovat data do klienta prostřednictvím ovládacího prvku uživatelského rozhraní je důležitou součástí datové vazby. <xref:System.Data.DataView> poskytuje několik způsobů, jak filtrovat data a vrácení podmnožin řádky dat meeting konkrétního filtrovací kritéria. Kromě podle řetězce možnosti filtrování <xref:System.Data.DataView> také nabízí možnost používat [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] výrazy pro kritéria filtrování. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] výrazy umožňují mnohem komplexnější a efektivní filtrování operací než filtrování založené na řetězci.  
  
 Existují dva způsoby, jak pomocí filtrování dat <xref:System.Data.DataView>:  
  
-   Vytvoření <xref:System.Data.DataView> z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazování umístění, kde se klauzule.  
  
-   Použít existující, založené na řetězci filtrování možností <xref:System.Data.DataView>.  
  
## <a name="creating-dataview-from-a-query-with-filtering-information"></a>Vytváření zobrazení dat z dotazu s informacemi o filtrování  
 A <xref:System.Data.DataView> objekt můžete vytvořit z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazu. Pokud tento dotaz obsahuje `Where` klauzule <xref:System.Data.DataView> vytvořené pomocí filtrování informace z dotazu. Výraz v `Where` klauzule slouží k určení, které řádky dat se zahrnou <xref:System.Data.DataView>, a slouží jako základ pro filtr.  
  
 Filtry založené na výrazu nabízejí výkonnější a složité filtrování než jednodušší filtry založené na řetězci. Filtry založené na řetězci a založené na výrazu se vzájemně vylučují. Při řetězec podle <xref:System.Data.DataView.RowFilter%2A> se nastaví po <xref:System.Data.DataView> je vytvořený z dotazu, výraz na základě filtru odvodit z dotazu je zrušeno.  
  
> [!NOTE]
>  Výrazy použité pro filtrování ve většině případů by neměl mít vedlejší účinky a musí být deterministický. Výrazů nesmí obsahovat žádný logiku, která závisí na stanovený počet spuštění, protože operace filtrování může být spuštěn libovolný počet pokusů.  
  
### <a name="example"></a>Příklad  
 Následující příklad dotazuje podrobnosti prodejní objednávky tabulky objednávek s množstvím větší než 2 a méně než 6; vytvoří <xref:System.Data.DataView> z dotazu; a vytvoří vazbu <xref:System.Data.DataView> k <xref:System.Windows.Forms.BindingSource>:  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhere](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhere)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhere](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhere)]  
  
### <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Data.DataView> z dotazu pro objednávky umístěný za 6. června 2001:  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhere3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhere3)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhere3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhere3)]  
  
### <a name="example"></a>Příklad  
 Filtrování můžete také kombinovat s řazením. Následující příklad vytvoří <xref:System.Data.DataView> z dotazu na kontakty jejichž název začíná "S" poslední a seřazené podle příjmení a pak křestní jméno:  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhereOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhereorderbythenby)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhereOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhereorderbythenby)]  
  
### <a name="example"></a>Příklad  
 Následující příklad používá algoritmus SoundEx Najít kontakty, jejichž příjmení je podobný "Zhu". Algoritmus SoundEx je implementovaná v metodě SoundEx.  
  
 [!code-csharp[DP DataView Samples#LDVSoundExFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvsoundexfilter)]
 [!code-vb[DP DataView Samples#LDVSoundExFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvsoundexfilter)]  
  
 SoundEx je zapsané ve fonetické algoritmus používají pro indexování názvy zvukovou, jako jsou vyslovováno v angličtině, původně vyvinutý USA Census Bureau. Vrátí metoda SoundEx kód čtyři znaky pro název skládající se z písmena anglické abecedy, za nímž následuje tří čísel. Písmenem je první písmeno názvu a čísla kódování zbývající souhláskami v názvu. Podobně jako to nezní názvy sdílet stejný kód SoundEx. Implementace SoundEx použitý v metodě SoundEx předchozího příkladu je znázorněna zde:  
  
 [!code-csharp[DP DataView Samples#SoundEx](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#soundex)]
 [!code-vb[DP DataView Samples#SoundEx](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#soundex)]  
  
## <a name="using-the-rowfilter-property"></a>Pomocí vlastnosti RowFilter  
 Existující založené na řetězci filtrování funkce <xref:System.Data.DataView> stále probíhá [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kontextu. Další informace o založené na řetězci <xref:System.Data.DataView.RowFilter%2A> filtrování, najdete v článku [řazení a filtrování dat](../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
 Následující příklad vytvoří <xref:System.Data.DataView> z tabulky Kontakt a poté nastaví <xref:System.Data.DataView.RowFilter%2A> vlastnost vrátí řádky, kde je "Zhu" příjmení kontaktu:  
  
 [!code-csharp[DP DataView Samples#LDVRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvrowfilter)]
 [!code-vb[DP DataView Samples#LDVRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvrowfilter)]  
  
 Po <xref:System.Data.DataView> byl vytvořen z <xref:System.Data.DataTable> nebo [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazu, můžete použít <xref:System.Data.DataView.RowFilter%2A> vlastnosti a určit tak podmnožiny řádků podle jejich hodnoty sloupce. Filtry založené na řetězci a založené na výrazu se vzájemně vylučují. Nastavení <xref:System.Data.DataView.RowFilter%2A> vlastnost vymaže odvodit z výrazu filtru [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazu a výraz filtru nelze obnovit.  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhereSetRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywheresetrowfilter)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhereSetRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywheresetrowfilter)]  
  
 Pokud chcete vrátit výsledky konkrétní dotaz na data, jako proti poskytující dynamické zobrazení podmnožinu dat, můžete použít <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> metody <xref:System.Data.DataView>, místo nastavení <xref:System.Data.DataView.RowFilter%2A> vlastnost. <xref:System.Data.DataView.RowFilter%2A> Vlastnost je nejvhodnější v aplikace vázané na data kde vázaného ovládacího prvku zobrazí filtrované výsledky. Nastavení <xref:System.Data.DataView.RowFilter%2A> vlastnost znovu sestaví index pro data, přidání režie pro vaši aplikaci a snížit výkon. <xref:System.Data.DataView.Find%2A> a <xref:System.Data.DataView.FindRows%2A> metody používat aktuální index bez nutnosti index znovu sestavit. Pokud se chystáte zavolat <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> pouze jednou, měli byste použít stávající <xref:System.Data.DataView>. Pokud se chystáte zavolat <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> více než jednou, měli byste vytvořit nový <xref:System.Data.DataView> znovu sestavovat index pro sloupec, který chcete vyhledat a následně zavolat <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> metody. Další informace o <xref:System.Data.DataView.Find%2A> a <xref:System.Data.DataView.FindRows%2A> metod naleznete v tématu [vyhledání řádků](../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md) a [výkon zobrazení dat](../../../../docs/framework/data/adonet/dataview-performance.md).  
  
## <a name="clearing-the-filter"></a>Vymazat filtr  
 Filtr na <xref:System.Data.DataView> lze zrušit po filtrování byla nastavena pomocí <xref:System.Data.DataView.RowFilter%2A> vlastnost. Filtr na <xref:System.Data.DataView> můžete vymazat dvěma různými způsoby:  
  
-   Nastavte <xref:System.Data.DataView.RowFilter%2A> vlastnost `null`.  
  
-   Nastavte <xref:System.Data.DataView.RowFilter%2A> vlastnost na prázdný řetězec.  
  
### <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Data.DataView> z dotazu a poté vymaže filtr tak, že nastavíte <xref:System.Data.DataView.RowFilter%2A> vlastnost `null`:  
  
 [!code-csharp[DP DataView Samples#LDVClearRowFilter2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearrowfilter2)]
 [!code-vb[DP DataView Samples#LDVClearRowFilter2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearrowfilter2)]  
  
### <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Data.DataView> z tabulky nastaví <xref:System.Data.DataView.RowFilter%2A> vlastnost a poté vymaže filtr tak, že nastavíte <xref:System.Data.DataView.RowFilter%2A> vlastnost na prázdný řetězec:  
  
 [!code-csharp[DP DataView Samples#LDVClearRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearrowfilter)]
 [!code-vb[DP DataView Samples#LDVClearRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearrowfilter)]  
  
## <a name="see-also"></a>Viz také:
- [Datová vazba a LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
- [Řazení se zobrazením dat](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)
