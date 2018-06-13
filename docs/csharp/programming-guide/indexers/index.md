---
title: Indexery (Průvodce programováním v C#)
ms.date: 03/10/2017
f1_keywords:
- cs.indexers
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
ms.openlocfilehash: acc82ca370a71a0469fc543d042da9c279d69fb2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334217"
---
# <a name="indexers-c-programming-guide"></a>Indexery (Průvodce programováním v C#)

Indexery povolit instancí třídě nebo struktuře indexovaných stejně jako pole. Indexované hodnotu můžete nastavit nebo načíst bez zadání explicitně členem typ, nebo instance. Indexery vypadat [vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md) s tím rozdílem, že jejich přístupových objektů trvat parametry.  
 
 Následující příklad definuje třídu obecné s jednoduchou [získat](../../../csharp/language-reference/keywords/get.md) a [nastavit](../../../csharp/language-reference/keywords/set.md) přístupových metod a přiřadit k získávání hodnot. `Program` Třída vytvoří instance této třídy pro ukládání řetězců.  
  
 [!code-csharp[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
>  Další příklady najdete v tématu [související oddíly](../../../csharp/programming-guide/indexers/index.md#BKMK_RelatedSections).  
  
## <a name="expression-body-definitions"></a>Výraz definice textu  
 
Je běžné pro get indexer nebo přistupující objekt set sestává z jedné příkaz, který vrátí nebo nastaví hodnotu. Výraz vozidlo členy poskytují zjednodušenou syntaxi pro podporu tohoto scénáře. Od verze jazyka C# 6, indexer jen pro čtení se dá implementovat jako výraz vozidlo člena, jak ukazuje následující příklad.

[!code-csharp[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

Všimněte si, že `=>` představuje výraz text a který `get` – klíčové slovo nepoužívá. 

Od verze jazyka C# 7.0, i get a přistupující objekt set může být implementovaná jako výraz vozidlo členy. V takovém případě obě `get` a `set` klíčová slova se musí použít. Příklad:

[!code-csharp[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a>Přehled indexerů  
  
-   Indexery povolit objekty indexovaných podobným způsobem jako na pole.  
  
-   A `get` přistupujícího objektu vrací hodnotu. A `set` přistupujícího objektu přiřazuje hodnotu.  
  
-   [To](../../../csharp/language-reference/keywords/this.md) – klíčové slovo se používá k definování indexeru.  
  
-   [Hodnotu](../../../csharp/language-reference/keywords/value.md) – klíčové slovo se používá k definování přiřazené podle `set` indexer.  
  
-   Indexery nemusíte indexovat pomocí celočíselnou hodnotu; Můžete se rozhodnout, jak definovat mechanismus konkrétní hledání.  
  
-   Indexery může být přetížený.  
  
-   Indexery může mít více než jeden formální parametr, například při přístupu k dvourozměrná pole.  
  
##  <a name="BKMK_RelatedSections"></a> Související oddíly  
  
-   [Použití indexerů](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [Indexery v rozhraní](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)  
  
-   [Porovnání mezi vlastnostmi a indexery](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
-   [Omezení přístupnosti přístupového objektu](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)
