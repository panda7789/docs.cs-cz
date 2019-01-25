---
title: Porovnávání s hodnotou Null
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ef88af8c-8dfe-4556-8b56-81df960a900b
ms.openlocfilehash: b5535343b5ac40b12aa06ffb5b587e114f5cd757
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521398"
---
# <a name="null-comparisons"></a>Porovnávání s hodnotou Null
A `null` hodnota ve zdroji dat znamená, že hodnota neznámý. V [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazy, můžete zkontrolovat hodnoty null, tak že určité výpočtů nebo porovnání se provádí pouze u řádků, které mají platný nebo není null, data. Sémantika s hodnotou null CLR, ale může lišit od sémantika s hodnotou null zdroj dat. Většina databází použijte verzi s hodnotou tři logiku ke zpracování porovnávání s hodnotou null. To znamená, že porovnání proti hodnota null není vyhodnocen na `true` nebo `false`, je vyhodnocen jako `unknown`. Často je jím implementace ANSI hodnoty Null, ale není to vždy.  
  
 Ve výchozím nastavení v systému SQL Server porovnání null. je rovno null, vrátí hodnotu null. V následujícím příkladu, řádky kde `ShipDate` má hodnotu null jsou vyloučeny ze sady výsledků a [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] příkaz vrátí 0 řádků.  
  
```  
-- Find order details and orders with no ship date.  
SELECT h.SalesOrderID  
FROM Sales.SalesOrderHeader h  
JOIN Sales.SalesOrderDetail o ON o.SalesOrderID = h.SalesOrderID  
WHERE h.ShipDate IS Null  
```  
  
 To je velmi liší od sémantiky null CLR, kde porovnání null. je rovno null, vrátí hodnotu true.  
  
 Následující dotaz LINQ je vyjádřen v modulu CLR, ale provádí se ve zdroji dat. Protože neexistuje žádná záruka, že sémantika CLR bude zachované ve zdroji dat, je neurčité očekávané chování.  
  
 [!code-csharp[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#joinonnull)]
 [!code-vb[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#joinonnull)]  
  
## <a name="key-selectors"></a>Klíče selektorů.  
 A *selektoru klíče* je funkce ve standardních operátorů pro dotazování použít k extrahování klíče z elementu. Ve funkci selektoru klíče může být výraz porovnáván s konstantou. Sémantika s hodnotou null CLR jsou vystaveny, pokud výrazu je porovnán s hodnotou null – konstanta, nebo pokud jsou porovnány dva null konstanty. Pokud jsou porovnány dva sloupce s hodnotami null ve zdroji dat jsou vystaveny Store sémantika s hodnotou null. Klíče selektory se nacházejí v mnoha seskupení a řazení operátory standardního dotazu, jako například <xref:System.Linq.Queryable.GroupBy%2A>a slouží k výběru klíče pomocí kterého pořadí nebo seskupení výsledků dotazu.  
  
## <a name="null-property-on-a-null-object"></a>Vlastnost Null na objekt s hodnotou Null  
 V [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)], mají hodnotu null vlastnosti objekt s hodnotou null. Při pokusu o odkazovat na vlastnost objekt s hodnotou null v modulu CLR, zobrazí se <xref:System.NullReferenceException>. Při dotazu LINQ zahrnuje vlastnost objekt s hodnotou null, to může způsobit nekonzistentní chování.  
  
 Například v následujícím dotazem, přetypování na `NewProduct` se provádí v příkazovou úroveň stromu, který může mít za následek `Introduced` vlastnost je null. Pokud databázi definována porovnávání s hodnotou null tak, aby <xref:System.DateTime> porovnání vyhodnotí jako true, budou zahrnuty řádku.  
  
 [!code-csharp[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#castresultsisnull)]
 [!code-vb[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#castresultsisnull)]  
  
## <a name="passing-null-collections-to-aggregate-functions"></a>Předání kolekcí Null pro agregační funkce  
 V [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], při předání kolekce, která podporuje `IQueryable` agregační funkce, jsou agregační operace prováděny v databázi. Mohou existovat rozdíly ve výsledcích dotazu, který se provádí v paměti a dotaz, který byl proveden v databázi. Pomocí dotazu v paměti Pokud neexistují žádné odpovídající položky, dotaz vrátí hodnotu 0. V databázi, stejný dotaz vrací `null`. Pokud `null` LINQ agregační funkce je předána hodnota, bude vyvolána výjimka. Tak, aby přijímal možné `null` hodnoty, přetypujte typy a vlastnosti typů, které se zobrazí výsledky dotazu na typy s možnou hodnotou Null.  
  
## <a name="see-also"></a>Viz také:
- [Výrazy v dotazech LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
