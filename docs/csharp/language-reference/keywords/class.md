---
title: klíčové slovo třídy – odkaz jazyka C#
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: 500160d3bc9280b866e5f5ba24c5edc623e752c1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77673092"
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

V c#. Jinými slovy, třída může dědit implementaci pouze z jedné základní třídy. Třída však může implementovat více než jedno rozhraní. V následující tabulce jsou uvedeny příklady dědičnosti třídy a implementace rozhraní:

|Dědičnost|Příklad|
|-----------------|-------------|
|Žádný|`class ClassA { }`|
|Single|`class DerivedClass : BaseClass { }`|
|Žádné, implementuje dvě rozhraní|`class ImplClass : IFace1, IFace2 { }`|
|Jediné, implementuje jedno rozhraní|`class ImplDerivedClass : BaseClass, IFace1 { }`|

Třídy, které deklarujete přímo v oboru názvů, nikoli vnořené do jiných tříd, mohou být [veřejné](./public.md) nebo [interní](./internal.md). Třídy `internal` jsou ve výchozím nastavení.

Členové třídy, včetně vnořených tříd, mohou být [veřejné](public.md), [chráněné vnitřní](protected-internal.md), [chráněné](protected.md), [interní](internal.md), [soukromé](private.md)nebo [soukromé chráněné](private-protected.md). Členové `private` jsou ve výchozím nastavení.

Další informace naleznete [v tématu Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).

Můžete deklarovat obecné třídy, které mají parametry typu. Další informace naleznete [v tématu Obecné třídy](../../programming-guide/generics/generic-classes.md).

Třída může obsahovat deklarace následujících členů:

- [Konstruktory](../../programming-guide/classes-and-structs/constructors.md)

- [Konstanty](../../programming-guide/classes-and-structs/constants.md)

- [Pole](../../programming-guide/classes-and-structs/fields.md)

- [Finalizační metody](../../programming-guide/classes-and-structs/destructors.md)

- [Metody](../../programming-guide/classes-and-structs/methods.md)

- [Vlastnosti](../../programming-guide/classes-and-structs/properties.md)

- [Indexery](../../programming-guide/indexers/index.md)

- [Operátory](../operators/index.md)

- [Akce](../../programming-guide/events/index.md)

- [Delegáty](../../programming-guide/delegates/index.md)

- [Třídy](../../programming-guide/classes-and-structs/classes.md)

- [Rozhraní](../../programming-guide/interfaces/index.md)

- [Typy struktur](../builtin-types/struct.md)

- [Typy výčtu](../builtin-types/enum.md)

## <a name="example"></a>Příklad

Následující příklad ukazuje deklarování polí třídy, konstruktorů a metod. Také ukazuje instanciontace objektu a tisk instancí dat. V tomto příkladu jsou deklarovány dvě třídy. První třída `Child`, obsahuje dvě`name` soukromá pole ( a `age`), dva veřejné konstruktory a jednu veřejnou metodu. Druhá třída `StringTest`, se používá `Main`k obsahují .

[!code-csharp[csrefKeywordsTypes#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#5)]

## <a name="comments"></a>Komentáře

Všimněte si, že v`name` předchozím `age`příkladu soukromé pole ( a `Child` ) lze přistupovat pouze prostřednictvím veřejné metody třídy. Například nelze vytisknout název dítěte, z `Main` metody, pomocí příkazu, jako je tento:

```csharp
Console.Write(child1.name);   // Error
```

Přístup k soukromým `Child` `Main` členům z `Main` by bylo možné pouze v případě, že by byli členy třídy.

Typy deklarované uvnitř třídy `private`bez modifikátoru přístupu `private` ve výchozím nastavení , takže datové členy v tomto příkladu by stále bylo, pokud klíčové slovo byly odebrány.

Nakonec si všimněte, že pro objekt vytvořený`child3`pomocí `age` konstruktoru bez parametrů ( ), bylo pole ve výchozím nastavení inicializováno na nulu.

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](./index.md)
- [Odkazové typy](./reference-types.md)
