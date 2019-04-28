---
title: Indexery - C# Průvodce programováním
ms.custom: seodec18
ms.date: 03/10/2017
f1_keywords:
- cs.indexers
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
ms.openlocfilehash: 5ab0a5e524979110c355391cf800cc82e6d6244f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61680154"
---
# <a name="indexers-c-programming-guide"></a>Indexery (Průvodce programováním v C#)

Indexery povolit instance třídy nebo struktury indexovaných stejně jako pole. Indexovanou hodnotu můžete nastavit nebo načíst bez explicitního určení typu nebo instance člena. Indexery se podobají [vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md) s tím rozdílem, že jejich přístupových objektů přijímají parametry.  
 
 Následující příklad definuje obecné třídy s jednoduchou [získat](../../../csharp/language-reference/keywords/get.md) a [nastavit](../../../csharp/language-reference/keywords/set.md) přístupové metody pro přiřazení a načítat hodnoty. `Program` Třídy vytvoří instanci této třídy pro uložení řetězce.  
  
 [!code-csharp[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
>  Další příklady najdete v tématu [související oddíly](../../../csharp/programming-guide/indexers/index.md#BKMK_RelatedSections).  
  
## <a name="expression-body-definitions"></a>Definice textu výrazu  
 
Je běžné, že indexování get nebo přístupový objekt set spočívají jediném příkazu, který vrátí nebo nastaví hodnotu. Členové tvoření poskytují zjednodušenou syntaxi pro podporu tohoto scénáře. Od verze C# 6, je možné implementovat jako člena s výrazem v těle, jak ukazuje následující příklad indexer jen pro čtení.

[!code-csharp[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

Všimněte si, že `=>` představuje text výrazu a, který `get` – klíčové slovo se nepoužívá. 

Od verze C# 7.0, jak získat a přístupový objekt set mohou být implementovaná jako členy s výrazem v těle. V takovém případě obě `get` a `set` klíčová slova musí být použita. Příklad:

[!code-csharp[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a>Přehled indexerů  
  
- Indexery povolují objekty, které mají být indexovány v podobným způsobem jako pole.  
  
- A `get` přistupující objekt vrací hodnotu. A `set` přístupového objektu přiřadí hodnotu.  
  
- [To](../../../csharp/language-reference/keywords/this.md) – klíčové slovo se používá k definování indexeru.  
  
- [Hodnotu](../../../csharp/language-reference/keywords/value.md) – klíčové slovo se používá k definování přiřazené podle hodnoty `set` indexeru.  
  
- Indexery není nutné indexovat pomocí celočíselnou hodnotu; je jenom na vás, jak definovat konkrétní vyhledávací mechanismus.  
  
- Indexery můžou být přetížené.  
  
- Indexery může mít více než jeden formální parametr, například při přístupu k dvourozměrné pole.  
  
## <a name="BKMK_RelatedSections"></a> Související oddíly  
  
- [Použití indexerů](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
- [Indexery v rozhraní](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)  
  
- [Porovnání mezi vlastnostmi a indexery](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
- [Omezení přístupnosti přístupového objektu](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  

Další informace najdete v tématu [indexery](~/_csharplang/spec/classes.md#indexers) v [ C# specifikace jazyka](../../language-reference/language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)
