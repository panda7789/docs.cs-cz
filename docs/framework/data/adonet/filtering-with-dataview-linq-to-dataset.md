---
title: Filtrování pomocí zobrazení dat (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5632d74a-ff53-4ea7-9fe7-4a148eeb1c68
ms.openlocfilehash: 426e8c43f0ff8af94ab56230cf002637f351cd75
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634856"
---
# <a name="filtering-with-dataview-linq-to-dataset"></a>Filtrování pomocí zobrazení dat (LINQ to DataSet)
Možnost filtrovat data pomocí konkrétních kritérií a potom data prezentovat klientovi prostřednictvím ovládacího prvku uživatelského rozhraní je důležitým aspektem datových vazeb. <xref:System.Data.DataView> poskytuje několik způsobů, jak filtrovat data a vracet podmnožiny datových řádků splňujících konkrétní kritéria filtru. Kromě možností filtrování založeného na řetězci <xref:System.Data.DataView> také umožňuje používat výrazy LINQ pro filtrovací kritéria. Výrazy LINQ umožňují mnohem složitější a výkonné operace filtrování než filtrování založené na řetězci.  
  
 Existují dva způsoby, jak filtrovat data pomocí <xref:System.Data.DataView>:  
  
- Vytvořte <xref:System.Data.DataView> z LINQ to DataSet dotaz s klauzulí WHERE.  
  
- Použijte existující možnosti filtrování založené na řetězcích <xref:System.Data.DataView>.  
  
## <a name="creating-dataview-from-a-query-with-filtering-information"></a>Vytvoření objektu DataView z dotazu s použitím informací o filtrování  
 Objekt <xref:System.Data.DataView> lze vytvořit z dotazu LINQ to DataSet. Pokud tento dotaz obsahuje klauzuli `Where`, vytvoří se <xref:System.Data.DataView> s informacemi o filtrování z dotazu. Výraz v klauzuli `Where` slouží k určení, které datové řádky budou zahrnuty do <xref:System.Data.DataView>a je základem pro filtr.  
  
 Filtry založené na výrazu nabízejí výkonnější a složité filtrování než zjednodušené filtry založené na řetězcích. Filtry založené na řetězcích a výrazech se vzájemně vylučují. Když je <xref:System.Data.DataView.RowFilter%2A> založené na řetězci nastavené po vytvoření <xref:System.Data.DataView> z dotazu, vymaže se filtr založený na výrazu odvozený z dotazu.  
  
> [!NOTE]
> Ve většině případů výrazy použité pro filtrování nesmí mít vedlejší účinky a musí být deterministické. Výrazy by neměly obsahovat ani žádnou logiku, která závisí na nastaveném počtu spuštění, protože operace filtrování mohou být provedeny libovolným počtem opakování.  
  
### <a name="example"></a>Příklad  
 Následující příklad dotazuje tabulku SalesOrderDetail pro objednávky s množstvím větším než 2 a menším než 6; Vytvoří z tohoto dotazu <xref:System.Data.DataView>. a váže <xref:System.Data.DataView> k <xref:System.Windows.Forms.BindingSource>:  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhere](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhere)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhere](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhere)]  
  
### <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Data.DataView> z dotazu pro objednávky, které byly vloženy po 6. června 2001:  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhere3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhere3)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhere3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhere3)]  
  
### <a name="example"></a>Příklad  
 Filtrování lze také kombinovat s řazením. Následující příklad vytvoří <xref:System.Data.DataView> z dotazu pro kontakty, jejichž příjmení začíná na "S" a seřazené podle příjmení a pak jméno:  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhereOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhereorderbythenby)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhereOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhereorderbythenby)]  
  
