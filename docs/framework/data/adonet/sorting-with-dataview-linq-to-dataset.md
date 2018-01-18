---
title: "Řazení s DataView (LINQ na DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 885b3b7b-51c1-42b3-bb29-b925f4f69a6f
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e8eda365fa1970f4fa836440151cc1ba0d3ae9dd
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="sorting-with-dataview-linq-to-dataset"></a>Řazení s DataView (LINQ na DataSet)
Možnost řazení dat na základě konkrétních kritérií a potom prezentovat data ke klientovi pomocí ovládacího prvku uživatelského rozhraní je důležitým aspektem datové vazby. <xref:System.Data.DataView>poskytuje několik způsobů, jak řadit data a vrátí řádky dat, které jsou seřazené podle konkrétní kritéria řazení. Kromě jeho řetězec na základě možnosti, řazení <xref:System.Data.DataView> také umožňuje používat [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] výrazy pro řazení kritéria. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]výrazy umožňují mnohem složitější a výkonné operace řazení než založené na řetězcích řazení. Toto téma popisuje obou přístupů k řazení pomocí <xref:System.Data.DataView>.  
  
## <a name="creating-dataview-from-a-query-with-sorting-information"></a>Vytváření zobrazení dat z dotazu s řazením informace  
 A <xref:System.Data.DataView> objekt můžete vytvořit z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazu. Pokud tento dotaz obsahuje <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.ThenBy%2A>, nebo <xref:System.Linq.Enumerable.ThenByDescending%2A> výrazy v těchto klauzule jsou použity jako základ pro řazení dat v klauzuli <xref:System.Data.DataView>. Například, pokud dotaz obsahuje `Order By…`a `Then By…` klauzule, výsledná <xref:System.Data.DataView> by řadit data podle oba sloupce zadané.  
  
 Založené na výrazech řazení nabízí výkonný a komplexní řazení než založené na řetězcích řazení jednodušší. Všimněte si, že na základě řetězců a založené na výrazech řazení se vzájemně vylučují. Pokud řetězec na základě <xref:System.Data.DataView.Sort%2A> se nastaví po <xref:System.Data.DataView> je vytvořena z dotazu, založené na výrazu filtru odvodit z dotazu není zaškrtnuté a nelze jej obnovit.  
  
 Index <xref:System.Data.DataView> vychází i v případě <xref:System.Data.DataView> je vytvořena a při řazení nebo filtrování je upravit informace. Získáte nejlepší výkon zadáním kritérií pro řazení [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotaz, který <xref:System.Data.DataView> je vytvořený z a není úprava řazení informace později. Další informace najdete v tématu [zobrazení dat výkonu](../../../../docs/framework/data/adonet/dataview-performance.md).  
  
> [!NOTE]
>  Ve většině případů výrazy použít k řazení nesmí mít vedlejší účinky a musí být deterministický. Výrazy nesmí obsahovat žádný logiky, která závisí na se stanoveným počtem spuštěních, protože může být operace řazení provést jakékoli stanovený počet.  
  
### <a name="example"></a>Příklad  
 V následujícím příkladu dotazuje tabulku SalesOrderHeader a pořadí vrácených řádků k datu objednávky; vytvoří <xref:System.Data.DataView> z tohoto dotazu; a váže <xref:System.Data.DataView> k <xref:System.Windows.Forms.BindingSource>.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby)]  
  
### <a name="example"></a>Příklad  
 V následujícím příkladu dotazuje tabulku SalesOrderHeader a řadí vrácený řádek podle celkové částky kvůli; vytvoří <xref:System.Data.DataView> z tohoto dotazu; a váže <xref:System.Data.DataView> k <xref:System.Windows.Forms.BindingSource>.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby2)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby2)]  
  
### <a name="example"></a>Příklad  
 V následujícím příkladu dotazuje tabulku, podrobnosti prodejní objednávky a pořadí vrácených řádků podle množství objednávky a poté podle ID prodejní objednávky; vytvoří <xref:System.Data.DataView> z tohoto dotazu; a váže <xref:System.Data.DataView> k <xref:System.Windows.Forms.BindingSource>.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderbythenby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderbythenby)]  
  
## <a name="using-the-string-based-sort-property"></a>Pomocí vlastnosti řazení založené na řetězec  
 Na základě řetězec řazení funkce <xref:System.Data.DataView> pořád funguje s [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. Po <xref:System.Data.DataView> byly vytvořeny z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazu, můžete použít <xref:System.Data.DataView.Sort%2A> vlastnost nastavující řazení na <xref:System.Data.DataView>.  
  
 Na základě řetězců a založené na výrazech řazení funkce se vzájemně vylučují. Nastavení <xref:System.Data.DataView.Sort%2A> vlastnost vymaže základě výraz řazení zděděno z dotazu, <xref:System.Data.DataView> byl vytvořen z.  
  
 Další informace o založené na řetězcích <xref:System.Data.DataView.Sort%2A> filtrování, najdete v části [řazení a filtrování dat](../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
### <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Data.DataView> z kontakt tabulky a řádky jsou řazeny podle příjmení v sestupném pořadí a pak křestní jméno ve vzestupném pořadí:  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
### <a name="example"></a>Příklad  
 Následující příklad dotazuje tabulku, obraťte se na pro poslední názvy, které začínají s písmenem "S".  A <xref:System.Data.DataView> je vytvořena z tohoto dotazu a vázána <xref:System.Windows.Forms.BindingSource> objektu.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="clearing-the-sort"></a>Vymazání řazení  
 Řazení informace o <xref:System.Data.DataView> lze vymazat po byla nastavena, pomocí <xref:System.Data.DataView.Sort%2A> vlastnost. Existují dva způsoby, jak vymazat řazení informace v <xref:System.Data.DataView>:  
  
-   Nastavte <xref:System.Data.DataView.Sort%2A> vlastnost `null`.  
  
-   Nastavte <xref:System.Data.DataView.Sort%2A> vlastnost prázdný řetězec.  
  
### <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Data.DataView> z dotazu a vymaže řazení podle nastavení <xref:System.Data.DataView.Sort%2A> vlastnost prázdný řetězec:  
  
 [!code-csharp[DP DataView Samples#LDVClearSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort)]
 [!code-vb[DP DataView Samples#LDVClearSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort)]  
  
### <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Data.DataView> z tabulky Kontakt a nastaví <xref:System.Data.DataView.Sort%2A> vlastnost seřadit podle příjmení v sestupném pořadí. Řazení informace je pak vymazán nastavením <xref:System.Data.DataView.Sort%2A> vlastnost `null`:  
  
 [!code-csharp[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort2)]
 [!code-vb[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort2)]  
  
## <a name="see-also"></a>Viz také  
 [Datová vazba a LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)  
 [Filtrování se zobrazením dat](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)  
 [Řazení dat](http://msdn.microsoft.com/library/6d76e2d7-b418-49b5-ac78-2bcd61169c48)
