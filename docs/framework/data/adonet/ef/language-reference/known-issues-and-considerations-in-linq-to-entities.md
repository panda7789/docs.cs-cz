---
title: "Známé problémy a aspekty v technologii LINQ to Entities"
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
ms.assetid: acd71129-5ff0-4b4e-b266-c72cc0c53601
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: b4517f34f3c7753b2aa0ee0ba576765f0d7cf83e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="known-issues-and-considerations-in-linq-to-entities"></a>Známé problémy a aspekty v technologii LINQ to Entities
Tato část obsahuje informace o známých problémech s [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazy.  
  
-   [LINQ dotazů, nelze uložit do mezipaměti](#LINQQueriesThatAreNotCached)  
  
-   [Ke ztrátě informace o objednávce](#OrderingInfoLost)  
  
-   [Znaménka není podporován](#UnsignedIntsUnsupported)  
  
-   [Chyby při převodu typu](#TypeConversionErrors)  
  
-   [Odkazování na Neskalární proměnné není podporován](#RefNonScalarClosures)  
  
-   [Vnořené dotazy pravděpodobně dojde k chybě systému SQL Server 2000](#NestedQueriesSQL2000)  
  
-   [Anonymní typ projekce](#ProjectToAnonymousType)  
  
<a name="LINQQueriesThatAreNotCached"></a>   
## <a name="linq-queries-that-cannot-be-cached"></a>LINQ dotazů, nelze uložit do mezipaměti  
 Od verze rozhraní .NET Framework 4.5, technologie LINQ to Entities dotazy jsou automaticky uloží do mezipaměti. Však technologie LINQ to Entities dotazy které se týkají `Enumerable.Contains` operátor do kolekcí v paměti neukládají do mezipaměti automaticky. Také Parametrizace kolekce v paměti v kompilovaném dotazů LINQ není povoleno.  
  
<a name="OrderingInfoLost"></a>   
## <a name="ordering-information-lost"></a>Ke ztrátě informace o objednávce  
 Projekce sloupce do anonymní typ způsobí, že řazení informace ztraceny v některé dotazy, které jsou spouštěny proti [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)] databázi nastavit úroveň kompatibility "80".  Tato situace nastane při název sloupce v seznamu order by odpovídá název sloupce v modulu pro výběr, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt543840)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt543840)]  
  
<a name="UnsignedIntsUnsupported"></a>   
## <a name="unsigned-integers-not-supported"></a>Znaménka není podporován  
 Určení typ celé číslo bez znaménka v [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotaz není podporována, protože [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] nepodporuje celých čísel bez znaménka. Pokud zadáte celé číslo bez znaménka <xref:System.ArgumentException> dojde k výjimce během překlad výrazu dotazu, jak je znázorněno v následujícím příkladu. Tento příklad dotazy pro pořadí s ID 48000.  
  
 [!code-csharp[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#uintasqueryparam)]
 [!code-vb[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#uintasqueryparam)]  
  
<a name="TypeConversionErrors"></a>   
## <a name="type-conversion-errors"></a>Chyby při převodu typu  
 V jazyce Visual Basic vlastnost je namapována na sloupec typu verze systému SQL Server s hodnotou 1 pomocí `CByte` funkce, <xref:System.Data.SqlClient.SqlException> je vyvolána se zpráva "Chyba aritmetického přetečení". Následující příklad dotazy `Product.MakeFlag` sloupec v ukázkové databázi AdventureWorks a výjimku se vyvolá, když výsledky dotazu jsou vstupní přes.  
  
 [!code-vb[DP L2E Conceptual Examples#SBUDT544355](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt544355)]  
  
<a name="RefNonScalarClosures"></a>   
## <a name="referencing-non-scalar-variables-not-supported"></a>Odkazování na Neskalární proměnné není podporován  
 Odkazování na neskalární proměnné, jako například entitu v dotazu není podporována. Když je takový dotaz spuštěn, <xref:System.NotSupportedException> se zpráva, že je vyvolána výjimka "nejde vytvořit konstantní hodnotu typu `EntityType`. Jenom primitivní typy ('například Int32, String a identifikátor Guid') jsou podporovány v tomto kontextu."  
  
> [!NOTE]
>  Odkazování na kolekci skalární proměnné je podporována.  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt555877)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt555877)]  
  
<a name="NestedQueriesSQL2000"></a>   
## <a name="nested-queries-may-fail-with-sql-server-2000"></a>Vnořené dotazy pravděpodobně dojde k chybě systému SQL Server 2000  
 Se serverem SQL Server 2000 technologie LINQ to Entities dotazy může selhat, pokud vytvářejí vnořené dotazy jazyka Transact-SQL, které jsou tři nebo více úrovněmi.  
  
<a name="ProjectToAnonymousType"></a>   
## <a name="projecting-to-an-anonymous-type"></a>Anonymní typ projekce  
 Pokud definujete počátečního dotazu cestu ke zahrnout související objekty pomocí <xref:System.Data.Objects.ObjectQuery%601.Include%2A> metodu <xref:System.Data.Objects.ObjectQuery%601> a pak pomocí LINQ vrácených objektů anonymní typ projektu, objekty uvedené v metodě zahrnout nejsou zahrnuty v dotazu výsledky.  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype1)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype1)]  
  
 Chcete-li získat související objekty, není vrácená typy projektů anonymní typ.  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype2)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype2)]  
  
## <a name="see-also"></a>Viz také  
 [LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
