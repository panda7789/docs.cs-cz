---
title: Kompilované dotazy (LINQ to Entities)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8025ba1d-29c7-4407-841b-d5a3bed40b7a
ms.openlocfilehash: 97ceef3377a67fc621a097843abade9c61c29ca1
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78848766"
---
# <a name="compiled-queries--linq-to-entities"></a>Kompilované dotazy (LINQ to Entities)
Pokud máte aplikaci, která provádí strukturálně podobné dotazy mnohokrát v entity framework, můžete často zvýšit výkon kompilací dotazu jednou a provádění několikrát s různými parametry. Aplikace může mít například načíst všechny zákazníky v určitém městě; město je specifikováno za běhu uživatelem ve formuláři. LINQ entity podporuje použití zkompilovaných dotazů pro tento účel.  
  
 Počínaje rozhraním .NET Framework 4.5 jsou dotazy LINQ ukládány do mezipaměti automaticky. Však můžete stále použít kompilované LINQ dotazy ke snížení těchto nákladů v pozdějších spuštění a zkompilované dotazy mohou být efektivnější než linq dotazy, které jsou automaticky uloženy do mezipaměti. Všimněte si, že linq entity `Enumerable.Contains` dotazy, které platí operátor v kolekcích v paměti nejsou automaticky ukládány do mezipaměti. Také parametrizace in-memory kolekce v kompilovaných linq dotazů není povoleno.  
  
 Třída <xref:System.Data.Objects.CompiledQuery> poskytuje kompilaci a ukládání dotazů do mezipaměti pro opakované použití. Koncepčně tato <xref:System.Data.Objects.CompiledQuery>třída `Compile` obsahuje 's metoda s několika přetížení. Volání `Compile` metody k vytvoření nového delegáta představují zkompilovaný dotaz. Metody, `Compile` které jsou <xref:System.Data.Objects.ObjectContext> k dispozici a hodnoty parametrů, vrátí delegáta, <xref:System.Linq.IQueryable%601> který vytváří určitý výsledek (například instanci). Dotaz zkompiluje jednou během pouze první spuštění. Možnosti sloučení nastavené pro dotaz v době kompilace nelze později změnit. Jakmile je dotaz zkompilován, můžete zadat pouze parametry primitivního typu, ale nelze nahradit části dotazu, které by změnily generované SQL. Další informace naleznete v tématu [ef merge options and compiled queries](https://docs.microsoft.com/archive/blogs/dsimmons/ef-merge-options-and-compiled-queries).
  
 Výraz dotazu LINQ to <xref:System.Data.Objects.CompiledQuery>Entities, který zkompiluje metodu 's, `Compile` je reprezentován jedním z obecných `Func` delegátů, například <xref:System.Func%605>. Výraz dotazu může maximálně zapouzdřit `ObjectContext` parametr, návratový parametr a parametry dotazu 16. Pokud je požadováno více než 16 parametrů dotazu, můžete vytvořit strukturu, jejíž vlastnosti představují parametry dotazu. Po nastavení vlastností pak můžete použít vlastnosti struktury ve výrazu dotazu.  
  
## <a name="example"></a>Příklad  
 Následující příklad zkompiluje a potom vyvolá <xref:System.Decimal> dotaz, který přijímá vstupní parametr a vrátí posloupnost objednávek, kde je součet splatných vyšší nebo roven $200.00:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery2)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery2)]  
  
## <a name="example"></a>Příklad  
 Následující příklad zkompiluje a potom <xref:System.Data.Objects.ObjectQuery%601> vyvolá dotaz, který vrací instanci:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery1_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery1_mq)]  
  
## <a name="example"></a>Příklad  
 Následující příklad zkompiluje a potom vyvolá dotaz, který vrací <xref:System.Decimal> průměr cen ceníků produktů jako hodnotu:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery3_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery3_mq)]  
  
## <a name="example"></a>Příklad  
 Následující příklad zkompiluje a potom vyvolá <xref:System.String> dotaz, který `Contact` přijímá vstupní parametr a pak vrátí, jehož e-mailová adresa začíná zadaným řetězcem:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery4_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery4_mq)]  
  
## <a name="example"></a>Příklad  
 Následující příklad zkompiluje a potom <xref:System.DateTime> vyvolá <xref:System.Decimal> dotaz, který přijímá a zadává parametry a vrací posloupnost objednávek, kde datum objednávky je pozdější než 8.  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery5)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery5)]  
  
## <a name="example"></a>Příklad  
 Následující příklad zkompiluje a potom vyvolá <xref:System.DateTime> dotaz, který přijímá vstupní parametr a vrátí posloupnost objednávek, kde datum objednávky je pozdější než 8. Tento dotaz vrátí informace o objednávce jako posloupnost anonymních typů. Anonymní typy jsou odvozeny kompilátorem, takže nelze zadat <xref:System.Data.Objects.CompiledQuery>parametry typu v metodě 's `Compile` a typ je definován v samotném dotazu.  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery6)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery6)]  
  
## <a name="example"></a>Příklad  
 Následující příklad zkompiluje a potom vyvolá dotaz, který přijímá vstupní parametr struktury definované uživatelem a vrací posloupnost objednávek. Struktura definuje počáteční datum, koncové datum a parametry celkového splatnosti dotazu a dotaz vrátí objednávky odeslané mezi 3.  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery7)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery7)]  
  
 Struktura, která definuje parametry dotazu:  
  
 [!code-csharp[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myparamsstruct)]
 [!code-vb[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myparamsstruct)]  
  
## <a name="see-also"></a>Viz také

- [ADO.NET Entity Framework](../index.md)
- [LINQ to Entities](linq-to-entities.md)
- [Možnosti sloučení EF a zkompilované dotazy](https://docs.microsoft.com/archive/blogs/dsimmons/ef-merge-options-and-compiled-queries)
