---
title: Postup inicializace objektů pomocí inicializátoru objektu – C# Průvodce programováním
ms.date: 12/20/2018
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: a2ecc9df211d0082bd4b413653e374758c877abc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705584"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a>Postup inicializace objektů pomocí inicializátoru objektu (C# Průvodce programováním)

Inicializátory objektů můžete použít k inicializaci typu objektů deklarativním způsobem bez explicitního vyvolání konstruktoru pro daný typ.  
  
Následující příklady ukazují, jak používat Inicializátory objektů s pojmenovanými objekty. Kompilátor zpracovává Inicializátory objektů, protože nejprve přistupuje k výchozímu konstruktoru instance a pak zpracovává inicializace členů. Proto pokud je konstruktor bez parametrů deklarován jako `private` ve třídě, Inicializátory objektů, které vyžadují veřejný přístup, se nezdaří.
  
Je nutné použít inicializátor objektu, pokud definujete anonymní typ. Další informace naleznete v tématu [jak vracet podmnožiny vlastností elementu v dotazu](how-to-return-subsets-of-element-properties-in-a-query.md).  
  
## <a name="example"></a>Příklad  

Následující příklad ukazuje, jak inicializovat nový typ `StudentName` pomocí inicializátorů objektů. Tento příklad nastaví vlastnosti v typu `StudentName`:
  
[!code-csharp[InitializerObjectExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToObjectInitializers.cs#HowToObjectInitializers)]  

Inicializátory objektů lze použít k nastavení indexerů v objektu. Následující příklad definuje třídu `BaseballTeam`, která používá indexer k získání a nastavení hráčů na různých pozicích. Inicializátor může přiřadit přehrávače na základě zkratky pro pozici nebo čísla používaného pro všechny baseballové Scorecardy na pozici:

[!code-csharp[InitializerIndexerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToIndexInitializer.cs#HowToIndexInitializer)]  

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Inicializátory objektu a kolekce](object-and-collection-initializers.md)
