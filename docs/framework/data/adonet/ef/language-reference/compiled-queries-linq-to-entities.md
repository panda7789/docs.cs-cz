---
title: Kompilované dotazy (LINQ to Entities)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8025ba1d-29c7-4407-841b-d5a3bed40b7a
ms.openlocfilehash: f3ba6bfd0f83270bc6b9e980fe92f6630c90ad49
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785343"
---
# <a name="compiled-queries--linq-to-entities"></a>Kompilované dotazy (LINQ to Entities)
Až budete mít aplikaci, která spustí dotazy strukturálně podobně jako v mnoha případech v Entity Framework, můžete často zvýšit výkon kompilaci dotazu jednou a spustíte ji několikrát s různými parametry. Například aplikace může mít k načtení všech zákazníků v konkrétním městě; Město je uživatel zadá za běhu ve formuláři. Technologie LINQ to Entities podporuje používání kompilované dotazy pro tento účel.  
  
 Od verze rozhraní .NET Framework 4.5, LINQ dotazy jsou uložené v mezipaměti automaticky. Nicméně stále můžete kompilované dotazy LINQ v pozdější spuštění tyto náklady snížit a kompilované dotazy může být efektivnější než LINQ dotazy, které se automaticky uloží do mezipaměti. Všimněte si, že technologie LINQ to Entities dotazy, které platí `Enumerable.Contains` nejsou v operátoru na kolekce v paměti automaticky uložené v mezipaměti. Také Parametrizace kolekce v paměti v kompilované dotazy LINQ není povoleno.  
  
 <xref:System.Data.Objects.CompiledQuery> Třída poskytuje kompilace a ukládání do mezipaměti dotazů pro opakované použití. Koncepčně, tato třída obsahuje <xref:System.Data.Objects.CompiledQuery>společnosti `Compile` metodu s několik přetížení. Volání `Compile` metodu pro vytvoření nového delegáta k reprezentaci kompilovaném dotazu. `Compile` Metody, opatřeného <xref:System.Data.Objects.ObjectContext> a hodnoty parametrů, vrátí delegáta, který vytváří některé výsledek (například <xref:System.Linq.IQueryable%601> instance). Dotaz zkompiluje jednou během prvního spuštění. Možnosti sloučení v době kompilace nastaven pro dotaz není možné později změnit. Jakmile je zkompilován dotaz lze zadat pouze primitivní typy parametrů, ale nelze nahradit části dotazu, který by změna generovaného SQL. Další informace najdete v tématu [možnosti sloučení Entity Framework a kompilaci dotazů](https://go.microsoft.com/fwlink/?LinkId=199591)  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] Výrazu dotazu, který <xref:System.Data.Objects.CompiledQuery>společnosti `Compile` je metoda zkompiluje reprezentované pomocí jedné z obecného `Func` delegátů, jako například <xref:System.Func%605>. Maximálně lze zapouzdřit výrazu dotazu `ObjectContext` parametr, návratový parametr a 16 parametry dotazu. Pokud požadujete víc než 16 parametry dotazu, můžete vytvořit strukturu, jejíž vlastnosti představují parametry dotazu. Pak můžete použít vlastnosti na struktuře ve výrazu dotazu po nastavení vlastnosti.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu zkompiluje a potom vyvolá dotaz, který přijímá <xref:System.Decimal> vstupní parametr a vrátí sekvenci objednávek, ve kterém je celková částka větší než nebo rovna hodnotě $200,00:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery2)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery2)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu zkompiluje a potom vyvolá dotaz, který vrátí <xref:System.Data.Objects.ObjectQuery%601> instance:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery1_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery1_mq)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu zkompiluje a potom vyvolá dotaz, který vrátí průměrnou hodnotu seznamu ceny produktu jako <xref:System.Decimal> hodnotu:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery3_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery3_mq)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu zkompiluje a potom vyvolá dotaz, který přijímá <xref:System.String> vstupní parametr a potom vrátí `Contact` jehož e-mailová adresa začíná zadaný řetězec:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery4_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery4_mq)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu zkompiluje a potom vyvolá dotaz, který přijímá <xref:System.DateTime> a <xref:System.Decimal> vstupní parametry a vrací posloupnost orders, ve kterém je datum objednávky pozdější než 8. března 2003 a součet z důvodu je menší než 300.00 $:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery5)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery5)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu zkompiluje a potom vyvolá dotaz, který přijímá <xref:System.DateTime> vstupní parametr a vrátí sekvenci objednávek, ve kterém je datum objednávky pozdější než 8. března 2004. Tento dotaz vrátí informace o objednávce jako sekvenci anonymních typů. Anonymní typy jsou odvozeny kompilátorem, takže nelze zadat parametry typu v <xref:System.Data.Objects.CompiledQuery>společnosti `Compile` metoda a typ je definován v samotném dotazu.  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery6)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery6)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu zkompiluje a potom vyvolá dotaz, který přijímá struktury uživatelem definované vstupní parametr a vrátí sekvenci objednávek. Definuje strukturu počáteční datum, datum ukončení a součet z důvodu parametrů dotazu a dotaz vrátí objednávky odeslané mezi dne 3 až 8. března 2003 celkem z důvodu větší než 700.00 $.  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery7)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery7)]  
  
 Struktura, která definuje parametry dotazu:  
  
 [!code-csharp[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myparamsstruct)]
 [!code-vb[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myparamsstruct)]  
  
## <a name="see-also"></a>Viz také:

- [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)
- [LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
- [Možnosti sloučení Entity Framework a kompilované dotazy](https://go.microsoft.com/fwlink/?LinkId=199591)
