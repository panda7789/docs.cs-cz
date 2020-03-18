---
title: Konstruktory – programovací příručka Jazyka C#
ms.date: 05/05/2017
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
ms.openlocfilehash: 8eedfaed111f01cc2ec55a2f42df66d4588bd42f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399789"
---
# <a name="constructors-c-programming-guide"></a>Konstruktory (Průvodce programováním v C#)

Vždy, když je vytvořena [třída](../../language-reference/keywords/class.md) nebo [struktura,](../../language-reference/builtin-types/struct.md) jeho konstruktor se nazývá. Třída nebo struktura může mít více konstruktorů, které berou různé argumenty. Konstruktory umožňují programátorovi nastavit výchozí hodnoty, omezit vytváření instancí a psát kód, který je flexibilní a snadno čitelný. Další informace a příklady naleznete [v tématu Použití konstruktorů](./using-constructors.md) a [konstruktorů instancí](./instance-constructors.md).  

## <a name="parameterless-constructors"></a>Konstruktory bez parametrů
  
Pokud nezadáte konstruktor pro vaši třídu, C# vytvoří jeden ve výchozím nastavení, který konkretizuje objekt a nastaví členské proměnné na výchozí hodnoty uvedené v [výchozím hodnotách c# typy](../../language-reference/builtin-types/default-values.md) článku. Pokud nezadáte konstruktor pro strukturu, C# spoléhá na *implicitní konstruktor bez parametrů* automaticky inicializovat každé pole na výchozí hodnotu. Další informace a příklady naleznete v tématu [Instance konstruktory](instance-constructors.md).  

## <a name="constructor-syntax"></a>Syntaxe konstruktoru

Konstruktor je metoda, jejíž název je stejný jako název jeho typu. Jeho podpis metody zahrnuje pouze název metody a seznam parametrů; neobsahuje návratový typ. Následující příklad ukazuje konstruktor pro `Person`třídu s názvem .

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

Pokud konstruktor lze implementovat jako jeden příkaz, můžete použít [definici těla výrazu](../statements-expressions-operators/expression-bodied-members.md). Následující příklad definuje `Location` třídu, jejíž konstruktor má jeden parametr řetězce s názvem *name*. Definice těla výrazu přiřadí `locationName` argument k poli.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a>Statické konstruktory

V předchozích příkladech jsou zobrazeny všechny konstruktory instancí, které vytvářejí nový objekt. Třída nebo struktura může mít také statický konstruktor, který inicializuje statické členy typu.  Statické konstruktory jsou bezparametrické. Pokud nezadáte statický konstruktor pro inicializaci statických polí, kompilátor Jazyka C# inicializuje statická pole na výchozí hodnotu uvedenou v článku [Výchozí hodnoty c# typů.](../../language-reference/builtin-types/default-values.md)

Následující příklad používá statický konstruktor k inicializaci statického pole.

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

Můžete také definovat statický konstruktor s definicí těla výrazu, jak ukazuje následující příklad.

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

Další informace a příklady naleznete [v tématu Statické konstruktory](./static-constructors.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Použití konstruktorů](./using-constructors.md)  
  
 [Konstruktory instancí](./instance-constructors.md)  
  
 [Soukromé konstruktory](./private-constructors.md)  
  
 [Statické konstruktory](./static-constructors.md)  
  
 [Jak napsat konstruktor kopie](./how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Třídy a struky](./index.md)
- [Finalizační metody](./destructors.md)
- [Statické](../../language-reference/keywords/static.md)
- [Proč inicializační spustit v opačném pořadí jako konstruktory? První část](https://docs.microsoft.com/archive/blogs/ericlippert/why-do-initializers-run-in-the-opposite-order-as-constructors-part-one)
