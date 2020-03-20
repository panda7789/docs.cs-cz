---
title: Známé problémy a aspekty u LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: acd71129-5ff0-4b4e-b266-c72cc0c53601
ms.openlocfilehash: 90119da0fce7a708323d790f91f28206cac0a0dc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150139"
---
# <a name="known-issues-and-considerations-in-linq-to-entities"></a>Známé problémy a aspekty u LINQ to Entities
Tato část obsahuje informace o známých problémech s dotazy LINQ na entity.  
  
- [Dotazy LINQ, které nelze uložit do mezipaměti](#LINQQueriesThatAreNotCached)  
  
- [Informace o objednávce ztraceny](#OrderingInfoLost)  
  
- [Nepodepsaná celá čísla nejsou podporována](#UnsignedIntsUnsupported)  
  
- [Chyby převodu typu](#TypeConversionErrors)  
  
- [Odkazování na neskalární proměnné není podporováno](#RefNonScalarClosures)  
  
- [Vnořené dotazy mohou selhat se serverem SQL Server 2000](#NestedQueriesSQL2000)  
  
- [Promítání na anonymní typ](#ProjectToAnonymousType)  
  
<a name="LINQQueriesThatAreNotCached"></a>
## <a name="linq-queries-that-cannot-be-cached"></a>Dotazy LINQ, které nelze uložit do mezipaměti  
 Počínaje rozhraním .NET Framework 4.5 jsou dotazy LINQ na entity automaticky ukládány do mezipaměti. Linq na entity dotazy, které `Enumerable.Contains` platí operátor v kolekcích v paměti nejsou automaticky ukládány do mezipaměti. Také parametrizace in-memory kolekce v kompilovaných linq dotazů není povoleno.  
  
<a name="OrderingInfoLost"></a>
## <a name="ordering-information-lost"></a>Informace o objednávce ztraceny  
 Promítání sloupců do anonymního typu způsobí ztrátu informací o objednávce v některých dotazech, které jsou provedeny proti databázi serveru SQL Server 2005 nastavené na úroveň kompatibility "80".  K tomu dochází, když název sloupce v seznamu podle pořadí odpovídá názvu sloupce v selektoru, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt543840)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt543840)]  
  
<a name="UnsignedIntsUnsupported"></a>
## <a name="unsigned-integers-not-supported"></a>Nepodepsaná celá čísla nejsou podporována  
 Zadání nepodepsaného celého typu v dotazu LINQ na entity není podporováno, protože entity Framework nepodporuje nepodepsaná celá čísla. Pokud zadáte nepodepsané celé číslo, <xref:System.ArgumentException> bude během překladu výrazu dotazu vyvolána výjimka, jak je znázorněno v následujícím příkladu. Tento příklad se dotazuje na objednávku s ID 48000.  
  
 [!code-csharp[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#uintasqueryparam)]
 [!code-vb[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#uintasqueryparam)]  
  
<a name="TypeConversionErrors"></a>
## <a name="type-conversion-errors"></a>Chyby převodu typu  
 V jazyce Visual Basic při namapovat vlastnost na sloupec sql server `CByte` typu bitu s hodnotou 1 pomocí funkce, <xref:System.Data.SqlClient.SqlException> je vyvolána s "aritmetické přetečení chyby" zpráva. Následující příklad dotazuje `Product.MakeFlag` sloupec v adventureworks ukázkové databáze a je vyvolána výjimka, když jsou výsledky dotazu iterovány přes.  
  
 [!code-vb[DP L2E Conceptual Examples#SBUDT544355](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt544355)]  
  
<a name="RefNonScalarClosures"></a>
## <a name="referencing-non-scalar-variables-not-supported"></a>Odkazování na neskalární proměnné není podporováno  
 Odkazování na neskalární proměnné, jako je entita, v dotazu není podporováno. Při spuštění takového dotazu <xref:System.NotSupportedException> je vyvolána výjimka se zprávou "Nelze vytvořit `EntityType`konstantní hodnotu typu . V tomto kontextu jsou podporovány pouze primitivní typy (například Int32, String a Guid).  
  
> [!NOTE]
> Odkazování na kolekci skalárních proměnných je podporováno.  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt555877)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt555877)]  
  
<a name="NestedQueriesSQL2000"></a>
## <a name="nested-queries-may-fail-with-sql-server-2000"></a>Vnořené dotazy mohou selhat se serverem SQL Server 2000  
 S SQL Server 2000 LINQ entity dotazy může selhat, pokud vytvářejí vnořené transact-SQL dotazy, které jsou tři nebo více úrovní hluboké.  
  
<a name="ProjectToAnonymousType"></a>
## <a name="projecting-to-an-anonymous-type"></a>Promítání na anonymní typ  
 Pokud definujete počáteční cestu dotazu zahrnout <xref:System.Data.Objects.ObjectQuery%601.Include%2A> související objekty pomocí metody na <xref:System.Data.Objects.ObjectQuery%601> a potom pomocí LINQ promítat vrácené objekty anonymní typ, objekty zadané v include metoda nejsou zahrnuty ve výsledcích dotazu.  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype1)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype1)]  
  
 Chcete-li získat související objekty, nepromítejte vrácené typy anonymnímu typu.  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype2)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype2)]  
  
## <a name="see-also"></a>Viz také

- [LINQ to Entities](linq-to-entities.md)
