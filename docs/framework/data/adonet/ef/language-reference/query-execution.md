---
title: Provádění dotazů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0e6cf23-63ac-47dd-bfe9-d5bdca826fac
ms.openlocfilehash: 7be5ca95732b4ddadf851ccf839e31be3c5b47bf
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="query-execution"></a>Provádění dotazů
Po vytvoření dotaz LINQ uživatelem je převést na strom příkazů. Stromu příkazů je reprezentace dotaz, který je kompatibilní s platformou Entity Framework. U zdroje dat je pak spustit strom příkazů. Během provádění dotazu se vyhodnocují všechny výrazy dotazů (všechny součásti dotaz), včetně těchto výrazů, které se používají v materialization výsledek.  
  
 Na jaké výrazy dotazů bodu jsou spouštěny se může lišit. Dotazy LINQ jsou vždy spustit, když proměnné v dotazu je vstupní přes, ne v případě, že se vytvoří proměnné v dotazu. To se označuje jako *odložené spouštění*. Můžete taky přinutit, dotaz spustit okamžitě, který je užitečný pro ukládání do mezipaměti výsledky dotazu. To je popsán dále v tomto tématu.  
  
 Po provedení dotazu LINQ to Entities některé výrazy v dotazu může být na serveru provést, a některé části mohou být prováděny místně na klientovi. Klientské vyhodnocení výrazu proběhne před provedením dotazu na serveru. Pokud se na klientovi vyhodnotí výraz, je je nahrazena výsledkem vyhodnocení výrazu v dotazu a potom spustit dotaz na serveru. Vzhledem k tomu, že dotazy jsou spouštěny ve zdroji dat, konfigurace zdroje dat přepíše nastavení chování v klientovi. Například zpracování hodnotu null nebo přesnost číselné závisí na nastavení serveru. Jakékoli výjimky během provádění dotazu na serveru jsou předávány přímo až klienta.  
  
