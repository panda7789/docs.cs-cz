---
title: je - C# odkaz
ms.custom: seodec18
ms.date: 04/09/2019
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: ac1ec7da7da465f4290000ac9c7254e9492c3c81
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66421813"
---
# <a name="is-c-reference"></a>is (Referenční dokumentace jazyka C#)

Zkontroluje, jestli je objekt kompatibilní s daným typem, nebo (od verze C# 7.0) testuje výraz se vzorem.

## <a name="testing-for-type-compatibility"></a>Testování kompatibility typu

`is` – Klíčové slovo vyhodnocen jako typ kompatibility za běhu. Určuje, zda instance objektu nebo výsledek výrazu lze převést na zadaný typ. Má syntaxi

```csharp
   expr is type
```

kde *expr* je výraz, který se vyhodnotí na instanci typu, a *typ* název typu, na který je výsledkem *expr* se má převést. `is` Příkaz je `true` Pokud *expr* je null a objekt, který je výsledkem vyhodnocení výrazu může být převeden na *typ*; v opačném případě vrátí `false`.

Například následující kód určuje, zda `obj` lze převést na instanci `Person` typu:

[!code-csharp[is#1](../../../../samples/snippets/csharp/language-reference/keywords/is/is1.cs#1)]

`is` Příkaz má hodnotu true pokud:

- *výraz* je instance stejného typu jako *typ*.

- *výraz* je instance typu, který je odvozen od *typ*. Jinými slovy, výsledek *expr* může být k instanci povýšení *typ*.

- *výraz* má typ za kompilace, která je základní třídou *typ*, a *expr* má typ modulu runtime, který je *typ* nebo odvozený od *typ*. *Typu v době kompilace* proměnné je typ proměnné definované v jeho deklaraci. *Typu prostředí runtime* proměnné je typ instance, který je přiřazen k této proměnné.

- *výraz* je instance typu, který implementuje *typ* rozhraní.

Následující příklad ukazuje, že `is` výraz vyhodnocen jako `true` pro každou z těchto převodů.

[!code-csharp[is#3](../../../../samples/snippets/csharp/language-reference/keywords/is/is3.cs#3)]

`is` – Klíčové slovo vygeneruje upozornění kompilace, pokud je známo, že výraz vždy být buď `true` nebo `false`. Uvažuje pouze převody odkazů, převodu zabalení a rozbalení převody; nepovažuje uživatelem definované převody nebo převody definované typem [implicitní](implicit.md) a [explicitní](explicit.md) operátory. Následující příklad generuje upozornění, protože výsledkem převodu je známá v době kompilace. `is` Výraz pro převod z `int` k `long` a `double` vrátí hodnotu false, protože tyto převody jsou zpracovávány [implicitní](implicit.md) operátor.

[!code-csharp[is#2](../../../../samples/snippets/csharp/language-reference/keywords/is/is2.cs#2)]

`expr` nemůže být anonymní metody nebo lambda výrazu. Může být libovolný výraz, který vrací hodnotu. Následující příklad používá `is` vyhodnotit vrácenou hodnotu volání metody.   
[!code-csharp[is#4](../../../../samples/snippets/csharp/language-reference/keywords/is/is4.cs#4)]

Od verze C# 7.0, můžete použít porovnávání vzorů s [vzor typu](#type) zapsat stručnější kód, který používá `is` příkazu.

## <a name="pattern-matching-with-is"></a>Porovnávání vzorů s `is`

Od verze C# 7.0, `is` a [přepnout](../../../csharp/language-reference/keywords/switch.md) příkazy podpory porovnávání vzorů. `is` – Klíčové slovo podporuje následující způsoby:

- [Typ vzorku](#type), který testuje, jestli výraz lze převést na zadaný typ a, pokud jej lze přetypování pro proměnnou daného typu.

- [Konstantní vzorek](#constant), který testuje, jestli je výraz vyhodnocen jako na zadanou hodnotu konstanty.

- [vzor var](#var), shoda, který je vždy úspěšné a přiřazuje hodnotu výrazu nové místní proměnné. 

### <a name="a-nametype-type-pattern"></a><a name="type" />Vzorek typu

Při použití typu modelu k provádění porovnávání vzorů, `is` testuje výraz lze převést na zadaný typ a pokud jej lze přetypování pro proměnnou daného typu. Je jednoduché rozšíření `is` příkaz, který umožňuje stručný typ vyhodnocení a převodu. Obecný tvar `is` vzor typu je:

```csharp
   expr is type varname 
```

kde *expr* je výraz, který se vyhodnotí na instanci typu, *typ* je název typu, na který výsledek *expr* se má převést a *název_proměnné* je objekt, na který výsledek *expr* je převedena, pokud `is` test je `true`. 

`is` Výraz je `true` Pokud *expr* není `null`, a je splněna některá z následujících akcí:

- *výraz* je instance stejného typu jako *typ*.

- *výraz* je instance typu, který je odvozen od *typ*. Jinými slovy, výsledek *expr* může být k instanci povýšení *typ*.

- *výraz* má typ za kompilace, která je základní třídou *typ*, a *expr* má typ modulu runtime, který je *typ* nebo odvozený od *typ*. *Typu v době kompilace* proměnné je typ proměnné definované v jeho deklaraci. *Typu prostředí runtime* proměnné je typ instance, který je přiřazen k této proměnné.

- *výraz* je instance typu, který implementuje *typ* rozhraní.

Počínaje C# 7.1, *expr* může mít za kompilace typu definované v parametru obecného typu a jeho omezení. 

Pokud *expr* je `true` a `is` se používá s `if` příkazu *název_proměnné* přiřazují v rámci `if` pouze příkaz. Rozsah *název_proměnné* z `is` výraz na konci uzavírající blok `if` příkazu. Pomocí *název_proměnné* v jiném umístění vygeneruje chybu kompilace pro použití proměnné, která nebyla přiřazena.

V následujícím příkladu `is` vzor typu k dispozici implementace typu <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> metody.

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

Bez porovnávání vzorů, může být napsán takto následujícím způsobem. Použití porovnávání vzorů typu produkuje kompaktnějším čitelné kódu pomocí tím eliminuje nutnost otestovat, jestli je výsledek převodu `null`.  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

`is` Vzor typu také vytvoří kompaktnějším kód při určování typu hodnotového typu. V následujícím příkladu `is` vzor typu k určení, zda je objekt `Person` nebo `Dog` instance před zobrazením hodnota příslušné vlastnosti. 

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

Ekvivalentní kód bez porovnávání vzorů vyžaduje samostatné přiřazení, který obsahuje explicitní přetypování.

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="a-nameconstant--constant-pattern"></a><a name="constant" /> Konstantní vzorek

Při provádění porovnávání vzorů s konstantní vzorek `is` testuje, zda výraz rovná zadané – konstanta. V jazyce C# 6 a starší verze, je podporován konstantní vzorek [přepnout](switch.md) příkazu. Počínaje C# 7.0, je podporována `is` také příkaz. Syntaxe je:

```csharp
   expr is constant
```

kde *expr* je výraz k vyhodnocení, a *konstantní* je hodnota pro testování. *konstantní* může být následující konstantní výrazy: 

- Hodnota literálu.

- Název deklarovanou `const` proměnné.

- Konstanta výčtu.

Konstantní výraz je vyhodnocen následujícím způsobem:

- Pokud *expr* a *konstantní* integrální typy jsou operátor rovnosti jazyka C# určuje, zda výraz vrací `true` (to znamená, zda `expr == constant`).

- V opačném případě je hodnota výrazu určena voláním statické [funkci Object.Equals (expr, konstantní)](xref:System.Object.Equals(System.Object,System.Object)) metody.  

Následující příklad kombinuje typ a konstantní vzory k ověření, zda je objekt `Dice` instance, a pokud se jedná, k určení, zda dice kumulativní hodnotu 6.

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

Kontrola `null` je možné provádět pomocí konstantní vzorek. `null` – Klíčové slovo je podporován `is` příkazu. Syntaxe je:

```csharp 
   expr is null
```

Následující příklad ukazuje porovnání `null` ověří:

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]
 
### <a name="var" /> vzor var </a>

`var` Vzor je pokrývající vše pro libovolným typem nebo hodnotou. Hodnota *expr* se vždycky přiřazuje lokální proměnná stejný typ jako typ času kompilace *expr*. Výsledkem `is` výraz je vždycky `true`. Syntaxe je:

```csharp 
   expr is var varname
```

Následující příklad používá vzor var výrazu přiřazení k proměnné s názvem `obj`. Potom zobrazí hodnotu a typ `obj`.

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

## <a name="c-language-specification"></a>Specifikace jazyka C#
  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)
- [typeof](../../../csharp/language-reference/keywords/typeof.md)
- [as](../../../csharp/language-reference/keywords/as.md)
