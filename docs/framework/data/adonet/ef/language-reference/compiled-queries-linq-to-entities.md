---
title: Kompilované dotazy (LINQ to Entities)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8025ba1d-29c7-4407-841b-d5a3bed40b7a
ms.openlocfilehash: 2d9df4d479605c0a2514fe30a9150ab7bcfe904e
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251158"
---
# <a name="compiled-queries--linq-to-entities"></a>Kompilované dotazy (LINQ to Entities)
Máte-li aplikaci, která provádí v Entity Framework strukturované podobné dotazy, můžete často zvýšit výkon kompilováním dotazu jednou a jeho spuštěním několikrát s různými parametry. Aplikace může například potřebovat načíst všechny zákazníky v určitém městě; Město je určeno za běhu uživatelem ve formuláři. LINQ to Entities podporuje pro tento účel použití kompilovaných dotazů.  
  
 Počínaje .NET Framework 4,5 jsou dotazy LINQ ukládány do mezipaměti automaticky. Přesto však můžete použít zkompilované dotazy LINQ k omezení těchto nákladů v pozdějším spuštění a zkompilované dotazy mohou být efektivnější než dotazy LINQ, které jsou automaticky uloženy v mezipaměti. Všimněte si, že LINQ to Entities dotazů, `Enumerable.Contains` které používají operátor na kolekce v paměti, nejsou automaticky ukládány do mezipaměti. V kompilovaných dotazech LINQ se taky Parametrizace kolekce v paměti, které se nepovolují.  
  
 <xref:System.Data.Objects.CompiledQuery> Třída poskytuje kompilaci a ukládání dotazů do mezipaměti pro opakované použití. V koncepčních případech tato třída obsahuje <xref:System.Data.Objects.CompiledQuery> `Compile` metodu s několika přetíženími. `Compile` Zavolejte metodu pro vytvoření nového delegáta, který bude reprezentovat kompilovaný dotaz. Metody, které jsou k dispozici <xref:System.Data.Objects.ObjectContext> s hodnotami parametrů a, vrátí delegáta, který vytváří nějaký <xref:System.Linq.IQueryable%601> výsledek (například instance). `Compile` Dotaz se zkompiluje jenom při prvním spuštění. Nastavení možností sloučení pro dotaz v době kompilace nelze později změnit. Jakmile je dotaz zkompilován, lze zadat pouze parametry primitivního typu, ale nemůžete nahradit části dotazu, které by změnily vygenerované SQL. Další informace najdete v tématu [Entity Framework možností sloučení a kompilovaných dotazech](https://go.microsoft.com/fwlink/?LinkId=199591) .  
  
 Výraz dotazu LINQ to Entities, který je <xref:System.Data.Objects.CompiledQuery>zkompilován `Compile` metodou, je reprezentován jedním z <xref:System.Func%605>generických `Func` delegátů, jako je například. Ve většině případů výraz dotazu může zapouzdřit `ObjectContext` parametr, návratový parametr a 16 parametrů dotazu. Pokud jsou vyžadovány více než 16 parametrů dotazu, můžete vytvořit strukturu, jejíž vlastnosti představují parametry dotazu. Po nastavení vlastností pak můžete použít vlastnosti struktury ve výrazu dotazu.  
  
## <a name="example"></a>Příklad  
 Následující příklad zkompiluje a poté vyvolá dotaz, který přijímá <xref:System.Decimal> vstupní parametr a vrací sekvenci objednávek, kde celková hodnota splatnosti je větší než nebo rovna $200,00:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery2)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery2)]  
  
## <a name="example"></a>Příklad  
 Následující příklad zkompiluje a poté vyvolá dotaz, který vrací <xref:System.Data.Objects.ObjectQuery%601> instanci:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery1_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery1_mq)]  
  
## <a name="example"></a>Příklad  
 Následující příklad zkompiluje a potom vyvolá dotaz, který vrací průměr cen seznamu produktů jako <xref:System.Decimal> hodnotu:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery3_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery3_mq)]  
  
## <a name="example"></a>Příklad  
 Následující příklad zkompiluje a poté vyvolá dotaz, který přijímá <xref:System.String> vstupní parametr, a potom vrátí, `Contact` jehož e-mailová adresa začíná zadaným řetězcem:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery4_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery4_mq)]  
  
## <a name="example"></a>Příklad  
 Následující příklad zkompiluje a poté vyvolá dotaz, který přijímá <xref:System.DateTime> a <xref:System.Decimal> vstupní parametry a vrací sekvenci objednávek, kde je datum objednávky pozdější než 8. března 2003 a celková hodnota je menší než $300,00:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery5)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery5)]  
  
## <a name="example"></a>Příklad  
 Následující příklad zkompiluje a poté vyvolá dotaz, který přijímá <xref:System.DateTime> vstupní parametr a vrátí sekvenci objednávek, kde je datum objednávky pozdější než 8. března 2004. Tento dotaz vrátí informace o objednávce jako posloupnost anonymních typů. Anonymní typy jsou odvozeny kompilátorem, takže nelze zadat parametry typu v <xref:System.Data.Objects.CompiledQuery> `Compile` metodě a typ je definován v samotném dotazu.  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery6)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery6)]  
  
## <a name="example"></a>Příklad  
 Následující příklad zkompiluje a poté vyvolá dotaz, který přijímá vstupní parametr struktury definované uživatelem a vrací sekvenci Orders. Struktura definuje počáteční a koncové datum a celkový počet parametrů dotazu a dotaz vrátí objednávky dodávané do 3. března 2003 s celkovým termínem větším než $700,00.  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery7)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery7)]  
  
 Struktura definující parametry dotazu:  
  
 [!code-csharp[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myparamsstruct)]
 [!code-vb[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myparamsstruct)]  
  
## <a name="see-also"></a>Viz také:

- [ADO.NET Entity Framework](../index.md)
- [LINQ to Entities](linq-to-entities.md)
- [Entity Framework možnosti sloučení a zkompilované dotazy](https://go.microsoft.com/fwlink/?LinkId=199591)
