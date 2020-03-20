---
title: Provádění dotazů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0e6cf23-63ac-47dd-bfe9-d5bdca826fac
ms.openlocfilehash: e372744eea3eed7fc3f7ee9c8bbdd711c95b586e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149970"
---
# <a name="query-execution"></a>Provádění dotazů
Po vytvoření dotazu LINQ uživatelem je převeden na strom příkazů. Strom příkazů je reprezentace dotazu, který je kompatibilní s entity framework. Strom příkazů je pak proveden proti zdroji dat. V době spuštění dotazu jsou vyhodnoceny všechny výrazy dotazu (tj. všechny součásti dotazu), včetně výrazů, které se používají při materializaci výsledku.  
  
 V jakém okamžiku jsou výrazy dotazu spuštěny se mohou lišit. Linq dotazy jsou vždy spuštěny, když je proměnná dotazu iterována, nikoli při vytvoření proměnné dotazu. To se nazývá *odložené spuštění*. Můžete také vynutit okamžité spuštění dotazu, což je užitečné pro ukládání výsledků dotazu do mezipaměti. To je popsáno dále v tomto tématu.  
  
 Při spuštění dotazu LINQ entity, některé výrazy v dotazu může být spuštěn a některé části mohou být provedeny místně na straně klienta. Vyhodnocení výrazu na straně klienta probíhá před spuštěním dotazu na serveru. Pokud je výraz vyhodnocen na straně klienta, výsledek tohoto vyhodnocení je nahrazen výrazem v dotazu a dotaz je pak proveden na serveru. Vzhledem k tomu, že dotazy jsou spouštěny ve zdroji dat, konfigurace zdroje dat přepíše chování zadané v klientovi. Například zpracování nulové hodnoty a číselná přesnost závisí na nastavení serveru. Všechny výjimky vyvoláné během provádění dotazu na serveru jsou předány přímo klientovi.  

