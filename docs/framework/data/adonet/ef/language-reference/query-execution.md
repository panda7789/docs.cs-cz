---
title: Provádění dotazů
description: Přečtěte si o různých způsobech, kterými se spouští dotaz LINQ to Entities, včetně odloženého provedení dotazu, okamžitého provedení dotazu a spuštění úložiště.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0e6cf23-63ac-47dd-bfe9-d5bdca826fac
ms.openlocfilehash: e776df6d35b6cc8c24cd83e902bc4d050347343b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286789"
---
# <a name="query-execution"></a>Provádění dotazů
Poté, co uživatel vytvoří dotaz LINQ, je převedena na strom příkazů. Strom příkazů je reprezentace dotazu, který je kompatibilní s Entity Framework. Strom příkazů se pak provede proti zdroji dat. Při spuštění dotazu jsou vyhodnoceny všechny výrazy dotazu (tj. všechny komponenty dotazu), včetně výrazů, které jsou použity v materializaci výsledků.  
  
 Výrazy dotazů na to, kde jsou spouštěny, se mohou lišit. Dotazy LINQ jsou vždy spouštěny, když je provedena iterace proměnné dotazu, nikoli při vytvoření proměnné dotazu. Tato operace se nazývá *odložené provedení*. Můžete také vynutit, aby se dotaz spustil okamžitě, což je užitečné pro ukládání výsledků dotazu do mezipaměti. Tento postup je popsán dále v tomto tématu.  
  
 Když se spustí dotaz LINQ to Entities, můžou se na serveru spustit některé výrazy a některé části můžou být spuštěné místně na klientovi. Vyhodnocení výrazu na straně klienta proběhne před provedením dotazu na serveru. Pokud je výraz vyhodnocen na straně klienta, je výsledek tohoto vyhodnocení nahrazen výrazem v dotazu a dotaz je následně proveden na serveru. Vzhledem k tomu, že dotazy jsou spouštěny ve zdroji dat, přepíše konfigurace zdroje dat chování zadané v klientovi. Například zpracování hodnot null a číselná přesnost závisí na nastavení serveru. Jakékoli výjimky vyvolané při provádění dotazu na serveru jsou předány přímo do klienta.  

