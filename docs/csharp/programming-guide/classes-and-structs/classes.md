---
title: Třídy (Průvodce programováním v C#)
description: Další informace o typy třídy a jejich vytvoření
ms.date: 04/05/2018
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
ms.openlocfilehash: 688736aa8556719789b02d7db25858f442b4309e
ms.sourcegitcommit: 895c7602386a6dfe7ca4facce3d965b27e5c6e87
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2018
---
# <a name="classes-c-programming-guide"></a>Třídy (Průvodce programováním v C#)
A *třída* je konstruktor, který umožňuje vytvořit vlastní typy společně seskupením proměnné jiné typy, metod a události. Třída je jako plán, podle kterého. Definuje data a chování typu. Pokud třída není deklarovaný jako statický, kód klienta můžete vytvořit *instance* ho. Tyto instance jsou *objekty* které jsou přiřazeny k proměnné. Instance třídy zůstane v paměti, dokud všechny odkazy na ni se dostala mimo rozsah. V té době modulu CLR označí je vhodné pro uvolňování paměti. Pokud třída je deklarován jako [statické](../../../csharp/language-reference/keywords/static.md), nelze vytvořit instance, a kód klienta pouze k němu přístup pomocí vlastní třídy. Další informace najdete v tématu [statické třídy a statické členy třídy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  

## <a name="reference-types"></a>Odkazové typy  
Typ, který je definován jako [třída](../../../csharp/language-reference/keywords/class.md) je *odkazují na typ*. V době běhu, když deklarovat proměnnou typu odkaz, proměnná obsahuje hodnotu [null](../../../csharp/language-reference/keywords/null.md) dokud explicitní vytvoření instance třídy pomocí [nové](../../../csharp/language-reference/keywords/new.md) operátor, nebo ji přiřadit objekt, byl vytvořen jinde, jak je znázorněno v následujícím příkladu:

```csharp
MyClass mc = new MyClass();
MyClass mc2 = mc;
```

Při vytvoření objektu je paměť přidělená v spravovaná halda a proměnná obsahuje pouze odkaz na objekt umístění. Typy v haldě spravované vyžadují režijní náklady na jejich přidělení i při jsou uvolnit pomocí funkce správy paměti automatické modulu CLR, která se označuje jako *uvolňování paměti*. Ale je také vysoce optimalizovaný uvolňování paměti a ve většině scénářů, nedojde k vytvoření problémy výkonem. Další informace o uvolňování paměti najdete v tématu [automatické paměti správy a uvolňování paměti kolekce](../../../standard/garbage-collection/gc.md).  
  
## <a name="declaring-classes"></a>Deklarace tříd  
 Třídy jsou deklarovány s použitím [třída](../../../csharp/language-reference/keywords/class.md) – klíčové slovo, jak je znázorněno v následujícím příkladu:

 ```csharp
 public class Customer
 {
    // Fields, properties, methods and events go here...
 }
```

 `class` – Klíčové slovo předchází úroveň přístupu. Protože [veřejné](../../../csharp/language-reference/keywords/public.md) se používá v tomto případě Kdokoliv může vytvořit instance této třídy. Následuje název třídy `class` – klíčové slovo. Zbývající část definice je tělo třídy, kde jsou definovány chování a data. Pole, vlastnosti, metod a události na třídě se souhrnně označují jako *třídy členy*.  
  
## <a name="creating-objects"></a>Vytváření objektů  
 I když se někdy používají zcela zaměnitelným významem, třídy a objekt jsou různých věcí. Třída definuje typ objektu, ale není objekt sám sebe. Objekt je založeno na třídě konkrétní entita a se někdy označuje jako instance třídy.  
  
 Objekty mohou být vytvořeny pomocí [nové](../../../csharp/language-reference/keywords/new.md) – klíčové slovo a název třídy, která objekt budou založeny na, jako jsou to:  

 ```csharp
 Customer object1 = new Customer();
 ```
  
 Když je vytvořena instance třídy, odkaz na objekt je předán zpět do programátorů. V předchozím příkladu `object1` je odkaz na objekt, který je založen na `Customer`. Tento odkaz odkazuje na nový objekt, ale neobsahuje samotná data objektu. Ve skutečnosti můžete vytvořit odkaz na objekt bez vytvoření objektu vůbec:  
  
  ```csharp
  Customer object2;
  ```
  
 Nedoporučujeme vytváření odkazy na objekty, jako je tato, které není odkaz na objekt, protože při pokusu o přístup k objektu pomocí odkazu v době běhu selže. Však můžete provést odkazu odkazovat na objekt, buď tím, že vytvoříte nový objekt, nebo jeho přiřazení k existující objekt, jako je tato:  

 ```csharp
 Customer object3 = new Customer();
 Customer object4 = object3;
 ```
  
 Tento kód vytvoří dvě odkazy na objekty, které odkazují na stejný objekt. Proto všechny změny provedené prostřednictvím objektu `object3` odrazí se to v následné použití `object4`. Protože objekty, které jsou založeny na třídy jsou označovány pomocí odkazu, třídy jsou známé jako odkazové typy.  
  
## <a name="class-inheritance"></a>Dědičnost tříd  

 Třídy plně podporují *dědičnosti*, základní vlastnosti objektově orientované programování. Při vytváření třídy lze dědit z jakéhokoli rozhraní nebo třídu, která není definován jako [zapečetěné](../../../csharp/language-reference/keywords/sealed.md), a ostatní třídy lze dědit z vaší třídy a přepsat virtuální metody třídy.

 Dědičnost se dá udělat pomocí *odvození*, což znamená, že třída je deklarovaná pomocí *základní třída* z který dědí dat a chování. Základní třída je určena připojením dvojtečkou a název základní třídy následující název odvozené třídy takto:  

 ```csharp
 public class Manager : Employee
 {
     // Employee fields, properties, methods and events are inherited
     // New Manager fields, properties, methods and events go here...
 }
 ```
  
 Třída deklaruje základní třídu, dědí všechny členy základní třídy, s výjimkou konstruktorů. Další informace najdete v tématu [dědičnosti](../../../csharp/programming-guide/classes-and-structs/inheritance.md).
  
 Na rozdíl od C++ lze pouze přímo třídu v jazyce C# dědit z jedné základní třídy. Ale protože sám základní třídy mohou dědit z jiné třídy, třídy mohou nepřímo dědit vícenásobné základní třídy. Kromě toho třída může implementovat přímo více než jedno rozhraní. Další informace najdete v tématu [rozhraní](../../../csharp/programming-guide/interfaces/index.md).  
  
 Třídu lze deklarovat [abstraktní](../../../csharp/language-reference/keywords/abstract.md). Abstraktní třída obsahuje abstraktní metody, které mají definici podpis, ale žádné implementace. Nelze vytvořit instanci abstraktní třídy. Je možné použít pouze prostřednictvím odvozené třídy, které implementují abstraktní metody. Naopak [zapečetěné](../../../csharp/language-reference/keywords/sealed.md) třídy není povoleno ostatní třídy k odvozování z něj. Další informace najdete v tématu [abstraktní a zapečetěné třídy a jejich členové](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
 Definice tříd můžete rozdělit mezi jiné zdrojové soubory. Další informace najdete v tématu [částečné třídy a metody](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu definuje veřejnou třídu, která obsahuje [automaticky implementované vlastnosti](auto-implemented-properties.md), metodu a speciální metodu s názvem konstruktor. Další informace najdete v tématu [vlastnosti](properties.md), [metody](methods.md), a [konstruktory](constructors.md) témata. Instance třídy jsou pak vytvořena s `new` – klíčové slovo.  
  
 [!code-csharp[Class Example](~/samples/snippets/csharp/programming-guide/classes-and-structs/class-example.cs)] 
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Objektově orientované programování](../concepts/object-oriented-programming.md)  
 [Polymorfismus](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
 [Členové](../../../csharp/programming-guide/classes-and-structs/members.md)  
 [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [Finalizační metody](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
 [Objekty](../../../csharp/programming-guide/classes-and-structs/objects.md)
