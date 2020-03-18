---
title: Indexery – programovací příručka Jazyka C#
ms.date: 03/10/2017
f1_keywords:
- cs.indexers
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
ms.openlocfilehash: 539b2861e975c0c758c43c8a5d4cca86e3d2bb2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79167535"
---
# <a name="indexers-c-programming-guide"></a>Indexery (Průvodce programováním v C#)

Indexery umožňují indexovat instance třídy nebo struktury stejně jako pole. Indexovnou hodnotu lze nastavit nebo načíst bez explicitního zadání typu nebo člena instance. Indexery se podobají [vlastnostem](../classes-and-structs/properties.md) s tím rozdílem, že jejich přístupové objekty přebírají parametry.  

 Následující příklad definuje obecnou třídu s jednoduchými metodami přístupového přístupu [get](../../language-reference/keywords/get.md) a [set](../../language-reference/keywords/set.md) pro přiřazení a načtení hodnot. Třída `Program` vytvoří instanci této třídy pro ukládání řetězců.  
  
 [!code-csharp[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
> Další příklady naleznete [v tématu Související oddíly](./index.md#BKMK_RelatedSections).  
  
## <a name="expression-body-definitions"></a>Definice textu výrazu  

Je běžné pro indexeru získat nebo nastavit přistupující objekt se skládá z jednoho příkazu, který vrátí nebo nastaví hodnotu. Členové s výrazem poskytují zjednodušenou syntaxi pro podporu tohoto scénáře. Počínaje C# 6, indexer jen pro čtení lze implementovat jako člen s výrazem, jak ukazuje následující příklad.

[!code-csharp[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

Všimněte `=>` si, že zavádí tělo `get` výrazu a klíčové slovo se nepoužívá.

Počínaje C# 7.0, jak získat a nastavit přistupující objekt může být implementována jako členy s výrazem. V tomto případě `get` `set` musí být použita klíčová slova i klíčová slova. Například:

[!code-csharp[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a>Přehled indexerů  
  
- Indexery umožňují objekty, které mají být indexovány podobným způsobem jako pole.  
  
- Přistupující `get` pole vrátí hodnotu. Přistupující `set` pole přiřadí hodnotu.  
  
- [Toto](../../language-reference/keywords/this.md) klíčové slovo se používá k definování indexeru.  
  
- Klíčové slovo [value](../../language-reference/keywords/value.md) se používá k definování `set` hodnoty přiřazené indexerem.  
  
- Indexery nemusí být indexovány podle celé hodnoty; je jen na vás, jak definovat konkrétní vyhledávací mechanismus.  
  
- Indexery mohou být přetížené.  
  
- Indexery mohou mít více než jeden formální parametr, například při přístupu k dvojrozměrné pole.  
  
## <a name="BKMK_RelatedSections"></a>Související oddíly  
  
- [Použití indexerů](./using-indexers.md)  
  
- [Indexery v rozhraních](./indexers-in-interfaces.md)  
  
- [Porovnání vlastností a indexerů](./comparison-between-properties-and-indexers.md)  
  
- [Omezení přístupnosti přístupového objektu](../classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  

Další informace naleznete v tématu [Indexery](~/_csharplang/spec/classes.md#indexers) ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Vlastnosti](../classes-and-structs/properties.md)
