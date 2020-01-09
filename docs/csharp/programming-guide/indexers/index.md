---
title: Indexery – C# Průvodce programováním
ms.date: 03/10/2017
f1_keywords:
- cs.indexers
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
ms.openlocfilehash: c00f506a682ec5d9805537b80159fd41d2174b67
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75702945"
---
# <a name="indexers-c-programming-guide"></a>Indexery (Průvodce programováním v C#)

Indexery umožňují, aby byly instance třídy nebo struktury indexovány stejně jako pole. Indexovaná hodnota může být nastavena nebo načtena bez explicitního určení typu nebo členu instance. Indexery připomínají [vlastnosti](../classes-and-structs/properties.md) s tím rozdílem, že jejich přístupové objekty přijímají parametry.  

 Následující příklad definuje obecnou třídu pomocí jednoduchých přístupových metod [Get](../../language-reference/keywords/get.md) a [set](../../language-reference/keywords/set.md) pro přiřazení a načtení hodnot. Třída `Program` vytvoří instanci této třídy pro ukládání řetězců.  
  
 [!code-csharp[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
> Další příklady najdete v části [související oddíly](./index.md#BKMK_RelatedSections).  
  
## <a name="expression-body-definitions"></a>Definice textu výrazu  
 
Je běžné, že přistupující objekt get nebo set indexeru se skládá z jednoho příkazu, který vrátí nebo nastaví hodnotu. Členové Expression-těle poskytují zjednodušenou syntaxi pro podporu tohoto scénáře. Počínaje C# 6 se indexer jen pro čtení dá implementovat jako člen s výrazem těle, jak ukazuje následující příklad.

[!code-csharp[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

Všimněte si, že `=>` zavádí tělo výrazu a nepoužívá se klíčové slovo `get`. 

Počínaje C# 7,0 se přístupové objekty get a set můžou implementovat jako členy Expression-těle. V takovém případě je nutné použít jak klíčová slova `get`, tak `set`. Příklad:

[!code-csharp[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a>Přehled indexerů  
  
- Indexery povolují, aby objekty byly indexovány podobným způsobem jako pole.  
  
- Přístupový objekt `get` vrací hodnotu. Přístupový objekt `set` přiřadí hodnotu.  
  
- Klíčové slovo [This](../../language-reference/keywords/this.md) slouží k definování indexeru.  
  
- Klíčové slovo [Value](../../language-reference/keywords/value.md) slouží k definování hodnoty, kterou přiřazuje služba `set` indexer.  
  
- Indexery nemusí být indexovány pomocí celočíselné hodnoty; je zde postup, jak definovat konkrétní vyhledávací mechanismus.  
  
- Indexery mohou být přetíženy.  
  
- Indexery mohou mít více než jeden formální parametr, například při přístupu k dvojrozměrnému poli.  
  
## <a name="BKMK_RelatedSections"></a>Související oddíly  
  
- [Použití indexerů](./using-indexers.md)  
  
- [Indexery v rozhraní](./indexers-in-interfaces.md)  
  
- [Porovnání mezi vlastnostmi a indexery](./comparison-between-properties-and-indexers.md)  
  
- [Omezení přístupnosti přístupového objektu](../classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a>C# – jazyková specifikace  

Další informace najdete v tématu [indexery](~/_csharplang/spec/classes.md#indexers) ve [ C# specifikaci jazyka](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Vlastnosti](../classes-and-structs/properties.md)
