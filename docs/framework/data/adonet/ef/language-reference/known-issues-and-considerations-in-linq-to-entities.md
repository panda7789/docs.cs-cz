---
title: Známé problémy a aspekty u LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: acd71129-5ff0-4b4e-b266-c72cc0c53601
ms.openlocfilehash: 7be3491af48ad29cd7892dd31a077aa7ac44ca63
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250490"
---
# <a name="known-issues-and-considerations-in-linq-to-entities"></a>Známé problémy a aspekty u LINQ to Entities
V této části najdete informace o známých problémech s LINQ to Entities dotazy.  
  
- [Dotazy LINQ, které nelze uložit do mezipaměti](#LINQQueriesThatAreNotCached)  
  
- [Došlo ke ztrátě informací o objednávání.](#OrderingInfoLost)  
  
- [Celá čísla bez znaménka nejsou podporovaná.](#UnsignedIntsUnsupported)  
  
- [Chyby konverze typu](#TypeConversionErrors)  
  
- [Odkazování na jiné než skalární proměnné se nepodporuje.](#RefNonScalarClosures)  
  
- [Vnořené dotazy mohou selhat s SQL Server 2000](#NestedQueriesSQL2000)  
  
- [Projektování na anonymní typ](#ProjectToAnonymousType)  
  
<a name="LINQQueriesThatAreNotCached"></a>   
## <a name="linq-queries-that-cannot-be-cached"></a>Dotazy LINQ, které nelze uložit do mezipaměti  
 Počínaje .NET Framework 4,5 jsou dotazy LINQ to Entities automaticky ukládány do mezipaměti. Nicméně LINQ to Entities dotazy, které aplikují `Enumerable.Contains` operátor na kolekce v paměti, nejsou automaticky ukládány do mezipaměti. V kompilovaných dotazech LINQ se taky Parametrizace kolekce v paměti, které se nepovolují.  
  
<a name="OrderingInfoLost"></a>   
## <a name="ordering-information-lost"></a>Došlo ke ztrátě informací o objednávání.  
 Při projednávání sloupců do anonymního typu dojde ke ztrátě informací o objednávce v některých dotazech, které jsou spouštěny s databází SQL Server 2005 nastavenou na úroveň kompatibility "80".  K tomu dochází, když název sloupce v seznamu ORDER-by odpovídá názvu sloupce v selektoru, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt543840)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt543840)]  
  
<a name="UnsignedIntsUnsupported"></a>   
## <a name="unsigned-integers-not-supported"></a>Celá čísla bez znaménka nejsou podporovaná.  
 Určení typu unsigned integer v dotazu LINQ to Entities není podporováno, protože [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] nepodporuje celá čísla bez znaménka. Zadáte-li unsigned integer, <xref:System.ArgumentException> bude vyvolána výjimka během překladu výrazu dotazu, jak je znázorněno v následujícím příkladu. V tomto příkladu se dotazuje na objednávku s ID 48000.  
  
 [!code-csharp[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#uintasqueryparam)]
 [!code-vb[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#uintasqueryparam)]  
  
<a name="TypeConversionErrors"></a>   
## <a name="type-conversion-errors"></a>Chyby konverze typu  
 V Visual Basic `CByte` <xref:System.Data.SqlClient.SqlException> je při mapování vlastnosti na sloupec SQL Server bitového typu s hodnotou 1 pomocí funkce vyvolána zpráva "Chyba aritmetického přetečení". Následující příklad provede dotaz na `Product.MakeFlag` sloupec v ukázkové databázi AdventureWorks a vyvolá výjimku při iteraci výsledků dotazu.  
  
 [!code-vb[DP L2E Conceptual Examples#SBUDT544355](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt544355)]  
  
<a name="RefNonScalarClosures"></a>   
## <a name="referencing-non-scalar-variables-not-supported"></a>Odkazování na jiné než skalární proměnné se nepodporuje.  
 Odkazování na jiné než skalární proměnné, jako je například entita, není v dotazu podporováno. Pokud se takový dotaz spustí, <xref:System.NotSupportedException> je vyvolána výjimka se zprávou, že se zobrazí zpráva "nelze vytvořit konstantní hodnotu typu. `EntityType` V tomto kontextu jsou podporovány pouze primitivní typy (například Int32, String a GUID). "  
  
> [!NOTE]
> Odkazování na kolekci skalárních proměnných je podporováno.  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt555877)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt555877)]  
  
<a name="NestedQueriesSQL2000"></a>   
## <a name="nested-queries-may-fail-with-sql-server-2000"></a>Vnořené dotazy mohou selhat s SQL Server 2000  
 V případě SQL Server 2000 mohou dotazy LINQ to Entities selhat, pokud budou vyprodukovány vnořené dotazy Transact-SQL, které mají hloubku tři nebo více úrovní.  
  
<a name="ProjectToAnonymousType"></a>   
## <a name="projecting-to-an-anonymous-type"></a>Projektování na anonymní typ  
 Definujete-li počáteční cestu dotazu pro zahrnutí souvisejících objektů pomocí <xref:System.Data.Objects.ObjectQuery%601.Include%2A> metody <xref:System.Data.Objects.ObjectQuery%601> v a poté pomocí LINQ k navrácení vrácených objektů do anonymního typu, objekty zadané v metodě include nejsou zahrnuty v dotazu. důsledk.  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype1)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype1)]  
  
 Chcete-li získat související objekty, neprojekt vrátí typy do anonymního typu.  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype2)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype2)]  
  
## <a name="see-also"></a>Viz také:

- [LINQ to Entities](linq-to-entities.md)
