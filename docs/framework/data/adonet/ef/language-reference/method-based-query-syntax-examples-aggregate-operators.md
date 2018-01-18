---
title: "Příklady syntaxe dotazu na základě metod: Agregační operátory"
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
ms.assetid: 0e306067-5720-4782-9719-2286570a7e47
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: afb7d7350e6b16a275fcd1dc2e697230e15ce3ed
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="method-based-query-syntax-examples-aggregate-operators"></a>Příklady syntaxe dotazu na základě metod: Agregační operátory
V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, a <xref:System.Linq.Enumerable.Sum%2A> metody k dotazování [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) pomocí syntaxe dotazu na základě metod. Model prodeje společnosti AdventureWorks použít v těchto příkladech je sestaven z kontaktu, adresu, produktu, SalesOrderHeader a podrobnosti prodejní objednávky tabulky v ukázkové databázi AdventureWorks.  
  
 V příkladech v tomto tématu použijte následující `using` / `Imports` příkazy:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="average"></a>Průměr  
  
### <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Linq.Enumerable.Average%2A> metody k vyhledání průměrná cena seznam produktů.  
  
 [!code-csharp[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average_mq)]
 [!code-vb[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average_mq)]  
  
### <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Linq.Enumerable.Average%2A> metody k vyhledání průměrná cena seznam produktů jednotlivých stylů.  
  
 [!code-csharp[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Linq.Enumerable.Average%2A> metody k vyhledání celkový kvůli průměr.  
  
 [!code-csharp[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageprojection_mq)]
 [!code-vb[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageprojection_mq)]  
  
### <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Linq.Enumerable.Average%2A> ID metoda získat průměr celkové potřebné pro každý kontakt.  
  
 [!code-csharp[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Linq.Enumerable.Average%2A> metoda získat příkazy se průměr celkové potřebné pro každý kontakt.  
  
 [!code-csharp[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a>Počet  
  
### <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Linq.Enumerable.Count%2A> metody, která vrátí počet produktů, v tabulce produktu.  
  
 [!code-csharp[DP L2E Examples#Count](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#count)]
 [!code-vb[DP L2E Examples#Count](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#count)]  
  
### <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Linq.Enumerable.Count%2A> metoda vrátí seznam obraťte se na ID a kolik řadí každý má.  
  
 [!code-csharp[DP L2E Examples#CountNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countnested)]
 [!code-vb[DP L2E Examples#CountNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a>Příklad  
 V následujícím příkladu skupiny produkty pomocí barev a používá <xref:System.Linq.Enumerable.Count%2A> metody, která vrátí počet produktů v každé skupině barev.  
  
 [!code-csharp[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="longcount"></a>LongCount  
  
### <a name="example"></a>Příklad  
 Následující příklad získá kontaktní počet jako dlouhých celých čísel.  
  
 [!code-csharp[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#longcountsimple)]
 [!code-vb[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#longcountsimple)]  
  
## <a name="max"></a>Max  
  
### <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Linq.Enumerable.Max%2A> metoda získat největší celkový splatnosti.  
  
 [!code-csharp[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxprojection_mq)]
 [!code-vb[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxprojection_mq)]  
  
### <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Linq.Enumerable.Max%2A> metoda získat největší celkový splatnosti pro každou obraťte se na ID.  
  
 [!code-csharp[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Linq.Enumerable.Max%2A> metodu za účelem získání objednávky se největší celkový termínem pro každou obraťte se na ID.  
  
 [!code-csharp[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a>Min.  
  
### <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Linq.Enumerable.Min%2A> metoda získat nejmenší celkový splatnosti.  
  
 [!code-csharp[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minprojection_mq)]
 [!code-vb[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minprojection_mq)]  
  
### <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Linq.Enumerable.Min%2A> metoda získat nejmenší celkový splatnosti pro každou obraťte se na ID.  
  
 [!code-csharp[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Linq.Enumerable.Min%2A> metoda získat příkazy se nejmenší celkem platnosti pro každý kontakt.  
  
 [!code-csharp[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a>Součet  
  
### <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Linq.Enumerable.Sum%2A> metoda získat celkový počet počty pořadí v tabulce Podrobnosti prodejní objednávky.  
  
 [!code-csharp[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumprojection_mq)]
 [!code-vb[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumprojection_mq)]  
  
### <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Linq.Enumerable.Sum%2A> metoda získat celkový splatnosti pro každou obraťte se na ID.  
  
 [!code-csharp[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a>Viz také  
 [Dotazy v technologii LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
