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
ms.openlocfilehash: b228f5db16ba01969b77d601becfb94ac0506d1e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287962"
---
# <a name="hashtable-and-dictionary-collection-types"></a>Typy kolekce Hashtable a Dictionary
<xref:System.Collections.Hashtable?displayProperty=nameWithType>Třídu a <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> Obecné třídy implementují <xref:System.Collections.IDictionary?displayProperty=nameWithType> rozhraní. <xref:System.Collections.Generic.Dictionary%602>Obecná třída také implementuje <xref:System.Collections.Generic.IDictionary%602> Obecné rozhraní. Proto každý prvek v těchto kolekcích je dvojice klíč-hodnota.  
  
 <xref:System.Collections.Hashtable>Objekt se skládá z kontejnerů, které obsahují prvky kolekce. Kontejner je virtuální podskupina prvků v rámci <xref:System.Collections.Hashtable> , která umožňuje vyhledávání a načítání snazší a rychlejší než ve většině kolekcí. Každý interval je přidružen k hodnotě hash, která je generována pomocí funkce hash a je založena na klíči elementu.  
  
 Obecná <xref:System.Collections.Generic.HashSet%601> Třída je neuspořádaná kolekce pro obsahující jedinečné prvky.  
  
 Funkce hash je algoritmus, který vrací číselný kód hash na základě klíče. Klíč je hodnota některé vlastnosti objektu, který se ukládá. Funkce hash musí vždycky vracet stejný kód hash pro stejný klíč. Funkce hash může generovat stejný kód hash pro dva různé klíče, ale funkce hash, která generuje jedinečný kód hash pro každý jedinečný klíč, má za následek lepší výkon při načítání prvků z zatřiďovací tabulky.  
  
 Každý objekt, který je použit jako element v <xref:System.Collections.Hashtable> musí být schopný vygenerovat kód hash sám pro sebe pomocí implementace <xref:System.Object.GetHashCode%2A> metody. Můžete však také zadat funkci hash pro všechny prvky v a <xref:System.Collections.Hashtable> pomocí <xref:System.Collections.Hashtable> konstruktoru, který přijímá <xref:System.Collections.IHashCodeProvider> implementaci jako jeden z jeho parametrů.  
  
 Když je objekt přidán do <xref:System.Collections.Hashtable> , je uložen v kontejneru, který je přidružen k hodnotě hash, která odpovídá kódu hash objektu. Při hledání hodnoty v rozhraní se <xref:System.Collections.Hashtable> pro tuto hodnotu vygeneruje kód hash a v kontejneru přidruženého k tomuto kódu hash se proprohledávají.  
  
 Například funkce hash pro řetězec může mít kódy ASCII každého znaku v řetězci a jejich přidáním společně pro vygenerování kódu hash. Řetězec "piknik" by měl kód hash, který se liší od kódu hash pro řetězec "košík"; Proto jsou řetězce "piknik" a "košík" v různých intervalech. Naopak "stresed" a "desserts" by měly stejný kód hash a by byl ve stejném kontejneru.  
  
 <xref:System.Collections.Generic.Dictionary%602>Třídy a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> mají stejné funkce jako <xref:System.Collections.Hashtable> Třída. Určitý <xref:System.Collections.Generic.Dictionary%602> typ (jiný než <xref:System.Object> ) poskytuje lepší výkon než <xref:System.Collections.Hashtable> pro typy hodnot. Důvodem je to, že prvky <xref:System.Collections.Hashtable> jsou typu <xref:System.Object> ; proto se k zabalení a rozbalení obvykle dochází, když ukládáte nebo načítáte typ hodnoty. <xref:System.Collections.Concurrent.ConcurrentDictionary%602>Třída by měla být použita, pokud více vláken může přistupovat ke kolekci současně.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Collections.Hashtable>
- <xref:System.Collections.IDictionary>
- <xref:System.Collections.IHashCodeProvider>
- <xref:System.Collections.Generic.Dictionary%602>
- <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>
- [Běžně používané typy kolekcí](commonly-used-collection-types.md)
