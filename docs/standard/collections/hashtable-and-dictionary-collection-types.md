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
ms.openlocfilehash: a6f234b6205fd30507b9342d9839db6adcddfc2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711373"
---
# <a name="hashtable-and-dictionary-collection-types"></a>Typy kolekce Hashtable a Dictionary
Třída <xref:System.Collections.Hashtable?displayProperty=nameWithType> a <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> a <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> obecné třídy <xref:System.Collections.IDictionary?displayProperty=nameWithType> implementovat rozhraní. Obecná <xref:System.Collections.Generic.Dictionary%602> třída také implementuje <xref:System.Collections.Generic.IDictionary%602> obecné rozhraní. Proto každý prvek v těchto kolekcích je dvojice klíč a hodnota.  
  
 Objekt <xref:System.Collections.Hashtable> se skládá z bloků, které obsahují prvky kolekce. Kontejner je virtuální podskupina prvků <xref:System.Collections.Hashtable>v rámci , což usnadňuje a načítání vyhledávání a načítání než ve většině kolekcí. Každý segment je přidružen ke kódu hash, který je generován pomocí funkce hash a je založen na klíči prvku.  
  
 Obecná <xref:System.Collections.Generic.HashSet%601> třída je neuspořádaná kolekce pro obsahující jedinečné prvky.  
  
 Funkce hash je algoritmus, který vrací číselný kód hash založený na klíči. Klíč je hodnota některé vlastnosti objektu, který je uložen. Funkce hash musí vždy vrátit stejný kód hash pro stejný klíč. Je možné, že funkce hash generovat stejný kód hash pro dva různé klíče, ale hash funkce, která generuje jedinečný hash kód pro každý jedinečný klíč má za následek lepší výkon při načítání prvků z tabulky hash.  
  
 Každý objekt, který se používá <xref:System.Collections.Hashtable> jako prvek v musí být schopen generovat hash <xref:System.Object.GetHashCode%2A> kód pro sebe pomocí implementace metody. Můžete však také určit funkci hash pro <xref:System.Collections.Hashtable> všechny <xref:System.Collections.Hashtable> prvky v a <xref:System.Collections.IHashCodeProvider> pomocí konstruktoru, který přijímá implementaci jako jeden z jeho parametrů.  
  
 Při přidání objektu <xref:System.Collections.Hashtable>do , je uložen v bloku, který je přidružen ke kódu hash, který odpovídá kódu hash objektu. Při hledání hodnoty v <xref:System.Collections.Hashtable>oblasti , je pro tuto hodnotu generován kód hash a prohledán kontejner přidružený k tomuto kódu hash.  
  
 Například funkce hash pro řetězec může trvat kódy ASCII každého znaku v řetězci a přidat je dohromady, aby se vygeneroval kód hash. Řetězec "piknik" by měl hash kód, který se liší od hash kód pro řetězec "košíku"; proto struny "piknik" a "koš" by byly v různých kbelíkech. Naproti tomu "zdůraznil" a "dezerty" by měl stejný hash kód a bude ve stejném kbelíku.  
  
 <xref:System.Collections.Generic.Dictionary%602> Třídy <xref:System.Collections.Concurrent.ConcurrentDictionary%602> a mají stejné funkce <xref:System.Collections.Hashtable> jako třída. A <xref:System.Collections.Generic.Dictionary%602> určitého typu (jinénež) <xref:System.Object>poskytuje <xref:System.Collections.Hashtable> lepší výkon než pro typy hodnot. Důvodem je, <xref:System.Collections.Hashtable> že prvky jsou typu <xref:System.Object>; proto zabalení a rozbalení obvykle dojít při ukládání nebo načtení typu hodnoty. Třída <xref:System.Collections.Concurrent.ConcurrentDictionary%602> by měla být použita, když více vláken může být přístup ke kolekci současně.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Collections.Hashtable>
- <xref:System.Collections.IDictionary>
- <xref:System.Collections.IHashCodeProvider>
- <xref:System.Collections.Generic.Dictionary%602>
- <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>
- [Běžně používané typy kolekcí](../../../docs/standard/collections/commonly-used-collection-types.md)
