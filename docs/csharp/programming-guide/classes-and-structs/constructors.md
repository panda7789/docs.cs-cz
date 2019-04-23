---
title: Konstruktory - C# Průvodce programováním
ms.custom: seodec18
ms.date: 05/05/2017
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
ms.openlocfilehash: becc3fc8a75cd4d2d5e0c1db2858b15b8b61ae20
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59978572"
---
# <a name="constructors-c-programming-guide"></a>Konstruktory (Průvodce programováním v C#)
Pokaždé, když se [třídy](../../../csharp/language-reference/keywords/class.md) nebo [– struktura](../../../csharp/language-reference/keywords/struct.md) je vytvořen, se nazývá konstruktoru. Třídy nebo struktury může mít více konstruktorů, které přijímají různé argumenty. Konstruktory povolit programátorovi, aby nastavení výchozích hodnot, omezení vytváření instancí a napsat kód, který je flexibilní a snadno čitelný. Další informace a příklady najdete v tématu [pomocí konstruktorů](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) a [konstruktory instancí](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  

## <a name="parameterless-constructors"></a>Konstruktory bez parametrů.
  
Pokud nezadáte konstruktor pro třídu, C# vytvoří ve výchozím nastavení vytvoří instanci objektu, který nastaví proměnné členů na výchozí hodnoty, jak je uvedeno v [tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md). Pokud nezadáte konstruktor pro struktury, C# spoléhá na *implicitní konstruktor bez parametrů* automaticky inicializovat každé pole typu hodnota na výchozí hodnotu, jak je uvedeno v [výchozí hodnoty Tabulka](../../../csharp/language-reference/keywords/default-values-table.md). Další informace a příklady najdete v tématu [konstruktory instancí](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  

## <a name="constructor-syntax"></a>Syntaxe konstruktoru

Konstruktor je metoda, jejíž název je stejný jako název jeho typu. Jeho podpis metody zahrnuje pouze název metody a jejího seznamu parametrů; Návratový typ neobsahuje. Následující příklad ukazuje konstruktor pro třídu s názvem `Person`.

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

Pokud konstruktor je možné implementovat jako jeden příkaz, můžete použít [definice těla výrazu](../statements-expressions-operators/expression-bodied-members.md). Následující příklad definuje `Location` třídy, jejíž konstruktor má jeden řetězcový parametr s názvem *název*. Definice textu výrazu přiřadí argument `locationName` pole.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a>Statické konstruktory

V předchozích příkladech mají všechny zobrazené instančních konstruktorech, které vytvoří nový objekt. Statický konstruktor, který inicializuje statické členy typu může mít také třídy nebo struktury.  Statické konstruktory jsou konstruktor bez parametrů. Pokud nezadáte statický konstruktor k inicializaci statická pole, kompilátor jazyka C# poskytne výchozí statický konstruktor, který inicializuje statická pole na výchozí hodnoty, jak je uvedeno v [tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md). 

Následující příklad používá statický konstruktor k inicializaci statické pole.

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

Můžete také definovat statický konstruktor s definici tělo výrazu, jak ukazuje následující příklad. 

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

Další informace a příklady najdete v tématu [statické konstruktory](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Použití konstruktorů](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)  
  
 [Konstruktory instancí](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)  
  
 [Soukromé konstruktory](../../../csharp/programming-guide/classes-and-structs/private-constructors.md)  
  
 [Statické konstruktory](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)  
  
 [Postupy: Zápis kopírovacího konstruktoru](../../../csharp/programming-guide/classes-and-structs/how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Finalizační metody](../../../csharp/programming-guide/classes-and-structs/destructors.md)
- [static](../../../csharp/language-reference/keywords/static.md)
- [Proč inicializátory spustit v opačném pořadí jako konstruktory? První část](https://blogs.msdn.microsoft.com/ericlippert/2008/02/15/why-do-initializers-run-in-the-opposite-order-as-constructors-part-one)
