---
title: "for (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords: for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
caps.latest.revision: "39"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cb7e83733fe026658f502b430975a0f8a27e9df3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="for-c-reference"></a>for (Referenční dokumentace jazyka C#)
Pomocí `for` smyčku, můžete spustit příkaz nebo blok příkazů opakovaně dokud vyhodnotí zadaný výraz pro `false`. Tento druh smyčky je užitečný pro iterování přes pole a pro jiné aplikace, ve kterých víte předem kolikrát chcete, aby k iteraci smyčky.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu, hodnota `i` je zapsána do konzoly a zvýší o 1 při každé iteraci smyčky.  
  
 [!code-csharp[csrefKeywordsIteration#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_1.cs)]  
  
 `for` Příkaz v předchozím příkladu provede následující akce.  
  
1.  První, počáteční hodnota proměnné `i` je vytvořeno. Tento krok se stane pouze jednou, bez ohledu na to, jak mnohokrát opakuje smyčky. Tato inicializace si můžete představit jako situaci mimo proces opakování.  
  
2.  Při vyhodnocení podmínky (`i <= 5`), hodnota `i` se porovná s 5.  
  
    -   Pokud `i` je menší než nebo rovna 5, je podmínka vyhodnocena jako `true`, a dojde k následujícím akcím.  
  
        1.  `Console.WriteLine` Příkaz do těla smyčky zobrazuje hodnotu `i`.  
  
        2.  Hodnota `i` se zvýší o 1.  
  
        3.  Smyčky vrátí začátek krok 2: vyhodnocení podmínky znovu.  
  
    -   Pokud `i` je větší než 5, je podmínka vyhodnocena jako `false`, a ukončení smyčky.  
  
 Všimněte si, že, pokud počáteční hodnota `i` je větší než 5, do těla smyčky nefunguje i jednou.  
  
 Každý `for` příkaz definuje inicializátoru, podmínku a iterator oddíly. Tyto části obvykle určit počet opakování iterace smyčky.  
  
```csharp  
for (initializer; condition; iterator)  
    body  
```  
  
 V částech slouží k následujícím účelům.  
  
-   V části inicializátoru nastaví počáteční podmínky. Příkazy v této části spustit jenom jednou před zadáním smyčky. V části může obsahovat pouze jednu z následujících dvou možností.  
  
    -   Deklarace a inicializace proměnné místní smyčky, jak ukazuje příklad první (`int i = 1`). Proměnná je místní pro smyčky a není přístupný z mimo smyčku.  
  
    -   Nula nebo více příkaz expressons z následujícího seznamu, oddělených čárkami.  
  
        -   [přiřazení](../../../csharp/language-reference/operators/assignment-operator.md) – příkaz  
  
        -   volání metody  
  
        -   předpony nebo přípony [přírůstek](../../../csharp/language-reference/operators/increment-operator.md) výrazu, jako například `++i` nebo`i++`  
  
        -   předpony nebo přípony [snížení](../../../csharp/language-reference/operators/decrement-operator.md) výrazu, jako například `--i` nebo`i--`  
  
        -   Vytvoření objektu pomocí [nové](../../../csharp/language-reference/keywords/new-operator.md)  
  
        -   [await](../../../csharp/language-reference/keywords/await.md) výraz  
  
-   Podmínka oddíl obsahuje logický výraz, který se vyhodnotí k určení, zda smyčky musí ukončit nebo měli znovu spustit.  
  
-   Iterator oddíl definuje, co se stane po každé iteraci těla smyčky. Iterator obsahuje nula nebo více z těchto výrazů příkaz oddělené čárkami:  
  
    -   [přiřazení](../../../csharp/language-reference/operators/assignment-operator.md) – příkaz  
  
    -   volání metody  
  
    -   předpony nebo přípony [přírůstek](../../../csharp/language-reference/operators/increment-operator.md) výrazu, jako například `++i` nebo`i++`  
  
    -   předpony nebo přípony [snížení](../../../csharp/language-reference/operators/decrement-operator.md) výrazu, jako například `--i` nebo`i--`  
  
    -   Vytvoření objektu pomocí [nové](../../../csharp/language-reference/keywords/new-operator.md)  
  
    -   [await](../../../csharp/language-reference/keywords/await.md) výraz  
  
-   Do těla smyčky se skládá z příkazu, prázdný příkaz nebo blok příkazů, které vytvoříte uzavřením nula nebo více příkazů do složených závorek.  
  
     Můžete rozdělit mimo `for` smyčky pomocí [zalomení](../../../csharp/language-reference/keywords/break.md) – klíčové slovo, nebo můžete do další iterace krok pomocí [pokračovat](../../../csharp/language-reference/keywords/continue.md) – klíčové slovo. Také můžete ukončit všechny smyčky pomocí [goto](../../../csharp/language-reference/keywords/goto.md), [vrátit](../../../csharp/language-reference/keywords/return.md), nebo [throw](../../../csharp/language-reference/keywords/throw.md) příkaz.  
  
 V prvním příkladu v tomto tématu uvádí některé běžné druh `for` smyčky, která umožňuje následující volby v částech.  
  
-   Inicializátoru deklaruje a inicializuje proměnnou místní smyčky `i`, který spravuje počet iterací smyčky.  
  
-   Podmínka kontroluje hodnotu proměnné smyčky proti známé konečná hodnota 5.  
  
-   V části iterator používá výpisu operátory přírůstku `i++`, zaznamenávat každé iteraci smyčky.  
  
 Následující příklad ilustruje několik méně běžné volby: přiřazení hodnoty proměnné externí smyčky v části inicializátoru, volání `Console.WriteLine` metoda v inicializátoru a iterator oddíly a změna hodnot dvě proměnné v části iterator.  
  
 [!code-csharp[csrefKeywordsIteration#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_2.cs)]  
  
 Všechny výrazy, které definují `for` příkaz jsou volitelné. Například následující příkaz vytvoří nekonečné smyčce.  
  
 [!code-csharp[csrefKeywordsIteration#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_3.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [foreach v](../../../csharp/language-reference/keywords/foreach-in.md)  
 [pro příkaz (C++)](/cpp/cpp/for-statement-cpp)  
 [Příkazy iterace](../../../csharp/language-reference/keywords/iteration-statements.md)
