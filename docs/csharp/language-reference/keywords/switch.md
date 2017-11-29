---
title: "Switch – klíčové slovo (referenční dokumentace jazyka C#)"
ms.date: 03/07/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- switch_CSharpKeyword
- switch
- case
- case_CSharpKeyword
helpviewer_keywords:
- switch statement [C#]
- switch keyword [C#]
- case statement [C#]
- default keyword [C#]
ms.assetid: 44bae8b8-8841-4d85-826b-8a94277daecb
caps.latest.revision: "47"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1c345d0c6c935271600a386752e18c19a25cc389
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="switch-c-reference"></a>switch – příkaz (referenční dokumentace jazyka C#)
`switch`je výběr příkaz, který vybere jeden *přepnout oddíl* provést ze seznamu kandidátů na základě vzor shody s *odpovídat výrazu*. 
  
 [!code-csharp[switch#1](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]  

`switch` Příkaz se často používá jako alternativu k [if-else](if-else.md) vytvořit, pokud jeden výraz je testován vůči tři nebo více podmínek. Například následující `switch` příkaz určuje, zda proměnná typu `Color` obsahuje jednu ze tří hodnot: 

[!code-csharp[switch#3](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)] 

Je ekvivalentní v následujícím příkladu, který používá `if` - `else` vytvořit. 

[!code-csharp[switch#3a](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)] 

## <a name="the-match-expression"></a>Výrazy

Výrazy poskytuje hodnoty k porovnání vzorů v `case` popisky. Jeho syntaxe je:

```csharp
   switch (expr)
```

Výrazy jazyka C# 6, musí být výraz, který vrací hodnotu z těchto typů:

- [char](char.md).
- [řetězec](string.md).
- [bool](bool.md). 
- integrální hodnoty, například [int](int.md) nebo [dlouho](long.md).
- [výčtu](enum.md) hodnotu.

Od verze jazyka C# 7, výrazu shody může být jakýkoli výraz nesmí být nulová.
 
## <a name="the-switch-section"></a>V části přepínače
 
 A `switch` příkaz obsahuje jeden nebo více oddíly přepínače. Každá část přepínač obsahuje jeden nebo více *případ popisky* následuje jeden nebo více příkazů. Následující příklad ukazuje jednoduchý `switch` příkaz, který má tři části přepínače. Každý oddíl přepínače má jednoho návěstí, jako například `case 1:`a dvou příkazů.
 
  A `switch` příkaz může obsahovat libovolný počet oddílů přepínače, a každé části může mít jeden nebo více štítků případu, jak je znázorněno v následujícím příkladu. Žádné dvě případu popisky však může obsahovat stejný výraz.  

 [!code-csharp[switch#2](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]  

 Přepínač pouze jeden oddíl v příkazu switch provede. C# neumožňuje spouštění z jednoho oddílu přepínač pokračovat na další. Z tohoto důvodu se následující kód vygeneruje chybu kompilátoru CS0163: "ovládacího prvku nelze přejít z jednoho návěstí (<case label>) na jiný."  

```csharp  
switch (caseSwitch)  
{  
    // The following switch section causes an error.  
    case 1:  
        Console.WriteLine("Case 1...");  
        // Add a break or other jump statement here.  
    case 2:  
        Console.WriteLine("... and/or Case 2");  
        break;  
}  
```  
Tento požadavek se splní obvykle explicitně ukončení části přepínač pomocí [zalomení](break.md), [goto](goto.md), nebo [vrátit](return.md) příkaz. Následující kód je však také platný, protože zajišťuje, že program řízení nelze přejít ke `default` přepnout oddíl.
  
 [!code-csharp[switch#4](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]    
  
 Spuštění příkazu seznamu v části přepínače s případu popiskem, který odpovídá výrazu shody začíná první příkaz a pokračuje prostřednictvím seznamu příkaz obvykle dokud výpis přechod, například `break`, `goto case`, `goto label`, `return`, nebo `throw`, je dostupný. V tomto okamžiku je ovládací prvek přenesen mimo `switch` příkaz nebo na jinou případu štítek. A `goto` příkaz, pokud se používá, musí přenos řízení na konstantní štítek. Toto omezení je nutné, protože probíhá pokus o přenos řízení na štítek nekonstantní může mít nežádoucí vedlejší účinky, takový přenos řízení na nezamýšleným umístění v kódu nebo vytváření nekonečné smyčce.

## <a name="case-labels"></a>Case popisky

 Každý popisek případu určuje vzor k porovnání shody výrazu ( `caseSwitch` proměnné v předchozích příkladech). Pokud se shodují, je ovládací prvek přenesen do části přepínač, který obsahuje **první** odpovídající případu popisek. Pokud žádné návěstí vzor odpovídá výrazu shody, je ovládací prvek přenesen do části s `default` případu štítku, pokud existuje. Pokud neexistuje žádné `default` případě žádné příkazy v žádné části přepínače jsou spouštěny a ovládací prvek je přenesen mimo `switch` příkaz.

 Informace o `switch` příkaz a porovnávání vzorů, najdete v článku [porovnávání vzorů s `switch` příkaz](#pattern) části.

 Protože C# 6 podporuje pouze konstantní vzor a nepovoluje opakování konstantní hodnoty, případu popisky definovat vzájemně se vylučuje hodnoty a pouze jeden vzor může odpovídat výrazu shody. V důsledku toho, v jakém pořadí `case` příkazy zobrazí, je důležitý.

 V jazyce C# 7 ale je podporována dalšími vzory případu popisky nemusíte definovat vzájemně se vylučuje hodnoty a více vzorů může odpovídat výrazu shody. Protože jsou vykonány pouze příkazy v části přepínač, který obsahuje první odpovídající vzor, v jakém pořadí `case` příkazy zobrazí, je důležité. Pokud C# zjistí části přepínač, jehož case – příkaz nebo příkazy odpovídají nebo jsou podmnožinou tohoto předchozí příkazy, vygeneruje Chyba kompilátoru, CS8120, "případy switch již byla zpracována předchozí případem." 

 Následující příklad ilustruje `switch` příkaz, který používá celou řadu jiných vzájemně se vylučuje vzory. Pokud přesunete `case 0:` přepnout oddíl tak, aby se už v první části v `switch` příkaz, C# generuje chybu kompilátoru, protože celé číslo, jehož hodnota je nulová je podmnožinou všechny celá čísla, což je vzoru definována podle `case int val` příkaz.

 [!code-csharp[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]    

Můžete opravit tento problém a eliminovat upozornění kompilátoru v jednom ze dvou způsobů:

- Změnou pořadí částí přepínače. 
 
- Pomocí < /a name = "při" > při klauzule</a> v `case` popisek.
 
## <a name="the-default-case"></a>`default` Případu

`default` Případ určuje oddílu přepínač, který má provést Pokud výrazu shody neodpovídá žádné jiné `case` popisek. Pokud `default` případu není k dispozici a výrazy neodpovídá žádné jiné `case` štítku, toku programu spadá `switch` příkaz.

`default` Případ se mohou objevit v libovolném pořadí, v `switch` příkaz. Bez ohledu na jeho pořadí ve zdrojovém kódu, vždy vyhodnotí poslední, po všech `case` byly vyhodnoceny popisky.

## <a name="a-namepattern--pattern-matching-with-the-switch-statement"></a><a name="pattern" />Shoda vzoru se `switch` – příkaz
  
Každý `case` příkaz definuje vzor, který odpovídá výrazu shody vede k jeho obsahující části přepínače má být proveden. Všechny verze jazyka C# podporovat vzoru konstantní. Zbývající vzory jsou podporované od verze jazyka C# 7. 
  
### <a name="constant-pattern"></a>Konstantní vzor 

Konstantní vzor ověřuje, zda výrazu shody rovná zadané konstanta. Jeho syntaxe je:

```csharp
   case constant:
```

kde *konstantní* je hodnota, kterou chcete otestovat. *konstantní* může být libovolná z následujících konstantní výrazy: 

- A [bool](bool.md) literálu, buď `true` nebo `false`.
- Všechny integrální konstanta, například [int](int.md), [dlouho](long.md), nebo [bajtů](byte.md). 
- Název deklarované `const` proměnné.
- Konstanta výčtu.
- A [char](char.md) literálu.
- A [řetězec](string.md) literálu.

Konstantní výraz je vyhodnotit takto:

- Pokud *expr* a *konstantní* jsou integrální typy operátor rovnosti jazyka C# určuje, zda výraz vrací `true` (to znamená, zda `expr == constant`).

- Jinak hodnota výrazu je určena voláním statických [Object.Equals (výraz, konstantní)](xref:System.Object.Equals(System.Object,System.Object)) metoda.  

Následující příklad používá k určení, zda je konkrétní datum víkendu, první den v týdnu pracovní poslední den pracovní týden nebo středu pracovní dny vzoru konstantní. Vyhodnocuje <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> vlastnost aktuálního dne na členech <xref:System.DayOfWeek> výčtu. 

[!code-csharp[switch#7](../../../../samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

Následující příklad používá konstantní vzor pro zpracování vstupu uživatele v konzolové aplikaci, která simuluje se automatické kávy počítač.
  
 [!code-csharp[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]  

### <a name="type-pattern"></a>Typ vzor

Vzor typ umožňuje stručným typ vyhodnocení a převod. Při použití s `switch` příkaz k provedení porovnávání vzorů testuje, zda výraz lze převést na zadaný typ a, pokud lze, obsahuje ji proměnné daného typu. Jeho syntaxe je:

```csharp
   case type varname 
```
kde *typ* je název typu, na který výsledek *expr* chcete převést, a *název_proměnné* je objekt, ke kterému výsledek *expr*je převést, pokud se podaří shody. 

`case` Výraz `true` Pokud žádné z následujících:

- *Expr* je instance stejného typu jako *typu*.

- *Expr* představuje instanci typu, která je odvozena z *typu*. Jinými slovy, výsledek *expr* může být přetypování nahoru na instanci *typu*.

- *Expr* má kompilaci typ, který je základní třídě *typ*, a *expr* má typ modulu runtime, který je *typ* nebo je odvozený od *typu* . *Typu v čase kompilace* proměnné je typ proměnné, jak jsou definovány v jeho deklaraci typu. *Typ modulu runtime* proměnné je typ instanci, která je přiřazena k této proměnné.

- *Expr* představuje instanci typu, který implementuje *typ* rozhraní.

Pokud je nastavena hodnota true, případu výraz *název_proměnné* výborný přiřazen a má místní oboru v části přepínače.

Všimněte si, že `null` neodpovídá typu. Tak, aby odpovídala `null`, použijte následující `case` štítku:

```csharp
case null:
```
 
Následující příklad používá typ vzor k zadání informací o různé druhy typy kolekcí.

[!code-csharp[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

Bez porovnávání vzorů, může tento kód zapsat takto. Použití porovnávání vzorů typu vytváří odstraněním potřeba otestovat, zda je výsledek převodu z kódu kompaktnější a čitelné `null` nebo provedení opakované přetypování.  

[!code-csharp[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="the-case-statement-and-the-when-clause"></a>`case` Příkaz a `when` – klauzule

Od verze jazyka C# 7, protože case – příkazy nemusí se vzájemně vylučují, můžete přidat `when` klauzule zadejte další podmínky, které musí být splněny pro příkaz case vyhodnotit na hodnotu true. `when` Klauzule může být jakýkoli výraz, který vrací logickou hodnotu. Jeden z běžných používá pro `when` klauzule slouží k části přepínač zabránit ve spouštění, pokud je hodnota výrazu shody `null`. 

 V následujícím příkladu definuje na základní `Shape` třída, `Rectangle` třídu odvozenou od `Shape`a `Square` třídu odvozenou od `Rectangle`. Používá `when` klauzule zajistit, aby `ShowShapeInfo` zpracovává `Rectangle` objekt, který byl přiřazen stejné délky a šířky jako `Square` i když je nebyla vytvořena instance jako `Square` objektu. Metoda nebude pokoušet o zobrazení informací o objekt, který je buď `null` nebo tvaru, jehož je nula. 

[!code-csharp[switch#8](../../../../samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]
  
Všimněte si, že `when` klauzule v příkladu, který se pokusí o test zda `Shape` objekt `null` nepracuje. Vzor správného typu chcete otestovat `null` je `case null:`.

## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](../../../../includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  

 [Referenční dokumentace jazyka C#](../index.md)  
 [Průvodce programováním v C#](../../programming-guide/index.md)  
 [Klíčová slova jazyka C#](index.md)  
 [if-else](if-else.md)  
 [Shoda vzoru](../../pattern-matching.md)  
 

 
