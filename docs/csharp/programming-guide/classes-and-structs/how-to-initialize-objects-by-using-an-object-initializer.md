---
title: Jak inicializovat objekty pomocí inicializačního systému objektu - Průvodce programováním jazyka C#
ms.date: 12/20/2018
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: a2ecc9df211d0082bd4b413653e374758c877abc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705584"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a>Jak inicializovat objekty pomocí inicializačního zařízení objektu (Průvodce programováním jazyka C#)

Inicializační metody objektu můžete použít k inicializaci objektů typu deklarativním způsobem bez explicitního vyvolání konstruktoru pro daný typ.  
  
Následující příklady ukazují, jak používat inicializační prvky objektu s pojmenovanými objekty. Kompilátor zpracovává inicializátory objektů tak, že nejprve přistupuje k výchozímu konstruktoru instance a poté zpracovává inicializace členů. Proto pokud konstruktor bez parametrů `private` je deklarován jako ve třídě, inicializátory objektu, které vyžadují veřejný přístup se nezdaří.
  
Inicializátor objektu je nutné použít, pokud definujete anonymní typ. Další informace naleznete v [tématu Jak vrátit podmnožiny vlastností elementu v dotazu](how-to-return-subsets-of-element-properties-in-a-query.md).  
  
## <a name="example"></a>Příklad  

Následující příklad ukazuje, jak inicializovat nový `StudentName` typ pomocí inicializačních objektů. Tento příklad nastaví `StudentName` vlastnosti v typu:
  
[!code-csharp[InitializerObjectExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToObjectInitializers.cs#HowToObjectInitializers)]  

Inicializátory objektů lze použít k nastavení indexerů v objektu. Následující příklad definuje `BaseballTeam` třídu, která používá indexer získat a nastavit hráče na různých pozicích. Inicializátor může přiřadit hráče na základě zkratky pro pozici nebo číslo použité pro každou pozici baseballscorecards:

[!code-csharp[InitializerIndexerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToIndexInitializer.cs#HowToIndexInitializer)]  

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Inicializátory objektu a kolekce](object-and-collection-initializers.md)
