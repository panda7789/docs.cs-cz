---
title: Filtrování pomocí zobrazení dat (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5632d74a-ff53-4ea7-9fe7-4a148eeb1c68
ms.openlocfilehash: aaa9ac0514f3e79f101bbcd9cbab60929f91d4fd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959132"
---
# <a name="filtering-with-dataview-linq-to-dataset"></a>Filtrování pomocí zobrazení dat (LINQ to DataSet)
Možnost filtrovat data pomocí konkrétních kritérií a potom data prezentovat klientovi prostřednictvím ovládacího prvku uživatelského rozhraní je důležitým aspektem datových vazeb. <xref:System.Data.DataView>poskytuje několik způsobů, jak filtrovat data a vracet podmnožiny datových řádků splňujících konkrétní kritéria filtru. Kromě schopností <xref:System.Data.DataView> filtrování založeného na řetězci také poskytuje možnost používat [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] výrazy pro kritéria filtrování. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]výrazy umožňují mnohem složitější a výkonné operace filtrování, než filtrování založené na řetězcích.  
  
 Existují dva způsoby, jak filtrovat data pomocí <xref:System.Data.DataView>:  
  
- <xref:System.Data.DataView> Vytvořte z LINQ to DataSet dotaz s klauzulí WHERE.  
  
- Použijte existující možnosti <xref:System.Data.DataView>filtrování založené na řetězcích.  
  
## <a name="creating-dataview-from-a-query-with-filtering-information"></a>Vytvoření objektu DataView z dotazu s použitím informací o filtrování  
 <xref:System.Data.DataView> Objekt lze vytvořit z LINQ to DataSetho dotazu. Pokud tento dotaz obsahuje `Where` klauzuli <xref:System.Data.DataView> , vytvoří se s informacemi o filtrování z dotazu. Výraz v `Where` klauzuli slouží k určení <xref:System.Data.DataView>, které datové řádky budou zahrnuty do, a je základem pro filtr.  
  
 Filtry založené na výrazu nabízejí výkonnější a složité filtrování než zjednodušené filtry založené na řetězcích. Filtry založené na řetězcích a výrazech se vzájemně vylučují. Když je založen <xref:System.Data.DataView.RowFilter%2A> na řetězci <xref:System.Data.DataView> po vytvoření z dotazu, je vymazán filtr založený na výrazu odvozený z dotazu.  
  
> [!NOTE]
> Ve většině případů výrazy použité pro filtrování nesmí mít vedlejší účinky a musí být deterministické. Výrazy by neměly obsahovat ani žádnou logiku, která závisí na nastaveném počtu spuštění, protože operace filtrování mohou být provedeny libovolným počtem opakování.  
  
### <a name="example"></a>Příklad  
 Následující příklad dotazuje tabulku SalesOrderDetail pro objednávky s množstvím větším než 2 a menším než 6; Vytvoří z tohoto dotazu a váže <xref:System.Data.DataView> <xref:System.Windows.Forms.BindingSource>na: <xref:System.Data.DataView>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhere](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhere)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhere](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhere)]  
  
### <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Data.DataView> dotaz z dotazu na objednávky, které byly vloženy po 6. června 2001:  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhere3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhere3)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhere3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhere3)]  
  
### <a name="example"></a>Příklad  
 Filtrování lze také kombinovat s řazením. Následující příklad vytvoří <xref:System.Data.DataView> z dotazu pro kontakty, jejichž příjmení začíná řetězcem "S" a seřazené podle příjmení a pak jméno:  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhereOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhereorderbythenby)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhereOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhereorderbythenby)]  
  
