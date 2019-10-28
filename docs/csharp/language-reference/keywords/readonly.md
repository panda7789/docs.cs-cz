---
title: ReadOnly – odkaz C# na klíčové slovo
ms.custom: seodec18
ms.date: 06/21/2018
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 6c48806e54f11bce930d03a53b010c337e6658f8
ms.sourcegitcommit: 9b2ef64c4fc10a4a10f28a223d60d17d7d249ee8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/26/2019
ms.locfileid: "72960857"
---
# <a name="readonly-c-reference"></a>readonly – modifikátor (Referenční dokumentace jazyka C#)

Klíčové slovo `readonly` je modifikátor, který lze použít ve čtyřech kontextech:

- V [deklaraci pole](#readonly-field-example)`readonly` označuje, že přiřazení k poli může být provedeno pouze jako součást deklarace nebo v konstruktoru ve stejné třídě. Pole jen pro čtení se dá přiřadit a přiřadit vícekrát v rámci deklarace a konstruktoru pole. 
  
  Po ukončení konstruktoru nelze přiřadit pole `readonly`. Toto pravidlo má různé dopady na typy hodnot a typy odkazů:
  
  - Vzhledem k tomu, že typy hodnot přímo obsahují svá data, pole, které je typu `readonly` hodnoty, je neměnné. 
  - Vzhledem k tomu, že typy odkazů obsahují odkaz na svá data, pole, které je `readonly` odkazový typ, musí vždy odkazovat na stejný objekt. Tento objekt není neměnný. Modifikátor `readonly` zabraňuje tomu, aby se pole nahradilo jinou instancí typu odkazu. Modifikátor však nebrání v úpravě dat instance pole v rámci pole jen pro čtení.

  > [!WARNING]
  > Externě viditelný typ, který obsahuje externě viditelné pole jen pro čtení, které je proměnlivým odkazovým typem, může představovat chybu zabezpečení a může aktivovat upozornění [CA2104](/visualstudio/code-quality/ca2104-do-not-declare-read-only-mutable-reference-types) : "Nedeklarujte pouze proměnlivé odkazy typu jen pro čtení."

- V [definici`readonly struct`](#readonly-struct-example)`readonly` označuje, že `struct` je neměnný.
- V [definici člena`readonly`](#readonly-member-examples)`readonly` označuje, že člen `struct` není obdobou vnitřního stavu struktury.
- V [`ref readonly` metoda vrátí](#ref-readonly-return-example)modifikátor `readonly`, že metoda vrátí odkaz a zápisy nejsou pro tento odkaz povoleny.

Do C# 7,2 se přidaly kontexty `readonly sturct` a `ref readonly`. členy `readonly` struktury byly přidány v C# 8,0.

## <a name="readonly-field-example"></a>Příklad pole jen pro čtení

V tomto příkladu nelze hodnotu pole `year` změnit v `ChangeYear`metody, a to i v případě, že je přiřazena hodnota v konstruktoru třídy:

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

`readonly` poli můžete přiřadit hodnotu pouze v následujících kontextech:

- Když je proměnná inicializována v deklaraci, například:

  ```csharp
  public readonly int y = 5;
  ```

- V konstruktoru instance třídy, která obsahuje deklaraci pole instance.
- Ve statickém konstruktoru třídy, která obsahuje deklaraci statického pole.

Tyto kontexty konstruktoru jsou také pouze kontexty, ve kterých je platný pro předání pole `readonly` jako parametr [out](out-parameter-modifier.md) nebo [ref](ref.md) .

> [!NOTE]
> Klíčové slovo `readonly` se liší od klíčového slova [const](const.md) . Pole `const` lze inicializovat pouze v deklaraci pole. Pole `readonly` lze v deklaraci pole a v jakémkoli konstruktoru přiřadit vícekrát. Proto `readonly` pole mohou mít různé hodnoty v závislosti na použitém konstruktoru. I když `const` pole je konstanta při kompilaci, pole `readonly` lze použít pro konstanty za běhu jako v následujícím příkladu:
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

V předchozím příkladu, pokud použijete příkaz jako v následujícím příkladu:

```csharp
p2.y = 66;        // Error
```

zobrazí se chybová zpráva kompilátoru:

`A readonly field cannot be assigned to (except in a constructor or a variable initializer)`

## <a name="readonly-struct-example"></a>Příklad struktury jen pro čtení

Modifikátor `readonly` v definici `struct` deklaruje, že struktura není **proměnlivá**. Každé pole instance `struct` musí být označeno `readonly`, jak je znázorněno v následujícím příkladu:

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyStruct)]

Předchozí příklad používá pro deklaraci svého úložiště [Automatické vlastnosti ReadOnly](../../properties.md#read-only) . Který instruuje kompilátor, aby vytvořil `readonly` pro tyto vlastnosti pole zálohování. Můžete také deklarovat `readonly` pole přímo:

```csharp
public readonly struct Point
{
    public readonly double X;
    public readonly double Y;

    public Point(double x, double y) => (X, Y) = (x, y);

    public override string ToString() => $"({X}, {Y})";
}
```

Přidání pole, které není označeno `readonly` generuje chybu kompilátoru `CS8340`: "pole instancí struktur jen pro čtení musí být jen pro čtení."

## <a name="readonly-member-examples"></a>Příklady členů jen pro čtení

Jindy můžete vytvořit strukturu, která podporuje mutace. V těchto případech některé členy instance nejspíš nemění vnitřní stav struktury. Tyto členy instance můžete deklarovat pomocí modifikátoru `readonly`. Kompilátor vynutil váš záměr. Pokud tento člen mění stav přímo nebo přistupuje ke členu, který není deklarován také pomocí modifikátoru `readonly`, výsledkem je chyba při kompilaci. Modifikátor `readonly` je platný pro členy `struct`, nikoli `class` nebo `interface` deklarace členů.

Pokud použijete modifikátor `readonly` na příslušné `struct` metody, získáte dvě výhody. Co je nejdůležitější, kompilátor vynutil váš záměr. Kód, který mění stav, není platný v metodě `readonly`. Kompilátor může také využít modifikátor `readonly` k povolení optimalizace výkonu. Pokud jsou typy velkých `struct` předány odkazem `in`, kompilátor musí vygenerovat obrannou linií kopii, pokud je možné změnit stav struktury. Pokud jsou k dispozici pouze `readonly` členové, kompilátor nemůže vytvořit kopii obrannou linií.

Modifikátor `readonly` je platný pro většinu členů `struct`, včetně metod, které přepíší metody deklarované v <xref:System.Object?displayProperty=nameWithType>. Existují určitá omezení:

- Nemůžete deklarovat `readonly` statických členů.
- Nelze deklarovat `readonly` konstruktory.

Můžete přidat modifikátor `readonly` k vlastnosti nebo deklaraci indexeru:

```csharp
readonly public int Counter
{
  get { return 0; }
  set {} // not useful, but legal
}
```

Můžete také přidat modifikátor `readonly` k jednotlivým `get` nebo `set` přistupující objekty vlastnosti nebo indexeru:

```csharp
public int Counter
{
  readonly get { return _counter; }
  set { _counter = value; }
}
int _counter;
```

Modifikátor `readonly` nemůžete přidat do vlastnosti i do jedné nebo více z těchto přístupových objektů stejné vlastnosti. Stejné omezení platí i pro indexery.

Kompilátor implicitně aplikuje modifikátor `readonly` na automaticky implementované vlastnosti, kde kód implementovaný kompilátorem nemění stav. Je ekvivalentem následujících deklarací:

```csharp
public readonly int Index { get; }
// Or:
public int Number { readonly get; }
public string Message { readonly get; set; }
``` 

V těchto umístěních můžete přidat modifikátor `readonly`, ale nebude mít žádný smysluplný efekt. Nemůžete přidat modifikátor `readonly` k automatické implementaci vlastnosti setter nebo k automaticky implementované vlastnosti pro čtení a zápis.

## <a name="ref-readonly-return-example"></a>Návratový příklad pro odkaz ReadOnly

Modifikátor `readonly` u `ref return` označuje, že vrácený odkaz nejde upravit. Následující příklad vrátí odkaz na počátek. Používá modifikátor `readonly` k označení, že volající nemohou upravovat původní:

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]
Vrácený typ nemusí být `readonly struct`. Všechny typy, které mohou být vráceny `ref` mohou být vráceny pomocí `ref readonly`.

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

Můžete si také prohlédnout návrhy specifikace jazyka:

- [struktura ReadOnly a ReadOnly](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [Členové struktury jen pro čtení](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Modifikátory](modifiers.md)
- [const](const.md)
- [Pole](../../programming-guide/classes-and-structs/fields.md)
