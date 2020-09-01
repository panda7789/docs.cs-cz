---
description: ReadOnly – klíčové slovo – Reference jazyka C#
title: ReadOnly – klíčové slovo – Reference jazyka C#
ms.date: 04/14/2020
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: b1bab5af18216fcef2162179493dbbb59e3470cf
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137172"
---
# <a name="readonly-c-reference"></a>readonly – modifikátor (Referenční dokumentace jazyka C#)

`readonly`Klíčové slovo je modifikátor, který lze použít ve čtyřech kontextech:

- V [deklaraci pole](#readonly-field-example) `readonly` označuje, že přiřazení k poli může být provedeno pouze v rámci deklarace nebo v konstruktoru ve stejné třídě. Pole jen pro čtení se dá přiřadit a přiřadit vícekrát v rámci deklarace a konstruktoru pole.
  
  `readonly`Po ukončení konstruktoru nelze pole přiřadit. Toto pravidlo má různé dopady na typy hodnot a typy odkazů:
  
  - Vzhledem k tomu, že typy hodnot přímo obsahují svá data, pole, které je  `readonly` hodnotový typ, je neměnné.
  - Vzhledem k tomu, že typy odkazů obsahují odkaz na jejich data, pole, které je `readonly` odkazový typ, musí vždy odkazovat na stejný objekt. Tento objekt není neměnný. `readonly`Modifikátor zabraňuje tomu, aby bylo pole nahrazeno jinou instancí typu odkazu. Modifikátor však nebrání v úpravě dat instance pole v rámci pole jen pro čtení.

  > [!WARNING]
  > Externě viditelný typ, který obsahuje externě viditelné pole jen pro čtení, které je proměnlivým odkazovým typem, může představovat chybu zabezpečení a může aktivovat upozornění [CA2104](/visualstudio/code-quality/ca2104) : "Nedeklarujte pouze proměnlivé odkazy typu jen pro čtení."

- V `readonly struct` definici typu `readonly` označuje, že typ struktury je neměnný. Další informace naleznete [ `readonly` v části struktura v článku](../builtin-types/struct.md#readonly-struct) [typy struktury](../builtin-types/struct.md) .
- V deklaraci člena instance v rámci typu struktury `readonly` označuje, že člen instance neupravuje stav struktury. Další informace naleznete v oddílu [ `readonly` instance členů](../builtin-types/struct.md#readonly-instance-members) článku [typy struktury](../builtin-types/struct.md) .
- V [ `ref readonly` metodě se vrátí](#ref-readonly-return-example) `readonly` modifikátor, že metoda vrátí odkaz a zápisy nejsou pro tento odkaz povoleny.

`readonly struct` `ref readonly` Kontexty a byly přidány v C# 7,2. `readonly` Členy struktury se přidaly v C# 8,0.

## <a name="readonly-field-example"></a>Příklad pole jen pro čtení

V tomto příkladu `year` nemůže být hodnota pole v metodě změněna `ChangeYear` , i když je přiřazena hodnota v konstruktoru třídy:

[!code-csharp[Readonly Field example](snippets/ReadonlyKeywordExamples.cs#ReadonlyField)]

K poli můžete přiřadit hodnotu `readonly` pouze v následujících kontextech:

- Když je proměnná inicializována v deklaraci, například:

  ```csharp
  public readonly int y = 5;
  ```

- V konstruktoru instance třídy, která obsahuje deklaraci pole instance.
- Ve statickém konstruktoru třídy, která obsahuje deklaraci statického pole.

Tyto kontexty konstruktoru jsou také pouze kontexty, ve kterých je platný pro předání `readonly` pole jako [výstupní](out-parameter-modifier.md) parametr nebo parametr [ref](ref.md) .

> [!NOTE]
> `readonly`Klíčové slovo se liší od klíčového slova [const](const.md) . `const`Pole lze inicializovat pouze v deklaraci pole. `readonly`Pole lze přiřadit vícekrát v deklaraci pole a v jakémkoli konstruktoru. Proto `readonly` pole mohou mít různé hodnoty v závislosti na použitém konstruktoru. I když `const` je pole konstanta při kompilaci, `readonly` pole lze použít pro konstanty run-time, jako v následujícím příkladu:
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](snippets/ReadonlyKeywordExamples.cs#InitReadonlyField)]

V předchozím příkladu, pokud použijete příkaz jako v následujícím příkladu:

```csharp
p2.y = 66;        // Error
```

zobrazí se chybová zpráva kompilátoru:

**K poli jen pro čtení se nedá přiřadit (kromě případu, kdy se nachází v konstruktoru nebo inicializátoru proměnné).**

## <a name="ref-readonly-return-example"></a>Návratový příklad pro odkaz ReadOnly

`readonly`Modifikátor na pozici `ref return` označuje, že vrácený odkaz nelze upravit. Následující příklad vrátí odkaz na počátek. Používá `readonly` Modifikátor k označení, že volající nemohou změnit původní:

[!code-csharp[readonly return example](snippets/ReadonlyKeywordExamples.cs#ReadonlyReturn)]

Vrácený typ nemusí být `readonly struct` . Libovolný typ, který může být vrácen pomocí, `ref` může být vrácen `ref readonly` .

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

Můžete si také prohlédnout návrhy specifikace jazyka:

- [struktura ReadOnly a ReadOnly](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [Členové struktury jen pro čtení](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Modifikátory](index.md)
- [const](const.md)
- [Pole](../../programming-guide/classes-and-structs/fields.md)
