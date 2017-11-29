---
title: "Třídy – průvodce C#"
description: "Další informace o typy třídy a jak vytvořit"
keywords: "Rozhraní .NET, rozhraní .NET core, C#"
author: BillWagner
ms.author: wiwagn
ms.date: 10/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 95c686ba-ae4f-440e-8e94-0dbd6e04d11f
ms.openlocfilehash: 13cbd3a5b53ea9b0f1acb22684b6a28639d00751
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="classes"></a>Třídy
A *třída* je konstruktor, který umožňuje vytvořit vlastní typy společně seskupením proměnné jiné typy, metod a události. Třída je jako plán, podle kterého. Definuje data a chování typu. Pokud třída není deklarovaný jako statický, kód klienta můžete ji použít tak, že vytvoříte *objekty* nebo *instance* které jsou přiřazeny k proměnné. Proměnná zůstane v paměti, dokud všechny odkazy na ni se dostala mimo rozsah. V té době modulu CLR označí je vhodné pro uvolňování paměti. Pokud třída je deklarován jako [statické](language-reference/keywords/static.md), pak existuje pouze jedna kopie v paměti a kód klienta pouze k němu přístup prostřednictvím třídy samostatně, není *proměnnou instance*. Další informace najdete v tématu [statické třídy a jejich členové](programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  

## <a name="reference-types"></a>Odkazové typy  
Typ, který je definován jako [třída](language-reference/keywords/class.md) je *odkazují na typ*. V době běhu, když deklarovat proměnnou typu odkaz, proměnná obsahuje hodnotu [null](language-reference/keywords/null.md) dokud explicitní vytvoření instance objektu pomocí [nové](language-reference/keywords/new.md) operátor, nebo ji přiřadit objekt která byla vytvořena jinam pomocí [nové](language-reference/keywords/new.md), jak je znázorněno v následujícím příkladu:  

[!code-csharp[Reference Types](../../samples/snippets/csharp/concepts/classes/reference-type.cs)]
  
Při vytvoření objektu je paměť přidělená v spravovaná halda a proměnná obsahuje pouze odkaz na objekt umístění. Typy v haldě spravované vyžadují režijní náklady na jejich přidělení i při jsou uvolnit pomocí funkce správy paměti automatické modulu CLR, která se označuje jako *uvolňování paměti*. Ale je také vysoce optimalizovaný uvolňování paměti a ve většině scénářů, nedojde k vytvoření problémy výkonem. Další informace o uvolňování paměti najdete v tématu [automatické paměti správy a uvolňování paměti kolekce](../standard/garbage-collection/gc.md).  
  
Typy odkazů, plně podporovat *dědičnosti*, základní vlastnosti objektově orientované programování. Při vytváření třídy lze dědit z jakéhokoli rozhraní nebo třídu, která není definován jako [zapečetěné](language-reference/keywords/sealed.md), a ostatní třídy lze dědit z vaší třídy a přepsat virtuální metody. Další informace najdete v tématu [dědičnosti](programming-guide/classes-and-structs/inheritance.md).

## <a name="declaring-classes"></a>Deklarace tříd  
Třídy jsou deklarovány s použitím [třída](language-reference/keywords/class.md) – klíčové slovo, jak je znázorněno v následujícím příkladu:  
  
[!code-csharp[Declaring Classes](../../samples/snippets/csharp/concepts/classes/declaring-classes.cs)]  
  
**Třída** – klíčové slovo předchází – modifikátor přístupu. Protože [veřejné](language-reference/keywords/public.md) se používá v tomto případě každý, kdo může vytvářet objekty z této třídy. Následuje název třídy **třída** – klíčové slovo. Zbývající část definice je tělo třídy, kde jsou definovány chování a data. Pole, vlastnosti, metod a události na třídě se souhrnně označují jako *třídy členy*.  
  
## <a name="creating-objects"></a>Vytváření objektů  
Třída definuje typ objektu, ale není objekt sám sebe. Objekt je založeno na třídě konkrétní entita a se někdy označuje jako instance třídy.  
  
Objekty mohou být vytvořeny pomocí [nové](language-reference/keywords/new.md) – klíčové slovo a název třídy, která objekt budou založeny na, jako jsou to:  
  
[!code-csharp[Creating Objects](../../samples/snippets/csharp/concepts/classes/creating-objects.cs)]   
  
Když je vytvořena instance třídy, odkaz na objekt je předán zpět do programátorů. V předchozím příkladu `object1` je odkaz na objekt, který je založen na `Customer`. Tento odkaz odkazuje na nový objekt, ale neobsahuje samotná data objektu. Ve skutečnosti můžete vytvořit odkaz na objekt bez vytvoření objektu vůbec:  
  
[!code-csharp[Creating Objects](../../samples/snippets/csharp/concepts/classes/creating-objects2.cs)]  
  
Nedoporučujeme vytváření odkazy na objekty, jako je například tento jeden, která neodkazuje na objekt, protože při pokusu o přístup k objektu pomocí odkazu v době běhu selže. Však můžete provést odkazu odkazovat na objekt, buď tím, že vytvoříte nový objekt, nebo jeho přiřazení k existující objekt, jako je tato:  
  
[!code-csharp[Creating Objects](../../samples/snippets/csharp/concepts/classes/creating-objects3.cs)]  
  
Tento kód vytvoří dvě odkazy na objekty, které odkazují na stejný objekt. Proto všechny změny provedené prostřednictvím objektu `object3` se projeví v následné použití `object4`. Protože objekty, které jsou založeny na třídy jsou označovány pomocí odkazu, třídy jsou známé jako odkazové typy.  
  
## <a name="class-inheritance"></a>Dědičnost třídy  
Dědičnost se dá udělat pomocí *odvození*, což znamená, že třída je deklarovaná pomocí *základní třída* z který dědí dat a chování. Základní třída je určena připojením dvojtečkou a název základní třídy následující název odvozené třídy takto:  
  
[!code-csharp[Inheritance](../../samples/snippets/csharp/concepts/classes/inheritance.cs)]  
  
Třída deklaruje základní třídu, dědí všechny členy základní třídy, s výjimkou konstruktorů.  
  
Na rozdíl od C++ lze pouze přímo třídu v jazyce C# dědit z jedné základní třídy. Ale protože sám základní třídy mohou dědit z jiné třídy, třídy mohou nepřímo dědit vícenásobné základní třídy. Kromě toho třída může implementovat přímo více než jedno rozhraní. Další informace najdete v tématu [rozhraní](programming-guide/interfaces/index.md).  
  
Třídu lze deklarovat [abstraktní](language-reference/keywords/abstract.md). Abstraktní třída obsahuje abstraktní metody, které mají definici podpis, ale žádné implementace. Nelze vytvořit instanci abstraktní třídy. Je možné použít pouze prostřednictvím odvozené třídy, které implementují abstraktní metody. Naopak [zapečetěné](language-reference/keywords/sealed.md) třídy není povoleno ostatní třídy k odvozování z něj. Další informace najdete v tématu [abstraktní a uzavřené třídy a členy třídy](programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
Definice tříd můžete rozdělit mezi jiné zdrojové soubory. Další informace najdete v tématu [definice třídu](programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
 
## <a name="example"></a>Příklad
V následujícím příkladu je definována veřejnou třídu, která obsahuje jednoho pole, metodu a speciální metodu s názvem konstruktor. Další informace najdete v tématu [konstruktory](programming-guide/classes-and-structs/constructors.md). Instance třídy je pak vytvářet pomocí **nové** – klíčové slovo.

[!code-csharp[Class Example](../../samples/snippets/csharp/concepts/classes/class-example.cs)]  
  
## <a name="c-language-specification"></a>specifikace jazyka C#  
Další informace najdete v tématu [specifikace jazyka C#](language-reference/language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také  
[Průvodce programováním C#](programming-guide/index.md)   
[Polymorfismus](programming-guide/classes-and-structs/polymorphism.md)   
[Členy třídy a struktury](programming-guide/classes-and-structs/members.md)   
[Metody třídy a struktury](programming-guide/classes-and-structs/methods.md)   
[Konstruktory](programming-guide/classes-and-structs/constructors.md)   
[Finalizační metody](programming-guide/classes-and-structs/destructors.md)   
[Objekty](programming-guide/classes-and-structs/objects.md)

