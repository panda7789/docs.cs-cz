---
title: 'Postupy: Inicializace objektů pomocí objektu inicializátoru - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 12/20/2018
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: 494b7625ff8e90b1b81fd32de031ff60d5c6d029
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646407"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a>Postupy: Inicializace objektů pomocí inicializátoru objektů (C# Průvodce programováním v)

Inicializátory objektů můžete použít třeba inicializovat objekty typu bez explicitní volání konstruktoru pro typ deklarativní způsobem.  
  
Následující příklady ukazují, jak používat inicializátory objektů s pojmenovaných objektů. Procesy, které kompilátor inicializátorech objektu tak, že první přístup k výchozí konstruktor instance a potom zpracování inicializace člena. Proto pokud konstruktor bez parametrů je deklarován jako `private` ve třídě, se nezdaří inicializátory objektů, které vyžadují přístup public.
  
Pokud definujete anonymního typu je nutné použít inicializátor objektu. Další informace najdete v tématu [jak: Vrácení podmnožin vlastností elementu v dotazu](how-to-return-subsets-of-element-properties-in-a-query.md).  
  
## <a name="example"></a>Příklad  

Následující příklad ukazuje způsob inicializace nového `StudentName` typu pomocí inicializátory objektů. V tomto příkladu nastaví vlastnosti `StudentName` typu:
  
[!code-csharp-interactive[InitializerObjectExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToObjectInitializers.cs#HowToObjectInitializers)]  

Inicializátory objektů je možné nastavit v objektu indexery. Následující příklad definuje `BaseballTeam` třídu, která používá indexeru k získání a nastavení hráče na různých místech. Inicializátor můžete přiřadit přehrávače, založené na zkratka pro umístění, nebo číslo používané pro každou pozici baseballu přehledů výkonnostních metrik:

[!code-csharp-interactive[InitializerIndexerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToIndexInitializer.cs#HowToIndexInitializer)]  

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Inicializátory objektu a kolekce](object-and-collection-initializers.md)
