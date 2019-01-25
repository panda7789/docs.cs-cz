---
title: Známé problémy a aspekty u LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: acd71129-5ff0-4b4e-b266-c72cc0c53601
ms.openlocfilehash: ca67a01d8f1bc76773a7794169e93d026fe222d7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717959"
---
# <a name="known-issues-and-considerations-in-linq-to-entities"></a>Známé problémy a aspekty u LINQ to Entities
Tato část obsahuje informace o známých problémech s [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazy.  
  
-   [Dotazy LINQ, nelze uložit do mezipaměti](#LINQQueriesThatAreNotCached)  
  
-   [Informace o ztrátě objednávce](#OrderingInfoLost)  
  
-   [Celá čísla bez znaménka není podporován](#UnsignedIntsUnsupported)  
  
-   [Chyby převodu typů](#TypeConversionErrors)  
  
-   [Odkazuje na Neskalární proměnné není podporován](#RefNonScalarClosures)  
  
-   [Vnořené dotazy může selhat s SQL Server 2000](#NestedQueriesSQL2000)  
  
-   [Promítání na anonymního typu](#ProjectToAnonymousType)  
  
<a name="LINQQueriesThatAreNotCached"></a>   
## <a name="linq-queries-that-cannot-be-cached"></a>Dotazy LINQ, nelze uložit do mezipaměti  
 Od verze rozhraní .NET Framework 4.5, dotazech LINQ to Entities jsou automaticky uloží do mezipaměti. Ale dotazech LINQ to Entities, které se týkají `Enumerable.Contains` nejsou v operátoru na kolekce v paměti automaticky uložené v mezipaměti. Také Parametrizace kolekce v paměti v kompilované dotazy LINQ není povoleno.  
  
<a name="OrderingInfoLost"></a>   
## <a name="ordering-information-lost"></a>Informace o ztrátě objednávce  
 Projekce sloupce do anonymního typu způsobí, že pořadí informace, které ztraceno v nějaké dotazy, které jsou spouštěny proti [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)] databáze nastavená na úroveň kompatibility "80".  Proběhne, když název sloupce v seznamu order by odpovídá názvu sloupce v modulu pro výběr, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt543840)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt543840)]  
  
<a name="UnsignedIntsUnsupported"></a>   
## <a name="unsigned-integers-not-supported"></a>Celá čísla bez znaménka není podporován  
 Určení typu celé číslo bez znaménka v [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotaz se nepodporuje, protože [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] nepodporuje celých čísel bez znaménka. Pokud zadáte celé číslo bez znaménka, <xref:System.ArgumentException> bude vyvolána výjimka při překladu výrazu dotazu, jak je znázorněno v následujícím příkladu. Tento příklad dotazy pro objednávky s ID 48000.  
  
 [!code-csharp[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#uintasqueryparam)]
 [!code-vb[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#uintasqueryparam)]  
  
<a name="TypeConversionErrors"></a>   
## <a name="type-conversion-errors"></a>Chyby převodu typů  
 V jazyce Visual Basic, když vlastnost je mapováno na sloupec typu verze SQL serveru s hodnotou 1 pomocí `CByte` funkce, <xref:System.Data.SqlClient.SqlException> je vyvolána výjimka se zpráva "Chyba aritmetického přetečení". Následující příklady dotazů `Product.MakeFlag` sloupec v ukázkové databázi AdventureWorks a výjimka je vyvolána, když jsou procházen výsledky dotazu.  
  
 [!code-vb[DP L2E Conceptual Examples#SBUDT544355](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt544355)]  
  
<a name="RefNonScalarClosures"></a>   
## <a name="referencing-non-scalar-variables-not-supported"></a>Odkazuje na Neskalární proměnné není podporován  
 Odkazování na neskalární proměnných, například entitu v dotazu se nepodporuje. Když takový dotaz spuštěn, <xref:System.NotSupportedException> je vyvolána výjimka a zobrazí se zpráva s oznámením "nelze vytvořit konstantní hodnotu typu `EntityType`. Pouze primitivní typy ("například Int32, String a Guid") jsou v tomto kontextu podporován."  
  
> [!NOTE]
>  Odkazování na sadu skalární proměnné je podporována.  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt555877)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt555877)]  
  
<a name="NestedQueriesSQL2000"></a>   
## <a name="nested-queries-may-fail-with-sql-server-2000"></a>Vnořené dotazy může selhat s SQL Server 2000  
 S SQL Server 2000 dotazech LINQ to Entities může selhat, pokud vytvářejí vnořené dotazy Transact-SQL, které jsou tři nebo více úrovní do hloubky.  
  
<a name="ProjectToAnonymousType"></a>   
## <a name="projecting-to-an-anonymous-type"></a>Promítání na anonymního typu  
 Pokud definujete vaší cesty počátečního dotazu, aby zahrnovala související objekty pomocí <xref:System.Data.Objects.ObjectQuery%601.Include%2A> metodu <xref:System.Data.Objects.ObjectQuery%601> a poté použít k projekci vrácených objektů na anonymní typ LINQ, objekty zadané v metodě zahrnout nejsou zahrnuty v dotazu výsledky.  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype1)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype1)]  
  
 Chcete-li získat související objekty, nejsou vrácené typy projektů do anonymního typu.  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype2)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype2)]  
  
## <a name="see-also"></a>Viz také:
- [LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