### <a name="example"></a>Příklad  
 Následující příklad používá algoritmus SoundEx k vyhledání kontaktů, jejichž příjmení se podobá "Zhu". SoundEx algoritmus je implementován v metodě SoundEx.  
  
 [!code-csharp[DP DataView Samples#LDVSoundExFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvsoundexfilter)]
 [!code-vb[DP DataView Samples#LDVSoundExFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvsoundexfilter)]  
  
 SoundEx je fonetický algoritmus, který se používá pro indexování názvů pomocí zvuku, protože se vyslovují v angličtině, původně vyvinutý úřadem pro sčítání v USA. Metoda SoundEx vrací čtyři kódy znaků pro název skládající se z anglického písmene následovaného třemi čísly. Písmeno je první písmeno názvu a čísla zakódují zbývající souhlásky v názvu. Podobné zvukové názvy sdílí stejný SoundEx kód. SoundEx implementace použitá v metodě SoundEx předchozího příkladu je znázorněna zde:  
  
 [!code-csharp[DP DataView Samples#SoundEx](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#soundex)]
 [!code-vb[DP DataView Samples#SoundEx](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#soundex)]  
  
## <a name="using-the-rowfilter-property"></a>Použití vlastnosti RowFilter vyžaduje hodnotu  
 Stávající funkce filtrování na základě řetězců <xref:System.Data.DataView> stále fungují v kontextu LINQ to DataSet. Další informace o filtrování <xref:System.Data.DataView.RowFilter%2A> založeném na řetězcích naleznete v tématu [řazení a filtrování dat](./dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
 Následující příklad vytvoří <xref:System.Data.DataView> z tabulky kontaktů a poté nastaví vlastnost <xref:System.Data.DataView.RowFilter%2A> na vrácení řádků, kde příjmení kontaktu je "Zhu":  
  
 [!code-csharp[DP DataView Samples#LDVRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvrowfilter)]
 [!code-vb[DP DataView Samples#LDVRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvrowfilter)]  
  
 Po vytvoření <xref:System.Data.DataView> z <xref:System.Data.DataTable> nebo LINQ to DataSet dotazu můžete použít vlastnost <xref:System.Data.DataView.RowFilter%2A> k určení podmnožiny řádků na základě hodnot jejich sloupce. Filtry založené na řetězcích a výrazech se vzájemně vylučují. Nastavením vlastnosti <xref:System.Data.DataView.RowFilter%2A> se vymaže výraz filtru odvozený z dotazu LINQ to DataSet a výraz filtru nejde resetovat.  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhereSetRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywheresetrowfilter)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhereSetRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywheresetrowfilter)]  
  
 Pokud chcete vrátit výsledky konkrétního dotazu na data, na rozdíl od poskytování dynamického zobrazení podmnožiny dat, můžete místo nastavení <xref:System.Data.DataView.RowFilter%2A> vlastnosti použít <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> metody <xref:System.Data.DataView>. Vlastnost <xref:System.Data.DataView.RowFilter%2A> se nejlépe používá v aplikaci vázané na data, kde vázaný ovládací prvek zobrazuje filtrované výsledky. Nastavením vlastnosti <xref:System.Data.DataView.RowFilter%2A> se znovu sestaví index dat, zvýší se režie do vaší aplikace a zmenší se výkon. Metody <xref:System.Data.DataView.Find%2A> a <xref:System.Data.DataView.FindRows%2A> používají aktuální index, aniž by bylo nutné znovu sestavit index. Pokud budete volat <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> pouze jednou, měli byste použít stávající <xref:System.Data.DataView>. Pokud budete volat <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> několikrát, měli byste vytvořit novou <xref:System.Data.DataView> pro opětovné sestavení indexu ve sloupci, který chcete vyhledat, a pak volat metody <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A>. Další informace o metodách <xref:System.Data.DataView.Find%2A> a <xref:System.Data.DataView.FindRows%2A> najdete v tématu [Vyhledání řádků](./dataset-datatable-dataview/finding-rows.md) a [výkon zobrazení dat](dataview-performance.md).  
  
## <a name="clearing-the-filter"></a>Mazání filtru  
 Filtr na <xref:System.Data.DataView> lze po nastavení filtrování pomocí vlastnosti <xref:System.Data.DataView.RowFilter%2A> vymazat. Filtr na <xref:System.Data.DataView> lze vymazat dvěma různými způsoby:  
  
- Nastavte <xref:System.Data.DataView.RowFilter%2A> vlastnost `null`.  
  
- Vlastnost <xref:System.Data.DataView.RowFilter%2A> nastavte na prázdný řetězec.  
  
### <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Data.DataView> z dotazu a poté zruší filtr nastavením vlastnosti <xref:System.Data.DataView.RowFilter%2A> na `null`:  
  
 [!code-csharp[DP DataView Samples#LDVClearRowFilter2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearrowfilter2)]
 [!code-vb[DP DataView Samples#LDVClearRowFilter2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearrowfilter2)]  
  
### <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Data.DataView> z tabulky nastaví vlastnost <xref:System.Data.DataView.RowFilter%2A> a poté zruší filtr nastavením vlastnosti <xref:System.Data.DataView.RowFilter%2A> na prázdný řetězec:  
  
 [!code-csharp[DP DataView Samples#LDVClearRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearrowfilter)]
 [!code-vb[DP DataView Samples#LDVClearRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearrowfilter)]  
  
## <a name="see-also"></a>Viz také:

- [Datová vazba a LINQ to DataSet](data-binding-and-linq-to-dataset.md)
- [Řazení se zobrazením dat](sorting-with-dataview-linq-to-dataset.md)
