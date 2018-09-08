---
title: Výrazy s výchozími hodnotami (C# Programming Guide)
description: Výrazy s výchozími hodnotami vytvořit výchozí hodnotu pro libovolný typ odkazu nebo typ hodnoty
ms.date: 04/25/2018
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
ms.openlocfilehash: 94866f22fb3ad921a834cffb16fe17e44cef5965
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44222289"
---
# <a name="default-value-expressions-c-programming-guide"></a>výrazy s výchozími hodnotami (C# programovací příručka)

Výraz výchozí hodnoty `default(T)` vytvoří výchozí hodnota typu `T`. V následující tabulce jsou uvedeny hodnoty, které jsou vytvořeny pro různé typy:

|Typ|Výchozí hodnota|
|---------|---------|
|jakéhokoliv odkazového typu|`null`|
|Zadejte číselnou hodnotu|Nula|
|[bool](../../language-reference/keywords/bool.md)|`false`|
|[char](../../language-reference/keywords/char.md)|`'\0'`|
|[enum](../../language-reference/keywords/enum.md)|Hodnota vytvořený podle výrazu `(E)0`, kde `E` je identifikátor výčtu.|
|[struct](../../language-reference/keywords/struct.md)|Hodnotu vytvořenou testovaným nastavení všechny hodnoty pole na výchozí hodnoty a všechny odkazují na typ pole na `null`.|
|Typ s možnou hodnotou Null|Instance, pro kterou <xref:System.Nullable%601.HasValue%2A> vlastnost `false` a <xref:System.Nullable%601.Value%2A> vlastnost není definována.|

Výrazy s výchozími hodnotami jsou zvláště užitečné při obecné třídy a metody. Jedním problémem, který nastane použití obecných typů je výchozí hodnota parametry typu přiřazení `T` Pokud neznáte následující předem:

- Zda `T` je typem odkazu nebo hodnotového typu.
- Pokud `T` je typ hodnoty, ať už se jedná o číselnou hodnotu nebo strukturu.

 Zadané proměnné `t` parametry typu `T`, příkaz `t = null` je platná pouze pokud `T` je typem odkazu. Přiřazení `t = 0` funguje jenom u typů číselnou hodnotu, ale nikoli pro struktury. Chcete-li to vyřešit, použijte výraz výchozí hodnoty:

```csharp
T t = default(T);
```

`default(T)` Výraz není omezena pouze na obecné třídy a metody. Výrazy s výchozími hodnotami lze použít s žádným typem spravované. Platné jsou některé z těchto výrazů:

 [!code-csharp[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]

 Následující příklad z `GenericList<T>` třídy ukazuje způsob použití `default(T)` operátor v obecné třídě. Další informace najdete v tématu [Úvod do obecných typů](../generics/introduction-to-generics.md).

 [!code-csharp[csProgGuideGenerics#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#Snippet41)]

## <a name="default-literal-and-type-inference"></a>Výchozí literál a odvození typu

Od verze C# 7.1, `default` literal lze použít pro výrazy s výchozími hodnotami, pokud kompilátor může odvodit typ výrazu. `default` Literál vytvoří stejnou hodnotu jako odpovídající `default(T)` kde `T` je odvozený typ. To lze díky kód stručnější snižují redundanci deklarování typu více než jednou. `default` Literál je možné v některém z následujících umístění:

- Inicializátor proměnné.
- přiřazení proměnné
- deklarování výchozí hodnota volitelného parametru
- poskytuje hodnoty pro argument volání metody
- návratový příkaz (nebo výrazu v vozidlo člen typu výrazu)

Následující příklad ukazuje mnoho použití `default` literál ve výrazu výchozí hodnoty:

[!code-csharp[csProgGuideGenerics#3](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-literal.cs)]

## <a name="see-also"></a>Viz také

- <xref:System.Collections.Generic>  
- [Průvodce programováním v jazyce C#](../index.md)  
- [Obecné typy (C# Programming Guide)](../generics/index.md)  
- [Obecné metody](../generics/generic-methods.md)  
- [Obecné typy v .NET](~/docs/standard/generics/index.md)  
- [Tabulka výchozích hodnot](../../language-reference/keywords/default-values-table.md)
