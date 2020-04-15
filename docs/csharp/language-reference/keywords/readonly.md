---
title: klíčové slovo jen pro čtení – odkaz jazyka C#
ms.date: 04/14/2020
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 03b0aa63eda3e7a9d8745baaa33479fd5e85b01b
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389061"
---
# <a name="readonly-c-reference"></a>readonly – modifikátor (Referenční dokumentace jazyka C#)

Klíčové `readonly` slovo je modifikátor, který lze použít ve čtyřech kontextech:

- V [deklaraci](#readonly-field-example) `readonly` pole označuje, že přiřazení k poli může nastat pouze jako součást deklarace nebo v konstruktoru ve stejné třídě. Pole jen pro čtení lze přiřadit a znovu přiřadit vícekrát v rámci deklarace pole a konstruktoru.
  
  Pole `readonly` nelze přiřadit po ukončení konstruktoru. Toto pravidlo má různé důsledky pro typy hodnot a typy odkazů:
  
  - Vzhledem k tomu, že typy hodnot `readonly` přímo obsahují jejich data, je pole, které je typem hodnoty, neměnné.
  - Vzhledem k tomu, že typy odkazů obsahují `readonly` odkaz na jejich data, pole, které je typem odkazu, musí vždy odkazovat na stejný objekt. Ten objekt není neměnný. Modifikátor `readonly` zabraňuje nahrazení pole jinou instancí typu odkazu. Modifikátor však nezabrání změně dat instance pole prostřednictvím pole jen pro čtení.

  > [!WARNING]
  > Externě viditelný typ, který obsahuje externě viditelné pole jen pro čtení, které je proměnlivým typem odkazu, může být chybou zabezpečení a může vyvolat upozornění [CA2104](/visualstudio/code-quality/ca2104) : "Nedeklarujte proměnlivé typy odkazů pouze pro čtení."

- V `readonly struct` definici `readonly` typu označuje, že typ struktury je neměnný. Další informace naleznete [ `readonly` v](../builtin-types/struct.md#readonly-struct) části struktura [typy struktury](../builtin-types/struct.md) článku.
- V deklaraci instance člen v `readonly` rámci typu struktury označuje, že člen instance nemění stav struktury. Další informace naleznete [ `readonly` ](../builtin-types/struct.md#readonly-instance-members) v části členové instance v článku [Typy struktury.](../builtin-types/struct.md)
- V [ `ref readonly` metodě](#ref-readonly-return-example)return `readonly` modifikátor označuje, že metoda vrátí odkaz a zápisy nejsou povoleny pro tento odkaz.

A `readonly struct` `ref readonly` kontexty byly přidány v C# 7.2. `readonly`členové struktury byli přidáni do jazyka C# 8.0

## <a name="readonly-field-example"></a>Příklad pole jen pro čtení

V tomto příkladu nelze `year` hodnotu pole změnit v `ChangeYear`metodě , i když je přiřazena hodnota v konstruktoru třídy:

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

Hodnotu `readonly` poli můžete přiřadit pouze v následujících kontextech:

- Když je proměnná inicializována v deklaraci, například:

  ```csharp
  public readonly int y = 5;
  ```

- V instanci konstruktor třídy, která obsahuje deklaraci pole instance.
- Ve statickém konstruktoru třídy, která obsahuje deklaraci statického pole.

Tyto kontexty konstruktoru jsou také pouze kontexty, ve `readonly` kterých je platný předat pole jako [out](out-parameter-modifier.md) nebo [ref](ref.md) parametr.

> [!NOTE]
> Klíčové `readonly` slovo se liší od klíčového slova [const.](const.md) Pole `const` lze inicializovat pouze při deklaraci tohoto pole. Pole `readonly` lze přiřadit vícekrát v deklaraci pole a v libovolném konstruktoru. `readonly` Pole proto mohou mít různé hodnoty v závislosti na použitém konstruktoru. Také zatímco `const` pole je konstanta v `readonly` době kompilace, pole lze použít pro konstanty za běhu jako v následujícím příkladu:
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

V předchozím příkladu, pokud použijete příkaz, jako je následující příklad:

```csharp
p2.y = 66;        // Error
```

zobrazí se chybová zpráva kompilátoru:

**Pole jen pro čtení nelze přiřadit (s výjimkou konstruktoru nebo proměnné inicializátoru)**

## <a name="ref-readonly-return-example"></a>Příklad vrácení pouze pro čtení od odkazu

Modifikátor `readonly` `ref return` na označuje, že vrácený odkaz nelze změnit. Následující příklad vrátí odkaz na původ. Používá `readonly` modifikátor k označení, že volající nelze změnit původ:

[!code-csharp[readonly return example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]

Vrácený typ nemusí být `readonly struct`. Libovolný typ, který `ref` může být `ref readonly`vrácena může být vrácena .

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

Můžete také zobrazit návrhy specifikace jazyka:

- [pouze pro čtení ref a jen pro čtení struct](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [jedině pro čtení členové struktury](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](index.md)
- [Modifikátory](index.md)
- [const](const.md)
- [Pole](../../programming-guide/classes-and-structs/fields.md)
