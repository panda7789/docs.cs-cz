---
title: Dědičnost – průvodce programováním jazyka C#
ms.date: 02/07/2020
helpviewer_keywords:
- abstract methods [C#]
- abstract classes [C#]
- inheritance [C#]
- derived classes [C#]
- virtual methods [C#]
- C# language, inheritance
ms.assetid: 81d64ee4-50f9-4d6c-a8dc-257c348d2eea
ms.openlocfilehash: 448b1695a4afc50f4afa20383e5fda280b9f12e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626656"
---
# <a name="inheritance-c-programming-guide"></a>Dědičnost (Průvodce programováním v C#)

Dědičnost, spolu s zapouzdření a polymorfismu, je jednou ze tří základních charakteristik objektově orientovaného programování. Dědičnost umožňuje vytvářet nové třídy, které znovu používají, rozšiřují a upravují chování definované v jiných třídách. Třída, jejíž členové jsou zděděni, se nazývá *základní třída*a třída, která tyto členy dědí, se nazývá *odvozená třída*. Odvozená třída může mít pouze jednu přímou základní třídu. Dědičnost je však přenositá. Pokud `ClassC` je odvozen `ClassB`od `ClassB` , a `ClassA` `ClassC` je odvozen od `ClassB` , `ClassA`dědí členy deklarované v a .

> [!NOTE]
> Struktury nepodporují dědičnost, ale mohou implementovat rozhraní. Další informace naleznete v [tématu Rozhraní](../interfaces/index.md).

Koncepčně odvozené třídy je specializace základní třídy. Například pokud máte základní `Animal`třídu , můžete mít jednu `Mammal` odvozenou třídu, `Reptile`která je pojmenována a další odvozené třídy, která je pojmenována . A `Mammal` je `Animal`, `Reptile` a `Animal`a je , ale každá odvozená třída představuje různé specializace základní třídy.

Deklarace rozhraní může definovat výchozí implementaci pro své členy. Tyto implementace jsou zděděny odvozené rozhraní a třídy, které implementují tato rozhraní. Další informace o výchozích metodách rozhraní naleznete v článku o [rozhraních](../../language-reference/keywords/interface.md) v části referenční jazyk.

Když definujete třídu, která má být odvozena z jiné třídy, odvozená třída implicitně získá všechny členy základní třídy, s výjimkou jejích konstruktorů a finalizačních metod. Odvozené třídy znovu používá kód v základní třídě bez nutnosti znovu implementovat. Můžete přidat další členy v odvozené třídě. Odvozená třída rozšiřuje funkce základní třídy.

Následující obrázek znázorňuje třídu, `WorkItem` která představuje položku práce v některém obchodním procesu. Stejně jako všechny třídy, odvozuje a <xref:System.Object?displayProperty=nameWithType> dědí všechny své metody. `WorkItem`přidává pět vlastních členů. Tyto členy zahrnují konstruktor, protože konstruktory nejsou zděděny. Třída `ChangeRequest` dědí `WorkItem` z a představuje určitý druh pracovní položky. `ChangeRequest`přidá další dva členy k členům, které dědí od `WorkItem` a od <xref:System.Object>. Musí přidat vlastní konstruktor a také `originalItemID`přidává . Vlastnost `originalItemID` umožňuje `ChangeRequest` instance být přidruženy `WorkItem` k originálu, na které se vztahuje požadavek na změnu.

![Diagram, který zobrazuje dědičnost třídy](./media/inheritance/class-inheritance-diagram.png)

Následující příklad ukazuje, jak jsou vyjádřeny vztahy třídy demonstrované na předchozím obrázku v c#. Příklad také `WorkItem` ukazuje, jak přepíše virtuální metodu <xref:System.Object.ToString%2A?displayProperty=nameWithType>a jak `ChangeRequest` třída dědí `WorkItem` implementaci metody. První blok definuje třídy:

[!code-csharp[DefineClasses](~/samples/snippets/csharp/objectoriented/inheritance.cs#Classes)]

Tento další blok ukazuje, jak používat základní a odvozené třídy:

[!code-csharp[UseClasses](~/samples/snippets/csharp/objectoriented/inheritance.cs#UseClasses)]

## <a name="abstract-and-virtual-methods"></a>Abstraktní a virtuální metody

Když základní třída deklaruje metodu [`virtual`](../../language-reference/keywords/virtual.md) [`override`](../../language-reference/keywords/override.md) jako , odvozená třída může metoda s vlastní implementací. Pokud základní třída deklaruje člen jako [`abstract`](../../language-reference/keywords/abstract.md), tato metoda musí být přepsána v jakékoli neabstraktní třídě, která přímo dědí z této třídy. Pokud je odvozená třída sama abstraktní, dědí abstraktní členy bez jejich implementace. Abstraktní a virtuální členové jsou základem polymorfismu, který je druhou primární charakteristikou objektově orientovaného programování. Další informace naleznete [v tématu Polymorfismus](./polymorphism.md).

## <a name="abstract-base-classes"></a>Abstraktní základní třídy

Můžete deklarovat třídu jako [abstraktní,](../../language-reference/keywords/abstract.md) pokud chcete zabránit přímé konkretizovat pomocí [nového](../../language-reference/operators/new-operator.md) operátoru. Abstraktní třídu lze použít pouze v případě, že je z ní odvozena nová třída. Abstraktní třída může obsahovat jeden nebo více podpisů metody, které jsou samy deklarovány jako abstraktní. Tyto podpisy určují parametry a vrácenou hodnotu, ale nemají žádnou implementaci (tělo metody). Abstraktní třída nemusí obsahovat abstraktní členy; pokud však třída obsahuje abstraktní člen, musí být samotná třída deklarována jako abstraktní. Odvozené třídy, které nejsou abstraktní samy o sobě musí poskytnout implementaci pro všechny abstraktní metody z abstraktní základní třídy. Další informace naleznete [v tématu Abstract and Sealed Classes and Class Members](abstract-and-sealed-classes-and-class-members.md).

## <a name="interfaces"></a>Rozhraní

*Rozhraní* je typ odkazu, který definuje sadu členů. Všechny třídy a struktury, které implementují toto rozhraní musí implementovat tuto sadu členů. Rozhraní může definovat výchozí implementaci pro některé nebo všechny tyto členy. Třída může implementovat více rozhraní, i když může být odvozena pouze z jedné přímé základní třídy.

Rozhraní se používají k definování specifických možností pro třídy, které nemusí mít nutně vztah "je a". Například <xref:System.IEquatable%601?displayProperty=nameWithType> rozhraní může být implementováno libovolnou třídou nebo strukturou k určení, zda jsou dva objekty typu ekvivalentní (ale typ definuje ekvivalenci). <xref:System.IEquatable%601>neznamená stejný druh vztahu "je a", který existuje mezi základní třídou a odvozenou `Mammal` třídou (například a `Animal`je). Další informace naleznete v [tématu Rozhraní](../interfaces/index.md).

## <a name="preventing-further-derivation"></a>Prevence dalšího odvození  

Třída může zabránit tomu, aby z ní dědili jiné třídy nebo od [`sealed`](../../language-reference/keywords/sealed.md)některého ze svých členů tím, že deklaruje sebe nebo člena jako . Další informace naleznete [v tématu Abstract and Sealed Classes and Class Members](./abstract-and-sealed-classes-and-class-members.md).

## <a name="derived-class-hiding-of-base-class-members"></a>Odvozené třídy skrývá ní členy základní třídy  

Odvozená třída může skrýt členy základní třídy deklarováním členů se stejným názvem a podpisem. Modifikátor [`new`](../../language-reference/keywords/new-modifier.md) lze explicitně označit, že člen není určen k přepsání základního člena. Použití [`new`](../../language-reference/keywords/new-modifier.md) není nutné, ale upozornění kompilátoru bude [`new`](../../language-reference/keywords/new-modifier.md) generováno, pokud se nepoužívá. Další informace naleznete [v tématu Správa verzí s přepsáním a novými klíčovými slovy](./versioning-with-the-override-and-new-keywords.md) a informace o [tom, kdy použít přepsání a nová klíčová slova](./knowing-when-to-use-override-and-new-keywords.md).

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Třídy a struky](./index.md)
- [Třída](../../language-reference/keywords/class.md)
