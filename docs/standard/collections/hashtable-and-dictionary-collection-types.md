---
title: Typy kolekce Hashtable a Dictionary
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Hashtable class, grouping data in collections
- Hashtable collection type
- hash tables
- grouping data in collections, Hashtable collection type
- hash function
- collections [.NET Framework], Hashtable collection type
ms.assetid: bfc20837-3d02-4fc7-8a8f-c5215b6b7913
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: aa2392775f0bd2d68c0aeb28aa0654b690b11808
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="hashtable-and-dictionary-collection-types"></a>Typy kolekce Hashtable a Dictionary
<xref:System.Collections.Hashtable?displayProperty=nameWithType> Třída a <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> a <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> implementovat obecné třídy <xref:System.Collections.IDictionary?displayProperty=nameWithType> rozhraní. <xref:System.Collections.Generic.Dictionary%602> Obecná třída také implementuje <xref:System.Collections.Generic.IDictionary%602> obecné rozhraní. Každý prvek v těchto kolekcí je proto pár klíč hodnota.  
  
 A <xref:System.Collections.Hashtable> objekt se skládá z bloků, které obsahují prvky kolekce. Blok je virtuální podskupina elementů v rámci <xref:System.Collections.Hashtable>, což usnadňuje hledání a načítání snadnější a rychlejší než v většiny kolekcí. Každý blok je přiřazen k hodnotu hash, která je generována pomocí funkce hash a je založena na klíči elementu.  
  
 Obecná <xref:System.Collections.Generic.HashSet%601> třída je neuspořádaného kolekci pro obsahující jedinečný elementy.  
  
 Funkce hash je algoritmus, který vrátí číselnou hodnotu hash podle klíče. Klíč je hodnota některé vlastnosti objektu. Funkce hash musí vracet vždycky stejnou hodnotu hash pro stejný klíč. Je možné funkce hash pro generování stejnou hodnotu hash pro dva různé klíče, ale funkce hash, která generuje jedinečnou hodnotu hash pro každý jedinečný klíč výsledky v lepší výkon při načítání elementy z zatřiďovací tabulku.  
  
 Každý objekt, který se používá jako element v <xref:System.Collections.Hashtable> musí být schopen generovat kód hash pro sebe pomocí implementace <xref:System.Object.GetHashCode%2A> metoda. Ale můžete také zadat funkce hash pro všechny elementy ve <xref:System.Collections.Hashtable> pomocí <xref:System.Collections.Hashtable> konstruktor, který přijímá <xref:System.Collections.IHashCodeProvider> implementaci jako jeden z jeho parametrů.  
  
 Když je objekt přidat do <xref:System.Collections.Hashtable>, uloží se do bloku, který je přidružen hash, která odpovídá hodnotě hash objektu. Pokud je hodnota vyhledána v <xref:System.Collections.Hashtable>, je generována hodnota hash pro tuto hodnotu a je prohledána sady přidružené k této hodnota hash.  
  
 Funkce hash pro řetězec může například trvat kódů ASCII o každý znak v řetězci a přidávat je, aby generoval hodnotu hash. Řetězec "výlet" by měla mít hodnotu hash, který se liší od kód hash pro řetězec "košík"; řetězce "výlet" a "košík" by proto být v různých blocích. Naproti tomu "zdůraznit" a "zákusků" by měla mít stejnou hodnotu hash a by být ve stejném bloku.  
  
 <xref:System.Collections.Generic.Dictionary%602> a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> třídy mají stejné funkce jako <xref:System.Collections.Hashtable> třídy. A <xref:System.Collections.Generic.Dictionary%602> určitého typu (jiné než <xref:System.Object>) poskytuje lepší výkon než <xref:System.Collections.Hashtable> u typů hodnot. Důvodem je, že elementy <xref:System.Collections.Hashtable> typu <xref:System.Object>; proto zabalení a rozbalení obvykle dojít při uložení nebo načíst typ hodnoty. <xref:System.Collections.Concurrent.ConcurrentDictionary%602> Třída by měl být použit při více vláken může přistupovat ke kolekci současně.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.Hashtable>  
 <xref:System.Collections.IDictionary>  
 <xref:System.Collections.IHashCodeProvider>  
 <xref:System.Collections.Generic.Dictionary%602>  
 <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>  
 [Běžně používané typy kolekcí](../../../docs/standard/collections/commonly-used-collection-types.md)
