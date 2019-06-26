---
title: Třídy – C# Průvodce programováním
ms.custom: seodec18
description: Seznamte se s typy třídy a jak je vytvořit
ms.date: 08/21/2018
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
ms.openlocfilehash: ad19099242a3bedbb7283219dfd7733db13231ec
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2019
ms.locfileid: "67398594"
---
# <a name="classes-c-programming-guide"></a>Třídy (Průvodce programováním v C#)

## <a name="reference-types"></a>Odkazové typy  
Typ, který je definován jako [třídy](../../../csharp/language-reference/keywords/class.md) je *odkazovat na typ*. V době běhu při deklarování proměnné typu odkazu proměnná obsahuje hodnotu [null](../../../csharp/language-reference/keywords/null.md) dokud explicitně nevytvoříte instanci třídy pomocí [nové](../../../csharp/language-reference/operators/new-operator.md) operátor nebo jí nepřiřadíte objekt kompatibilní typ, který byl možná vytvořen jinde, jak je znázorněno v následujícím příkladu:

```csharp
//Declaring an object of type MyClass.
MyClass mc = new MyClass();

//Declaring another object of the same type, assigning it the value of the first object.
MyClass mc2 = mc;
```

Při vytvoření objektu je dostatečná paměť je přidělena na spravované haldě pro tento konkrétní objekt a proměnná obsahuje pouze odkaz na umístění uvedené objektu. Typy na spravované haldě zdržovat při přidělování i při jejich převzetí pomocí funkce správy automatické paměti modulu CLR, která se nazývá *uvolňování*. Nicméně uvolňování paměti je také vysoce optimalizováno a ve většině případů nedojde k vytvoření problému s výkonem. Další informace o uvolňování paměti naleznete v tématu [paměti automatické správy a uvolňování paměti kolekce](../../../standard/garbage-collection/gc.md).  
  
## <a name="declaring-classes"></a>Deklarace tříd

 Třídy jsou deklarované pomocí [třídy](../../../csharp/language-reference/keywords/class.md) – klíčové slovo, za nímž následuje jedinečný identifikátor, jak je znázorněno v následujícím příkladu:

 ```csharp
//[access modifier] - [class] - [identifier]
 public class Customer
 {
    // Fields, properties, methods and events go here...
 }
```

 `class` – Klíčové slovo předchází úroveň přístupu. Protože [veřejné](../../language-reference/keywords/public.md) se používá v tomto případě Kdokoliv může vytvořit instance této třídy. Následuje název třídy `class` – klíčové slovo. Název třídy musí být platný C# [název identifikátoru](../inside-a-program/identifier-names.md). Zbývající část definice je tělo třídy, kde jsou definovány chování a data. Pole, vlastnosti, metody a události na třídu se souhrnně označují jako *členy třídy*.  
  
## <a name="creating-objects"></a>Vytváření objektů

Přestože se někdy používají Zaměnitelně, třídy a objekt jsou různé věci. Třída definuje typ objektu, ale není samotného objektu. Objekt je konkrétní entity podle třídy a jsou někdy označovány jako instance třídy.  
  
 Objekty mohou být vytvořeny pomocí [nové](../../language-reference/operators/new-operator.md) – klíčové slovo, za nímž následuje název třídy, která objekt bude založen na, tímto způsobem:  

 ```csharp
 Customer object1 = new Customer();
 ```

 Když je vytvořena instance třídy, odkaz na objekt je předán zpět na programátorovi. V předchozím příkladu `object1` je odkaz na objekt, který je založen na `Customer`. Tento odkaz odkazuje na nový objekt, ale neobsahuje vlastní data objektu. Ve skutečnosti můžete vytvořit odkaz na objekt bez vytvoření všech objektů:  
 
```csharp
 Customer object2;
```
 
 Nedoporučujeme ale, vytváření odkazů na objekty, jako je například tento, které není odkaz na objekt, protože se pokouší získat přístup k objektu prostřednictvím odkazu selže v době běhu. Však můžete provést odkazu k odkazování na objekt, buď tak, že vytvoříte nový objekt, nebo jejím přiřazením k existující objekt, jako je například tento:  

 ```csharp
 Customer object3 = new Customer();
 Customer object4 = object3;
```
  
 Tento kód vytvoří dva odkazy na objekty, které odkazují na stejný objekt. Proto všechny změny provedené prostřednictvím objektu `object3` se projeví v následné použití `object4`. Protože objekty, které jsou založeny na třídách jsou uvedené odkazem, třídy jsou označovány jako referenční typy.  
  
## <a name="class-inheritance"></a>Dědičnost tříd  

Třídy plně podporují *dědičnosti*, základní charakteristiku objektově orientované programování. Při vytváření třídy můžete dědit ze kteréhokoli rozhraní nebo třídu, která není definován jako [zapečetěné](../../../csharp/language-reference/keywords/sealed.md), a jiné třídy mohou dědit z vaší třídy a přepsat třídy virtuální metody.

Dědičnost se dá udělat pomocí *odvození*, což znamená, že třída je deklarována pomocí *základní třída* ze které dědí data a chování. Základní třída zadaná přidáním dvojtečku a název základní třídy za název odvozené třídy takto:  

 ```csharp
 public class Manager : Employee
 {
     // Employee fields, properties, methods and events are inherited
     // New Manager fields, properties, methods and events go here...
 }
 ```

Třída deklaruje základní třídu, zdědí všechny členy základní třídy s výjimkou konstruktorů. Další informace najdete v tématu [dědičnosti](inheritance.md).
  
Na rozdíl od C++ třídy v jazyce C# může dědit pouze přímo z jedné základní třídy. Ale protože samotný základní třída může dědit z jiné třídy, třída může nepřímo dědit více základních tříd. Třída navíc můžete přímo implementovat více než jedno rozhraní. Další informace najdete v tématu [rozhraní](../interfaces/index.md).  
  
Třídy lze deklarovat [abstraktní](../../language-reference/keywords/abstract.md). Abstraktní třída obsahuje abstraktní metody, které mají definici podpis ale nemá žádnou implementaci. Nelze vytvořit instanci abstraktní třídy. Je možné použít pouze prostřednictvím odvozené třídy, které implementují abstraktní metody. Naopak [zapečetěné](../../language-reference/keywords/sealed.md) třídy nepovoluje ostatní třídy odvozovat z něj. Další informace najdete v tématu [abstraktní a zapečetěné třídy a členové](abstract-and-sealed-classes-and-class-members.md).  
  
Definice tříd lze rozdělit do jiných zdrojových souborů. Další informace najdete v tématu [částečné třídy a metody](partial-classes-and-methods.md).  
  
## <a name="example"></a>Příklad

Následující příklad definuje veřejnou třídu, která obsahuje [automaticky implementované vlastnosti](auto-implemented-properties.md), metoda a speciální metoda volá konstruktor. Další informace najdete v tématu [vlastnosti](properties.md), [metody](methods.md), a [konstruktory](constructors.md) témata. Instance třídy jsou pak vytvořeny s `new` – klíčové slovo.  
  
[!code-csharp[Class Example](~/samples/snippets/csharp/programming-guide/classes-and-structs/class-example.cs)] 
  
## <a name="c-language-specification"></a>Specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Objektově orientované programování](../concepts/object-oriented-programming.md)
- [Polymorfismus](polymorphism.md)
- [Názvy identifikátorů](../inside-a-program/identifier-names.md)
- [Členové](members.md)
- [Metody](methods.md)
- [Konstruktory](constructors.md)
- [Finalizační metody](destructors.md)
- [Objekty](objects.md)
