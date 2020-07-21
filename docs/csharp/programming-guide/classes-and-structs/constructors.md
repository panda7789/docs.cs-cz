---
title: Konstruktory – Průvodce programováním v C#
description: Konstruktor v jazyce C# je volán při vytvoření třídy nebo struktury. Použijte konstruktory k nastavení výchozích hodnot, omezení vytváření instancí a psaní flexibilního, snadno čitelného kódu.
ms.date: 05/05/2017
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
ms.openlocfilehash: 4a731e648143f5e0ecf8860625962d8baa29fe26
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474901"
---
# <a name="constructors-c-programming-guide"></a>Konstruktory (Průvodce programováním v C#)

Pokaždé, když se vytvoří [Třída](../../language-reference/keywords/class.md) nebo [Struktura](../../language-reference/builtin-types/struct.md) , zavolá se její konstruktor. Třída nebo struktura může mít více konstruktorů, které přijímají různé argumenty. Konstruktory umožňují programátorovi nastavit výchozí hodnoty, omezit vytváření instancí a napsat kód, který je flexibilní a snadno čitelný. Další informace a příklady naleznete v tématu [using](./using-constructors.md) a [konstruktory instancí](./instance-constructors.md).  

## <a name="parameterless-constructors"></a>Konstruktory bez parametrů
  
Pokud neposkytnete konstruktor pro třídu, C# vytvoří jednu ve výchozím nastavení, která vytvoří instanci objektu a nastaví proměnné členů na výchozí hodnoty, jak je uvedeno v článku [výchozí hodnoty typů C#](../../language-reference/builtin-types/default-values.md) . Pokud neposkytnete konstruktor pro vaši strukturu, jazyk C# při automatické inicializaci každého pole na jeho výchozí hodnotu spoléhá na *implicitní konstruktor bez parametrů* . Další informace a příklady naleznete v tématu [konstruktory instancí](instance-constructors.md).  

## <a name="constructor-syntax"></a>Syntaxe konstruktoru

Konstruktor je metoda, jejíž název je stejný jako název jeho typu. Signatura metody obsahuje pouze název metody a její seznam parametrů; nezahrnuje návratový typ. Následující příklad ukazuje konstruktor pro třídu s názvem `Person` .

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

Pokud konstruktor může být implementován jako jediný příkaz, můžete použít [definici těla výrazu](../statements-expressions-operators/expression-bodied-members.md). Následující příklad definuje třídu, `Location` jejíž konstruktor má jeden řetězcový parametr s názvem *Name*. Definice těla výrazu přiřadí argument `locationName` poli.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a>Statické konstruktory

Předchozí příklady mají všechny zobrazené konstruktory instancí, které vytvoří nový objekt. Třída nebo struktura může mít také statický konstruktor, který inicializuje statické členy typu.  Statické konstruktory jsou bez parametrů. Pokud neposkytnete statický konstruktor pro inicializaci statických polí, kompilátor C# inicializuje statická pole na jejich výchozí hodnotu, jak je uvedeno v článku [výchozí hodnoty typů C#](../../language-reference/builtin-types/default-values.md) .

Následující příklad používá statický konstruktor pro inicializaci statického pole.

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

Můžete také definovat statický konstruktor pomocí definice těla výrazu, jak ukazuje následující příklad.

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

Další informace a příklady naleznete v tématu [statické konstruktory](./static-constructors.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Použití konstruktorů](./using-constructors.md)  
  
 [Konstruktory instancí](./instance-constructors.md)  
  
 [Soukromé konstruktory](./private-constructors.md)  
  
 [Statické konstruktory](./static-constructors.md)  
  
 [Jak zapsat kopírovací konstruktor](./how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Třídy a struktury](./index.md)
- [Finalizační metody](./destructors.md)
- [static](../../language-reference/keywords/static.md)
- [Proč jsou Inicializátory spouštěny v opačném pořadí jako konstruktory? První část](https://docs.microsoft.com/archive/blogs/ericlippert/why-do-initializers-run-in-the-opposite-order-as-constructors-part-one)
