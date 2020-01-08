---
title: klíčové slovo třídy C# – referenční informace
ms.custom: seodec18
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: 61f15550482e8499e57197e35970e7ec8a096947
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345508"
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

V C#je povolena pouze jedna dědičnost. Jinými slovy třída může dědit pouze implementaci pouze z jedné základní třídy. Třída však může implementovat více než jedno rozhraní. V následující tabulce jsou uvedeny příklady dědičnosti tříd a implementace rozhraní:

|Dědičnost|Příklad|
|-----------------|-------------|
|Žádné|`class ClassA { }`|
|Jednoduché|`class DerivedClass: BaseClass { }`|
|Žádné, implementuje dvě rozhraní|`class ImplClass: IFace1, IFace2 { }`|
|Single, implementuje jedno rozhraní.|`class ImplDerivedClass: BaseClass, IFace1 { }`|

Třídy, které deklarujete přímo v rámci oboru názvů, nikoli vnořené v rámci jiných tříd, mohou být buď [veřejné](./public.md) , nebo [interní](./internal.md). Třídy jsou ve výchozím nastavení `internal`.

Členy třídy, včetně vnořených tříd, mohou být [Veřejná](public.md), [chráněná interní](protected-internal.md), [chráněná](protected.md), [interní](internal.md), [soukromá](private.md)nebo [soukromá](private-protected.md). Ve výchozím nastavení jsou členy `private`.

Další informace najdete v tématu [modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md).

Můžete deklarovat obecné třídy, které mají parametry typu. Další informace naleznete v tématu [Obecné třídy](../../programming-guide/generics/generic-classes.md).

Třída může obsahovat deklarace následujících členů:

- [Konstruktory](../../programming-guide/classes-and-structs/constructors.md)

- [Konstanty](../../programming-guide/classes-and-structs/constants.md)

- [Pole](../../programming-guide/classes-and-structs/fields.md)

- [Finalizační metody](../../programming-guide/classes-and-structs/destructors.md)

- [Metody](../../programming-guide/classes-and-structs/methods.md)

- [Vlastnosti](../../programming-guide/classes-and-structs/properties.md)

- [Indexery](../../programming-guide/indexers/index.md)

- [Operátory](../operators/index.md)

- [Události](../../programming-guide/events/index.md)

- [Delegáti](../../programming-guide/delegates/index.md)

- [Třídy](../../programming-guide/classes-and-structs/classes.md)

- [Rozhraní](../../programming-guide/interfaces/index.md)

- [Struktury](../../programming-guide/classes-and-structs/structs.md)

- [Výčty](../builtin-types/enum.md)

## <a name="example"></a>Příklad

Následující příklad ukazuje deklaraci polí třídy, konstruktorů a metod. Ukazuje také vytváření instancí objektů a data instance tisku. V tomto příkladu jsou deklarovány dvě třídy. První třída, `Child`, obsahuje dvě soukromá pole (`name` a `age`), dva veřejné konstruktory a jedna veřejná metoda. Druhá třída, `StringTest`, slouží k zahrnutí `Main`.

[!code-csharp[csrefKeywordsTypes#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#5)]

## <a name="comments"></a>Komentáře

Všimněte si, že v předchozím příkladu mohou být soukromá pole (`name` a `age`) dostupná pouze prostřednictvím veřejné metody třídy `Child`. Nemůžete například vytisknout název podřízeného objektu z metody `Main` pomocí příkazu podobného tomuto:

```csharp
Console.Write(child1.name);   // Error
```

Přístup k soukromým členům `Child` z `Main` by byl možný pouze v případě, že `Main` byly členem třídy.

Typy deklarované uvnitř třídy bez modifikátoru přístupu `private`výchozí, takže datové členy v tomto příkladu budou nadále `private`, pokud bylo klíčové slovo odebráno.

Nakonec si všimněte, že pro objekt vytvořený pomocí konstruktoru bez parametrů (`child3`) se ve výchozím nastavení `age` pole inicializoval jako nula.

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](./index.md)
- [Odkazové typy](./reference-types.md)
