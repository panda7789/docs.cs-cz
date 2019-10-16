---
title: Porovnávání s hodnotou Null
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ef88af8c-8dfe-4556-8b56-81df960a900b
ms.openlocfilehash: 8eca2ee1afec5662e40d4f43347c469bd538c066
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319500"
---
# <a name="null-comparisons"></a>Porovnávání s hodnotou Null
Hodnota `null` ve zdroji dat označuje, že hodnota je neznámá. V LINQ to Entities dotazy můžete vyhledat hodnoty null, aby se určité výpočty nebo porovnání prováděly pouze v řádcích, které mají platné nebo nenulové, data. Sémantika CLR null se však může lišit od hodnoty null sémantiky zdroje dat. Většina databází používá ke zpracování porovnávání s hodnotou null verzi se třemi hodnotami logiky. To znamená, že porovnání s hodnotou null není vyhodnoceno jako `true` nebo `false`, je vyhodnoceno jako `unknown`. Často se jedná o implementaci hodnot null standardu ANSI, ale to není vždy u tohoto případu.  
  
 Ve výchozím nastavení v SQL Server porovnání null-EQUAL-null vrátí hodnotu null. V následujícím příkladu jsou z výsledné sady vyloučené řádky, kde `ShipDate` je null, a příkaz Transact-SQL vrátí 0 řádků.  
  
```sql  
-- Find order details and orders with no ship date.  
SELECT h.SalesOrderID  
FROM Sales.SalesOrderHeader h  
JOIN Sales.SalesOrderDetail o ON o.SalesOrderID = h.SalesOrderID  
WHERE h.ShipDate IS Null  
```  
  
 To se velmi liší od sémantiky null CLR, kde porovnání null-EQUAL-null vrátí hodnotu true.  
  
 Následující dotaz LINQ je vyjádřen v modulu CLR, ale je spuštěn ve zdroji dat. Vzhledem k tomu, že není zaručeno, že se sémantika CLR bude respektovat ve zdroji dat, je očekávané chování neurčité.  
  
 [!code-csharp[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#joinonnull)]
 [!code-vb[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#joinonnull)]  
  
## <a name="key-selectors"></a>Selektory klíčů  
 *Selektor klíčů* je funkce použitá ve standardních operátorech dotazu k extrakci klíče z prvku. Ve funkci selektoru klíče lze výraz porovnat s konstantou. Sémantika s hodnotou null CLR se zobrazí, pokud je výraz porovnán s konstantou NULL nebo pokud jsou porovnány dvě konstanty s hodnotou null. Pokud jsou porovnávány dva sloupce s hodnotami null ve zdroji dat, jsou v úložišti sémantiky hodnoty null. Selektory klíčů se nacházejí v mnoha standardních operátorech dotazu seskupení a řazení, například <xref:System.Linq.Queryable.GroupBy%2A>, a používají se k výběru klíčů, podle kterých se mají seřadit nebo seskupit výsledky dotazu.  
  
## <a name="null-property-on-a-null-object"></a>Vlastnost null objektu s hodnotou null  
 V Entity Framework vlastnosti objektu null mají hodnotu null. Při pokusu o odkaz na vlastnost objektu s hodnotou null v modulu CLR se zobrazí <xref:System.NullReferenceException>. Když dotaz LINQ zahrnuje vlastnost objektu s hodnotou null, může to mít za následek nekonzistentní chování.  
  
 Například v následujícím dotazu je přetypování na `NewProduct` provedeno ve vrstvě stromu příkazů, což může způsobit, že vlastnost `Introduced` bude mít hodnotu null. Pokud databáze definovala porovnání s hodnotou null, například porovnání <xref:System.DateTime> je vyhodnoceno jako true, bude řádek zahrnut.  
  
 [!code-csharp[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#castresultsisnull)]
 [!code-vb[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#castresultsisnull)]  
  
## <a name="passing-null-collections-to-aggregate-functions"></a>Předání kolekcí s hodnotou null do agregačních funkcí  
 Pokud v LINQ to Entities předáte kolekci, která podporuje `IQueryable` agregační funkce, jsou v databázi provedeny agregační operace. V důsledku výsledků dotazu, který byl proveden v paměti a dotazu, který byl proveden v databázi, může dojít ke rozdílům. Pokud se dotaz v paměti neshoduje, dotaz vrátí hodnotu nula. V databázi vrátí stejný dotaz `null`. Pokud je hodnota `null` předána agregační funkci LINQ, bude vyvolána výjimka. Chcete-li přijmout možné hodnoty `null`, přetypujte typy a vlastnosti typů, které přijímají výsledky dotazu na typy s možnou hodnotou null.  
  
## <a name="see-also"></a>Viz také:

- [Výrazy v dotazech LINQ to Entities](expressions-in-linq-to-entities-queries.md)
