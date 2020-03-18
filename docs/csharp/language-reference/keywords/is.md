---
title: je - C# Odkaz
ms.date: 06/21/2019
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: e64b690482419963a92764b2c97a42dbb231fbfc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399635"
---
# <a name="is-c-reference"></a>is (Referenční dokumentace jazyka C#)

Operátor `is` zkontroluje, zda je výsledek výrazu kompatibilní s daným typem, nebo (počínaje c# 7.0) testuje výraz proti vzoru. Informace o operátoru `is` testování typu naleznete v části [is operátor](../operators/type-testing-and-cast.md#is-operator) v článku [Operátory testování typu a přetypovátí.](../operators/type-testing-and-cast.md)

## <a name="pattern-matching-with-is"></a>Porovnávání vzorů s`is`

Počínaje C# 7.0, `is` a [switch](switch.md) příkazy podporují porovnávání vzorů. Klíčové `is` slovo podporuje následující vzory:

- [Vzorek typu](#type-pattern), který testuje, zda lze výraz převést na zadaný typ, a pokud může být, přetypuje jej na proměnnou tohoto typu.

- [Konstantní vzor](#constant-pattern), který testuje, zda výraz vyhodnotí zadanou konstantní hodnotu.

- [var pattern](#var-pattern), shoda, která vždy uspěje a váže hodnotu výrazu na novou místní proměnnou.

### <a name="type-pattern"></a>Vzor typu

Při použití vzoru typu k `is` provedení porovnávání vzorků testuje, zda lze výraz převést na zadaný typ, a pokud může být, přetypuje do proměnné tohoto typu. Je to jednoduché rozšíření `is` prohlášení, které umožňuje stručné hodnocení typu a převod. Obecná forma `is` vzoru typu je:

```csharp
   expr is type varname
```

Kde *expr* je výraz, který je vyhodnocen jako instance nějakého typu, *typ* je název typu, na který má být výsledek *expr* převeden, a `is` *varname* je objekt, na který je výsledek *expr* převeden, pokud je `true`test .

Výraz `is` je, `true` pokud *expr* není `null`a platí některá z následujících hodnot:

- *expr* je instancí stejného typu jako *typ*.

- *expr* je instancí typu, který je odvozen od *typu*. Jinými slovy, výsledek *expr* může být upcast na instanci *typu*.

- *expr* má typ kompilace, který je základní třídou *typu*, a *expr* má typ runtime, který je *typu* nebo je odvozen od *typu*. Typ proměnné v *době kompilace* je typ proměnné, jak je definován v jeho deklaraci. *Typ runtime* proměnné je typ instance, která je přiřazena k této proměnné.

- *expr* je instancí třídy typu, který implementuje *rozhraní typu.*

Počínaje C# 7.1 *expr* může mít typ kompilace definovaný parametrem obecného typu a jeho omezeními.

Pokud *expr* `true` je a `is` `if` používá se s příkazem, *varname* je přiřazen a to pouze v rámci příkazu. `if` Obor *varname* je z `is` výrazu na konec bloku `if` ohraničující příkaz. Použití *varname* v jiném umístění generuje chybu v době kompilace pro použití proměnné, která nebyla přiřazena.

Následující příklad používá `is` vzorek typu k zajištění implementace <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> metody typu.

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

Bez porovnávání vzorů může být tento kód zapsán následujícím způsobem. Použití odpovídající vzorek typu vytváří kompaktnější, čitelný kód tím, že eliminuje potřebu `null`otestovat, zda je výsledkem převodu .  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

Vzorek `is` typu také vytváří kompaktnější kód při určování typu typu hodnoty. Následující příklad používá `is` vzorek typu k určení, `Person` zda `Dog` je objekt nebo instance před zobrazením hodnoty příslušné vlastnosti.

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

Ekvivalentní kód bez porovnávání vzorů vyžaduje samostatné přiřazení, které obsahuje explicitní přetypování.

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="constant-pattern"></a>Konstantní vzor

Při porovnávání vzorků s konstantním vzorkem testuje, `is` zda se výraz rovná zadané konstantě. V C# 6 a starší verze konstantní vzor je podporován [příkazem switch.](switch.md) Počínaje C# 7.0, je podporován `is` prohlášení také. Jeho syntaxe je:

```csharp
   expr is constant
```

kde *expr* je výraz k vyhodnocení a *konstanta* je hodnota, pro kterou se má testovat. *konstanta* může být některý z následujících konstantních výrazů:

- Doslovná hodnota.

- Název deklarované `const` proměnné.

- Konstanta výčtu.

Konstantní výraz je vyhodnocen takto:

- Pokud *expr* a *konstanta* jsou integrální typy, c# operátor rovnosti určuje, zda výraz vrátí `true` (to znamená, zda `expr == constant`).

- Jinak je hodnota výrazu určena voláním statické [metody Object.Equals(expr, constant).](xref:System.Object.Equals(System.Object,System.Object))  

Následující příklad kombinuje text a konstantní vzorky k testování, zda je objekt `Dice` instance a pokud je, chcete-li zjistit, zda je hodnota kostky hod u 6.

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

Kontrola pro `null` lze provést pomocí konstantní vzor. Klíčové `null` slovo je `is` podporováno příkazem. Jeho syntaxe je:

```csharp
   expr is null
```

Následující příklad ukazuje porovnání `null` kontrol:

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]

### <a name="var-pattern"></a>var vzor

Vzor shoda se `var` vzorem vždy úspěšné. Jeho syntaxe je:

```csharp
   expr is var varname
```

Kde je hodnota *expr* vždy přiřazena místní proměnné s názvem *varname*. *varname* je proměnná stejného typu jako typ *expr*v době kompilace .

Pokud *expr* vyhodnotí `null`, `is` výraz vytvoří `true` a přiřadí `null` *varname*. Vzor var je jedním z `is` mála použití, které vytváří `true` pro hodnotu. `null`

`var` Vzor můžete použít k vytvoření dočasné proměnné v logickém výrazu, jak ukazuje následující příklad:

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

V předchozím příkladu se dočasná proměnná používá k uložení výsledku nákladné operace. Proměnnou lze pak použít vícekrát.

## <a name="c-language-specification"></a>specifikace jazyka C#
  
Další informace naleznete v části [Is operátor](~/_csharplang/spec/expressions.md#the-is-operator) specifikace jazyka [C#](~/_csharplang/spec/introduction.md) a následující návrhy jazyka C#:

- [Porovnávání vzorů](~/_csharplang/proposals/csharp-7.0/pattern-matching.md)
- [Porovnávání vzorů s obecnými typy](~/_csharplang/proposals/csharp-7.1/generics-pattern-match.md)
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Klíčová slova jazyka C#](index.md)
- [Operátory pro testování typů a přetypování](../operators/type-testing-and-cast.md)
