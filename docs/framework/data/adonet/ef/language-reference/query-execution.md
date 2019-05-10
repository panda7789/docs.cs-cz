---
title: Provádění dotazů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0e6cf23-63ac-47dd-bfe9-d5bdca826fac
ms.openlocfilehash: ee63b6df4f99415e5d36f0717ff325d9fbabd9e3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64641612"
---
# <a name="query-execution"></a>Provádění dotazů
Po vytvoření dotazu LINQ uživatelem je převést na strom příkazů. Stromu příkazů je reprezentace dotaz, který je kompatibilní s rozhraním Entity Framework. Zdroji dat je pak provést strom příkazů. V době spuštění dotazu jsou vyhodnoceny všechny výrazy dotazů (to znamená všechny součásti dotazu), včetně těchto výrazů, které se používají v materializace výsledek.  
  
 Na jaké výrazy dotazu bodu provádějí se může lišit. Dotazy LINQ jsou vždy spouštěny, když proměnné dotazu není procházen, ne v případě, že proměnná dotazu je vytvořen. Tento postup se nazývá *odložené provedení*. Můžete také vynutit dotaz spustit okamžitě, což je užitečné pro ukládání výsledků dotazu. To je popsána dále v tomto tématu.  
  
 Pokud je spuštěn dotazu LINQ to Entities, některé výrazy v dotazu může být spuštěn na serveru a některé části může být spuštěn lokálně na straně klienta. Vyhodnocení výrazu na straně klienta se provádí před provedením dotazu na serveru. Pokud výraz je vyhodnocen na straně klienta, je nahrazen výsledek vyhodnocení výrazu v dotazu a poté spuštění dotazu na serveru. Protože dotazy se spouštějí na zdroj dat, konfigurace zdroje dat potlačí chování určené v klientovi. Například zpracování hodnotu null a číselná přesnost závisí na nastavení serveru. Výjimky vyvolané při provádění dotazu na serveru jsou předány přímo do klienta.  
 