> [!TIP]
> Pro pohodlný souhrn operátorů dotazů ve formátu tabulky, který umožňuje rychle identifikovat chování spuštění operátoru, naleznete [v tématu Klasifikace operátorů standardních dotazů podle způsobu spuštění (C#)](../../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md).

## <a name="deferred-query-execution"></a>Odložené spuštění dotazu  
 V dotazu, který vrací posloupnost hodnot, samotná proměnná dotazu nikdy neobsahuje výsledky dotazu a ukládá pouze příkazy dotazu. Spuštění dotazu je odloženo, dokud je proměnná `foreach` dotazu iterována ve smyčce nebo. `For Each` To se označuje jako *odložené spuštění*; to znamená, že spuštění dotazu nastane nějaký čas po vytvoření dotazu. To znamená, že můžete spustit dotaz tak často, jak chcete. To je užitečné například v případě, že máte databázi, která je aktualizována jinými aplikacemi. V aplikaci můžete vytvořit dotaz pro načtení nejnovějších informací a opakovaně spustit dotaz, vrácení aktualizovaných informací pokaždé.  
  
 Odložené spuštění umožňuje více dotazů, které mají být kombinovány nebo dotaz, který má být rozšířen. Při rozšíření dotazu je upraven tak, aby zahrnovala nové operace a případné spuštění bude odrážet změny. V následujícím příkladu první dotaz vrátí všechny produkty. Druhý dotaz rozšiřuje první pomocí `Where` vrátit všechny produkty velikosti "L":  
  
 [!code-csharp[DP L2E Conceptual Examples#Composing1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#composing1)]
 [!code-vb[DP L2E Conceptual Examples#Composing1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#composing1)]  
  
 Po spuštění dotazu budou všechny následné dotazy používat operátory LINQ v paměti. Iterace přes proměnnou dotazu pomocí `foreach` nebo `For Each` příkaz nebo voláním jednoho z operátorů převodu LINQ způsobí okamžité spuštění. Tyto operátory převodu <xref:System.Linq.Enumerable.ToList%2A> <xref:System.Linq.Enumerable.ToArray%2A>zahrnují <xref:System.Linq.Enumerable.ToLookup%2A>následující: , , a <xref:System.Linq.Enumerable.ToDictionary%2A>.  
  
## <a name="immediate-query-execution"></a>Okamžité spuštění dotazu  
 Na rozdíl od odložené provádění dotazů, které vytvářejí posloupnost hodnot, dotazy, které vracejí hodnotu singleton jsou provedeny okamžitě. Některé příklady singleton dotazů <xref:System.Linq.Enumerable.Count%2A> <xref:System.Linq.Enumerable.First%2A>jsou <xref:System.Linq.Enumerable.Average%2A> <xref:System.Linq.Enumerable.Max%2A>, , a . Tyto spustit okamžitě, protože dotaz musí vytvořit posloupnost pro výpočet výsledku singleton. Můžete také vynutit okamžitou popravu. To je užitečné, pokud chcete uložit výsledky dotazu do mezipaměti. Chcete-li vynutit okamžité spuštění dotazu, který nevytváří <xref:System.Linq.Enumerable.ToList%2A> hodnotu <xref:System.Linq.Enumerable.ToDictionary%2A> singleton, <xref:System.Linq.Enumerable.ToArray%2A> můžete volat metodu, metodu nebo metodu v proměnné dotazu nebo dotazu. Následující příklad používá <xref:System.Linq.Enumerable.ToArray%2A> metodu okamžitě vyhodnotit sekvenci do pole.  
  
 [!code-csharp[DP L2E Examples#ToArray](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#toarray)]
 [!code-vb[DP L2E Examples#ToArray](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#toarray)]  
  
 Můžete také vynutit `foreach` spuštění `For Each` vložením nebo smyčky bezprostředně <xref:System.Linq.Enumerable.ToList%2A> za <xref:System.Linq.Enumerable.ToArray%2A> výraz dotazu, ale voláním nebo mezipaměti všechna data v jednom objektu kolekce.  
  
## <a name="store-execution"></a>Spuštění úložiště  
 Obecně platí, že výrazy v LINQ entity jsou vyhodnocovány na serveru a chování výrazu by nemělo být očekáváno, že bude následovat sémantiku cltime společného jazyka (CLR), ale sémantiku zdroje dat. Existují však výjimky, například při spuštění výrazu na straně klienta. To může způsobit neočekávané výsledky, například pokud jsou server a klient v různých časových pásmech.  
  
 Některé výrazy v dotazu mohou být spuštěny na straně klienta. Obecně se očekává, že většina spuštění dotazu dojde na serveru. Kromě metod prováděných proti prvkům dotazu mapovaným na zdroj dat jsou často výrazy v dotazu, které lze spustit místně. Místní spuštění výrazu dotazu poskytuje hodnotu, která může být použita při provádění dotazu nebo konstrukci výsledků.  
  
 Některé operace jsou vždy prováděny na straně klienta, jako je například vazba hodnot, dílčí výrazy, dílčí dotazy z uzavření a materializace objektů do výsledků dotazu. Čistým důsledkem je, že tyto prvky (například hodnoty parametrů) nelze aktualizovat během provádění. Anonymní typy mohou být vytvořeny vložku na zdroj dat, ale nemělo by se předpokládat, že tak učiníte. Vložková seskupení mohou být vytvořena také ve zdroji dat, ale to by nemělo být předpokládáno v každém případě. Obecně je nejlepší neprovádět žádné předpoklady o tom, co je konstruováno na serveru.  
  
 Tato část popisuje scénáře, ve kterých je kód spuštěn místně na straně klienta. Další informace o typech výrazů jsou spouštěny místně, naleznete [v tématu Výrazy v LINQ k entitám dotazy](expressions-in-linq-to-entities-queries.md).  
  
### <a name="literals-and-parameters"></a>Literály a parametry  
 Místní proměnné, jako `orderID` je například proměnná v následujícím příkladu, jsou vyhodnocovány na straně klienta.  
  
 [!code-csharp[DP L2E Conceptual Examples#LiteralParameter1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#literalparameter1)]
 [!code-vb[DP L2E Conceptual Examples#LiteralParameter1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#literalparameter1)]  
  
 Parametry metody jsou také vyhodnocovány na straně klienta. Parametr `orderID` předaný `MethodParameterExample` do metody, níže, je příkladem.  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodParameterExample](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodparameterexample)]
 [!code-vb[DP L2E Conceptual Examples#MethodParameterExample](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodparameterexample)]  
  
### <a name="casting-literals-on-the-client"></a>Odlévání literály na klienta  
 Přetypování z `null` typu CLR je spuštěno na straně klienta:  
  
 [!code-csharp[DP L2E Conceptual Examples#NullCastToString](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#nullcasttostring)]
 [!code-vb[DP L2E Conceptual Examples#NullCastToString](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#nullcasttostring)]  
  
 Přetypování na typ, například hodnotu null, <xref:System.Decimal>je na straně klienta spuštěno:  
  
 [!code-csharp[DP L2E Conceptual Examples#CastToNullable](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#casttonullable)]
 [!code-vb[DP L2E Conceptual Examples#CastToNullable](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#casttonullable)]  
  
### <a name="constructors-for-literals"></a>Konstruktory pro literály  
 Nové typy CLR, které lze mapovat na konceptuální typy modelů, jsou spouštěny na straně klienta:  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstructorForLiteral](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constructorforliteral)]
 [!code-vb[DP L2E Conceptual Examples#ConstructorForLiteral](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constructorforliteral)]  
  
 Nová pole jsou také spuštěny na straně klienta.  
  
## <a name="store-exceptions"></a>Výjimky úložiště  
 Všechny chyby úložiště, ke kterým došlo při spuštění dotazu, jsou předány klientovi a nejsou mapovány nebo zpracovávány.  
  
## <a name="store-configuration"></a>Konfigurace úložiště  
 Při spuštění dotazu v úložišti konfigurace úložiště přepíše všechna chování klienta a sémantiku úložiště jsou vyjádřeny pro všechny operace a výrazy. To může mít za následek rozdíl v chování mezi CLR a provádění úložiště v oblastech, jako je například null porovnání, GUID <xref:System.DateTime>řazení, přesnost a přesnost operací zahrnující chod nepřesné datové typy (například typy s plovoucí desetinnou čárkou nebo ) a operace řetězce. Je důležité mít na paměti při zkoumání výsledků dotazu.  
  
 Například jsou následující rozdíly v chování mezi CLR a SQL Server:  
  
- SQL Server objednávky GUID jinak než CLR.  
  
- Mohou také existovat rozdíly v přesnosti výsledků při práci s desetinným typem na serveru SQL Server. To je způsobeno požadavky na pevnou přesnost typu desetinné číslo serveru SQL Server. Například průměr <xref:System.Decimal> hodnot 0.0, 0.0 a 1.0 je 0.333333333333333333333333333333333333333333333v paměti na straně klienta, ale 0,3333333 v úložišti (na základě výchozí přesnosti pro desítkový typ serveru SQL Server).  
  
- Některé operace porovnání řetězců jsou také zpracovány odlišně v SQL Server než v CLR. Chování porovnání řetězců závisí na nastavení řazení na serveru.  
  
- Volání funkce nebo metody, pokud jsou zahrnuty v linq entity dotazu, jsou mapovány na kanonické funkce v entity framework, které jsou pak přeloženy do Transact-SQL a provedeny v databázi SQL Server. Existují případy, kdy chování těchto mapovaných funkcí exponát se může lišit od implementace v knihovnách základní třídy. Například volání <xref:System.String.Contains%2A>, <xref:System.String.StartsWith%2A>a <xref:System.String.EndsWith%2A> metody s prázdným řetězcem `true` jako parametr se vrátí při `false` spuštění v CLR, ale vrátí při spuštění v SQL Server. Metoda <xref:System.String.EndsWith%2A> může také vrátit různé výsledky, protože SQL Server považuje dva řetězce za rovné, pokud se liší pouze v koncové prázdné místo, zatímco CLR považuje za není stejné. To ilustruje následující příklad:  
  
 [!code-csharp[DP L2E Conceptual Examples#CanonicalFuncVsCLRBaseType](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#canonicalfuncvsclrbasetype)]
 [!code-vb[DP L2E Conceptual Examples#CanonicalFuncVsCLRBaseType](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#canonicalfuncvsclrbasetype)]
