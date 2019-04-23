---
title: Class – klíčové slovo - C# odkaz
ms.custom: seodec18
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: fbb685abcc5c2e79a64501385edf8f6c2041861d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59974893"
---
# <a name="class-c-reference"></a>class (Referenční dokumentace jazyka C#)

Třídy jsou deklarované pomocí klíčového slova `class`, jak je znázorněno v následujícím příkladu:

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates
    // and nested classes go here.
}
```

## <a name="remarks"></a>Poznámky

V jazyce C# je povolena pouze jedna dědičnost. Jinými slovy třída může dědit implementace z pouze jednu základní třídu. Nicméně třída může implementovat více než jedno rozhraní. Následující tabulka uvádí příklady dědičnost třídy a implementace rozhraní:

|Dědičnost|Příklad|
|-----------------|-------------|
|Žádné|`class ClassA { }`|
|Single|`class DerivedClass: BaseClass { }`|
|NONE, implementuje dvě rozhraní|`class ImplClass: IFace1, IFace2 { }`|
|Jediné, jedno rozhraní implementuje|`class ImplDerivedClass: BaseClass, IFace1 { }`|

Třídy, které deklarujete přímo v rámci oboru názvů, ne vnořené v rámci jiné třídy, může být buď [veřejné](../../../csharp/language-reference/keywords/public.md) nebo [interní](../../../csharp/language-reference/keywords/internal.md). Třídy jsou `internal` ve výchozím nastavení.

Členy třídy, včetně vnořené třídy, může být [veřejné](public.md), [interní chráněné](protected-internal.md), [chráněné](protected.md), [interní](internal.md), [ privátní](private.md), nebo [private, protected](private-protected.md). Jsou členové `private` ve výchozím nastavení.

Další informace najdete v tématu [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).

Je možné deklarovat obecných tříd, které má parametry typu. Další informace najdete v tématu [obecné třídy](../../../csharp/programming-guide/generics/generic-classes.md).

Třída může obsahovat deklarace následující členy:

- [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)

- [Konstanty](../../../csharp/programming-guide/classes-and-structs/constants.md)

- [Pole](../../../csharp/programming-guide/classes-and-structs/fields.md)

- [Finalizační metody](../../../csharp/programming-guide/classes-and-structs/destructors.md)

- [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)

- [Vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)

- [Indexery](../../../csharp/programming-guide/indexers/index.md)

- [Operátory](../../../csharp/programming-guide/statements-expressions-operators/operators.md)

- [Události](../../../csharp/programming-guide/events/index.md)

- [Delegáti](../../../csharp/programming-guide/delegates/index.md)

- [Třídy](../../../csharp/programming-guide/classes-and-structs/classes.md)

- [Rozhraní](../../../csharp/programming-guide/interfaces/index.md)

- [Struktury](../../../csharp/programming-guide/classes-and-structs/structs.md)

- [Výčty](../../../csharp/programming-guide/enumeration-types.md)

## <a name="example"></a>Příklad

Následující příklad ukazuje deklarující polí tříd, konstruktory a metody. Také ukazuje vytvoření instance objektu a tisk data instance. V tomto příkladu dvě třídy jsou deklarované. První třída `Child`, obsahuje dvě soukromé pole (`name` a `age`), dvě veřejné konstruktory a jednu veřejnou metodu. Druhá třída `StringTest`, se používá pro jiné `Main`.

[!code-csharp[csrefKeywordsTypes#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#5)]

## <a name="comments"></a>Komentáře

Všimněte si, že v předchozím příkladu privátní pole (`name` a `age`) lze přistupovat pouze prostřednictvím veřejné metody `Child` třídy. Například nelze tisknout název podřízené tabulky z `Main` metodu, pomocí příkazu takto:

```csharp
Console.Write(child1.name);   // Error
```

Přístup k soukromým členům `Child` z `Main` pouze by bylo možné Pokud `Main` byly člena třídy.

Typy deklarované uvnitř třídy bez výchozí modifikátor přístupu `private`, takže datových členů v tomto příkladu bude stále `private` Pokud klíčové slovo byly odebrány.

A konečně, Všimněte si, že pro objekt vytvořený pomocí konstruktoru bez parametrů (`child3`), `age` pole byla inicializována na nulovou hodnotu ve výchozím nastavení.

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)
- [Odkazové typy](../../../csharp/language-reference/keywords/reference-types.md)
