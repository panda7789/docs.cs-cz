---
title: klíčové slovo jen pro čtení – odkaz jazyka C#
ms.date: 03/26/2020
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 344d5e54fcd500e283c52fa7953c6366823f13f0
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345153"
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
- V [ `readonly` definici](#readonly-member-examples) `readonly` člena označuje, že `struct` člen člena struktury vnitřní stav.
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

## <a name="readonly-member-examples"></a>Příklady členů pouze pro Čtení

Jindy můžete vytvořit strukturu, která podporuje mutaci. V těchto případech několik členů instance pravděpodobně nezmění vnitřní stav struktury. Tyto členy instance můžete `readonly` deklarovat pomocí modifikátoru. Kompilátor vynucuje váš záměr. Pokud tento člen upraví stav přímo nebo přistupuje k `readonly` členu, který není také deklarován s modifikátorem, výsledkem je chyba v době kompilace. Modifikátor `readonly` je `struct` platný `class` pro `interface` členy, nikoli nebo deklarace členů.

Můžete získat dvě výhody `readonly` použitím modifikátoru na příslušné `struct` metody. A co je nejdůležitější, kompilátor vynucuje váš záměr. Kód, který upravuje stav není platný `readonly` v metodě. Kompilátor může také použít `readonly` modifikátor povolit optimalizace výkonu. Při `struct` velké typy `in` jsou předány odkazem, kompilátor musí generovat obrannou kopii, pokud stav struktury může být změněn. Pokud `readonly` jsou přístupné pouze členy, kompilátor nemusí vytvořit obrannou kopii.

Modifikátor `readonly` je platný pro `struct`většinu členů , včetně <xref:System.Object?displayProperty=nameWithType>metod, které přepsat metody deklarované v . Existují určitá omezení:

- Nelze deklarovat `readonly` statické metody nebo vlastnosti.
- Nelze deklarovat `readonly` konstruktory.

`readonly` Modifikátor můžete přidat do deklarace vlastnosti nebo indexeru:

```csharp
readonly public int Counter
{
  get { return 0; }
  set {} // not useful, but legal
}
```

Můžete také přidat `readonly` modifikátor pro jednotlivé `get` nebo `set` přistupující objekty vlastnosti nebo indexeru:

```csharp
public int Counter
{
  readonly get { return _counter; }
  set { _counter = value; }
}
int _counter;
```

`readonly` Modifikátor nesmíte přidat do vlastnosti a jednoho nebo více přístupových objektů stejné vlastnosti. Stejné omezení platí pro indexery.

Kompilátor implicitně použije `readonly` modifikátor na automaticky implementované vlastnosti, kde kompilátor implementovaný kód nemění stav. Je to ekvivalentní následujícím prohlášením:

```csharp
public readonly int Index { get; }
// Or:
public int Number { readonly get; }
public string Message { readonly get; set; }
```

`readonly` Modifikátor můžete přidat v těchto umístěních, ale nebude mít žádný smysluplný účinek. `readonly` Modifikátor nesmíte přidat do automaticky implementovaného nastavení vlastností nebo do automaticky implementované vlastnosti pro čtení a zápis.

## <a name="ref-readonly-return-example"></a>Příklad vrácení pouze pro čtení od odkazu

Modifikátor `readonly` `ref return` na označuje, že vrácený odkaz nelze změnit. Následující příklad vrátí odkaz na původ. Používá `readonly` modifikátor k označení, že volající nelze změnit původ:

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]

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
