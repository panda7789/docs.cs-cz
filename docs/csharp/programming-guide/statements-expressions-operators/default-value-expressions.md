---
title: Výchozí hodnota výrazy (C# programování průvodce)
description: Výchozí hodnota výrazy vytvořit výchozí hodnota pro všechny odkaz na typ nebo typ hodnoty
ms.date: 04/25/2018
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
ms.openlocfilehash: be51ad253a2939f538144caf4500f39e144c1664
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="default-value-expressions-c-programming-guide"></a>Výchozí hodnota výrazy (C# programovací průvodce)

Výraz výchozí hodnoty `default(T)` vytvoří výchozí hodnota typu `T`. V následující tabulce jsou uvedeny hodnoty, které vytváří pro různé typy:

|Typ|Výchozí hodnota|
|---------|---------|
|žádný odkaz na typ|`null`|
|Typ číselné hodnoty|Nula|
|[bool](../../language-reference/keywords/bool.md)|`false`|
|[char](../../language-reference/keywords/char.md)|`'\0'`|
|[enum](../../language-reference/keywords/enum.md)|Hodnota vyprodukované výraz `(E)0`, kde `E` je identifikátor výčtu.|
|[struct](../../language-reference/keywords/struct.md)|Hodnota vyprodukované nastavení všechny hodnoty typu pole na jejich výchozí hodnoty a všechny odkazovat typ pole k `null`.|
|Typ s možnou hodnotou Null|Instance pro kterou <xref:System.Nullable%601.HasValue%2A> vlastnost je `false` a <xref:System.Nullable%601.Value%2A> vlastnosti není definován.|

Výchozí hodnota výrazy jsou užitečné zejména v obecné třídy a metody. Tom, jak přiřadit výchozí hodnotu parametrizované typu je jedním z problémů často vyvstává použití obecných typů `T` Pokud nevíte, následující předem:

- Jestli `T` odkazového typu nebo typ hodnoty.
- Pokud `T` je typ hodnoty, zda je číselná hodnota nebo struktury.

 Zadané proměnné `t` parametrizované typu `T`, příkaz `t = null` je platná pouze v případě `T` typem je odkaz. Přiřazení `t = 0` funguje pouze pro typy číselnou hodnotu, ale ne pro struktury. K řešení, které, použijte výraz výchozí hodnoty:

```csharp
T t = default(T);
```

`default(T)` Výraz není omezen na obecné třídy a metody. Výchozí hodnota výrazy lze použít všechny spravovaného typu. Platné jsou některé z těchto výrazů:

 [!code-csharp[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]

 Následující příklad z `GenericList<T>` třída ukazuje způsob použití `default(T)` operátor v obecné třídy. Další informace najdete v tématu [Úvod do obecných typů](../generics/introduction-to-generics.md).

 [!code-csharp[csProgGuideGenerics#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#Snippet41)]

## <a name="default-literal-and-type-inference"></a>Výchozí literálu a odvození typu

Od verze jazyka C# 7.1, `default` literál lze použít pro výchozí hodnotu výrazy při kompilátor lze odvodit typ výrazu. `default` Literál vytváří stejnou hodnotu jako ekvivalentní `default(T)` kde `T` je odvozeném typu. To můžete provést kód přesnější snížením redundance deklarování typu více než jednou. `default` Literál lze použít v některém z následujících umístění:

- Inicializátor proměnné
- přiřazení proměnné
- Výchozí hodnota pro volitelný parametr deklarace
- poskytnutí hodnota pro argument volání – metoda
- vrátí příkaz (nebo výraz v vozidlo člen výrazu)

Následující příklad ukazuje použití mnoha `default` literálu ve výrazu výchozí hodnota:

[!code-csharp[csProgGuideGenerics#3](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-literal.cs)]

## <a name="see-also"></a>Viz také

 <xref:System.Collections.Generic>  
 [Průvodce programováním v jazyce C#](../index.md)  
 [Obecné typy (C# Průvodce programováním)](../generics/index.md)  
 [Obecné metody](../generics/generic-methods.md)  
 [Obecné typy v rozhraní .NET](~/docs/standard/generics/index.md)  
 [Tabulka výchozích hodnot](../../language-reference/keywords/default-values-table.md)
