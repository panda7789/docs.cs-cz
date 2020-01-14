---
title: Rozhraní – C# Průvodce programováním
ms.date: 08/21/2018
helpviewer_keywords:
- interfaces [C#]
- C# language, interfaces
ms.assetid: 2feda177-ce11-432d-81b4-d50f5f35fd37
ms.openlocfilehash: 43e37dc4b0977542add05c8cc13e2d7fa47b19bf
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937491"
---
# <a name="interfaces-c-programming-guide"></a>Rozhraní (Průvodce programováním v C#)

Rozhraní obsahuje definice pro skupinu souvisejících funkcí, které musí implementovat neabstraktní [Třída](../../language-reference/keywords/class.md) nebo [Struktura](../../language-reference/keywords/struct.md) .
  
Pomocí rozhraní můžete například zahrnout chování z více zdrojů ve třídě. Tato funkce je důležitá v C# , protože jazyk nepodporuje vícenásobnou dědičnost tříd. Kromě toho je nutné použít rozhraní, pokud chcete simulovat dědičnost pro struktury, protože nemohou být ve skutečnosti děděny z jiné struktury nebo třídy.  
  
Rozhraní definujete pomocí klíčového slova [rozhraní](../../language-reference/keywords/interface.md) . Jak ukazuje následující příklad.  
  
 [!code-csharp[csProgGuideInheritance#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#47)]  

Název rozhraní musí být platný C# [název identifikátoru](../inside-a-program/identifier-names.md). Podle konvence názvy rozhraní začínají velkým `I`.

Všechny třídy nebo struktury, které implementují rozhraní <xref:System.IEquatable%601> musí obsahovat definici pro metodu <xref:System.IEquatable%601.Equals%2A>, která odpovídá signatuře, kterou určuje rozhraní. V důsledku toho můžete spočítat třídu, která implementuje `IEquatable<T>`, aby obsahovala metodu `Equals`, se kterou může instance třídy určit, zda je rovna jiné instanci stejné třídy.  
  
Definice `IEquatable<T>` neposkytuje implementaci pro `Equals`. Třída nebo struktura může implementovat více rozhraní, ale třída může dědit pouze z jedné třídy.
  
Další informace o abstraktních třídách naleznete v tématu [abstraktní a zapečetěné třídy a členy třídy](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
Rozhraní mohou obsahovat metody, vlastnosti, události, indexery nebo libovolnou kombinaci těchto čtyř typů členů. Odkazy na příklady najdete v části [související oddíly](./index.md#BKMK_RelatedSections). Rozhraní nemůže obsahovat konstanty, pole, operátory, konstruktory instancí, finalizační metody ani typy. Členy rozhraní jsou automaticky veřejné a nemohou obsahovat žádné modifikátory přístupu. Členy také nemohou být [statické](../../language-reference/keywords/static.md).  
  
Chcete-li implementovat člena rozhraní, musí být odpovídající člen třídy implementace Public, nestatický a musí mít stejný název a signaturu jako člen rozhraní.  
  
Pokud třída nebo struktura implementuje rozhraní, třída nebo struktura musí poskytovat implementaci pro všechny členy, které definuje rozhraní. Samotné rozhraní neposkytuje žádnou funkci, kterou třída nebo struktura může dědit v tom, jak může dědit funkčnost základní třídy. Nicméně pokud základní třída implementuje rozhraní, jakákoliv třída odvozená od základní třídy zdědí tuto implementaci.  
  
Následující příklad ukazuje implementaci rozhraní <xref:System.IEquatable%601>. Implementující třída `Car`musí poskytovat implementaci <xref:System.IEquatable%601.Equals%2A> metody.  
  
 [!code-csharp[csProgGuideInheritance#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#48)]  
  
Vlastnosti a indexery třídy mohou definovat nadbytečné přistupující objekty pro vlastnost nebo indexer, který je definován v rozhraní. Rozhraní může například deklarovat vlastnost, která má přistupující objekt [Get](../../language-reference/keywords/get.md) . Třída, která implementuje rozhraní, může deklarovat stejnou vlastnost s přístupovým objektem `get` a [nastavením](../../language-reference/keywords/set.md) . Pokud však vlastnost nebo indexer používá explicitní implementaci, přistupující objekty se musí shodovat. Další informace o explicitní implementaci naleznete v tématu [explicitní implementace rozhraní](explicit-interface-implementation.md) a [Vlastnosti rozhraní](../classes-and-structs/interface-properties.md).  

Rozhraní můžou dědit z jiných rozhraní. Třída může obsahovat rozhraní několikrát prostřednictvím základních tříd, které dědí nebo prostřednictvím rozhraní, která dědí jiná rozhraní. Nicméně třída může poskytnout implementaci rozhraní pouze jednou a pouze v případě, že třída deklaruje rozhraní jako součást definice třídy (`class ClassName : InterfaceName`). Pokud je rozhraní zděděné, protože jste zdědili základní třídu, která implementuje rozhraní, základní třída poskytuje implementaci členů rozhraní. Odvozená třída však může znovu implementovat jakékoli členy virtuálních rozhraní namísto použití zděděné implementace.  
  
Základní třída může také implementovat členy rozhraní pomocí virtuálních členů. V takovém případě může odvozená třída změnit chování rozhraní přepsáním virtuálních členů. Další informace o virtuálních členech naleznete v tématu [polymorfismus](../classes-and-structs/polymorphism.md).  
  
## <a name="interfaces-summary"></a>Souhrn rozhraní

Rozhraní má následující vlastnosti:  

- Rozhraní je jako abstraktní základní třída s pouze abstraktními členy. Všechny třídy nebo struktury, které implementují rozhraní, musí implementovat všechny jeho členy.
- Nelze vytvořit instanci rozhraní přímo. Jeho členové jsou implementováni jakoukoliv třídou nebo strukturou, která implementuje rozhraní.
- Rozhraní můžou obsahovat události, indexery, metody a vlastnosti.
- Rozhraní neobsahují žádnou implementaci metod ( C# v 8,0, rozhraní můžou mít [výchozí implementaci pro metody](../../whats-new/csharp-8.md#default-interface-methods)).
- Třída nebo struktura může implementovat více rozhraní. Třída může dědit základní třídu a také implementovat jedno nebo více rozhraní.

## <a name="in-this-section"></a>V tomto oddílu

[Implementace explicitního rozhraní](explicit-interface-implementation.md)  
 Vysvětluje, jak vytvořit člena třídy, který je specifický pro rozhraní.  
  
 [Postup explicitní implementace členů rozhraní](how-to-explicitly-implement-interface-members.md)  
 Poskytuje příklad explicitní implementace členů rozhraní.  
  
 [Postup explicitní implementace členů dvou rozhraní](how-to-explicitly-implement-members-of-two-interfaces.md)  
 Poskytuje příklad, jak explicitně implementovat členy rozhraní s děděním.  
  
## <a name="BKMK_RelatedSections"></a>Související oddíly

- [Vlastnosti rozhraní](../classes-and-structs/interface-properties.md)  
- [Indexery v rozhraní](../indexers/indexers-in-interfaces.md)  
- [Postup implementace událostí rozhraní](../events/how-to-implement-interface-events.md)
- [Třídy a struktury](../classes-and-structs/index.md)  
- [Dědičnost](../classes-and-structs/inheritance.md)  
- [Metody](../classes-and-structs/methods.md)  
- [Polymorfismus](../classes-and-structs/polymorphism.md)  
- [Abstraktní a uzavřené třídy a jejich členové](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
- [Vlastnosti](../classes-and-structs/properties.md)  
- [Události](../events/index.md)  
- [Indexery](../indexers/index.md)  
  
## <a name="featured-book-chapter"></a>Doporučená kapitola knihy

[Rozhraní](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652489%28v%3Dorm.10%29) ve [studiu C# 3,0: hlavní základy C# pro 3,0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v%253dorm.10%29)

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Dědičnost](../classes-and-structs/inheritance.md)
- [Názvy identifikátorů](../inside-a-program/identifier-names.md)
