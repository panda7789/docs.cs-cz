---
title: Třídy - Průvodce programováním jazyka C#
description: Informace o typech tříd a jejich vytváření
ms.date: 08/21/2018
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
ms.openlocfilehash: aadf555fb47963eab323bbb6105227c5b119e6f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170309"
---
# <a name="classes-c-programming-guide"></a>Třídy (Průvodce programováním v C#)

## <a name="reference-types"></a>Odkazové typy  
Typ, který je definován jako [třída,](../../language-reference/keywords/class.md) je *typ odkazu*. Za běhu, když deklarujete proměnnou typu odkazu, proměnná obsahuje hodnotu [null,](../../language-reference/keywords/null.md) dokud explicitně nevytvoříte instanci třídy pomocí [nového](../../language-reference/operators/new-operator.md) operátoru, nebo jí přiřadíte objekt kompatibilního typu, který mohl být vytvořen jinde, jak je znázorněno v následujícím příkladu:

```csharp
//Declaring an object of type MyClass.
MyClass mc = new MyClass();

//Declaring another object of the same type, assigning it the value of the first object.
MyClass mc2 = mc;
```

Při vytvoření objektu je na spravované haldě pro daný objekt přidělendostatek paměti a proměnná obsahuje pouze odkaz na umístění uvedeného objektu. Typy na spravované haldy vyžadují režii, jak při přidělení, tak při jejich uvolnění funkcí automatické správy paměti CLR, která je známá jako *uvolňování paměti*. Uvolňování paměti je však také vysoce optimalizované a ve většině scénářů nevytváří problém s výkonem. Další informace o uvolňování paměti naleznete v [tématu Automatická správa paměti a uvolňování paměti](../../../standard/garbage-collection/gc.md).  
  
## <a name="declaring-classes"></a>Deklarace tříd

 Třídy jsou deklarovány pomocí klíčového slova [třídy](../../language-reference/keywords/class.md) následovaného jedinečným identifikátorem, jak je znázorněno v následujícím příkladu:

 ```csharp
//[access modifier] - [class] - [identifier]
 public class Customer
 {
    // Fields, properties, methods and events go here...
 }
```

 Klíčovému `class` slovu předchází úroveň přístupu. Vzhledem k tomu, [že veřejné](../../language-reference/keywords/public.md) se používá v tomto případě, kdokoli můžete vytvořit instance této třídy. Název třídy následuje za `class` klíčovým slovem. Název třídy musí být platný [název identifikátoru](../inside-a-program/identifier-names.md)Jazyka C# . Zbývající část definice je tělo třídy, kde jsou definovány chování a data. Pole, vlastnosti, metody a události ve třídě jsou souhrnně označovány jako *členové třídy*.  
  
## <a name="creating-objects"></a>Vytváření objektů

I když jsou někdy používány zaměnitelně, třída a objekt jsou různé věci. Třída definuje typ objektu, ale není samotnýobjekt. Objekt je konkrétní entita založená na třídě a je někdy označována jako instance třídy.  
  
 Objekty lze vytvořit pomocí [novéklíčové](../../language-reference/operators/new-operator.md) slovo následuje název třídy, která bude založena na objektu, například takto:  

 ```csharp
 Customer object1 = new Customer();
 ```

 Při vytvoření instance třídy je odkaz na objekt předán zpět programátorovi. V předchozím příkladu je odkaz na `object1` objekt, `Customer`který je založen na . Tento odkaz odkazuje na nový objekt, ale neobsahuje samotná data objektu. Ve skutečnosti můžete vytvořit odkaz na objekt bez vytvoření objektu vůbec:  

```csharp
 Customer object2;
```

 Nedoporučujeme vytvářet odkazy na objekty, jako je tento, které neodkazují na objekt, protože pokus o přístup k objektu prostřednictvím takového odkazu se nezdaří za běhu. Takový odkaz však lze odkazovat na objekt, buď vytvořením nového objektu, nebo jeho přiřazením k existujícímu objektu, například takto:  

 ```csharp
 Customer object3 = new Customer();
 Customer object4 = object3;
```
  
 Tento kód vytvoří dva odkazy na objekty, které oba odkazují na stejný objekt. Proto všechny změny objektu `object3` provedené prostřednictvím se `object4`projeví v následné použití . Vzhledem k tomu, že objekty, které jsou založeny na třídách, jsou označovány odkazem, jsou třídy označovány jako typy odkazů.  
  
## <a name="class-inheritance"></a>Dědičnost třídy  

Třídy plně podporují *dědičnost*, základní charakteristiku objektově orientovaného programování. Při vytváření třídy můžete dědit z jakéhokoli jiného rozhraní nebo třídy, která není definována jako [zapečetěné](../../language-reference/keywords/sealed.md)a jiné třídy mohou dědit z vaší třídy a přepsat třídy virtuální metody.

Dědičnost se provádí pomocí *odvození*, což znamená, že třída je deklarována pomocí *základní třídy,* ze které dědí data a chování. Základní třída je určena připojením dvojtečky a názvu základní třídy za názvem odvozené třídy, například takto:  

 ```csharp
 public class Manager : Employee
 {
     // Employee fields, properties, methods and events are inherited
     // New Manager fields, properties, methods and events go here...
 }
 ```

Když třída deklaruje základní třídu, dědí všechny členy základní třídy s výjimkou konstruktorů. Další informace naleznete v [tématu Dědičnost](inheritance.md).
  
Na rozdíl od Jazyka C++ může třída v jazyce C# přímo dědit pouze z jedné základní třídy. Však vzhledem k tomu, že základní třída může dědit z jiné třídy, třída může nepřímo dědit více základních tříd. Kromě toho třídy můžete přímo implementovat více než jedno rozhraní. Další informace naleznete v [tématu Rozhraní](../interfaces/index.md).  
  
Třída může být deklarována [jako abstraktní](../../language-reference/keywords/abstract.md). Abstraktní třída obsahuje abstraktní metody, které mají definici podpisu, ale žádnou implementaci. Abstraktní třídy nelze vytvořit instanci. Lze je použít pouze prostřednictvím odvozených tříd, které implementují abstraktní metody. Naproti tomu [zapečetěné](../../language-reference/keywords/sealed.md) třídy neumožňuje jiné třídy odvodit z něj. Další informace naleznete [v tématu Abstract and Sealed Classes and Class Members](abstract-and-sealed-classes-and-class-members.md).  
  
Definice tříd lze rozdělit mezi různé zdrojové soubory. Další informace naleznete [v tématu Částečné třídy a metody](partial-classes-and-methods.md).  
  
## <a name="example"></a>Příklad

Následující příklad definuje veřejnou třídu, která obsahuje [automaticky implementovanou vlastnost](auto-implemented-properties.md), metodu a speciální metodu nazvanou konstruktor. Další informace naleznete v [tématech Vlastnosti](properties.md), [Metody](methods.md)a [Konstruktory](constructors.md) témata. Instance třídy jsou pak vytvořena instance s `new` klíčovým slovem.  
  
[!code-csharp[Class Example](~/samples/snippets/csharp/programming-guide/classes-and-structs/class-example.cs)]
  
## <a name="c-language-specification"></a>Specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Objektově orientované programování](../concepts/object-oriented-programming.md)
- [Polymorfismus](polymorphism.md)
- [Názvy identifikátorů](../inside-a-program/identifier-names.md)
- [Členové](members.md)
- [Metody](methods.md)
- [Konstruktory](constructors.md)
- [Finalizační metody](destructors.md)
- [Objekty](objects.md)
