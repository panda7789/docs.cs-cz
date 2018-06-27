---
title: Class – klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: 04e64e825e4297ceb432393c7bd145a6cf4fcb2c
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948508"
---
# <a name="class-c-reference"></a>class (Referenční dokumentace jazyka C#)

Třídy jsou deklarovány pomocí klíčového slova `class`, jak je znázorněno v následujícím příkladu:

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates
    // and nested classes go here.
}
```

## <a name="remarks"></a>Poznámky

V jazyce C# je povolena pouze jedna dědičnost. Třída jinými slovy, můžete implementace dědí pouze jeden základní třídy. Třída, však může implementovat více než jedno rozhraní. V následující tabulce jsou uvedeny příklady dědičnosti tříd a implementace rozhraní:

|Dědičnost|Příklad|
|-----------------|-------------|
|Žádné|`class ClassA { }`|
|Single|`class DerivedClass: BaseClass { }`|
|NONE, implementuje dvě rozhraní|`class ImplClass: IFace1, IFace2 { }`|
|Jedinou implementuje jedno rozhraní|`class ImplDerivedClass: BaseClass, IFace1 { }`|

Třídy, které je deklarovat přímo v rámci oboru názvů, nejsou vnořené v rámci jiné třídy, může být buď [veřejné](../../../csharp/language-reference/keywords/public.md) nebo [interní](../../../csharp/language-reference/keywords/internal.md). Třídy jsou `internal` ve výchozím nastavení.

Členy třídy, včetně vnořené třídy, může být [veřejné](../../../csharp/language-reference/keywords/public.md), `protected internal`, [chráněné](../../../csharp/language-reference/keywords/protected.md), [interní](../../../csharp/language-reference/keywords/internal.md), [privátní](../../../csharp/language-reference/keywords/private.md), nebo `private protected`. Členy jsou [privátní](../../../csharp/language-reference/keywords/private.md) ve výchozím nastavení.

Další informace najdete v tématu [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).

Obecné třídy, které mají parametry typu můžou deklarovat. Další informace najdete v tématu [obecné třídy](../../../csharp/programming-guide/generics/generic-classes.md).

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

## <a name="example"></a>Příklad

Následující příklad ukazuje deklarující třída polí, konstruktorů a metod. Také ukazuje vytvoření instance objektu a tisk data instance. V tomto příkladu jsou deklarovány dvou tříd. První třída `Child`, obsahuje dva privátní polí (`name` a `age`), dvě veřejné konstruktory a jedna veřejná metoda. Druhé třídy `StringTest`, se používá pro jiné `Main`.

[!code-csharp[csrefKeywordsTypes#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#5)]

## <a name="comments"></a>Komentáře

Všimněte si, že se v předchozím příkladu privátním polím (`name` a `age`) lze přistupovat pouze prostřednictvím veřejné metody `Child` třídy. Její název, například nelze tisknout z `Main` metodu, pomocí příkazu takto:

```csharp
Console.Write(child1.name);   // Error
```

Přístup ke členům privátní `Child` z `Main` pouze by bylo možné Pokud `Main` byly člena třídy.

Typy deklarovat uvnitř třídu bez výchozí modifikátor přístupu k `private`, takže stále datových členů v tomto příkladu by `private` Pokud klíčové slovo byly odebrány.

Nakonec, Všimněte si, že pro objekt vytvořený pomocí výchozího konstruktoru (`child3`), pole byla inicializována tak, aby stáří nula ve výchozím nastavení.

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
[Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
[Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
[Odkazové typy](../../../csharp/language-reference/keywords/reference-types.md)