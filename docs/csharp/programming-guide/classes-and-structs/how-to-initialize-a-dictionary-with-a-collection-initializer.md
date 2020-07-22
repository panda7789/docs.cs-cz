---
title: Postup inicializace slovníku pomocí inicializátoru kolekce – Průvodce programováním v C#
description: Naučte se inicializovat slovník v jazyce C# pomocí metody Add nebo inicializátoru indexu. Tento příklad ukazuje obě možnosti.
ms.date: 12/20/2018
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: 2f33240b02785c5c886a1ebebb8984d29c9f7795
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865044"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a>Postup inicializace slovníku pomocí inicializátoru kolekce (Průvodce programováním v C#)

<xref:System.Collections.Generic.Dictionary%602>Obsahuje kolekci párů klíč/hodnota. Jeho <xref:System.Collections.Generic.Dictionary%602.Add%2A> Metoda přijímá dva parametry, jednu pro klíč a jednu pro hodnotu. Jedním ze způsobů, jak inicializovat <xref:System.Collections.Generic.Dictionary%602> nebo jakékoli kolekce, jejichž `Add` Metoda přijímá více parametrů, je uzavřít každou sadu parametrů do složených závorek, jak je znázorněno v následujícím příkladu. Další možností je použít inicializátor indexu, který je také znázorněn v následujícím příkladu.

## <a name="example"></a>Příklad

V následujícím příkladu kódu <xref:System.Collections.Generic.Dictionary%602> je inicializována s instancemi typu `StudentName` .  První inicializace používá `Add` metodu se dvěma argumenty. Kompilátor vygeneruje volání `Add` pro každou dvojici `int` klíčů a `StudentName` hodnot. Druhý používá metodu public pro čtení/zápis `Dictionary` třídy:

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToDictionaryInitializer.cs#HowToDictionaryInitializer)]  

Všimněte si dvou párů složených závorek v každém elementu kolekce v první deklaraci. Nejvnitřnější složené závorky ohraničují inicializátor objektu pro `StudentName` a vnější složené závorky mají k dispozici inicializátor pro dvojici klíč/hodnota, která bude přidána do `students` <xref:System.Collections.Generic.Dictionary%602> . Nakonec je celý inicializátor kolekce pro slovník uzavřený ve složených závorkách. Při druhé inicializaci je levá strana přiřazení klíč a pravá strana je hodnota s použitím inicializátoru objektu pro `StudentName` .

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Inicializátory objektu a kolekce](./object-and-collection-initializers.md)
