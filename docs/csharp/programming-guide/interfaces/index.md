---
title: Rozhraní – programovací průvodce C#
ms.date: 02/20/2020
helpviewer_keywords:
- interfaces [C#]
- C# language, interfaces
ms.assetid: 2feda177-ce11-432d-81b4-d50f5f35fd37
ms.openlocfilehash: 5e39279183f7e3745c9373df246d14d69d5ff99b
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805904"
---
# <a name="interfaces-c-programming-guide"></a>Rozhraní (Průvodce programováním v C#)

Rozhraní obsahuje definice pro skupinu souvisejících funkcí, které musí implementovat neabstraktní [třída](../../language-reference/keywords/class.md) nebo [struktura.](../../language-reference/builtin-types/struct.md) Rozhraní může `static` definovat metody, které musí mít implementaci. Počínaje C# 8.0 rozhraní může definovat výchozí implementaci pro členy. Rozhraní nesmí deklarovat data instance, jako jsou pole, automaticky implementované vlastnosti nebo události podobné vlastnosti.

Pomocí rozhraní můžete například zahrnout chování z více zdrojů ve třídě. Tato schopnost je důležité v jazyce C#, protože jazyk nepodporuje více dědičnosti tříd. Kromě toho je nutné použít rozhraní, pokud chcete simulovat dědičnost pro struktury, protože nemohou ve skutečnosti dědit z jiné struktury nebo třídy.

Rozhraní definujete pomocí klíčového slova [rozhraní,](../../language-reference/keywords/interface.md) jak ukazuje následující příklad.

[!code-csharp[Equatable](~/samples/snippets/csharp/objectoriented/interfaces.cs#Equatable)]

Název rozhraní musí být platný [název identifikátoru](../inside-a-program/identifier-names.md)Jazyka C# . Podle konvence začínají názvy `I`rozhraní velkým písmenem .

Všechny třídy nebo struktury, <xref:System.IEquatable%601> která implementuje <xref:System.IEquatable%601.Equals%2A> rozhraní musí obsahovat definici metody, která odpovídá podpisu, který určuje rozhraní. V důsledku toho se můžete spolehnout na `IEquatable<T>` třídu, která implementuje obsahovat metodu, `Equals` pomocí které instance třídy můžete určit, zda se rovná jiné instanci stejné třídy.

Definice `IEquatable<T>` neposkytuje implementaci pro `Equals`. Třída nebo struktura může implementovat více rozhraní, ale třída může dědit pouze z jedné třídy.

Další informace o abstraktních třídách naleznete v [tématu Abstract and Sealed Classes and Class Members](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md).

Rozhraní může obsahovat metody instance, vlastnosti, události, indexery nebo libovolnou kombinaci těchto čtyř typů členů. Rozhraní mohou obsahovat statické konstruktory, pole, konstanty nebo operátory. Odkazy na příklady najdete [v tématu Související oddíly](./index.md#BKMK_RelatedSections). Rozhraní nemůže obsahovat pole instancí, konstruktory instancí nebo finalizační metody. Členové rozhraní jsou ve výchozím nastavení veřejné.

Chcete-li implementovat člen rozhraní, musí být odpovídající člen implementující třídy veřejný, nestatický a musí mít stejný název a podpis jako člen rozhraní.

Když třída nebo struktura implementuje rozhraní, třída nebo struktura musí poskytnout implementaci pro všechny členy, které rozhraní deklaruje, ale neposkytuje výchozí implementaci. Pokud však základní třída implementuje rozhraní, každá třída, která je odvozena ze základní třídy, tuto implementaci zdědí.

Následující příklad ukazuje implementaci <xref:System.IEquatable%601> rozhraní. Implementující třída `Car`, musí poskytnout implementaci <xref:System.IEquatable%601.Equals%2A> metody.

[!code-csharp[ImplementEquatable](~/samples/snippets/csharp/objectoriented/interfaces.cs#ImplementEquatable)]

Vlastnosti a indexery třídy můžete definovat další přístupové objekty pro vlastnost nebo indexer, který je definován v rozhraní. Rozhraní může například deklarovat vlastnost, která má [get](../../language-reference/keywords/get.md) přistupujícího objektu. Třída, která implementuje rozhraní můžete deklarovat stejnou vlastnost s `get` a a [nastavit](../../language-reference/keywords/set.md) přistupujícího objektu. Však pokud vlastnost nebo indexer používá explicitní implementaci, přístupové objekty musí odpovídat. Další informace o explicitní implementaci naleznete [v tématu Explicitní implementace rozhraní](explicit-interface-implementation.md) a [vlastnosti rozhraní](../classes-and-structs/interface-properties.md).

Rozhraní mohou dědit z jednoho nebo více rozhraní. Odvozené rozhraní dědí členy ze svých základních rozhraní. Třída, která implementuje odvozené rozhraní musí implementovat všechny členy v odvozené rozhraní, včetně všech členů základní rozhraní odvozené rozhraní. Tato třída může být implicitně převedena na odvozené rozhraní nebo některé z jeho základních rozhraní. Třída může obsahovat rozhraní vícekrát prostřednictvím základních tříd, které dědí, nebo prostřednictvím rozhraní, které dědí jiná rozhraní. Třída však může poskytnout implementaci rozhraní pouze jednou a pouze v případě, že třída deklaruje rozhraní jako součást definice třídy (`class ClassName : InterfaceName`). Pokud je rozhraní zděděno, protože jste zdědili základní třídu, která implementuje rozhraní, základní třída poskytuje implementaci členů rozhraní. Odvozené třídy však můžete znovu implementovat všechny členy virtuálního rozhraní namísto použití zděděné implementace. Když rozhraní deklarují výchozí implementaci metody, všechny třídy implementující toto rozhraní dědí tuto implementaci. Implementace definované v rozhraní jsou virtuální a implementující třída může přepsat tuto implementaci.

Základní třída můžete také implementovat členy rozhraní pomocí virtuálních členů. V takovém případě odvozené třídy můžete změnit chování rozhraní přepsáním virtuální členy. Další informace o virtuálních členech naleznete [v tématu Polymorfismus](../classes-and-structs/polymorphism.md).

## <a name="interfaces-summary"></a>Souhrn rozhraní

Rozhraní má následující vlastnosti:

- Rozhraní je obvykle jako abstraktní základní třídy s pouze abstraktní členy. Všechny třídy nebo struktury, která implementuje rozhraní musí implementovat všechny své členy. Volitelně rozhraní může definovat výchozí implementace pro některé nebo všechny jeho členy.
- Rozhraní nelze vytvořit instanci přímo. Jeho členy jsou implementovány libovolnou třídu nebo strukturu, která implementuje rozhraní.
- Třída nebo struktura může implementovat více rozhraní. Třída může dědit základní třídu a také implementovat jedno nebo více rozhraní.

## <a name="related-sections"></a><a name="BKMK_RelatedSections"></a>Související oddíly

- [Vlastnosti rozhraní](../classes-and-structs/interface-properties.md)  
- [Indexery v rozhraních](../indexers/indexers-in-interfaces.md)  
- [Jak implementovat události rozhraní](../events/how-to-implement-interface-events.md)
- [Třídy a struktury](../classes-and-structs/index.md)  
- [Dědičnost](../classes-and-structs/inheritance.md)  
- [Metody](../classes-and-structs/methods.md)  
- [Polymorfismus](../classes-and-structs/polymorphism.md)  
- [Abstraktní a uzavřené třídy a jejich členové](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
- [Vlastnosti](../classes-and-structs/properties.md)  
- [Události](../events/index.md)  
- [Indexery](../indexers/index.md)  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Dědičnost](../classes-and-structs/inheritance.md)
- [Názvy identifikátorů](../inside-a-program/identifier-names.md)