### <a name="example"></a>Příklad  
 Následující příklad používá algoritmus SoundEx k vyhledání kontaktů, jejichž příjmení se podobá "Zhu". SoundEx algoritmus je implementován v metodě SoundEx.  
  
 [!code-csharp[DP DataView Samples#LDVSoundExFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvsoundexfilter)]
 [!code-vb[DP DataView Samples#LDVSoundExFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvsoundexfilter)]  
  
 SoundEx je fonetický algoritmus, který se používá pro indexování názvů pomocí zvuku, protože se vyslovují v angličtině, původně vyvinutý v USA. Sčítání v kanceláři Metoda SoundEx vrací čtyři kódy znaků pro název skládající se z anglického písmene následovaného třemi čísly. Písmeno je první písmeno názvu a čísla zakódují zbývající souhlásky v názvu. Podobné zvukové názvy sdílí stejný SoundEx kód. SoundEx implementace použitá v metodě SoundEx předchozího příkladu je znázorněna zde:  
  
 [!code-csharp[DP DataView Samples#SoundEx](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#soundex)]
 [!code-vb[DP DataView Samples#SoundEx](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#soundex)]  
  
## <a name="using-the-rowfilter-property"></a>Použití vlastnosti RowFilter vyžaduje hodnotu  
 Stávající funkce <xref:System.Data.DataView> filtrování na základě řetězců stále funguje v kontextu LINQ to DataSet. Další informace o filtrování na základě <xref:System.Data.DataView.RowFilter%2A> řetězců najdete v tématu [řazení a filtrování dat](../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
 Následující příklad vytvoří <xref:System.Data.DataView> z tabulky kontaktů a poté <xref:System.Data.DataView.RowFilter%2A> nastaví vlastnost tak, aby vracela řádky, kde příjmení kontaktu je "Zhu":  
  
 [!code-csharp[DP DataView Samples#LDVRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvrowfilter)]
 [!code-vb[DP DataView Samples#LDVRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvrowfilter)]  
  
 Po vytvoření z nebo LINQ to DataSet dotazu můžete použít <xref:System.Data.DataView.RowFilter%2A> vlastnost k určení podmnožiny řádků na základě hodnot jejich sloupce. <xref:System.Data.DataTable> <xref:System.Data.DataView> Filtry založené na řetězcích a výrazech se vzájemně vylučují. <xref:System.Data.DataView.RowFilter%2A> Nastavením vlastnosti se vymaže výraz filtru odvozený z LINQ to DataSet dotazu a výraz filtru nejde resetovat.  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhereSetRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywheresetrowfilter)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhereSetRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywheresetrowfilter)]  
  
 Pokud chcete vrátit výsledky konkrétního dotazu na data, na rozdíl od poskytnutí dynamického zobrazení podmnožiny dat, můžete <xref:System.Data.DataView.Find%2A> místo nastavení <xref:System.Data.DataView.RowFilter%2A> vlastnosti použít metody <xref:System.Data.DataView>nebo <xref:System.Data.DataView.FindRows%2A> . Tato <xref:System.Data.DataView.RowFilter%2A> vlastnost se nejlépe používá v aplikaci vázané na data, kde vázaný ovládací prvek zobrazuje filtrované výsledky. <xref:System.Data.DataView.RowFilter%2A> Nastavením vlastnosti se znovu sestaví index dat, zvýší se režie do vaší aplikace a zmenší se výkon. Metody <xref:System.Data.DataView.Find%2A> a<xref:System.Data.DataView.FindRows%2A> používají aktuální index, aniž by bylo nutné znovu sestavit index. Pokud budete volat <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> pouze jednou, měli byste použít stávající <xref:System.Data.DataView>. Pokud se chystáte zavolat <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> víckrát, měli byste vytvořit nový <xref:System.Data.DataView> , chcete-li znovu sestavit index ve sloupci, který chcete vyhledat, a pak zavolat <xref:System.Data.DataView.Find%2A> metody nebo <xref:System.Data.DataView.FindRows%2A> . Další informace o <xref:System.Data.DataView.Find%2A> metodách a <xref:System.Data.DataView.FindRows%2A> najdete v tématu [Vyhledání řádků](../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md) a výkonu zobrazení [dat](../../../../docs/framework/data/adonet/dataview-performance.md).  
  
## <a name="clearing-the-filter"></a>Mazání filtru  
 Filtr na <xref:System.Data.DataView> může být vymazán po nastavení filtrování <xref:System.Data.DataView.RowFilter%2A> pomocí vlastnosti. Filtr na <xref:System.Data.DataView> může být smazán dvěma různými způsoby:  
  
- Nastavte <xref:System.Data.DataView.RowFilter%2A> vlastnost `null`.  
  
- <xref:System.Data.DataView.RowFilter%2A> Nastavte vlastnost na prázdný řetězec.  
  
### <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Data.DataView> z dotazu a poté zruší filtr <xref:System.Data.DataView.RowFilter%2A> nastavením vlastnosti na `null`:  
  
 [!code-csharp[DP DataView Samples#LDVClearRowFilter2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearrowfilter2)]
 [!code-vb[DP DataView Samples#LDVClearRowFilter2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearrowfilter2)]  
  
### <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Data.DataView> z tabulky <xref:System.Data.DataView.RowFilter%2A> sadu vlastností a poté zruší filtr <xref:System.Data.DataView.RowFilter%2A> nastavením vlastnosti na prázdný řetězec:  
  
 [!code-csharp[DP DataView Samples#LDVClearRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearrowfilter)]
 [!code-vb[DP DataView Samples#LDVClearRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearrowfilter)]  
  
## <a name="see-also"></a>Viz také:

- [Datová vazba a LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
- [Řazení se zobrazením dat](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)
