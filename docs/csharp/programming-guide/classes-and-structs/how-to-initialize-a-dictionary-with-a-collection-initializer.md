---
title: Jak inicializovat slovník s inicializátorem kolekce - C# Programovací průvodce
ms.date: 12/20/2018
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: 1e6e7fac9dd49ad1943ac9046bd9e4932c383257
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75741367"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a>Jak inicializovat slovník s inicializátorem kolekce (Průvodce programováním jazyka C#)

A <xref:System.Collections.Generic.Dictionary%602> obsahuje kolekci párů klíč/hodnota. Jeho <xref:System.Collections.Generic.Dictionary%602.Add%2A> metoda trvá dva parametry, jeden pro klíč a jeden pro hodnotu. Jedním ze způsobů, <xref:System.Collections.Generic.Dictionary%602>jak inicializovat , nebo všechny kolekce, jejichž `Add` metoda trvá více parametrů, je uzavřít každou sadu parametrů v závorkách, jak je znázorněno v následujícím příkladu. Další možností je použít inicializátor indexu, který je také uveden v následujícím příkladu.

## <a name="example"></a>Příklad

V následujícím příkladu <xref:System.Collections.Generic.Dictionary%602> kódu je inicializován `StudentName`a s instancemi typu .  První inicializace `Add` používá metodu se dvěma argumenty. Kompilátor generuje volání `Add` pro každou dvojici `int` klíčů `StudentName` a hodnot. Druhý používá veřejné čtení / zápis indexer metoda třídy: `Dictionary`

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToDictionaryInitializer.cs#HowToDictionaryInitializer)]  

Všimněte si dvou párů závorek v každém prvku kolekce v první deklaraci. Nejvnitřnější závorky uzavřete `StudentName`inicializační prostředek objektu pro a vnější závorky uzavřou `students` <xref:System.Collections.Generic.Dictionary%602>inicializátor pro dvojici klíč/hodnota, která bude přidána do . Nakonec je uzavřena celá inicializátor kolekce pro slovník. Při druhé inicializaci je klíčem levá strana přiřazení a pravá strana je hodnota `StudentName`pomocí inicializátoru objektu pro .

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Inicializátory objektu a kolekce](./object-and-collection-initializers.md)
