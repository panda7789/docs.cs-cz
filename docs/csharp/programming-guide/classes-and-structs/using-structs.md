---
title: Using Structs - C# Programming Guide
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], using
ms.assetid: cea4a459-9eb9-442b-8d08-490e0797ba38
ms.openlocfilehash: 491ee0224ffa39262992f7f42d20e5f97560b73f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429496"
---
# <a name="using-structs-c-programming-guide"></a>Using structs (C# Programming Guide)

The `struct` type is suitable for representing lightweight objects such as `Point`, `Rectangle`, and `Color`. Although it is just as convenient to represent a point as a [class](../../language-reference/keywords/class.md) with [Auto-Implemented Properties](./auto-implemented-properties.md), a [struct](../../language-reference/keywords/struct.md) might be more efficient in some scenarios. For example, if you declare an array of 1000 `Point` objects, you will allocate additional memory for referencing each object; in this case, a struct would be less expensive. Because .NET already contains an object called <xref:System.Drawing.Point>, the struct in this example is named `Coords` instead.

[!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]

It is an error to define a parameterless constructor for a struct. It is also an error to initialize an instance field in a struct body. You can initialize externally accessible struct members only by using a parameterized constructor, the implicit, parameterless constructor, an [object initializer](object-and-collection-initializers.md), or by accessing the members individually after the struct is declared. Any private or otherwise inaccessible members require the use of constructors exclusively.

When you create a struct object using the [new](../../language-reference/operators/new-operator.md) operator, it gets created and the appropriate constructor is called according to the [constructor's signature](constructors.md#constructor-syntax). Unlike classes, structs can be instantiated without using the `new` operator. In such a case, there is no constructor call, which makes the allocation more efficient. However, the fields will remain unassigned and the object cannot be used until all of the fields are initialized. This includes the inability to get or set values through properties.

If you instantiate a struct object using the parameterless constructor, all members are assigned according to their [default values](../../language-reference/keywords/default-values-table.md).

When writing a constructor with parameters for a struct, you must explicitly initialize all members; otherwise one or more members remain unassigned and the struct cannot be used, producing compiler error [CS0171](../../misc/cs0171.md).

There is no inheritance for structs as there is for classes. A struct cannot inherit from another struct or class, and it cannot be the base of a class. Structs, however, inherit from the base class <xref:System.Object>. A struct can implement interfaces, and it does that exactly as classes do.

You cannot declare a class using the keyword `struct`. In C#, classes and structs are semantically different. A struct is a value type, while a class is a reference type. For more information, see [Value types](../../language-reference/keywords/value-types.md) and [Reference types](../../language-reference/keywords/reference-types.md).

Unless you need reference-type semantics, a small class may be more efficiently handled by the system if you declare it as a struct instead.

## <a name="example-1"></a>Příklad 1

This example demonstrates `struct` initialization using both parameterless and parameterized constructors.

[!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]

[!code-csharp[csProgGuideObjects#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#2)]

## <a name="example-2"></a>Příklad 2

This example demonstrates a feature that is unique to structs. It creates a Coords object without using the `new` operator. If you replace the word `struct` with the word `class`, the program will not compile.

[!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]

[!code-csharp[csProgGuideObjects#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#3)]

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Třídy a struktury](index.md)
- [Struktury](structs.md)
