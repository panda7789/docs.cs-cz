---
title: Třídy – Průvodce programováním v C#
description: Přečtěte si o typech tříd a o tom, jak je vytvořit
ms.date: 08/21/2018
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
ms.openlocfilehash: d726ab3a882d2e6913fa69c7b82f1d6db78dd47d
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102044"
---
# <a name="classes-c-programming-guide"></a>Třídy (Průvodce programováním v C#)

## <a name="reference-types"></a>Odkazové typy  
Typ, který je definován jako [Třída](../../language-reference/keywords/class.md) , je *odkazový typ*. V době běhu, pokud deklarujete proměnnou typu odkazu, proměnná obsahuje hodnotu [null](../../language-reference/keywords/null.md) , dokud explicitně nevytvoříte instanci třídy pomocí operátoru [New](../../language-reference/operators/new-operator.md) , nebo přiřadíte objekt kompatibilního typu, který mohl být vytvořen jinde, jak je znázorněno v následujícím příkladu:

```csharp
//Declaring an object of type MyClass.
MyClass mc = new MyClass();

//Declaring another object of the same type, assigning it the value of the first object.
MyClass mc2 = mc;
```

Když je objekt vytvořen, je k dispozici dostatek paměti na spravované haldě pro daný objekt a proměnná obsahuje pouze odkaz na umístění daného objektu. Typy na spravované haldě vyžadují režii při jejich přidělování a v případě, že jsou uvolněny automatickou funkcí správy paměti modulu CLR, která se označuje jako *uvolňování*paměti. Uvolňování paměti je ale také vysoce optimalizované a ve většině scénářů nevytváří problém s výkonem. Další informace o uvolňování paměti najdete v tématu [Automatická správa paměti a uvolňování](../../../standard/garbage-collection/fundamentals.md)paměti.  
  
## <a name="declaring-classes"></a>Deklarace tříd

 Třídy jsou deklarovány pomocí klíčového slova [Class](../../language-reference/keywords/class.md) následovaný jedinečným identifikátorem, jak je znázorněno v následujícím příkladu:

 ```csharp
//[access modifier] - [class] - [identifier]
 public class Customer
 {
    // Fields, properties, methods and events go here...
 }
```

 `class`Klíčovému slovu předchází úroveň přístupu. Vzhledem k tomu, že v tomto případě je použita možnost [Public](../../language-reference/keywords/public.md) , může kdokoli vytvořit instance této třídy. Název třídy následuje za `class` klíčovým slovem. Název třídy musí být platný [název identifikátoru](../inside-a-program/identifier-names.md)C#. Zbytek definice je tělo třídy, kde jsou definovány chování a data. Pole, vlastnosti, metody a události třídy jsou souhrnně označovány jako *členy třídy*.  
  
## <a name="creating-objects"></a>Vytváření objektů

I když se někdy používají jako zaměnitelné, třída a objekt jsou různé věci. Třída definuje typ objektu, ale není to samotný objekt. Objekt je konkrétní entita založená na třídě a je někdy označována jako instance třídy.  
  
 Objekty lze vytvořit pomocí klíčového slova [New](../../language-reference/operators/new-operator.md) následovaného názvem třídy, na které bude objekt založen, podobně jako toto:  

 ```csharp
 Customer object1 = new Customer();
 ```

 Když je vytvořena instance třídy, odkaz na objekt je předán zpět do programátora. V předchozím příkladu `object1` je odkaz na objekt, který je založen na `Customer` . Tento odkaz odkazuje na nový objekt, ale neobsahuje data objektu samotné. Ve skutečnosti můžete vytvořit odkaz na objekt, aniž byste vůbec vytvořili objekt:  

```csharp
 Customer object2;
```

 Nedoporučujeme vytvářet odkazy na objekty, jako je takový, který neodkazuje na objekt, protože při pokusu o přístup k objektu prostřednictvím takového odkazu se v době běhu nezdaří. Takový odkaz však lze použít pro odkazování na objekt, buď vytvořením nového objektu, nebo přiřazením k existujícímu objektu, například:  

 ```csharp
 Customer object3 = new Customer();
 Customer object4 = object3;
```
  
 Tento kód vytvoří dva odkazy na objekty, které odkazují na stejný objekt. Proto se všechny změny objektu provedené prostřednictvím `object3` projeví v následných použitích `object4` . Vzhledem k tomu, že objekty, které jsou založeny na třídách, jsou odkazovány odkazem, třídy jsou označovány jako typy odkazů.  
  
## <a name="class-inheritance"></a>Dědičnost tříd  

Třídy plně podporují *Dědičnost*, základní charakteristiky objektově orientovaného programování. Při vytváření třídy můžete dědit z jakéhokoli jiného rozhraní nebo třídy, která není definována jako [sealed](../../language-reference/keywords/sealed.md), a jiné třídy mohou dědit z vaší třídy a přepsat virtuální metody třídy.

Dědičnost je provedeno pomocí *odvození*, což znamená, že třída je deklarována pomocí *základní třídy* , ze které dědí data a chování. Základní třída je určena připojením dvojtečky a názvem základní třídy za názvem odvozené třídy, například takto:  

 ```csharp
 public class Manager : Employee
 {
     // Employee fields, properties, methods and events are inherited
     // New Manager fields, properties, methods and events go here...
 }
 ```

Když třída deklaruje základní třídu, dědí všechny členy základní třídy s výjimkou konstruktorů. Další informace najdete v tématu [Dědičnost](inheritance.md).
  
Na rozdíl od jazyka C++ může třída v jazyce C# přímo dědit pouze z jedné základní třídy. Protože však základní třída může dědit z jiné třídy, třída může nepřímo zdědit více základních tříd. Kromě toho třída může přímo implementovat více než jedno rozhraní. Další informace naleznete v tématu [rozhraní](../interfaces/index.md).  
  
Třída může být deklarována jako [abstraktní](../../language-reference/keywords/abstract.md). Abstraktní třída obsahuje abstraktní metody, které mají definici signatury, ale žádnou implementaci. Nelze vytvořit instanci abstraktních tříd. Lze je použít pouze prostřednictvím odvozených tříd, které implementují abstraktní metody. Naproti tomu [zapečetěná](../../language-reference/keywords/sealed.md) třída nepovoluje odvození jiných tříd. Další informace naleznete v tématu [abstraktní a zapečetěné třídy a členy třídy](abstract-and-sealed-classes-and-class-members.md).  
  
Definice tříd mohou být rozděleny mezi různé zdrojové soubory. Další informace naleznete v tématu [částečné třídy a metody](partial-classes-and-methods.md).  
  
## <a name="example"></a>Příklad

Následující příklad definuje veřejnou třídu, která obsahuje [automaticky implementovanou vlastnost](auto-implemented-properties.md), metodu a speciální metodu, která se nazývá konstruktor. Další informace naleznete v tématech [vlastnosti](properties.md), [metody](methods.md)a [konstruktory](constructors.md) . Instance třídy se pak vytvoří s `new` klíčovým slovem.  
  
[!code-csharp[Class Example](~/samples/snippets/csharp/programming-guide/classes-and-structs/class-example.cs)]
  
## <a name="c-language-specification"></a>Specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Objektově orientované programování](../concepts/object-oriented-programming.md)
- [Polymorfismus](polymorphism.md)
- [Názvy identifikátorů](../inside-a-program/identifier-names.md)
- [Členové](members.md)
- [Metody](methods.md)
- [Konstruktory](constructors.md)
- [Finalizační metody](destructors.md)
- [Objekty](objects.md)
