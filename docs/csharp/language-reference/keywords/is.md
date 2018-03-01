---
title: "is (Referenční dokumentace jazyka C#)"
keywords: "je klíčové slovo (C#), je (C#)"
ms.date: 02/17/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9f0242439caa21268a6c314409f41587890c4126
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="is-c-reference"></a>is (Referenční dokumentace jazyka C#) #

Zkontroluje, jestli je objekt kompatibilní s daného typu, nebo (C# 7 počínaje) testy výraz se vzorem.

## <a name="testing-for-type-compatibility"></a>Testování kompatibility typu ##

`is` – Klíčové slovo vyhodnotí kompatibility typu za běhu. Určuje, zda instanci objektu nebo výsledek výrazu lze převést na zadaný typ. Má syntaxe

```csharp
   expr is type
```

kde *expr* je výraz, který se vyhodnotí na instanci typu, a *typ* je název typu, na který výsledek *expr* chcete převést. `is` Příkaz je `true` Pokud *expr* jinou hodnotu než null a objekt, který výsledků vyhodnocení výrazu může být převeden na *typ*, jinak vrátí `false`.

Například následující kód určuje, zda `obj` lze převést na instanci `Person` typu:

[!code-csharp[is#1](../../../../samples/snippets/csharp/language-reference/keywords/is/is1.cs#1)]

`is` Příkaz je hodnota true, pokud:

- *Expr* je instance stejného typu jako *typu*.

- *Expr* představuje instanci typu, která je odvozena z *typu*. Jinými slovy, výsledek *expr* může být přetypování nahoru na instanci *typu*.

- *Expr* má kompilaci typ, který je základní třídě *typ*, a *expr* má typ modulu runtime, který je *typ* nebo je odvozený od *typu* . *Typu v čase kompilace* proměnné je typ proměnné, jak jsou definovány v jeho deklaraci. *Typ modulu runtime* proměnné je typ instanci, která je přiřazena k této proměnné.

- *Expr* představuje instanci typu, který implementuje *typ* rozhraní.

Následující příklad ukazuje, že `is` výraz vyhodnocen jako `true` pro každou z těchto převody.

[!code-csharp[is#3](../../../../samples/snippets/csharp/language-reference/keywords/is/is3.cs#3)]

`is` – Klíčové slovo vygeneruje kompilaci upozornění, pokud je znám výraz vždycky být buď `true` nebo `false`. Uvažuje pouze převody odkazů, převodů zabalení a rozbalení převody; nepovažuje uživatelem definované převody nebo převody definované typem [implicitní](implicit.md) a [explicitní](explicit.md) operátory. V následujícím příkladu generuje upozornění, protože je v době kompilace výsledek převodu. Všimněte si, že `is` výraz převody z `int` k `long` a `double` vrátí hodnotu false, protože tyto převody jsou zpracovávány [implicitní](implicit.md) operátor.

[!code-csharp[is#2](../../../../samples/snippets/csharp/language-reference/keywords/is/is2.cs#2)]

`expr`může být jakékoli výraz, který vrátí hodnotu, s výjimkou anonymní metody a výrazy lambda. Následující příklad používá `is` vyhodnotit návratovou hodnotu volání metody.   
[!code-csharp[is#4](../../../../samples/snippets/csharp/language-reference/keywords/is/is4.cs#4)]

Od verze jazyka C# 7, můžete použít porovnávání vzorů s [typ vzor](#type) napsat přesnější kód, který používá `is` příkaz.

## <a name="pattern-matching-with-is"></a>Pro porovnávání s`is` ##

Od verze jazyka C# 7, `is` a [přepínače](../../../csharp/language-reference/keywords/switch.md) příkazy podpory porovnávání vzorů. `is` – Klíčové slovo podporuje následující vzorce:

- [Typ vzor](#type), který kontroluje, zda výraz lze převést na zadaný typ a, pokud lze, obsahuje ji proměnné daného typu.

- [Konstantní vzor](#constant), který kontroluje, zda výsledkem konstantní hodnotu zadaného výrazu.

- [var – vzor](#var), shoda, který vždy úspěšné a sváže hodnotu výrazu nové místní proměnné. 

### <a name="type" />Typ vzor</a>

Při provádění porovnávání vzorů pomocí vzoru typ `is` testuje, zda výraz lze převést na zadaný typ a pokud jej lze obsahuje ji proměnné daného typu. Je přehledné rozšíření `is` příkaz, který umožňuje stručným typ vyhodnocení a převod. Obecná forma `is` typ vzor je:

```csharp
   expr is type varname 
```

kde *expr* je výraz, který se vyhodnotí na instanci typu, *typ* je název typu, na který výsledek *expr* chcete převést a *název_proměnné* je objekt, ke kterému výsledek *expr* je převést, pokud `is` test je `true`. 

`is` Výraz `true` Pokud žádné z následujících:

- *Expr* je instance stejného typu jako *typu*.

- *Expr* představuje instanci typu, která je odvozena z *typu*. Jinými slovy, výsledek *expr* může být přetypování nahoru na instanci *typu*.

- *Expr* má kompilaci typ, který je základní třídě *typ*, a *expr* má typ modulu runtime, který je *typ* nebo je odvozený od *typu* . *Typu v čase kompilace* proměnné je typ proměnné, jak jsou definovány v jeho deklaraci. *Typ modulu runtime* proměnné je typ instanci, která je přiřazena k této proměnné.

- *Expr* představuje instanci typu, který implementuje *typ* rozhraní.

Pokud *exp* je `true` a `is` se používá s `if` příkaz *název_proměnné* je přiřazen a má místní rozsah v rámci `if` pouze příkaz.

Následující příklad používá `is` typ vzor k zajištění implementace typu <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> metoda.

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

Bez porovnávání vzorů, může tento kód zapsat takto. Použití porovnávání vzorů typu vytváří odstraněním potřeba otestovat, zda je výsledek převodu z kódu kompaktnější a čitelné `null`.  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

`is` Typ vzor také vytváří kompaktnější kód při určování typ typ hodnoty. Následující příklad používá `is` typ vzor k určení, zda je objekt `Person` nebo `Dog` instance, než se zobrazí hodnota příslušné vlastnosti. 

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

Kód ekvivalentní bez odpovídající vzor vyžaduje samostatné přiřazení, které obsahuje explicitní přetypování.

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="a-nameconstant--constant-pattern"></a><a name="constant" />Konstantní vzor ###

Při provádění porovnávání s konstantní vzor vzorů `is` testuje, zda výraz rovná zadané konstanta. V jazyce C# 6 a starší verze, konstantní vzor podporuje [přepínač](switch.md) příkaz. Od verze jazyka C# 7, je podporována `is` příkaz také. Jeho syntaxe je:

```csharp
   expr is constant
```

kde *expr* se výraz, který chcete vyhodnotit, a *konstantní* je hodnota, kterou chcete otestovat. *konstantní* může být libovolná z následujících konstantní výrazy: 

- Hodnota literálu.

- Název deklarované `const` proměnné.

- Konstanta výčtu.

Konstantní výraz je vyhodnotit takto:

- Pokud *expr* a *konstantní* jsou integrální typy operátor rovnosti jazyka C# určuje, zda výraz vrací `true` (to znamená, zda `expr == constant`).

- Jinak hodnota výrazu je určena voláním statických [Object.Equals (výraz, konstantní)](xref:System.Object.Equals(System.Object,System.Object)) metoda.  

Následující příklad kombinuje typu a konstanta vzory k ověření, zda je objekt `Dice` instance, a pokud se jedná, chcete-li zjistit jestli rozčlenění kumulativní hodnotu 6.

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]
 
### <a name="var" />var – vzor</a>

Vzor shody s var vzor je vždy úspěšné. Jeho syntaxe je

```csharp 
   expr is var varname
```

kde hodnota *expr* se vždycky přiřazuje místní proměnné s názvem *název_proměnné*. *název_proměnné* je statická proměnná stejného typu jako *expr*. Následující příklad používá var vzor výrazu přiřadit proměnné s názvem `obj`. Potom zobrazí hodnota a typ `obj`.

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

Všimněte si, že pokud *expr* je `null`, `is` výraz stále platí a přiřadí `null` k *název_proměnné*. 

# <a name="c-language-specification"></a>Specifikace jazyka C#
  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [typeof](../../../csharp/language-reference/keywords/typeof.md)  
 [jako](../../../csharp/language-reference/keywords/as.md)  
 [Klíčová slova operátorů](../../../csharp/language-reference/keywords/operator-keywords.md)
