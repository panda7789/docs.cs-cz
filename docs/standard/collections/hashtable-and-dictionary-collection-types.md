---
title: Typy kolekce Hashtable a Dictionary
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Hashtable class, grouping data in collections
- Hashtable collection type
- hash tables
- grouping data in collections, Hashtable collection type
- hash function
- collections [.NET Framework], Hashtable collection type
ms.assetid: bfc20837-3d02-4fc7-8a8f-c5215b6b7913
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fefd9f95a669c9c0384cefe41322c7a10a96a3b7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514709"
---
# <a name="hashtable-and-dictionary-collection-types"></a>Typy kolekce Hashtable a Dictionary
<xref:System.Collections.Hashtable?displayProperty=nameWithType> Třídy a <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> a <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> implementovat obecné třídy <xref:System.Collections.IDictionary?displayProperty=nameWithType> rozhraní. <xref:System.Collections.Generic.Dictionary%602> Obecnou třídu také implementuje <xref:System.Collections.Generic.IDictionary%602> obecného rozhraní. Každý prvek v těchto kolekcích tedy pár klíč hodnota.  
  
 A <xref:System.Collections.Hashtable> objekt se skládá z bloků, které obsahují elementy kolekce. Blok je virtuální podskupina elementů v rámci <xref:System.Collections.Hashtable>, takže se dají vyhledávání a načítání jednodušší a rychlejší než v většiny kolekcí. Každý blok souvisí s hodnotu hash, která je generována pomocí funkce hash a je založena na klíči elementu.  
  
 Obecné <xref:System.Collections.Generic.HashSet%601> třída je Neseřazený kolekce obsahující jedinečných prvků.  
  
 Funkce hash je algoritmus, který vrátí číselnou hodnotu hash na základě klíče. Klíč je hodnota některé vlastnosti objektu ukládají. Funkce hash musí vracet vždycky stejnou hodnotu hash pro stejný klíč. Je možné pro funkce hash pro generování stejnou hodnotu hash pro dva různé klíče, ale funkce hash, který generuje kód hash jedinečný pro každý jedinečných klíčů výsledky lepší výkon při načítání prvků z tabulky hash.  
  
 Každý objekt, který se používá jako prvek v <xref:System.Collections.Hashtable> musí být schopna generovat kód hash sama za sebe pomocí implementace <xref:System.Object.GetHashCode%2A> metody. Ale můžete také zadat funkce hash pro všechny prvky v <xref:System.Collections.Hashtable> pomocí <xref:System.Collections.Hashtable> konstruktor, který přijímá <xref:System.Collections.IHashCodeProvider> implementaci jako jeden ze svých parametrů.  
  
 Při přidání objektu <xref:System.Collections.Hashtable>, uloží se v bloku, který je spojen s hodnotou hash, která odpovídá hodnotě hash objektu. Pokud hodnota je prohledávána v <xref:System.Collections.Hashtable>, je generována hodnota hash pro tuto hodnotu a je prohledána sady přidružené k tento kód hash.  
  
 Funkce hash pro řetězce může například trvat kódy ASCII každého znaku v řetězci a přidejte je dohromady a generovat kód hash. Řetězec "výlet" by mít hodnotu hash, která se liší od hodnoty hash pro řetězec "nákupní košík"; řetězce "výlet" a "nákupní košík" by proto být v různých kontejnerů. Naproti tomu "zdůraznit" a "My jsme zvolili zákusky" bude mít stejnou hodnotu hash a by být ve stejném bloku.  
  
 <xref:System.Collections.Generic.Dictionary%602> a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> třídy mají stejně jako <xref:System.Collections.Hashtable> třídy. A <xref:System.Collections.Generic.Dictionary%602> určitého typu (jiných než <xref:System.Object>) poskytuje lepší výkon než <xref:System.Collections.Hashtable> pro typy hodnot. Důvodem je, že prvky <xref:System.Collections.Hashtable> jsou typu <xref:System.Object>; proto zabalení a rozbalení obvykle dojde ukládat nebo načítat hodnotového typu. <xref:System.Collections.Concurrent.ConcurrentDictionary%602> Třída má být použit, při více vláken může přístupu ke kolekci současně.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Hashtable>
- <xref:System.Collections.IDictionary>
- <xref:System.Collections.IHashCodeProvider>
- <xref:System.Collections.Generic.Dictionary%602>
- <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>
- [Běžně používané typy kolekcí](../../../docs/standard/collections/commonly-used-collection-types.md)
