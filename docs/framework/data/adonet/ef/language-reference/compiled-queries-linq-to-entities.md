---
title: "Kompilované dotazy (LINQ to Entities)"
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
ms.assetid: 8025ba1d-29c7-4407-841b-d5a3bed40b7a
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 7ca9848d4640fe9d941b3bfc15a7762135871861
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="compiled-queries--linq-to-entities"></a>Kompilované dotazy (LINQ to Entities)
Když máte aplikaci, která provádí strukturálně podobné dotazy mnohokrát v rozhraní Entity Framework, můžete zvýšit výkon často kompilování dotazu jednou a spouštění s odlišnými parametry několikrát. Například aplikace může mít načíst všechny zákazníky z určitého města; Město je zadána v době běhu uživatele ve formuláři. Technologie LINQ to Entities podporuje používání kompilované dotazy pro tento účel.  
  
 Od verze rozhraní .NET Framework 4.5, dotazů LINQ jsou uložené v mezipaměti automaticky. Však můžete nadále používat kompilované dotazů LINQ na snížení nákladů na tento v novější spuštěních a kompilované dotazy může být efektivnější než LINQ dotazů, které jsou automaticky uloží do mezipaměti. Všimněte si, že technologie LINQ to Entities dotazuje použít `Enumerable.Contains` operátor do kolekcí v paměti neukládají do mezipaměti automaticky. Také Parametrizace kolekce v paměti v kompilovaném dotazů LINQ není povoleno.  
  
 <xref:System.Data.Objects.CompiledQuery> Třída poskytuje kompilace a ukládání do mezipaměti dotazů pro opakované použití. Koncepčně, tato třída obsahuje <xref:System.Data.Objects.CompiledQuery>na `Compile` metoda s několik přetížení. Volání `Compile` metodu pro vytvoření nového delegáta představují kompilovaném dotazu. `Compile` Metody, pokud se <xref:System.Data.Objects.ObjectContext> a hodnoty parametrů, vrátí delegáta, který vytváří některé výsledek (například <xref:System.Linq.IQueryable%601> instance). Jednou během pouze první provádění zkompiluje dotaz. Možnosti sloučení nastavit dotazu v době kompilace není možné později změnit. Jakmile zkompilován dotaz můžete jenom zadat parametry primitivní typ, ale nelze nahradit částí dotazu, který by způsobila změnu generovaného SQL. Další informace najdete v tématu [možnosti sloučení Entity Framework a zkompilovat dotazy](http://go.microsoft.com/fwlink/?LinkId=199591)  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] Výraz dotazu, <xref:System.Data.Objects.CompiledQuery>na `Compile` je metoda zkompiluje reprezentované pomocí jedné z obecná `Func` deleguje, jako například <xref:System.Func%605>. Maximálně může zapouzdřit výrazu dotazu `ObjectContext` parametr, návratový parametr a 16 parametry dotazu. Pokud jsou vyžadovány víc než 16 parametry dotazu, můžete vytvořit strukturu, jehož vlastnosti představují parametry dotazu. Potom můžete vytvořit vlastnosti ve struktuře ve výrazu dotazu po nastavení vlastností.  
  
## <a name="example"></a>Příklad  
 Následující příklad zkompiluje a potom se vyvolá dotaz, který přijímá <xref:System.Decimal> vstupní parametr a vrátí posloupnost objednávky, kde splatnosti celkový počet je větší než nebo rovna hodnotě $200,00:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery2)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery2)]  
  
## <a name="example"></a>Příklad  
 Následující příklad zkompiluje a potom se vyvolá dotaz, který vrátí <xref:System.Data.Objects.ObjectQuery%601> instance:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery1_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery1_mq)]  
  
## <a name="example"></a>Příklad  
 Následující příklad zkompiluje a potom se vyvolá dotaz, který vrátí průměrnou hodnotu seznamu ceny produktů jako <xref:System.Decimal> hodnotu:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery3_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery3_mq)]  
  
## <a name="example"></a>Příklad  
 Následující příklad zkompiluje a potom se vyvolá dotaz, který přijímá <xref:System.String> vstupní parametr a potom vrátí `Contact` jejichž e-mailová adresa začíná zadaný řetězec:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery4_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery4_mq)]  
  
## <a name="example"></a>Příklad  
 Následující příklad zkompiluje a potom se vyvolá dotaz, který přijímá <xref:System.DateTime> a <xref:System.Decimal> vstupní parametry a vrátí posloupnost řadí kde datu objednávky je novější než 8. března 2003 a celkový počet z důvodu je menší než 300.00 $:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery5)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery5)]  
  
## <a name="example"></a>Příklad  
 Následující příklad zkompiluje a potom se vyvolá dotaz, který přijímá <xref:System.DateTime> vstupní parametr a vrátí posloupnost objednávky, kde je novější než 8. března 2004 datu objednávky. Tento dotaz vrací informace o objednávce jako posloupnost anonymní typů. Anonymní typy jsou odvodit kompilátorem, takže nelze zadat parametry typu v <xref:System.Data.Objects.CompiledQuery>na `Compile` metoda a typ je definována v samotném dotazu.  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery6)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery6)]  
  
## <a name="example"></a>Příklad  
 Následující příklad zkompiluje a potom se vyvolá dotaz, který přijímá struktura uživatelem definované vstupní parametr a vrátí posloupnost objednávky. Struktura definuje počáteční datum, koncové datum a celkový počet kvůli parametry dotazu a dotaz vrátí objednávky zaslané mezi března 3 až 8. března 2003 celkem z důvodu větší než 700.00 $.  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery7)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery7)]  
  
 Struktura, která definuje parametry dotazu:  
  
 [!code-csharp[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myparamsstruct)]
 [!code-vb[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myparamsstruct)]  
  
## <a name="see-also"></a>Viz také  
 [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)  
 [LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)  
 [Rozhraní Entity Framework možnosti sloučení a zkompilovat dotazy](http://go.microsoft.com/fwlink/?LinkId=199591)