> [!TIP]
> Praktické souhrn operátorů dotazu ve formátu tabulky, které vám umožní rychle identifikovat operátoru chování při spuštění, naleznete v tématu [klasifikace z standardních operátorů dotazu podle způsobu spuštění (C#)](../../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md).

## <a name="deferred-query-execution"></a>Odložený dotaz  
 V dotazu, který vrací posloupnost hodnot že proměnné dotazu samy nikdy neobsahují výsledky dotazu a ukládá pouze příkazy dotazu. Provádění dotazu je odloženo, dokud proměnná dotazu je procházena `foreach` nebo `For Each` smyčky. To se označuje jako *odložené provedení*; to znamená, dotaz spuštěn nějakou dobu, po dotazu je vytvořený. To znamená, že můžete spustit dotaz tak často, jak chcete. To je užitečné, pokud například máte databázi, která se aktualizuje jiné aplikace. Ve vaší aplikaci můžete vytvořit dotaz pro načtení nejnovějších informací a opakovaně spustit dotaz, vrácení aktualizované informace pokaždé, když.  
  
 Odložené provedení umožňuje více dotazů a nelze jej zkombinovat nebo dotaz, který rozšířit. Jakmile se rozšíří dotazu, dojde k úpravě zahrnout nové operace a konečný výsledek spuštění bude odrážet provedené změny. V následujícím příkladu první dotaz vrátí všechny produkty. Druhý dotaz rozšíří první pomocí `Where` vrátit všechny produkty o velikosti "L":  
  
 [!code-csharp[DP L2E Conceptual Examples#Composing1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#composing1)]
 [!code-vb[DP L2E Conceptual Examples#Composing1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#composing1)]  
  
 Po provedení dotazu bude použít všechny po sobě jdoucí dotazy operátory LINQ v paměti. Pomocí provádí iterace proměnné dotazu `foreach` nebo `For Each` příkaz nebo jeden z převodu LINQ voláním operátory způsobí okamžité spuštění. Tyto operátory převodu patří následující: <xref:System.Linq.Enumerable.ToList%2A>, <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToLookup%2A>, a <xref:System.Linq.Enumerable.ToDictionary%2A>.  
  
## <a name="immediate-query-execution"></a>Provedení okamžitého dotazu  
 Na rozdíl od odložené provedení dotazů, které vytvářejí posloupnost hodnot jsou dotazy, které vracejí hodnotu singleton spuštěna ihned. Tady je několik příkladů dotazů singleton <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.First%2A>, a <xref:System.Linq.Enumerable.Max%2A>. Provádějí se okamžitě vzhledem k tomu, že dotaz pro dotazovaní musí předložit pořadí pro výpočet jednoznačný výsledek. Můžete také vynuceno okamžité spuštění. To je užitečné, pokud chcete výsledky dotazu do mezipaměti. Chcete-li vynutit okamžité spuštění dotazu, který nevytváří hodnotu singleton, můžete volat <xref:System.Linq.Enumerable.ToList%2A> metody <xref:System.Linq.Enumerable.ToDictionary%2A> metodu, nebo <xref:System.Linq.Enumerable.ToArray%2A> metodu dotazu nebo proměnné dotazu. V následujícím příkladu <xref:System.Linq.Enumerable.ToArray%2A> metodu pro vyhodnocení okamžitě sekvence na pole.  
  
 [!code-csharp[DP L2E Examples#ToArray](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#toarray)]
 [!code-vb[DP L2E Examples#ToArray](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#toarray)]  
  
 Můžete také vynutit spuštění vložením `foreach` nebo `For Each` smyčky ihned za výraz dotazu, ale při volání <xref:System.Linq.Enumerable.ToList%2A> nebo <xref:System.Linq.Enumerable.ToArray%2A> mezipaměti všech dat v jednoho objektu kolekce.  
  
## <a name="store-execution"></a>Spuštění Store  
 Obecně platí výrazy v technologii LINQ to Entities jsou vyhodnoceny na serveru a chování výraz by neměl být očekáván common language runtime (CLR) sémantiku, ale u zdroje dat. Například při spouštění výraz se na straně klienta, ale existují výjimky. To může vést k neočekávaným výsledkům, například když serveru a klienta jsou v různých časových pásmech.  
  
 Některé výrazy v dotazu může být provedeny na straně klienta. Obecně platí provádění většiny dotazů má na serveru. Kromě metod pro elementy dotazu mapovat na zdroj dat často nejsou výrazy dotazu, které lze spustit místně. Místní spuštění výrazu dotazu vrací hodnotu, která lze použít v provádění dotazu nebo výsledek konstrukce.  
  
 Některé operace jsou provedeny vždy na straně klienta, jako je například vazby hodnoty, dílčí výrazy, sub dotazy z uzávěry a materializace objektů do výsledků dotazu. Čistým důsledkem tohoto je, že tyto prvky (například hodnoty parametrů) nemůže být aktualizováno během provádění. Anonymní typy mohou být vytvořený vložením ve zdroji dat, ale by neměly být předpokládá, že provedete to tak. Vložené seskupení lze zkonstruovat ve zdroji dat, stejně, ale to by neměl být předpokládá, že v každé instanci. Obecně je nejvhodnější nevyvozujte předpoklady o tom, co je vytvořen na serveru.  
  
 Tato část popisuje scénáře, ve kterých je místně spustit kód na straně klienta. Další informace o tom, které jsou typy výrazů spuštěn lokálně, naleznete v tématu [výrazy v dotazech LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md).  
  
### <a name="literals-and-parameters"></a>Literály a parametry  
 Lokální proměnné, jako `orderID` proměnné v následujícím příkladu jsou vyhodnoceny na straně klienta.  
  
 [!code-csharp[DP L2E Conceptual Examples#LiteralParameter1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#literalparameter1)]
 [!code-vb[DP L2E Conceptual Examples#LiteralParameter1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#literalparameter1)]  
  
 Parametry metody jsou také vyhodnotit na straně klienta. `orderID` Parametr předán `MethodParameterExample` metody, tady je příklad.  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodParameterExample](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodparameterexample)]
 [!code-vb[DP L2E Conceptual Examples#MethodParameterExample](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodparameterexample)]  
  
### <a name="casting-literals-on-the-client"></a>Literály přetypování na straně klienta  
 Přetypování z: `null` pro modul CLR. typ spuštění na straně klienta:  
  
 [!code-csharp[DP L2E Conceptual Examples#NullCastToString](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#nullcasttostring)]
 [!code-vb[DP L2E Conceptual Examples#NullCastToString](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#nullcasttostring)]  
  
 Přetypování na typ, jako je například s povolenou hodnotou Null <xref:System.Decimal>, je provést v klientovi:  
  
 [!code-csharp[DP L2E Conceptual Examples#CastToNullable](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#casttonullable)]
 [!code-vb[DP L2E Conceptual Examples#CastToNullable](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#casttonullable)]  
  
### <a name="constructors-for-literals"></a>Konstruktory pro literály.  
 Nové typy CLR, které je možné mapovat na typy konceptuálních modelů jsou spouštěny na straně klienta:  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstructorForLiteral](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constructorforliteral)]
 [!code-vb[DP L2E Conceptual Examples#ConstructorForLiteral](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constructorforliteral)]  
  
 Nové pole jsou také provést na straně klienta.  
  
## <a name="store-exceptions"></a>Store výjimky  
 Všechny chyby úložiště, které se vyskytují během provádění dotazu jsou předány do klienta a nejsou namapovány nebo zpracovat.  
  
## <a name="store-configuration"></a>Konfigurace Store  
 Při dotazu se provede na úložišti, konfigurace úložiště přepíše všechny chování klientů a pro všechny operace a výrazy jsou vyjádřeny úložiště sémantikou. Může způsobit rozdíl v chování mezi CLR a ukládat provádění v oblasti, například porovnávání s hodnotou null, GUID řazení, přesnost a správnost operace, které zahrnují-přesné datové typy (jako je například bod typy s plovoucí desetinnou čárkou nebo <xref:System.DateTime>) a řetězce operace. Je důležité to vzít v úvahu při prohlížení výsledků dotazu.  
  
 Následující příklad, jsou určité rozdíly v chování mezi CLR a systému SQL Server:  
  
- SQL Server odlišně od CLR objednávky identifikátory GUID.  
  
- Můžete také existovat rozdíly v přesnost výsledků při práci s typem Decimal na SQL serveru. Toto je z důvodu požadavků na pevnou přesnost typu desetinného čísla systému SQL Server. Například průměr <xref:System.Decimal> hodnoty 0.0, 0.0 a 1.0 je 0.3333333333333333333333333333 v paměti na straně klienta, ale 0.333333 v úložišti (podle výchozí přesnost typu decimal systému SQL Server).  
  
- Některé operace porovnání řetězců jsou zpracovány jinak také v systému SQL Server než v CLR. Chování porovnání řetězců závisí na nastavení řazení na serveru.  
  
- Volání funkce nebo metoda, když součástí dotazu LINQ to Entities, jsou mapovány na kanonické funkce v rozhraní Entity Framework, které jsou pak přeložit do jazyka Transact-SQL a spustit pro databázi systému SQL Server. Existují případy, kdy tyto funkce pro mapovanou vykazuje chování se mohou lišit od implementace v knihovně základních tříd. Například volání <xref:System.String.Contains%2A>, <xref:System.String.StartsWith%2A>, a <xref:System.String.EndsWith%2A> vrátí prázdný řetězec jako parametr metody `true` při spuštění v modulu CLR, ale vrátí `false` při spuštění v systému SQL Server. <xref:System.String.EndsWith%2A> Metoda může také vrátit různé výsledky, protože systém SQL Server považuje dva řetězce být rovny, pokud se liší pouze v prázdný znak, že je se nesmí rovnat považuje za CLR. To je znázorněno v následujícím příkladu:  
  
 [!code-csharp[DP L2E Conceptual Examples#CanonicalFuncVsCLRBaseType](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#canonicalfuncvsclrbasetype)]
 [!code-vb[DP L2E Conceptual Examples#CanonicalFuncVsCLRBaseType](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#canonicalfuncvsclrbasetype)]