## <a name="deferred-query-execution"></a>Při provádění dotazu odložené  
 V dotazu, který vrací pořadí hodnot proměnné v dotazu samotné nikdy obsahuje výsledky dotazu a ukládá jenom příkazy dotazu. Spuštění dotazu je odložení, dokud proměnnou dotazu je vstupní přes `foreach` nebo `For Each` smyčky. To se označuje jako *odložené spouštění*; to znamená, dotaz provádění dojde k delší dobu, po dotazu je vytvořený. To znamená, že je spuštěn dotaz často chcete. To je užitečné, pokud například máte databázi, která se právě aktualizuje jiné aplikace. V aplikaci můžete vytvořit dotaz, který získat nejnovější informace a opakovaně spuštění dotazu a vrácení aktualizované informace o každém.  
  
 Odložené provedení umožňuje více dotazů a nelze jej zkombinovat nebo dotaz, který rozšířit. Jakmile se rozšíří dotazu, se mění zahrnout nových operací a případné provádění se projeví změny. V následujícím příkladu první dotaz vrátí všechny produkty. Druhý dotazu rozšiřuje první pomocí `Where` vrátit všechny produkty velikosti "L":  
  
 [!code-csharp[DP L2E Conceptual Examples#Composing1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#composing1)]
 [!code-vb[DP L2E Conceptual Examples#Composing1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#composing1)]  
  
 Po provedení dotazu použije všechny následné dotazy LINQ operátory v paměti. Iterování přes proměnnou dotazu pomocí `foreach` nebo `For Each` příkaz nebo jeden z převodu LINQ voláním operátory způsobí okamžité spuštění. Tyto operátory převodu patří: <xref:System.Linq.Enumerable.ToList%2A>, <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToLookup%2A>, a <xref:System.Linq.Enumerable.ToDictionary%2A>.  
  
## <a name="immediate-query-execution"></a>Při provádění okamžitou dotazu  
 Odložené provedení dotazů s pořadí hodnot, na rozdíl od dotazů, které vrátí hodnotu typu singleton spustit okamžitě. Některé příklady dotazů singleton <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.First%2A>, a <xref:System.Linq.Enumerable.Max%2A>. Tyto spustit okamžitě protože dotaz musí vytvořit pořadí vypočítat výsledek typu singleton. Můžete taky přinutit, okamžité spuštění. To je užitečné, pokud chcete pro ukládání do mezipaměti výsledků dotazu. Pokud chcete vynutit okamžitou provádění dotazu, který nevytváří hodnotu singleton, můžete zavolat <xref:System.Linq.Enumerable.ToList%2A> metody <xref:System.Linq.Enumerable.ToDictionary%2A> metoda, nebo <xref:System.Linq.Enumerable.ToArray%2A> metoda v dotazu nebo proměnné dotazu. Následující příklad používá <xref:System.Linq.Enumerable.ToArray%2A> metoda okamžitě vyhodnotit posloupnost do pole.  
  
 [!code-csharp[DP L2E Examples#ToArray](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#toarray)]
 [!code-vb[DP L2E Examples#ToArray](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#toarray)]  
  
 Můžete také může vynutit spuštění umístěním `foreach` nebo `For Each` smyčky ihned po výrazu dotazu, ale voláním <xref:System.Linq.Enumerable.ToList%2A> nebo <xref:System.Linq.Enumerable.ToArray%2A> mezipaměti všechna data v objektu jedinou kolekci.  
  
## <a name="store-execution"></a>Provádění úložiště  
 Obecně platí na serveru se vyhodnotí výrazy v technologii LINQ to Entities a chování výraz by neměl být očekávaných podle common language runtime (CLR) sémantiku, ale u zdroje dat. Například když výraz se spouští na klientovi, ale existují výjimky. To může vést k neočekávaným výsledkům, například při serveru a klienta jsou v různých časových pásmech.  
  
 Některé výrazy v dotazu mohou být prováděny v klientovi. Obecně platí většina provádění dotazu je očekávané na serveru. Kromě metod spustit pro elementy dotazu namapované na zdroj dat neexistují často výrazy v dotazu může být spuštěn místně. Místní spuštění výrazu dotazu vypočítá hodnotu, která mohou být používány při provádění dotazu nebo vytváření výsledek.  
  
 Vždy provedení určité operace na klientovi, jako je například vazba hodnot sub výrazy, sub dotazy z uzavření a materialization objektů do výsledků dotazu. Projeví tohoto objektu je, že tyto prvky (například hodnoty parametrů) nemůže být aktualizováno během provádění. Anonymní typy mohou být vytvořený vložené ve zdroji dat, ale nesmí být předpokládá, že uděláte to tak. Vložené seskupení konstruovat ve zdroji dat, je také možné, ale to by neměl být předpokládá, že v každé instanci. Obecně platí je nejlepší vytvořit žádný odhad o co je sestavený na serveru.  
  
 Tato část popisuje scénáře, ve kterých je kód spuštěn místně na klientovi. Další informace o tom, které jsou typy výrazů spustit místně najdete v tématu [výrazy v technologii LINQ to Entities dotazy](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md).  
  
### <a name="literals-and-parameters"></a>Literály a parametry  
 Lokální proměnné, jako `orderID` proměnné v následujícím příkladu se vyhodnocují na straně klienta.  
  
 [!code-csharp[DP L2E Conceptual Examples#LiteralParameter1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#literalparameter1)]
 [!code-vb[DP L2E Conceptual Examples#LiteralParameter1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#literalparameter1)]  
  
 Parametry metody se také vyhodnocují na straně klienta. `orderID` Parametr předaný do `MethodParameterExample` metody, dole je příklad.  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodParameterExample](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodparameterexample)]
 [!code-vb[DP L2E Conceptual Examples#MethodParameterExample](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodparameterexample)]  
  
### <a name="casting-literals-on-the-client"></a>Přetypování literály na straně klienta  
 Přetypování z `null` Chcete-li CLR je typ spustit v klientském počítači:  
  
 [!code-csharp[DP L2E Conceptual Examples#NullCastToString](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#nullcasttostring)]
 [!code-vb[DP L2E Conceptual Examples#NullCastToString](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#nullcasttostring)]  
  
 Přetypování na typ, například s možnou hodnotou Null <xref:System.Decimal>, se spustí v klientském počítači:  
  
 [!code-csharp[DP L2E Conceptual Examples#CastToNullable](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#casttonullable)]
 [!code-vb[DP L2E Conceptual Examples#CastToNullable](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#casttonullable)]  
  
### <a name="constructors-for-literals"></a>Konstruktory pro literály  
 Nové typy CLR, které lze mapovat na konceptuálního modelu typy jsou spouštěny na straně klienta:  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstructorForLiteral](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constructorforliteral)]
 [!code-vb[DP L2E Conceptual Examples#ConstructorForLiteral](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constructorforliteral)]  
  
 Nové pole jsou také provést u klienta.  
  
## <a name="store-exceptions"></a>Uložení výjimky  
 Všechny chyby úložiště, které jsou došlo během provádění dotazu se budou předávat klienta a nejsou namapované nebo zpracovat.  
  
## <a name="store-configuration"></a>Konfigurace úložiště  
 Když dotazu se provede v úložišti, konfigurace úložiště přepíše všechny chování klientů a pro všechny operace a výrazy jsou vyjádřeny sémantiky store. To může vést k rozdíl v chování mezi CLR a provádění ukládání v oblastech, jako je například null porovnávání, řazení identifikátor GUID, přesnost a správnost operací zahrnujících-přesné datové typy (například plovoucí typy bodů nebo <xref:System.DateTime>) a řetězce operace. Je důležité mějte na paměti při zkoumání výsledků dotazu.  
  
 Následující příklady určité rozdíly v chování mezi CLR a SQL Server:  
  
-   SQL Server řadí identifikátory GUID jinak než modulu CLR.  
  
-   Může mít taky rozdíly ve výsledku přesnost při plánování práce s typ Decimal na serveru SQL Server. To je kvůli požadavkům pevné přesnost typu desetinného čísla systému SQL Server. Například průměr <xref:System.Decimal> hodnoty 0,0, 0,0 a 1,0 je 0.3333333333333333333333333333 v paměti na straně klienta, ale 0.333333 v úložišti (podle výchozí přesnost pro typ decimal systému SQL Server).  
  
-   Některé operace porovnání řetězce jsou zpracovány jinak také v systému SQL Server než v modulu CLR. Chování porovnání řetězců závisí na nastavení kolace na serveru.  
  
-   Volání funkce nebo metoda, když je zahrnutý v dotazu LINQ to Entities, jsou namapované na kanonické funkce v Entity Framework, která jsou pak přeložit Transact-SQL a spustit na databázi systému SQL Server. Existují případy, kdy chování vykazovat tyto namapované funkce se může lišit od implementace v knihovnách základní třída. Například volání <xref:System.String.Contains%2A>, <xref:System.String.StartsWith%2A>, a <xref:System.String.EndsWith%2A> vrátí metody s prázdný řetězec jako parametr `true` při provedení modulu CLR, ale vrátí `false` při spuštění v systému SQL Server. <xref:System.String.EndsWith%2A> Metoda můžete také vrátit odlišné výsledky, protože systém SQL Server považuje dva řetězce být rovno, pokud se liší pouze v prázdné znaky, zatímco modulu CLR je považuje za není rovno. To je znázorněno v následujícím příkladu:  
  
 [!code-csharp[DP L2E Conceptual Examples#CanonicalFuncVsCLRBaseType](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#canonicalfuncvsclrbasetype)]
 [!code-vb[DP L2E Conceptual Examples#CanonicalFuncVsCLRBaseType](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#canonicalfuncvsclrbasetype)]
