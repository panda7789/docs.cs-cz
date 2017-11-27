---
title: "Rozhraní (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- interfaces [C#]
- C# language, interfaces
ms.assetid: 2feda177-ce11-432d-81b4-d50f5f35fd37
caps.latest.revision: "45"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f14d4bf48d117558a4019a8f016e194af27a9ebf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="interfaces-c-programming-guide"></a>Rozhraní (Průvodce programováním v C#)
Rozhraní obsahuje definice pro skupinu související funkce, [třída](../../../csharp/language-reference/keywords/class.md) nebo [struktura](../../../csharp/language-reference/keywords/struct.md) můžete implementovat.  
  
 Pomocí rozhraní může například obsahovat chování z více zdrojů v třídě. Tuto možnost je důležité v jazyce C#, protože jazyk nepodporuje vícenásobná dědičnost tříd. Kromě toho musíte použít rozhraní, pokud chcete simulovat dědičnosti pro struktury, protože nemůže ve skutečnosti Zdědit z jiné třídy nebo struktury.  
  
 Definovat rozhraní pomocí [rozhraní](../../../csharp/language-reference/keywords/interface.md) – klíčové slovo, jak ukazuje následující příklad.  
  
 [!code-csharp[csProgGuideInheritance#47](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interfaces_1.cs)]  
  
 Každá třída nebo struktura, která implementuje <xref:System.IEquatable%601> rozhraní musí obsahovat definici <xref:System.IEquatable%601.Equals%2A> metodu, která odpovídá podpisu, který určuje rozhraní. V důsledku toho se můžete spolehnout na třídu, která implementuje `IEquatable<T>` tak, aby obsahovala `Equals` metodu, pomocí kterého můžete instance třídy určují, zda je rovno jiná instance stejné třídy.  
  
 Definice `IEquatable<T>` neposkytuje implementace pro `Equals`. Rozhraní definuje pouze podpis. Tento způsob je podobná abstraktní třídu, ve kterém jsou všechny metody abstraktní rozhraní v jazyce C#. Třídě nebo struktuře můžete implementovat více rozhraní, ale třídu může dědit vlastnosti pouze jednu třídu abstraktní, nebo ne. Proto můžete pomocí rozhraní zahrnout chování z více zdrojů v třídě.  
  
 Další informace o abstraktní třídy najdete v tématu [abstraktní a zapečetěné třídy a jejich členové](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
 Rozhraní může obsahovat metody, vlastnosti, události, indexery nebo libovolnou kombinaci těchto typů čtyři člen. Odkazy na příklady najdete v části [související oddíly](../../../csharp/programming-guide/interfaces/index.md#BKMK_RelatedSections). Rozhraní nemůže obsahovat konstanty, pole, operátory, konstruktory instancí, finalizační metody nebo typů. Členové rozhraní jsou automaticky veřejné a nemůžou obsahovat žádné modifikátory přístupu. Členové také nemohou být [statické](../../../csharp/language-reference/keywords/static.md).  
  
 K implementaci člena rozhraní, musíte odpovídající členem implementující třídu být nestatická, veřejná a mít stejný název a podpis jako člen rozhraní.  
  
 Když třídě nebo struktuře implementuje rozhraní, třídu nebo strukturu třeba poskytnout implementaci pro všechny členy, kteří definuje rozhraní. Rozhraní samotného poskytuje žádné funkce, které třídě nebo struktuře může dědit vlastnosti způsobem, že může dědit vlastnosti funkce základní třídy. Ale pokud základní třída implementuje rozhraní, dědí všechny třídy, která je odvozena ze základní třídy tuto implementaci.  
  
 Následující příklad ukazuje implementaci IEquatable < T\> rozhraní. Implementující třídu `Car`, musíte poskytnout implementaci <xref:System.IEquatable%601.Equals%2A> metoda.  
  
 [!code-csharp[csProgGuideInheritance#48](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interfaces_2.cs)]  
  
 Vlastnostmi a indexery třídy můžete definovat další přistupující objekty pro vlastnost nebo indexer, který je definován v rozhraní. Například může rozhraní deklarovat vlastnost, která má [získat](../../../csharp/language-reference/keywords/get.md) přistupujícího objektu. Třídu, která implementuje rozhraní můžou deklarovat stejnou vlastnost s oběma `get` a [nastavit](../../../csharp/language-reference/keywords/set.md) přistupujícího objektu. Pokud jsou vlastnost nebo indexer používá explicitní implementace, musí odpovídat přistupující objekty. Další informace o explicitní implementaci, najdete v části [explicitní implementace rozhraní](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md) a [rozhraní vlastnosti](../../../csharp/programming-guide/classes-and-structs/interface-properties.md).  
  
 Rozhraní můžete implementovat dalších rozhraní. Třída může zahrnovat rozhraní několikrát prostřednictvím základní třídy, které dědí nebo prostřednictvím rozhraní, které implementují rozhraní. Ale třída může poskytovat implementace rozhraní pouze jeden čas a pouze pokud třída deklaruje rozhraní jako součást definice třídy (`class ClassName : InterfaceName`). Pokud je zděděn rozhraní, protože je zděděno základní třídu, která implementuje rozhraní, poskytuje základní třídu implementace členů rozhraní. Odvozené třídy mohou však přeimplementovat členové rozhraní místo použití zděděné implementace.  
  
 Základní třída může také implementace členů rozhraní pomocí virtuální členy. Odvozené třídy v takovém případě můžete změnit chování rozhraní přepisování virtuální členy. Další informace o virtuální členové najdete v tématu [polymorfismus](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).  
  
## <a name="interfaces-summary"></a>Přehled rozhraní  
 Rozhraní má následující vlastnosti:  
  
-   Rozhraní je jako abstraktní základní třídu. Každá třída nebo struktura, která implementuje rozhraní musí implementovat všichni její členové.  
  
-   Rozhraní nemůže být přímo vytvořeny instance. Členy jsou implementované všechny třídě nebo struktuře, která implementuje rozhraní.  
  
-   Rozhraní může obsahovat události, indexery, metod a vlastností.  
  
-   Rozhraní obsahovat žádné implementace metod.  
  
-   Třídě nebo struktuře můžete implementovat více rozhraní. Třídy lze dědit vlastnosti základní třída a také implementovat jednu nebo více rozhraní.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Implementace explicitního rozhraní](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)  
 Vysvětluje, jak vytvořit člena třídy, které jsou specifické pro rozhraní.  
  
 [Postupy: explicitní implementace členů rozhraní](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)  
 Poskytuje příklad explicitní implementace členů rozhraní.  
  
 [Postupy: explicitní implementace členů dvou rozhraní](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)  
 Poskytuje příklad explicitní implementace členů rozhraní s použitím dědičnosti.  
  
##  <a name="BKMK_RelatedSections"></a>Související oddíly  
  
-   [Vlastnosti rozhraní](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)  
  
-   [Indexery v rozhraní](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)  
  
-   [Postupy: implementace událostí rozhraní](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
  
-   [Dědičnost](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
  
-   [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [Polymorfismus](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
  
-   [Abstraktní a uzavřené třídy a jejich členové](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
  
-   [Vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)  
  
-   [Události](../../../csharp/programming-guide/events/index.md)  
  
-   [Indexery](../../../csharp/programming-guide/indexers/index.md)  
  
## <a name="featured-book-chapter"></a>Doporučená kapitola knihy  
 [Rozhraní](http://msdn.microsoft.com/library/orm-9780596521066-01-13.aspx) v [Learning C# 3.0: Master the Fundamentals of C# 3.0](http://msdn.microsoft.com/library/orm-9780596521066-01.aspx)  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Dědičnost](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
