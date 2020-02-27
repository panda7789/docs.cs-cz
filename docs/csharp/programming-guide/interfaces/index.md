---
title: Rozhraní – C# Průvodce programováním
ms.date: 02/20/2020
helpviewer_keywords:
- interfaces [C#]
- C# language, interfaces
ms.assetid: 2feda177-ce11-432d-81b4-d50f5f35fd37
ms.openlocfilehash: 99cbaa458e86c644a46eb62823f1854b3684c6c4
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627744"
---
# <a name="interfaces-c-programming-guide"></a>Rozhraní (Průvodce programováním v C#)

Rozhraní obsahuje definice pro skupinu souvisejících funkcí, které musí implementovat neabstraktní [Třída](../../language-reference/keywords/class.md) nebo [Struktura](../../language-reference/builtin-types/struct.md) . Rozhraní může definovat `static` metody, které musí mít implementaci. Rozhraní může poskytovat výchozí implementaci pro všechny nebo všechny deklarované členy instance. Rozhraní nesmí deklarovat data instance, jako jsou pole, automaticky implementované vlastnosti nebo události podobné vlastnostem.

Pomocí rozhraní můžete například zahrnout chování z více zdrojů ve třídě. Tato funkce je důležitá v C# , protože jazyk nepodporuje vícenásobnou dědičnost tříd. Kromě toho je nutné použít rozhraní, pokud chcete simulovat dědičnost pro struktury, protože nemohou být ve skutečnosti děděny z jiné struktury nebo třídy.

Rozhraní definujete pomocí klíčového slova [rozhraní](../../language-reference/keywords/interface.md) , jak ukazuje následující příklad.

[!code-csharp[Equatable](~/samples/snippets/csharp/objectoriented/interfaces.cs#Equatable)]

Název rozhraní musí být platný C# [název identifikátoru](../inside-a-program/identifier-names.md). Podle konvence názvy rozhraní začínají velkým `I`.

Všechny třídy nebo struktury, které implementují rozhraní <xref:System.IEquatable%601> musí obsahovat definici pro metodu <xref:System.IEquatable%601.Equals%2A>, která odpovídá signatuře, kterou určuje rozhraní. V důsledku toho můžete spočítat třídu, která implementuje `IEquatable<T>`, aby obsahovala metodu `Equals`, se kterou může instance třídy určit, zda je rovna jiné instanci stejné třídy.

Definice `IEquatable<T>` neposkytuje implementaci pro `Equals`. Třída nebo struktura může implementovat více rozhraní, ale třída může dědit pouze z jedné třídy.

Další informace o abstraktních třídách naleznete v tématu [abstraktní a zapečetěné třídy a členy třídy](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md).

Rozhraní mohou obsahovat metody instance, vlastnosti, události, indexery nebo libovolnou kombinaci těchto čtyř typů členů. Rozhraní mohou obsahovat statické konstruktory, pole, konstanty nebo operátory. Odkazy na příklady najdete v části [související oddíly](./index.md#BKMK_RelatedSections). Rozhraní nemůže obsahovat pole instancí, konstruktory instancí ani finalizační metody. Členy rozhraní jsou ve výchozím nastavení veřejné.

Chcete-li implementovat člena rozhraní, musí být odpovídající člen třídy implementace Public, nestatický a musí mít stejný název a signaturu jako člen rozhraní.

Pokud třída nebo struktura implementuje rozhraní, třída nebo struktura musí poskytovat implementaci pro všechny členy, které rozhraní deklaruje, ale neposkytuje výchozí implementaci pro. Nicméně pokud základní třída implementuje rozhraní, jakákoliv třída odvozená od základní třídy zdědí tuto implementaci.

Následující příklad ukazuje implementaci rozhraní <xref:System.IEquatable%601>. Implementující třída `Car`musí poskytovat implementaci <xref:System.IEquatable%601.Equals%2A> metody.

[!code-csharp[ImplementEquatable](~/samples/snippets/csharp/objectoriented/interfaces.cs#ImplementEquatable)]

Vlastnosti a indexery třídy mohou definovat nadbytečné přistupující objekty pro vlastnost nebo indexer, který je definován v rozhraní. Rozhraní může například deklarovat vlastnost, která má přistupující objekt [Get](../../language-reference/keywords/get.md) . Třída, která implementuje rozhraní, může deklarovat stejnou vlastnost s přístupovým objektem `get` a [nastavením](../../language-reference/keywords/set.md) . Pokud však vlastnost nebo indexer používá explicitní implementaci, přistupující objekty se musí shodovat. Další informace o explicitní implementaci naleznete v tématu [explicitní implementace rozhraní](explicit-interface-implementation.md) a [Vlastnosti rozhraní](../classes-and-structs/interface-properties.md).

Rozhraní mohou dědit z jednoho nebo více rozhraní. Odvozené rozhraní dědí členy z jeho základních rozhraní. Třída, která implementuje odvozené rozhraní, musí implementovat všechny členy v odvozeném rozhraní, včetně všech členů základních rozhraní odvozeného rozhraní. Tato třída může být implicitně převedena na odvozené rozhraní nebo na kterékoli z jeho základních rozhraní. Třída může obsahovat rozhraní několikrát prostřednictvím základních tříd, které dědí nebo prostřednictvím rozhraní, která dědí jiná rozhraní. Nicméně třída může poskytnout implementaci rozhraní pouze jednou a pouze v případě, že třída deklaruje rozhraní jako součást definice třídy (`class ClassName : InterfaceName`). Pokud je rozhraní zděděné, protože jste zdědili základní třídu, která implementuje rozhraní, základní třída poskytuje implementaci členů rozhraní. Odvozená třída však může znovu implementovat jakékoli členy virtuálních rozhraní namísto použití zděděné implementace. Když rozhraní deklaruje výchozí implementaci metody, jakákoliv třída implementující rozhraní dědí tuto implementaci. Implementace definované v rozhraních jsou virtuální a implementující třída může tuto implementaci přepsat.

Základní třída může také implementovat členy rozhraní pomocí virtuálních členů. V takovém případě může odvozená třída změnit chování rozhraní přepsáním virtuálních členů. Další informace o virtuálních členech naleznete v tématu [polymorfismus](../classes-and-structs/polymorphism.md).

## <a name="interfaces-summary"></a>Souhrn rozhraní

Rozhraní má následující vlastnosti:

- Rozhraní je obvykle jako abstraktní základní třída s pouze abstraktními členy. Všechny třídy nebo struktury, které implementují rozhraní, musí implementovat všechny jeho členy. Volitelně může rozhraní definovat výchozí implementace pro některé nebo všechny jeho členy.
- Nelze vytvořit instanci rozhraní přímo. Jeho členové jsou implementováni jakoukoliv třídou nebo strukturou, která implementuje rozhraní.
- Třída nebo struktura může implementovat více rozhraní. Třída může dědit základní třídu a také implementovat jedno nebo více rozhraní.

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
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Dědičnost](../classes-and-structs/inheritance.md)
- [Názvy identifikátorů](../inside-a-program/identifier-names.md)
