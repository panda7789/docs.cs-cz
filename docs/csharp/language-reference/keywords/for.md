---
title: for (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: 2c099411499c6ca8396c55955bdc634e48caf621
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/18/2018
ms.locfileid: "34306524"
---
# <a name="for-c-reference"></a>pro (referenční dokumentace jazyka C#)

Pomocí `for` smyčku, můžete spustit příkaz nebo blok příkazů opakovaně dokud vyhodnotí zadaný výraz pro `false`. Tento druh smyčky je užitečný pro iterování přes pole a pro jiné aplikace, ve kterých víte předem kolikrát chcete, aby k iteraci smyčky.
  
## <a name="example"></a>Příklad

V následujícím příkladu, hodnota `i` je zapsána do konzoly a při každé iteraci smyčky zvýší o 1:
  
[!code-csharp[csrefKeywordsIteration#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_1.cs)]
  
[Pro příkaz](/dotnet/csharp/language-reference/language-specification/statements#the-for-statement) v předchozím příkladu provede následující akce:
  
1.  První, počáteční hodnota proměnné `i` je vytvořeno. Tento krok se stane pouze jednou, bez ohledu na to, jak mnohokrát opakuje smyčky. Tato inicializace si můžete představit jako situaci mimo proces opakování.
  
2.  Při vyhodnocení podmínky (`i <= 5`), hodnota `i` se porovná s 5.
  
    -   Pokud `i` je menší než nebo rovna 5, je podmínka vyhodnocena jako `true`, a dojde k následujícím akcím.  
  
        1.  `Console.WriteLine` Příkaz do těla smyčky zobrazuje hodnotu `i`.  
  
        2.  Hodnota `i` se zvýší o 1.  
  
        3.  Smyčky vrátí začátek krok 2: vyhodnocení podmínky znovu.  
  
    -   Pokud `i` je větší než 5, je podmínka vyhodnocena jako `false`, a ukončení smyčky.  
  
Všimněte si, že, pokud počáteční hodnota `i` je větší než 5, do těla smyčky nefunguje i jednou.

## <a name="sections-of-a-for-statement"></a>Části pro příkaz
  
Každý [pro příkaz](/dotnet/csharp/language-reference/language-specification/statements#the-for-statement) definuje *inicializátoru*, *podmínku*, a *iterator* oddíly. Tyto části obvykle určit počet opakování iterace smyčky.  
  
```csharp  
for (initializer; condition; iterator)  
    body  
```  
  
V částech slouží k následujícím účelům:
  
-   V části inicializátoru nastaví počáteční podmínky. Příkazy v této části spustit jenom jednou před zadáním smyčky. V části může obsahovat pouze jednu z následujících dvou možností.  
  
    -   Deklarace a inicializace proměnné místní smyčky, jak ukazuje příklad první (`int i = 1`). Proměnná je místní pro smyčky a není přístupný z mimo smyčku.  
  
    -   Nula nebo více příkaz expressons z následujícího seznamu, oddělených čárkami.  
  
        -   [přiřazení](../../../csharp/language-reference/operators/assignment-operator.md) – příkaz  
  
        -   volání metody  
  
        -   předpony nebo přípony [přírůstek](../../../csharp/language-reference/operators/increment-operator.md) výrazu, jako například `++i` nebo `i++`  
  
        -   předpony nebo přípony [snížení](../../../csharp/language-reference/operators/decrement-operator.md) výrazu, jako například `--i` nebo `i--`  
  
        -   Vytvoření objektu pomocí [nové](../../../csharp/language-reference/keywords/new-operator.md)  
  
        -   [await](../../../csharp/language-reference/keywords/await.md) výraz  
  
-   Podmínka oddíl obsahuje logický výraz, který se vyhodnotí k určení, zda smyčky musí ukončit nebo měli znovu spustit.  
  
-   Iterator oddíl definuje, co se stane po každé iteraci těla smyčky. Iterator obsahuje nula nebo více z těchto výrazů příkaz oddělené čárkami:  
  
    -   [přiřazení](../../../csharp/language-reference/operators/assignment-operator.md) – příkaz  
  
    -   volání metody  
  
    -   předpony nebo přípony [přírůstek](../../../csharp/language-reference/operators/increment-operator.md) výrazu, jako například `++i` nebo `i++`  
  
    -   předpony nebo přípony [snížení](../../../csharp/language-reference/operators/decrement-operator.md) výrazu, jako například `--i` nebo `i--`  
  
    -   Vytvoření objektu pomocí [nové](../../../csharp/language-reference/keywords/new-operator.md)  
  
    -   [await](../../../csharp/language-reference/keywords/await.md) výraz  
  
-   Do těla smyčky se skládá z příkazu, prázdný příkaz nebo blok příkazů, které vytvoříte uzavřením nula nebo více příkazů do složených závorek.  
  
     Můžete rozdělit mimo `for` smyčky pomocí [zalomení](../../../csharp/language-reference/keywords/break.md) – klíčové slovo, nebo můžete do další iterace krok pomocí [pokračovat](../../../csharp/language-reference/keywords/continue.md) – klíčové slovo. Také můžete ukončit všechny smyčky pomocí [goto](../../../csharp/language-reference/keywords/goto.md), [vrátit](../../../csharp/language-reference/keywords/return.md), nebo [throw](../../../csharp/language-reference/keywords/throw.md) příkaz.  
  
V prvním příkladu v tomto tématu uvádí některé běžné druh `for` smyčky, která umožňuje následující volby v částech:
  
-   Inicializátoru deklaruje a inicializuje proměnnou místní smyčky `i`, který spravuje počet iterací smyčky.  
  
-   Podmínka kontroluje hodnotu proměnné smyčky proti známé konečná hodnota 5.  
  
-   V části iterator používá výpisu operátory přírůstku `i++`, zaznamenávat každé iteraci smyčky.

## <a name="more-examples"></a>Další příklady
  
Následující příklad ilustruje několik méně běžné volby: přiřazení hodnoty proměnné externí smyčky v části inicializátoru, volání `Console.WriteLine` metoda v inicializátoru a iterator oddíly a změna hodnot dvě proměnné v části iterator.
  
[!code-csharp[csrefKeywordsIteration#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_2.cs)]  
  
Všechny výrazy, které definují `for` příkaz jsou volitelné. Například následující příkaz vytvoří nekonečná smyčka:
  
[!code-csharp[csrefKeywordsIteration#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_3.cs)]  
  
## <a name="c-language-specification"></a>specifikace jazyka C#  

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
  
## <a name="see-also"></a>Viz také

[Pro příkaz (specifikace jazyka C#)](/dotnet/csharp/language-reference/language-specification/statements#the-for-statement)  
[Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
[Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
[Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
[foreach, in](../../../csharp/language-reference/keywords/foreach-in.md)  
[for – příkaz (C++)](/cpp/cpp/for-statement-cpp)  
[Příkazy iterace](../../../csharp/language-reference/keywords/iteration-statements.md)
