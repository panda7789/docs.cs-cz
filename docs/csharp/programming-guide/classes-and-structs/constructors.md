---
title: Konstruktory (Průvodce programováním v C#)
ms.date: 05/05/2017
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
ms.openlocfilehash: 40e3b73221159e191bd34c928e7513f715fa3370
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33314031"
---
# <a name="constructors-c-programming-guide"></a>Konstruktory (Průvodce programováním v C#)
Vždy, když [třída](../../../csharp/language-reference/keywords/class.md) nebo [struktura](../../../csharp/language-reference/keywords/struct.md) je vytvořen, se nazývá jeho konstruktoru. Třídě nebo struktuře může mít několik konstruktory, které nepřebírají různých argumenty. Konstruktory povolit programátorů nastavit výchozí hodnoty, omezení vytváření instancí a napsat kód, který je flexibilní a snadno čitelný. Další informace a příklady naleznete v tématu [pomocí konstruktorů](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) a [konstruktory instancí](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  

## <a name="default-constructors"></a>Výchozí konstruktory
  
Pokud nezadáte konstruktor pro třídu, C# vytvoří ve výchozím nastavení, která vytvoří instanci objektu a nastaví členské proměnné na výchozí hodnoty, jak je uvedeno v [tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md). Pokud nezadáte konstruktor pro vaši strukturu, C# využívá *implicitní výchozí konstruktor* automaticky inicializovat každé pole typu hodnota na výchozí hodnotu, jak je uvedeno v [tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md). Další informace a příklady naleznete v tématu [konstruktory instancí](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  

## <a name="constructor-syntax"></a>Syntaxe – konstruktor

Konstruktor je metoda, jejíž název je stejný jako název daného typu. Podpis metoda obsahuje pouze název metody a její seznam parametrů; Návratový typ neobsahuje. Následující příklad ukazuje v konstruktoru pro třídu s názvem `Person`.

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

Pokud konstruktor může být implementováno jako jediný příkaz, můžete použít [výraz text definice](../statements-expressions-operators/expression-bodied-members.md). V následujícím příkladu definuje `Location` třídu, jejíž konstruktor má jednoho řetězce parametr s názvem *název*. Definice textu výraz přiřadí argument `locationName` pole.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a>Statické konstruktory

V předchozích příkladech mají všechny uvedené instance konstruktory, které vytvořit nový objekt. Statický konstruktor, který inicializuje statické členy typu může mít také třídě nebo struktuře.  Statické konstruktory jsou bez parametrů. Pokud nezadáte statického konstruktoru k chybě při inicializaci statických polí, kompilátor jazyka C# poskytne výchozí statický konstruktor, který inicializuje statická pole na jejich výchozí hodnoty, jak je uvedeno v [tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md). 

Následující příklad používá statický konstruktor k chybě při inicializaci statické pole.

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

Můžete také definovat statického konstruktoru pomocí výrazu textu definice, jak ukazuje následující příklad. 

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

Další informace a příklady naleznete v tématu [statické konstruktory](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Použití konstruktorů](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)  
  
 [Konstruktory instancí](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)  
  
 [Soukromé konstruktory](../../../csharp/programming-guide/classes-and-structs/private-constructors.md)  
  
 [Statické konstruktory](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)  
  
 [Postupy: Zápis kopírovacího konstruktoru](../../../csharp/programming-guide/classes-and-structs/how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Finalizační metody](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
 [static](../../../csharp/language-reference/keywords/static.md)  
 [Proč inicializátory spustit v opačném pořadí jako konstruktory? První část](https://blogs.msdn.microsoft.com/ericlippert/2008/02/15/why-do-initializers-run-in-the-opposite-order-as-constructors-part-one)
