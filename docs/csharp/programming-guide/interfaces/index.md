---
title: Rozhraní (Průvodce programováním v C#)
ms.date: 08/21/2018
helpviewer_keywords:
- interfaces [C#]
- C# language, interfaces
ms.assetid: 2feda177-ce11-432d-81b4-d50f5f35fd37
ms.openlocfilehash: fba595cca4d96fc9cd0f0966f45d1668181b2ec9
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43873312"
---
# <a name="interfaces-c-programming-guide"></a>Rozhraní (Průvodce programováním v C#)

Rozhraní obsahuje definice pro skupiny související funkce, která [třídy](../../language-reference/keywords/class.md) nebo [struktura](../../language-reference/keywords/struct.md) můžete implementovat.
  
Pomocí rozhraní mohou například zahrnovat chování z několika zdrojů ve třídě. Tato funkce je důležitá v jazyce C#, protože jazyk nepodporuje vícenásobnou dědičnost tříd. Kromě toho musíte použít rozhraní, pokud chcete simulovat dědičnosti struktur, protože nemůže ve skutečnosti dědit z jiné třídy nebo struktury.  
  
Definujte rozhraní pomocí [rozhraní](../../language-reference/keywords/interface.md) – klíčové slovo. jak ukazuje následující příklad.  
  
[!code-csharp[csProgGuideInheritance#47](../classes-and-structs/codesnippet/CSharp/interfaces_1.cs)]  

Název struktury musí být platný C# [název identifikátoru](../inside-a-program/identifier-names.md). Podle úmluvy názvy rozhraní, které začínají na velké `I`.

Každá třída nebo struktura, která implementuje <xref:System.IEquatable%601> rozhraní může obsahovat definici <xref:System.IEquatable%601.Equals%2A> metodu, která odpovídá podpisu, který určuje rozhraní. V důsledku toho se můžete spolehnout na třídu, která implementuje `IEquatable<T>` tak, aby obsahovala `Equals` metodu, pomocí kterého můžete určit, zda je rovna jiná instance stejné třídy instance třídy.  
  
Definice `IEquatable<T>` neposkytuje implementaci pro `Equals`. Rozhraní definuje pouze podpis. Tímto způsobem je podobný abstraktní třída, ve kterém jsou všechny metody abstraktní rozhraní v jazyce C#. Třídy nebo struktury může implementovat více rozhraní, ale třída může dědit pouze jednu třídu, abstraktní nebo ne. Proto to s využitím rozhraní, můžete zahrnout chování z různých zdrojů ve třídě.  
  
Další informace o abstraktních tříd naleznete v tématu [abstraktní a zapečetěné třídy a členové](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
Rozhraní může obsahovat metody, vlastnosti, události, indexerů nebo libovolnou kombinaci těchto typů čtyři člena. Odkazy na příklady naleznete v části [související oddíly](../interfaces/index.md#BKMK_RelatedSections). Rozhraní nemůže obsahovat konstanty, pole, operátory, konstruktory instancí, finalizační metody nebo typy. Jsou automaticky veřejné členy rozhraní a nemůžou obsahovat žádné modifikátory přístupu. Nemůže být také členy [statické](../../language-reference/keywords/static.md).  
  
Implementovat člen rozhraní, odpovídající člen implementující třídu musí být nestatická, veřejná a mají stejný název a signaturu jako člena rozhraní.  
  
Pokud třída nebo struktura implementuje rozhraní, třídy nebo struktury musí poskytnout implementaci pro všechny členy, které definuje rozhraní. Rozhraní samotné poskytuje funkce, které tato třída nebo struktura může dědit tak, jak, že funkce základní třídy lze dědit. Nicméně pokud základní třída implementuje rozhraní, dědí všechny třídy, která je odvozena ze základní třídy tuto implementaci.  
  
Následující příklad ukazuje implementaci IEquatable < T\> rozhraní. Implementující třída `Car`, musí poskytnout implementaci položky <xref:System.IEquatable%601.Equals%2A> metody.  
  
[!code-csharp[csProgGuideInheritance#48](../classes-and-structs/codesnippet/CSharp/interfaces_2.cs)]  
  
Vlastnostmi a indexery třídy můžete definovat další přistupující objekty vlastnosti nebo indexovacího člena, který je definován v rozhraní. Například rozhraní může deklarovat vlastnost, která má [získat](../../language-reference/keywords/get.md) přistupujícího objektu. Třída, která implementuje rozhraní může deklarovat stejnou vlastnost s oběma `get` a [nastavit](../../language-reference/keywords/set.md) přistupujícího objektu. Pokud vlastnost nebo indexovací člen používá explicitní implementaci, musí odpovídat přístupové objekty. Další informace o explicitní implementaci, najdete v části [explicitní implementaci rozhraní](explicit-interface-implementation.md) a [vlastností rozhraní](../classes-and-structs/interface-properties.md).  

Rozhraní můžou implementovat jiná rozhraní. Třída může obsahovat rozhraní více než jednou prostřednictvím základní třídy, které dědí nebo rozhraní, které implementují rozhraní. Však třídu poskytnout implementaci rozhraní jenom jeden čas a pouze pokud třída deklaruje rozhraní jako součást definice třídy (`class ClassName : InterfaceName`). Pokud rozhraní se dědí, protože dědí základní třídu, která implementuje rozhraní, poskytuje základní třídy implementace členů rozhraní. Odvozená třída může znovu implementovat členy rozhraní namísto použití zděděná implementace.  
  
Základní třídu můžete také implementovat členy rozhraní pomocí virtuální členy. Odvozené třídy v takovém případě můžete změnit chování rozhraní tak, že přepíšete virtuální členy. Další informace o virtuální členy v tématu [polymorfismus](../classes-and-structs/polymorphism.md).  
  
## <a name="interfaces-summary"></a>Přehled rozhraní

Rozhraní má následující vlastnosti:  

- Rozhraní je jako abstraktní základní třídu. Každá třída nebo struktura, která implementuje rozhraní musí implementovat všechny její členy.
- Rozhraní nemůže být přímo vytvořeny instance. Její členy jsou implementované všechny třídy nebo struktury, která implementuje rozhraní.
- Rozhraní může obsahovat události, indexery, metody a vlastnosti.
- Rozhraní obsahovat žádnou implementaci metody.
- Třídy nebo struktury může implementovat více rozhraní. Třída může dědit základní třídy a také implementovat jedno nebo více rozhraní.

## <a name="in-this-section"></a>V tomto oddílu

[Implementace explicitního rozhraní](explicit-interface-implementation.md)  
 Vysvětluje, jak vytvořit člena třídy, která je specifická pro rozhraní.  
  
 [Postupy: Explicitní implementace členů rozhraní](how-to-explicitly-implement-interface-members.md)  
 Obsahuje příklad toho, jak explicitní implementace členů rozhraní.  
  
 [Postupy: Explicitní implementace členů dvou rozhraní](how-to-explicitly-implement-members-of-two-interfaces.md)  
 Obsahuje příklad toho, jak explicitní implementace členů rozhraní s dědičnosti.  
  
##  <a name="BKMK_RelatedSections"></a> Související oddíly

- [Vlastnosti rozhraní](../classes-and-structs/interface-properties.md)  
- [Indexery v rozhraní](../indexers/indexers-in-interfaces.md)  
- [Postupy: implementace událostí rozhraní](../events/how-to-implement-interface-events.md)  
- [Třídy a struktury](../classes-and-structs/index.md)  
- [Dědičnost](../classes-and-structs/inheritance.md)  
- [Metody](../classes-and-structs/methods.md)  
- [Polymorfismus](../classes-and-structs/polymorphism.md)  
- [Abstraktní a uzavřené třídy a jejich členové](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
- [Vlastnosti](../classes-and-structs/properties.md)  
- [Události](../events/index.md)  
- [Indexery](../indexers/index.md)  
  
## <a name="featured-book-chapter"></a>Doporučená kapitola knihy

[Rozhraní](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652489%28v%3Dorm.10%29) v [Learning C# 3.0: Master the Fundamentals of C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v%253dorm.10%29)

## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../index.md)
- [Dědičnost](../classes-and-structs/inheritance.md)
- [Názvy identifikátorů](../inside-a-program/identifier-names.md)
