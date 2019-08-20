---
title: Postup inicializace slovníku pomocí inicializátoru kolekce – C# Průvodce programováním
ms.custom: seodec18
ms.date: 12/20/2018
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: 22f80365b974df66999ac68f7bc2a9ffa7d445a5
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596817"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a>Postup inicializace slovníku pomocí inicializátoru kolekce (C# Průvodce programováním)

<xref:System.Collections.Generic.Dictionary%602> Obsahuje kolekci párů klíč/hodnota. Jeho <xref:System.Collections.Generic.Dictionary%602.Add*> metoda přijímá dva parametry, jednu pro klíč a jednu pro hodnotu. Jedním ze způsobů <xref:System.Collections.Generic.Dictionary%602>, jak inicializovat nebo jakékoli kolekce, `Add` jejichž metoda přijímá více parametrů, je uzavřít každou sadu parametrů do složených závorek, jak je znázorněno v následujícím příkladu. Další možností je použít inicializátor indexu, který je také znázorněn v následujícím příkladu.

## <a name="example"></a>Příklad

V následujícím příkladu <xref:System.Collections.Generic.Dictionary%602> kódu je inicializována s instancemi typu `StudentName`.  První inicializace používá `Add` metodu se dvěma argumenty. Kompilátor vygeneruje volání `Add` pro každou `int` dvojici klíčů a `StudentName` hodnot. Druhý používá metodu `Dictionary` Public pro čtení/zápis třídy:

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToDictionaryInitializer.cs#HowToDictionaryInitializer)]  

Všimněte si dvou párů složených závorek v každém elementu kolekce v první deklaraci. Nejvnitřnější složené závorky ohraničují inicializátor objektu pro `StudentName`a vnější složené závorky mají k dispozici inicializátor pro dvojici klíč/hodnota, která bude přidána `students` <xref:System.Collections.Generic.Dictionary%602>do. Nakonec je celý inicializátor kolekce pro slovník uzavřený ve složených závorkách. Při druhé inicializaci je levá strana přiřazení klíč a pravá strana je hodnota s použitím inicializátoru objektu pro `StudentName`.

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Inicializátory objektu a kolekce](./object-and-collection-initializers.md)
