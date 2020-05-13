---
title: Kompilované dotazy (LINQ to Entities)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8025ba1d-29c7-4407-841b-d5a3bed40b7a
ms.openlocfilehash: b4594932b6ed21de98faab57d80404a7b763067d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207920"
---
# <a name="compiled-queries--linq-to-entities"></a>Zkompilované dotazy (LINQ to Entities)

Máte-li aplikaci, která provádí v Entity Framework strukturované podobné dotazy, můžete často zvýšit výkon kompilováním dotazu jednou a jeho spuštěním několikrát s různými parametry. Aplikace může například potřebovat načíst všechny zákazníky v určitém městě; Město je určeno za běhu uživatelem ve formuláři. LINQ to Entities podporuje pro tento účel použití kompilovaných dotazů.  
  
 Počínaje .NET Framework 4,5 jsou dotazy LINQ ukládány do mezipaměti automaticky. Přesto však můžete použít zkompilované dotazy LINQ k omezení těchto nákladů v pozdějším spuštění a zkompilované dotazy mohou být efektivnější než dotazy LINQ, které jsou automaticky uloženy v mezipaměti. LINQ to Entities dotazy, které aplikují `Enumerable.Contains` operátor na kolekce v paměti, nejsou automaticky ukládány do mezipaměti. V kompilovaných dotazech LINQ se taky nepovoluje Parametrizace kolekce v paměti.  
  
 <xref:System.Data.Objects.CompiledQuery>Třída poskytuje kompilaci a ukládání dotazů do mezipaměti pro opakované použití. V koncepčních případech tato třída obsahuje <xref:System.Data.Objects.CompiledQuery> `Compile` metodu s několika přetíženími. Zavolejte `Compile` metodu pro vytvoření nového delegáta, který bude reprezentovat kompilovaný dotaz. `Compile`Metody, které jsou k dispozici s <xref:System.Data.Objects.ObjectContext> hodnotami parametrů a, vrátí delegáta, který vytváří nějaký výsledek (například <xref:System.Linq.IQueryable%601> instance). Dotaz se zkompiluje jenom při prvním spuštění. Nastavení možností sloučení pro dotaz v době kompilace nelze později změnit. Jakmile je dotaz zkompilován, lze zadat pouze parametry primitivního typu, ale nelze nahradit části dotazu, které by změnily vygenerovaný příkaz SQL. Další informace naleznete v tématu [možnosti sloučení EF a zkompilované dotazy](https://docs.microsoft.com/archive/blogs/dsimmons/ef-merge-options-and-compiled-queries).
  
 Výraz dotazu LINQ to Entities, který je <xref:System.Data.Objects.CompiledQuery> `Compile` zkompilován metodou, je reprezentován jedním z generických `Func` delegátů, jako je například <xref:System.Func%605> . Ve většině případů výraz dotazu může zapouzdřit `ObjectContext` parametr, návratový parametr a 16 parametrů dotazu. Pokud jsou vyžadovány více než 16 parametrů dotazu, můžete vytvořit strukturu, jejíž vlastnosti představují parametry dotazu. Po nastavení vlastností pak můžete použít vlastnosti struktury ve výrazu dotazu.  
  
## <a name="example-1"></a>Příklad 1  
 Následující příklad zkompiluje a poté vyvolá dotaz, který přijímá <xref:System.Decimal> vstupní parametr a vrací sekvenci objednávek, kde celková hodnota splatnosti je větší než nebo rovna $200,00:  
  
 [!code-csharp[DP L2E Conceptual Examples - compiled query 2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery2)]
 [!code-vb[DP L2E Conceptual Examples - compiled query2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery2)]  
  
## <a name="example-2"></a>Příklad 2  
 Následující příklad zkompiluje a poté vyvolá dotaz, který vrací <xref:System.Data.Objects.ObjectQuery%601> instanci:  
  
 [!code-csharp[DP L2E Conceptual Examples - compiled query1_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery1_mq)]
 [!code-vb[DP L2E Conceptual Examples - compiled query1_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery1_mq)]  
  
## <a name="example-3"></a>Příklad 3  
 Následující příklad zkompiluje a potom vyvolá dotaz, který vrací průměr cen seznamu produktů jako <xref:System.Decimal> hodnotu:  
  
 [!code-csharp[DP L2E Conceptual Examples - compiled query3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery3_mq)]
 [!code-vb[DP L2E Conceptual Examples - compiled query3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery3_mq)]  
  
## <a name="example-4"></a>Příklad 4  
 Následující příklad zkompiluje a poté vyvolá dotaz, který přijímá <xref:System.String> vstupní parametr, a potom vrátí, `Contact` jehož e-mailová adresa začíná zadaným řetězcem:  
  
 [!code-csharp[DP L2E Conceptual Examples - compiled query4_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery4_mq)]
 [!code-vb[DP L2E Conceptual Examples - compiled query4_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery4_mq)]  
  
## <a name="example-5"></a>Příklad 5  
 Následující příklad zkompiluje a poté vyvolá dotaz, který přijímá <xref:System.DateTime> a <xref:System.Decimal> vstupní parametry a vrací sekvenci objednávek, kde je datum objednávky pozdější než 8. března 2003 a celková hodnota je menší než $300,00:  
  
 [!code-csharp[DP L2E Conceptual Examples - compiled query5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery5)]
 [!code-vb[DP L2E Conceptual Examples - compiled query5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery5)]  
  
## <a name="example-6"></a>Příklad 6  
 Následující příklad zkompiluje a poté vyvolá dotaz, který přijímá <xref:System.DateTime> vstupní parametr a vrátí sekvenci objednávek, kde je datum objednávky pozdější než 8. března 2004. Tento dotaz vrátí informace o objednávce jako posloupnost anonymních typů. Anonymní typy jsou odvozeny kompilátorem, takže nelze zadat parametry typu v <xref:System.Data.Objects.CompiledQuery> `Compile` metodě a typ je definován v samotném dotazu.  
  
 [!code-csharp[DP L2E Conceptual Examples - compiled query6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery6)]
 [!code-vb[DP L2E Conceptual Examples - compiled query6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery6)]  
  
## <a name="example-7"></a>Příklad 7  
 Následující příklad zkompiluje a poté vyvolá dotaz, který přijímá vstupní parametr struktury definované uživatelem a vrací sekvenci Orders. Struktura definuje počáteční a koncové datum a celkový počet parametrů dotazu a dotaz vrátí objednávky dodávané do 3. března 2003 s celkovým termínem větším než $700,00.  
  
 [!code-csharp[DP L2E Conceptual Examples - compiled query7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery7)]
 [!code-vb[DP L2E Conceptual Examples - compiled query7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery7)]  
  
 Struktura definující parametry dotazu:  
  
 [!code-csharp[DP L2E Conceptual Examples - MyParamsStruct](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myparamsstruct)]
 [!code-vb[DP L2E Conceptual Examples - MyParamsStruct](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myparamsstruct)]  
  
## <a name="see-also"></a>Viz také

- [ADO.NET Entity Framework](../index.md)
- [LINQ to Entities](linq-to-entities.md)
- [Možnosti sloučení EF a zkompilované dotazy](https://docs.microsoft.com/archive/blogs/dsimmons/ef-merge-options-and-compiled-queries)
