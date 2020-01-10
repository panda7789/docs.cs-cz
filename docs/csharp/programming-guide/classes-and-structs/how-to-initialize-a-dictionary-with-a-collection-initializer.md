---
title: Postup inicializace slovníku pomocí inicializátoru kolekce – C# Průvodce programováním
ms.date: 12/20/2018
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: 1e6e7fac9dd49ad1943ac9046bd9e4932c383257
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741367"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a>Postup inicializace slovníku pomocí inicializátoru kolekce (C# Průvodce programováním)

<xref:System.Collections.Generic.Dictionary%602> obsahuje kolekci párů klíč/hodnota. Jeho metoda <xref:System.Collections.Generic.Dictionary%602.Add%2A> přijímá dva parametry, jednu pro klíč a jednu pro hodnotu. Jedním ze způsobů, jak inicializovat <xref:System.Collections.Generic.Dictionary%602>, nebo jakoukoli kolekci, jejíž `Add` metoda přijímá více parametrů, je uzavřít každou sadu parametrů do složených závorek, jak je znázorněno v následujícím příkladu. Další možností je použít inicializátor indexu, který je také znázorněn v následujícím příkladu.

## <a name="example"></a>Příklad

V následujícím příkladu kódu je <xref:System.Collections.Generic.Dictionary%602> inicializován s instancemi typu `StudentName`.  První inicializace používá metodu `Add` se dvěma argumenty. Kompilátor vygeneruje volání `Add` pro každou dvojici klíčů `int` a hodnoty `StudentName`. Druhý používá metodu pro `Dictionary` třídy Public pro čtení a zápis:

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToDictionaryInitializer.cs#HowToDictionaryInitializer)]  

Všimněte si dvou párů složených závorek v každém elementu kolekce v první deklaraci. Nejvnitřnější složené závorky obklopují inicializátor objektu pro `StudentName`a vnější složené závorky mají k dispozici inicializátor pro dvojici klíč/hodnota, která bude přidána do `students` <xref:System.Collections.Generic.Dictionary%602>. Nakonec je celý inicializátor kolekce pro slovník uzavřený ve složených závorkách. Při druhé inicializaci je levá strana přiřazení klíč a pravá strana je hodnota pomocí inicializátoru objektu pro `StudentName`.

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Inicializátory objektu a kolekce](./object-and-collection-initializers.md)
