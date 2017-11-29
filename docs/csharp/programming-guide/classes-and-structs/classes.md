---
title: "Třídy (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
caps.latest.revision: "40"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 37e810fc5a5397a6b9240346ac28505b11b1e817
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="classes-c-programming-guide"></a>Třídy (Průvodce programováním v C#)
A *třída* je konstruktor, který umožňuje vytvořit vlastní typy společně seskupením proměnné jiné typy, metod a události. Třída je jako plán, podle kterého. Definuje data a chování typu. Pokud třída není deklarovaný jako statický, kód klienta můžete ji použít tak, že vytvoříte *objekty* nebo *instance* které jsou přiřazeny k proměnné. Proměnná zůstane v paměti, dokud všechny odkazy na ni se dostala mimo rozsah. V té době modulu CLR označí je vhodné pro uvolňování paměti. Pokud třída je deklarován jako [statické](../../../csharp/language-reference/keywords/static.md), pak existuje pouze jedna kopie v paměti a kód klienta pouze k němu přístup prostřednictvím třídy samostatně, není *proměnnou instance*. Další informace najdete v tématu [statické třídy a statické členy třídy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Na rozdíl od struktury, třídy podporu *dědičnosti*, základní vlastnosti objektově orientované programování. Další informace najdete v tématu [dědičnosti](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
## <a name="declaring-classes"></a>Deklarace tříd  
 Třídy jsou deklarovány s použitím [třída](../../../csharp/language-reference/keywords/class.md) – klíčové slovo, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideObjects#79](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_1.cs)]  
  
 `class` – Klíčové slovo předchází úroveň přístupu. Protože [veřejné](../../../csharp/language-reference/keywords/public.md) se používá v tomto případě každý, kdo může vytvářet objekty z této třídy. Následuje název třídy `class` – klíčové slovo. Zbývající část definice je tělo třídy, kde jsou definovány chování a data. Pole, vlastnosti, metod a události na třídě se souhrnně označují jako *třídy členy*.  
  
## <a name="creating-objects"></a>Vytváření objektů  
 I když se někdy používají zcela zaměnitelným významem, třídy a objekt jsou různých věcí. Třída definuje typ objektu, ale není objekt sám sebe. Objekt je založeno na třídě konkrétní entita a se někdy označuje jako instance třídy.  
  
 Objekty mohou být vytvořeny pomocí [nové](../../../csharp/language-reference/keywords/new.md) – klíčové slovo a název třídy, která objekt budou založeny na, jako jsou to:  
  
 [!code-csharp[csProgGuideObjects#80](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_2.cs)]  
  
 Když je vytvořena instance třídy, odkaz na objekt je předán zpět do programátorů. V předchozím příkladu `object1` je odkaz na objekt, který je založen na `Customer`. Tento odkaz odkazuje na nový objekt, ale neobsahuje samotná data objektu. Ve skutečnosti můžete vytvořit odkaz na objekt bez vytvoření objektu vůbec:  
  
 [!code-csharp[csProgGuideObjects#81](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_3.cs)]  
  
 Nedoporučujeme vytváření odkazy na objekty, jako je tato, které není odkaz na objekt, protože při pokusu o přístup k objektu pomocí odkazu v době běhu selže. Však můžete provést odkazu odkazovat na objekt, buď tím, že vytvoříte nový objekt, nebo jeho přiřazení k existující objekt, jako je tato:  
  
 [!code-csharp[csProgGuideObjects#82](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_4.cs)]  
  
 Tento kód vytvoří dvě odkazy na objekty, které odkazují na stejný objekt. Proto všechny změny provedené prostřednictvím objektu `object3` se projeví v následné použití `object4`. Protože objekty, které jsou založeny na třídy jsou označovány pomocí odkazu, třídy jsou známé jako odkazové typy.  
  
## <a name="class-inheritance"></a>Dědičnost tříd  
 Dědičnost se dá udělat pomocí *odvození*, což znamená, že třída je deklarovaná pomocí *základní třída* z který dědí dat a chování. Základní třída je určena připojením dvojtečkou a název základní třídy následující název odvozené třídy takto:  
  
 [!code-csharp[csProgGuideObjects#83](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_5.cs)]  
  
 Třída deklaruje základní třídu, dědí všechny členy základní třídy, s výjimkou konstruktorů.  
  
 Na rozdíl od C++ lze pouze přímo třídu v jazyce C# dědit z jedné základní třídy. Ale protože sám základní třídy mohou dědit z jiné třídy, třídy mohou nepřímo dědit vícenásobné základní třídy. Kromě toho třída může implementovat přímo více než jedno rozhraní. Další informace najdete v tématu [rozhraní](../../../csharp/programming-guide/interfaces/index.md).  
  
 Třídu lze deklarovat [abstraktní](../../../csharp/language-reference/keywords/abstract.md). Abstraktní třída obsahuje abstraktní metody, které mají definici podpis, ale žádné implementace. Nelze vytvořit instanci abstraktní třídy. Je možné použít pouze prostřednictvím odvozené třídy, které implementují abstraktní metody. Naopak [zapečetěné](../../../csharp/language-reference/keywords/sealed.md) třídy není povoleno ostatní třídy k odvozování z něj. Další informace najdete v tématu [abstraktní a zapečetěné třídy a jejich členové](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
 Definice tříd můžete rozdělit mezi jiné zdrojové soubory. Další informace najdete v tématu [částečné třídy a metody](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
## <a name="description"></a>Popis  
 V následujícím příkladu je definována veřejnou třídu, která obsahuje jednoho pole, metodu a speciální metodu s názvem konstruktor. Další informace najdete v tématu [konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md). Instance třídy je pak vytvářet pomocí `new` – klíčové slovo.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideObjects#84](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_6.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Objektově orientované programování](../concepts/object-oriented-programming.md)  
 [Polymorfismus](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
 [Členy](../../../csharp/programming-guide/classes-and-structs/members.md)  
 [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [Finalizační metody](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
 [Objekty](../../../csharp/programming-guide/classes-and-structs/objects.md)
