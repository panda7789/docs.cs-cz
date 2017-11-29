---
title: "Výchozí hodnota výrazy (C# programování průvodce)"
description: "Výchozí hodnota výrazy vytvořit výchozí hodnota pro všechny odkaz na typ nebo typ hodnoty"
ms.date: 08/23/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
ms.assetid: b9daf449-4e64-496e-8592-6ed2c8875a98
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c2bb1c269e5347d615c47ab828506aef538c4761
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="default-value-expressions-c-programming-guide"></a>Výchozí hodnota výrazy (C# programovací průvodce)

Výraz výchozí hodnoty vytvoří výchozí hodnota pro typ. Výchozí hodnota výrazy jsou užitečné zejména v obecné třídy a metody. Jak přiřadit výchozí hodnotu typu parametrizované je jedním z problémů často vyvstává použití obecných typů `T` Pokud si nejste jisti následující předem:

- Jestli `T` odkazového typu nebo typ hodnoty.
- Pokud `T` je typ hodnoty, zda je číselná hodnota nebo struktury definovaný uživatelem.

 Zadané proměnné `t` parametrizované typu `T`, příkaz `t = null` je platná pouze v případě `T` typem je odkaz. Přiřazení `t = 0` funguje pouze pro typy číselnou hodnotu, ale ne pro struktury. Řešení, je použít výraz výchozí hodnotu, která vrátí hodnotu `null` pro odkazové typy (typy třídy a rozhraní typy) a pro typy číselnou hodnotu nula. Pro vlastní struktury vrátí struktura inicializována tak, aby nulové bit vzor, který vytváří 0 nebo `null` pro každého člena v závislosti na tom, jestli je daný člen typu hodnotu nebo odkaz. U typů hodnot s povolenou hodnotou Null `default` vrátí <xref:System.Nullable%601?displayProperty=nameWithType>, který je inicializován jako jakékoli struktura.

`default(T)` Výraz není omezen na obecné třídy a metody. Výchozí hodnota výrazy lze použít všechny spravovaného typu. Platné jsou některé z těchto výrazů:

 [!code-csharp[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]

 Následující příklad z `GenericList<T>` třída ukazuje způsob použití `default(T)` operátor v obecné třídy. Další informace najdete v tématu [přehled obecných typů](../generics/introduction-to-generics.md).

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

 <xref:System.Collections.Generic>[Průvodce programováním v C#](../index.md)  
 [Obecné typy](../generics/index.md)  
 [Obecné metody](../generics/generic-methods.md)  
 [Obecné typy](~/docs/standard/generics/index.md)  
