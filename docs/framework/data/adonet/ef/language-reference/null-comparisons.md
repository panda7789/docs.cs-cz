---
title: "Porovnávání s hodnotou Null"
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
ms.assetid: ef88af8c-8dfe-4556-8b56-81df960a900b
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fefbd3894063c0298a7ad5110ed6867408869107
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="null-comparisons"></a>Porovnávání s hodnotou Null
A `null` hodnota ve zdroji dat znamená, že hodnota neznámý. V [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazy, můžete zkontrolovat, že některé výpočty hodnoty null nebo porovnání se provádí pouze na řádky, které mají platný nebo jinou hodnotu než null, data. CLR sémantiku hodnotu null, ale může lišit od null sémantika zdroj dat. Většina databáze použijte verzi s hodnotou tři logiku pro zpracování porovnání null. To znamená, porovnání s hodnotou null nejsou vyhodnocena `true` nebo `false`, se vyhodnotí jako `unknown`. Často je jím implementace ANSI hodnoty Null, ale není to vždy.  
  
 Ve výchozím nastavení v systému SQL Server vrátí hodnotu null. rovná null porovnání hodnotu null. V následujícím příkladu, řádky kde `ShipDate` má hodnotu null budou vyloučeny ze sady výsledků a [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] příkaz by vrátit 0 řádků.  
  
```  
-- Find order details and orders with no ship date.  
SELECT h.SalesOrderID  
FROM Sales.SalesOrderHeader h  
JOIN Sales.SalesOrderDetail o ON o.SalesOrderID = h.SalesOrderID  
WHERE h.ShipDate IS Null  
```  
  
 Toto je příliš neliší od CLR null sémantikou, kde porovnání null. rovná null, vrátí hodnotu true.  
  
 Následující dotaz LINQ vyjádřeného v modulu CLR, ale je provést v datovém zdroji. Vzhledem k tomu, že neexistuje žádná záruka, že bude CLR sémantiku uplatněn ve zdroji dat, je očekávané chování neurčitou.  
  
 [!code-csharp[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#joinonnull)]
 [!code-vb[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#joinonnull)]  
  
## <a name="key-selectors"></a>Selektorů klíče  
 A *selektoru klíče* je funkce použité v standardní operátory dotazu extrahovat klíč z elementu. Ve funkci selektoru klíče je možné porovnávat s konstantní výraz. Null sémantiku CLR jsou vystavených, pokud výraz se porovnává se konstanta null, nebo pokud jsou porovnávány dvě konstanty hodnotu null. Null sémantiky Store jsou vystavených, pokud dva sloupce s hodnotami null ve zdroji dat jsou porovnávány. Selektorů klíče se nacházejí v mnoha seskupení a řazení standardní operátory dotazu, jako například <xref:System.Linq.Queryable.GroupBy%2A>a slouží k výběru klíče podle kterého k seřazení nebo seskupení výsledků dotazu.  
  
## <a name="null-property-on-a-null-object"></a>Vlastnosti NULL u objektu hodnotu Null.  
 V [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)], vlastnosti na hodnotu null. objekt má hodnotu null. Když zkusíte odkazovat na vlastnost objektu null v modulu CLR, zobrazí se <xref:System.NullReferenceException>. Pokud dotaz LINQ zahrnuje vlastnost objektu null, to může způsobit nekonzistentní chování.  
  
 Například v následujícím dotazu, přetypování na `NewProduct` se provádí v vrstvě stromu příkaz, který může mít za následek `Introduced` vlastnost je null. Pokud databázi definované null porovnání tak, aby <xref:System.DateTime> porovnání se vyhodnotí jako true, budou zahrnuty řádek.  
  
 [!code-csharp[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#castresultsisnull)]
 [!code-vb[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#castresultsisnull)]  
  
## <a name="passing-null-collections-to-aggregate-functions"></a>Předání hodnotou Null kolekcí pro agregační funkce  
 V [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], při předání kolekce, která podporuje `IQueryable` agregační funkce, agregační operací v databázi. Může docházet k rozdílům ve výsledcích dotazu, který se provádí v paměti a dotaz, který byl proveden v databázi. Pomocí dotazu v paměti Pokud nejsou nalezeny žádné shody, dotaz vrátí hodnotu 0. V databázi, stejný dotaz vrací `null`. Pokud `null` LINQ agregační funkci je předána hodnota, bude vyvolána výjimka. Tak, aby přijímal možné `null` přetypovat hodnoty, typy a vlastnosti typy, které zobrazí výsledky dotazu a typy podporující hodnoty Null.  
  
## <a name="see-also"></a>Viz také  
 [Výrazy v technologii LINQ to Entities dotazy](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
