---
title: Porovnávání s hodnotou Null
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ef88af8c-8dfe-4556-8b56-81df960a900b
ms.openlocfilehash: 697c933daeb3c68fb4ea89a957b639a79a9407f8
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249653"
---
# <a name="null-comparisons"></a>Porovnávání s hodnotou Null
Hodnota `null` ve zdroji dat označuje, že hodnota není známa. V linq na entity dotazy, můžete zkontrolovat hodnoty null tak, aby některé výpočty nebo porovnání jsou prováděny pouze na řádky, které mají platná nebo non-null, data. Clr null sémantiku, ale může lišit od null sémantiku zdroje dat. Většina databází používá verzi logiky se třemi hodnotami ke zpracování porovnání null. To znamená porovnání s hodnotou null `true` není `false`vyhodnocena `unknown`nebo , je vyhodnocena . Často se jedná o implementaci ANSI nulls, ale to není vždy případ.  
  
 Ve výchozím nastavení v SQL Server, null rovná se null porovnání vrátí hodnotu null. V následujícím příkladu řádky, kde `ShipDate` je null jsou vyloučeny ze sady výsledků a Příkaz Transact-SQL vrátí 0 řádků.  
  
```sql  
-- Find order details and orders with no ship date.  
SELECT h.SalesOrderID  
FROM Sales.SalesOrderHeader h  
JOIN Sales.SalesOrderDetail o ON o.SalesOrderID = h.SalesOrderID  
WHERE h.ShipDate IS Null  
```  
  
 To je velmi odlišné od CLR null sémantiku, kde null rovná se null porovnání vrátí true.  
  
 Následující dotaz LINQ je vyjádřen v CLR, ale je spuštěn ve zdroji dat. Vzhledem k tomu, že neexistuje žádná záruka, že clr sémantiku bude dodržena ve zdroji dat, očekávané chování je neurčitý.  
  
 [!code-csharp[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#joinonnull)]
 [!code-vb[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#joinonnull)]  
  
## <a name="key-selectors"></a>Voliči klíčů  
 *Volič klíčů* je funkce používaná ve standardních operátorech dotazů k extrahování klíče z prvku. Ve funkci voliče kláves lze výraz porovnat s konstantou. Clr null sémantiku jsou vystaveny, pokud je výraz porovnán s konstantou null nebo pokud jsou porovnány dvě konstanty null. Úložiště null sémantiku jsou vystaveny, pokud jsou porovnány dva sloupce s hodnotami null ve zdroji dat. Selektory klíčů se nacházejí v mnoha operátorech seskupování a objednávání standardních dotazů, například <xref:System.Linq.Queryable.GroupBy%2A>v aplikaci , a slouží k výběru klíčů, podle kterých mají být výsledky dotazu seřazovány nebo seskupovány.  
  
## <a name="null-property-on-a-null-object"></a>Vlastnost Null u nulového objektu  
 V entity Framework vlastnosti null objektu jsou null. Při pokusu o odkaz na vlastnost null objektu v <xref:System.NullReferenceException>CLR, obdržíte . Pokud dotaz LINQ zahrnuje vlastnost nulového objektu, může to mít za následek nekonzistentní chování.  
  
 Například v následujícím dotazu se `NewProduct` přetypování na provádí ve vrstvě `Introduced` stromu příkazů, což může mít za následek, že vlastnost bude null. Pokud databáze definovala porovnání null <xref:System.DateTime> tak, aby porovnání vyhodnoceno jako true, řádek bude zahrnut.  
  
 [!code-csharp[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#castresultsisnull)]
 [!code-vb[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#castresultsisnull)]  
  
## <a name="passing-null-collections-to-aggregate-functions"></a>Předávání nulových kolekcí agregačním funkcím  
 V LINQ entity, když předáte `IQueryable` kolekci, která podporuje agregační funkce, agregační operace jsou prováděny v databázi. Mohou existovat rozdíly ve výsledcích dotazu, který byl proveden v paměti a dotaz, který byl proveden v databázi. S dotazem v paměti, pokud neexistují žádné shody, dotaz vrátí nulu. V databázi vrátí stejný `null`dotaz . Pokud `null` je hodnota předána agregační funkci LINQ, bude vyvolána výjimka. Chcete-li `null` přijmout možné hodnoty, přetypování typy a vlastnosti typů, které přijímají výsledky dotazu na hodnoty s možnou hodnotou null.  
  
## <a name="see-also"></a>Viz také

- [Výrazy v dotazech LINQ to Entities](expressions-in-linq-to-entities-queries.md)
