---
title: Způsob inicializace slovníku pomocí inicializátoru kolekce - C# Průvodce programováním pro službu
ms.custom: seodec18
ms.date: 12/20/2018
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: acd426b7652705ff395df9a81cde8ef549af0e31
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646394"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a>Způsob inicializace slovníku pomocí inicializátoru kolekce (C# Programming Guide)

A <xref:System.Collections.Generic.Dictionary%602> obsahuje kolekci dvojic klíč/hodnota. Jeho <xref:System.Collections.Generic.Dictionary%602.Add*> metoda přebírá dva parametry, jeden pro klíč a jeden pro hodnotu. Jeden ze způsobů, jak inicializovat <xref:System.Collections.Generic.Dictionary%602>, nebo jakoukoli kolekci jehož `Add` metoda přijímá několik parametrů, je pro každou sadu parametrů uzavřete do složených závorek, jak je znázorněno v následujícím příkladu. Další možností je použít inicializátor indexu, je také znázorněno v následujícím příkladu.

## <a name="example"></a>Příklad

V následujícím příkladu kódu <xref:System.Collections.Generic.Dictionary%602> je inicializován pomocí instance typu `StudentName`.  První inicializace používá `Add` metodu se dvěma argumenty. Kompilátor vygeneruje volání `Add` pro každou z dvojice `int` klíče a `StudentName` hodnoty. Druhý používá veřejnou čtení / zápis metoda indexer `Dictionary` třídy:

[!code-csharp-interactive[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToDictionaryInitializer.cs#HowToDictionaryInitializer)]  

Všimněte si dvě dvojice složených závorek v jednotlivých prvcích objektu kolekce v první deklaraci. Vnitřní závorky uzavřete inicializátor objektu pro `StudentName`, a uzavřete inicializátor pro dvojice klíč/hodnota, která se přidá do vnějšího složené závorky `students` <xref:System.Collections.Generic.Dictionary%602>. Nakonec celé kolekce inicializátor slovníku uzavřen ve složených závorkách. V druhém inicializace levé části přiřazení je klíč a pravé straně je hodnota, pomocí inicializátoru objektu pro `StudentName`.

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Inicializátory objektu a kolekce](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
