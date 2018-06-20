---
title: for (Referenční dokumentace jazyka C#)
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: beac7727c8ce83d8ea20f0fc578f80ceef3053e7
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208358"
---
# <a name="for-c-reference"></a>pro (referenční dokumentace jazyka C#)

`for` Příkaz spustí příkaz nebo blok příkazů při zadaný logický výraz vyhodnocen jako `true`.

Kdykoli bodu v rámci `for` příkaz bloku, může dojít k narušení mimo smyčky pomocí [zalomení](break.md) příkaz nebo krok do další iterace ve smyčce pomocí [pokračovat](continue.md) příkaz. Také můžete ukončit `for` cykly pomocí [goto](goto.md), [vrátit](return.md), nebo [throw](throw.md) příkazy.
  
## <a name="structure-of-the-for-statement"></a>Struktura `for` – příkaz

`for` Definuje příkaz *inicializátoru*, *podmínku*, a *iterator* částech:
  
```csharp
for (initializer; condition; iterator)  
    body  
```

Všechny tři části jsou volitelné. Do těla smyčky je příkaz nebo blok příkazů.

Následující příklad ukazuje `for` příkaz s všechny oddíly definované:

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a>*Inicializátoru* části

Příkazy v *inicializátoru* části jsou vykonány pouze jednou před vstupem smyčky. *Inicializátoru* část se z následujících:

- Deklarace a inicializace proměnnou místní smyčky, která není přístupná z mimo smyčku.

- Nula nebo více výrazů příkaz z následujícího seznamu, oddělených čárkami:

  - [přiřazení](../operators/assignment-operator.md) – příkaz

  - volání metody  

  - předpony nebo přípony [přírůstek](../operators/increment-operator.md) výrazu, jako například `++i` nebo `i++`  

  - předpony nebo přípony [snížení](../operators/decrement-operator.md) výrazu, jako například `--i` nebo `i--`  

  - Vytvoření objektu pomocí [nové](new-operator.md) – klíčové slovo

  - [await](await.md) výraz

*Inicializátoru* část v předchozím příkladu deklaruje a inicializuje proměnnou místní smyčky `i`:

```csharp
int i = 0
```

### <a name="the-condition-section"></a>*Podmínku* části

*Podmínku* část, pokud existuje, musí být logický výraz. Tento výraz se vyhodnocují před každou iteraci smyčky. Pokud *podmínku* části není k dispozici nebo je logický výraz vyhodnocen `true`další iterace smyčky je provedeno; jinak, smyčky je byl ukončen.

*Podmínku* část v předchozím příkladu určuje Pokud smyčky ukončí na základě hodnoty proměnné místní smyčka:

```csharp
i < 5
```

### <a name="the-iterator-section"></a>*Iterator* části

*Iterator* oddíl definuje, co se stane po každé iteraci těla smyčky. *Iterator* část obsahuje nula nebo více z těchto výrazů příkaz oddělené čárkami:  

- [přiřazení](../operators/assignment-operator.md) – příkaz

- volání metody  

- předpony nebo přípony [přírůstek](../operators/increment-operator.md) výrazu, jako například `++i` nebo `i++`  

- předpony nebo přípony [snížení](../operators/decrement-operator.md) výrazu, jako například `--i` nebo `i--`  

- Vytvoření objektu pomocí [nové](new-operator.md) – klíčové slovo

- [await](await.md) výraz

*Iterator* část v předchozím příkladu zvýší proměnnou místní smyčka:

```csharp
i++
```

## <a name="examples"></a>Příklady

Následující příklad ilustruje několik méně běžné použití `for` příkaz částech: přiřazení hodnoty proměnné externí smyčky v *inicializátoru* části volání metody v obou  *Inicializátor* a *iterator* části a změna hodnoty dvou proměnných ve *iterator* části. Vyberte **spustit** spustit ukázkový kód. Poté můžete upravit kód a potom ho spusťte znovu.
  
[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]
  
V následujícím příkladu definuje nekonečné `for` smyčka:
  
[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]
  
## <a name="c-language-specification"></a>specifikace jazyka C#  

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
  
## <a name="see-also"></a>Viz také:

[Pro příkaz (specifikace jazyka C#)](/dotnet/csharp/language-reference/language-specification/statements#the-for-statement)  
[Referenční dokumentace jazyka C#](../index.md)  
[Průvodce programováním v jazyce C#](../../programming-guide/index.md)  
[Klíčová slova jazyka C#](index.md)  
[foreach, in](foreach-in.md)  
[for – příkaz (C++)](/cpp/cpp/for-statement-cpp)  
[Příkazy iterace](iteration-statements.md)