> [!TIP]
> Pro pohodlné Shrnutí operátorů dotazů ve formátu tabulky, který vám umožní rychle identifikovat chování při spuštění operátoru, přečtěte si téma [klasifikace standardních operátorů dotazu podle způsobu spuštění (C#)](../../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md).

## <a name="deferred-query-execution"></a>Odložené provádění dotazu  
 V dotazu, který vrací sekvenci hodnot, samotná proměnná dotazu nikdy nedrží výsledky dotazu a ukládá pouze příkazy dotazu. Provedení dotazu je odloženo, dokud se proměnná dotazu neopakuje v rámci `foreach` `For Each` smyčky or. Tato operace se označuje jako *odložené provádění*; To znamená, že provádění dotazů probíhá určitou dobu po sestavení dotazu. To znamená, že můžete spustit dotaz tak často, jak chcete. To je užitečné, když například máte databázi, která je aktualizována jinými aplikacemi. V aplikaci můžete vytvořit dotaz, který načte nejnovější informace a opakovaně spustí dotaz, a to tak, že se aktualizované informace pokaždé vrátí.  
  
 Odložené spouštění umožňuje kombinovat více dotazů nebo dotaz, který se má rozšířit. Když je dotaz rozšířený, je upravený tak, aby zahrnoval nové operace, a konečné spuštění projeví změny. V následujícím příkladu první dotaz vrátí všechny produkty. Druhý dotaz rozšiřuje první pomocí `Where` a vrátí všechny produkty velikosti "L":  
  
 [!code-csharp[DP L2E Conceptual Examples#Composing1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#composing1)]
 [!code-vb[DP L2E Conceptual Examples#Composing1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#composing1)]  
  
 Po provedení dotazu budou všechny úspěšné dotazy používat operátory LINQ v paměti. Iterace nad proměnnou dotazu pomocí `foreach` `For Each` příkazu nebo nebo voláním jednoho z operátorů převodu LINQ způsobí okamžité provedení. Tyto operátory převodu zahrnují následující: <xref:System.Linq.Enumerable.ToList%2A> , <xref:System.Linq.Enumerable.ToArray%2A> , a <xref:System.Linq.Enumerable.ToLookup%2A> <xref:System.Linq.Enumerable.ToDictionary%2A> .  
  
## <a name="immediate-query-execution"></a>Okamžité provedení dotazu  
 Na rozdíl od odloženého spuštění dotazů, které tvoří sekvenci hodnot, se okamžitě spustí dotazy, které vracejí hodnotu typu singleton. Příklady dotazů typu Singleton jsou <xref:System.Linq.Enumerable.Average%2A> , <xref:System.Linq.Enumerable.Count%2A> , <xref:System.Linq.Enumerable.First%2A> a <xref:System.Linq.Enumerable.Max%2A> . Tyto kroky se okamžitě spustí, protože dotaz musí vytvořit sekvenci pro výpočet výsledku typu singleton. Můžete také vynutit okamžité provedení. To je užitečné, pokud chcete výsledky dotazu ukládat do mezipaměti. Chcete-li vynutit okamžité provedení dotazu, který nevytvoří hodnotu typu Singleton, můžete zavolat <xref:System.Linq.Enumerable.ToList%2A> metodu, <xref:System.Linq.Enumerable.ToDictionary%2A> metodu nebo <xref:System.Linq.Enumerable.ToArray%2A> metodu pro dotaz nebo proměnnou dotazu. Následující příklad používá <xref:System.Linq.Enumerable.ToArray%2A> metodu k okamžitému vyhodnocení sekvence do pole.  
  
 [!code-csharp[DP L2E Examples#ToArray](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#toarray)]
 [!code-vb[DP L2E Examples#ToArray](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#toarray)]  
  
 Můžete také vynutit provádění vložením `foreach` smyčky nebo `For Each` hned za výraz dotazu, ale voláním <xref:System.Linq.Enumerable.ToList%2A> nebo <xref:System.Linq.Enumerable.ToArray%2A> uložením dat do mezipaměti v jediném objektu kolekce.  
  
## <a name="store-execution"></a>Spuštění úložiště  
 Obecně platí, že výrazy ve LINQ to Entities jsou vyhodnocovány na serveru a chování výrazu by nemělo být očekáváno podle sémantiky modulu CLR (Common Language Runtime), ale u zdroje dat. Existují však výjimky, například když je výraz spuštěn na klientovi. To může vést k neočekávaným výsledkům, například když je server a klient v různých časových pásmech.  
  
 Některé výrazy v dotazu mohou být provedeny na klientovi. Obecně se očekává, že na serveru proběhne většina spuštění dotazu. Kromě metod, které jsou spouštěny proti elementům dotazu mapovaným na zdroj dat, jsou často výrazy v dotazu, které lze spustit místně. Místní spuštění výrazu dotazu vrací hodnotu, která se dá použít při provádění dotazu nebo vytváření výsledků.  
  
 Některé operace jsou vždy spouštěny na klientovi, jako je například vazba hodnot, dílčích výrazů, poddotazů z uzavření a materializace objektů do výsledků dotazu. Čistý efekt tohoto je, že tyto prvky (například hodnoty parametrů) nelze během provádění aktualizovat. Anonymní typy mohou být sestaveny na zdroj dat, ale neměly by se předpokládat. Vložená seskupení mohou být vytvořena také ve zdroji dat, ale tato hodnota by se neměla předpokládat v každé instanci. Obecně platí, že není vhodné dělat žádné předpoklady o tom, co je na serveru vytvořeno.  
  
 Tato část popisuje scénáře, ve kterých je kód spouštěn místně na klientovi. Další informace o tom, jaké typy výrazů jsou spouštěny místně, naleznete [v tématu Expressions in LINQ to Entities dotazy](expressions-in-linq-to-entities-queries.md).  
  
### <a name="literals-and-parameters"></a>Literály a parametry  
 Místní proměnné, jako je například `orderID` Proměnná v následujícím příkladu, jsou vyhodnocovány na klientovi.  
  
 [!code-csharp[DP L2E Conceptual Examples#LiteralParameter1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#literalparameter1)]
 [!code-vb[DP L2E Conceptual Examples#LiteralParameter1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#literalparameter1)]  
  
 Parametry metody jsou také vyhodnocovány na klientovi. `orderID`Parametr předaný `MethodParameterExample` metodě, níže je příklad.  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodParameterExample](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodparameterexample)]
 [!code-vb[DP L2E Conceptual Examples#MethodParameterExample](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodparameterexample)]  
  
### <a name="casting-literals-on-the-client"></a>Přetypování literálů na klientovi  
 Přetypování z `null` na typ CLR je prováděno na klientovi:  
  
 [!code-csharp[DP L2E Conceptual Examples#NullCastToString](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#nullcasttostring)]
 [!code-vb[DP L2E Conceptual Examples#NullCastToString](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#nullcasttostring)]  
  
 Přetypování na typ, například s možnou hodnotou null <xref:System.Decimal> , je provedeno na klientovi:  
  
 [!code-csharp[DP L2E Conceptual Examples#CastToNullable](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#casttonullable)]
 [!code-vb[DP L2E Conceptual Examples#CastToNullable](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#casttonullable)]  
  
### <a name="constructors-for-literals"></a>Konstruktory pro literály  
 Nové typy CLR, které lze namapovat na typy konceptuálních modelů, jsou spouštěny v klientovi:  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstructorForLiteral](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constructorforliteral)]
 [!code-vb[DP L2E Conceptual Examples#ConstructorForLiteral](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constructorforliteral)]  
  
 V klientovi se také spouštějí nová pole.  
  
## <a name="store-exceptions"></a>Ukládat výjimky  
 Všechny chyby úložiště, které se vyskytly při provádění dotazu, jsou předány klientovi a nejsou namapovány nebo zpracovávány.  
  
## <a name="store-configuration"></a>Konfigurace úložiště  
 Když se dotaz spustí na úložišti, přepíše konfigurace úložiště všechna chování klienta a sémantika úložiště se vyjádří pro všechny operace a výrazy. To může mít za následek rozdíl mezi chováním CLR a provádění úložiště v oblastech, jako jsou například porovnání hodnoty null, pořadí identifikátorů GUID, přesnost a přesnost operací zahrnující nepřesné datové typy (například typy plovoucí desetinné čárky nebo <xref:System.DateTime> ) a operace s řetězci. Je důležité mít na paměti, že při zkoumání výsledků dotazu.  
  
 Například následuje několik rozdílů v chování mezi CLR a SQL Server:  
  
- Identifikátory GUID se SQL Server řadí jinak než CLR.  
  
- Při práci s typem Decimal na SQL Server může také docházet k rozdílům v přesnosti výsledků. Důvodem jsou pevné požadavky na přesnost SQL Serverho typu Decimal. Například průměr <xref:System.Decimal> hodnot 0,0, 0,0 a 1,0 je 0.3333333333333333333333333333 v paměti na klientovi, ale 0,333333 ve Storu (na základě výchozí přesnosti pro typ decimal SQL Server).  
  
- Některé operace porovnání řetězců jsou také zpracovávány jinak než v SQL Server než v modulu CLR. Chování porovnávání řetězců závisí na nastavení kolace na serveru.  
  
- Volání funkce nebo metody, pokud je součástí LINQ to Entitiesho dotazu, jsou mapována na kanonické funkce v Entity Framework, které jsou poté přeloženy do jazyka Transact-SQL a provedeny v databázi SQL Server. Existují případy, kdy chování těchto namapovaných funkcí se může lišit od implementace v knihovně základních tříd. Například volání <xref:System.String.Contains%2A> <xref:System.String.StartsWith%2A> metody, a <xref:System.String.EndsWith%2A> s prázdným řetězcem jako parametr vrátí `true` při spuštění v modulu CLR, ale vrátí se `false` při spuštění v SQL Server. <xref:System.String.EndsWith%2A>Metoda může také vracet různé výsledky, protože SQL Server považuje dva řetězce za stejné, pokud se liší pouze na konci prázdného místa, zatímco CLR je považuje za nerovnost. To je znázorněno v následujícím příkladu:  
  
 [!code-csharp[DP L2E Conceptual Examples#CanonicalFuncVsCLRBaseType](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#canonicalfuncvsclrbasetype)]
 [!code-vb[DP L2E Conceptual Examples#CanonicalFuncVsCLRBaseType](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#canonicalfuncvsclrbasetype)]
