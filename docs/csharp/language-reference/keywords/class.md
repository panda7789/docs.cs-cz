---
description: klíčové slovo class – Referenční dokumentace jazyka C#
title: klíčové slovo class – Referenční dokumentace jazyka C#
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: 67c9c4be55cce25edf9ecb84b257a8523f193bec
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142112"
---
# <a name="class-c-reference"></a>class (Referenční dokumentace jazyka C#)

Třídy jsou deklarovány pomocí klíčového slova `class` , jak je znázorněno v následujícím příkladu:

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates
    // and nested classes go here.
}
```

## <a name="remarks"></a>Poznámky

V jazyce C# je povolena pouze jedna dědičnost. Jinými slovy třída může dědit pouze implementaci pouze z jedné základní třídy. Třída však může implementovat více než jedno rozhraní. V následující tabulce jsou uvedeny příklady dědičnosti tříd a implementace rozhraní:

|Dědičnost|Příklad|
|-----------------|-------------|
|Žádné|`class ClassA { }`|
|Jednoduché|`class DerivedClass : BaseClass { }`|
|Žádné, implementuje dvě rozhraní|`class ImplClass : IFace1, IFace2 { }`|
|Single, implementuje jedno rozhraní.|`class ImplDerivedClass : BaseClass, IFace1 { }`|

Třídy, které deklarujete přímo v rámci oboru názvů, nikoli vnořené v rámci jiných tříd, mohou být buď [veřejné](./public.md) , nebo [interní](./internal.md). Třídy jsou `internal` ve výchozím nastavení.

Členy třídy, včetně vnořených tříd, mohou být [Veřejná](public.md), [chráněná interní](protected-internal.md), [chráněná](protected.md), [interní](internal.md), [soukromá](private.md)nebo [soukromá](private-protected.md). Členy jsou `private` ve výchozím nastavení.

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

- [Typy struktur](../builtin-types/struct.md)

- [Výčtové typy](../builtin-types/enum.md)

## <a name="example"></a>Příklad

Následující příklad ukazuje deklaraci polí třídy, konstruktorů a metod. Ukazuje také vytváření instancí objektů a data instance tisku. V tomto příkladu jsou deklarovány dvě třídy. První třída `Child` obsahuje dvě soukromá pole ( `name` a `age` ), dva veřejné konstruktory a jednu veřejnou metodu. Druhá třída, `StringTest` ,,, je použita k zahrnutí `Main` .

[!code-csharp[csrefKeywordsTypes#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#5)]

## <a name="comments"></a>Komentáře

Všimněte si, že v předchozím příkladu k soukromým polím ( `name` a `age` ) lze přistupovat pouze prostřednictvím veřejné metody `Child` třídy. Nemůžete například vytisknout název podřízeného objektu z `Main` metody pomocí příkazu, například takto:

```csharp
Console.Write(child1.name);   // Error
```

Přístup k soukromým členům `Child` z `Main` by byl možný pouze v případě, že `Main` byl členem třídy.

Typy deklarované uvnitř třídy bez modifikátoru přístupu výchozí pro `private` , takže datové členy v tomto příkladu budou pořád i v `private` případě, že se klíčové slovo odebralo.

Nakonec si všimněte, že pro objekt vytvořený pomocí konstruktoru bez parametrů ( `child3` ) `age` bylo ve výchozím nastavení inicializováno pole nula.

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](./index.md)
- [Typy odkazů](./reference-types.md)
