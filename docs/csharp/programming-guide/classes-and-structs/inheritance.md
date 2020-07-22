---
title: Dědičnost – Průvodce programováním v C#
description: Dědičnost v jazyce C# umožňuje vytvořit nové třídy, které znovu použije, rozšíří a mění chování definované v jiných třídách.
ms.date: 02/07/2020
helpviewer_keywords:
- abstract methods [C#]
- abstract classes [C#]
- inheritance [C#]
- derived classes [C#]
- virtual methods [C#]
- C# language, inheritance
ms.assetid: 81d64ee4-50f9-4d6c-a8dc-257c348d2eea
ms.openlocfilehash: 6b94f58801af188655474f9c7de76b79381e721d
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864252"
---
# <a name="inheritance-c-programming-guide"></a>Dědičnost (Průvodce programováním v C#)

Dědičnost, spolu s zapouzdřením a polymorfismus, je jednou ze tří základních vlastností objektově orientovaného programování. Dědičnost umožňuje vytvořit nové třídy, které znovu použije, rozšíří a mění chování definované v jiných třídách. Třída, jejíž členové jsou zděděni, se nazývají *základní třídu*a třída, která dědí tyto členy, se nazývá *odvozená třída*. Odvozená třída může mít pouze jednu přímou základní třídu. Dědičnost je však tranzitivní. Pokud `ClassC` je odvozen z a `ClassB` `ClassB` je odvozen z `ClassA` , `ClassC` dědí členy deklarované v `ClassB` a `ClassA` .

> [!NOTE]
> Struktury nepodporují dědění, ale mohou implementovat rozhraní. Další informace naleznete v tématu [rozhraní](../interfaces/index.md).

V koncepčním případě je odvozená třída specializací základní třídy. Například pokud máte základní třídu `Animal` , může mít jednu odvozenou třídu s názvem `Mammal` a jinou odvozenou třídu s názvem `Reptile` . A je `Mammal` `Animal` , a `Reptile` je `Animal` , ale každá odvozená třída představuje různé specializace základní třídy.

Deklarace rozhraní mohou definovat výchozí implementaci pro své členy. Tyto implementace jsou zděděny odvozenými rozhraními a třídami, které implementují tato rozhraní. Další informace o metodách výchozích rozhraní naleznete v článku o [rozhraních](../../language-reference/keywords/interface.md) v části referenční příručka jazyka.

Při definování třídy pro odvození z jiné třídy odvozená třída implicitně získá všechny členy základní třídy, s výjimkou jejích konstruktorů a finalizační metody. Odvozená třída znovu používá kód v základní třídě, aniž by bylo nutné ho znovu implementovat. V odvozené třídě můžete přidat další členy. Odvozená třída rozšiřuje funkčnost základní třídy.

Následující ilustrace znázorňuje třídu `WorkItem` , která představuje položku práce v některém obchodním procesu. Podobně jako všechny třídy je odvozen z <xref:System.Object?displayProperty=nameWithType> a dědí všechny metody. `WorkItem`Přidá pět členů vlastního typu. Tyto členy zahrnují konstruktor, protože konstruktory nejsou děděny. Třída `ChangeRequest` dědí z `WorkItem` a představuje konkrétní typ pracovní položky. `ChangeRequest`přidá dva členy do členů, které dědí z `WorkItem` a z <xref:System.Object> . Je nutné přidat svůj vlastní konstruktor a přidá také `originalItemID` . Vlastnost `originalItemID` umožňuje `ChangeRequest` instanci přidružit k původnímu, `WorkItem` na kterou se vztahuje žádost o změnu.

![Diagram, který znázorňuje dědičnost tříd](./media/inheritance/class-inheritance-diagram.png)

Následující příklad ukazuje, jak jsou vztahy tříd znázorněny na předchozím obrázku, vyjádřeny v jazyce C#. Příklad také ukazuje, jak `WorkItem` Přepisuje virtuální metodu <xref:System.Object.ToString%2A?displayProperty=nameWithType> a jak `ChangeRequest` Třída dědí `WorkItem` implementaci metody. První blok definuje třídy:

[!code-csharp[DefineClasses](~/samples/snippets/csharp/objectoriented/inheritance.cs#Classes)]

Tento další blok ukazuje, jak použít základní a odvozené třídy:

[!code-csharp[UseClasses](~/samples/snippets/csharp/objectoriented/inheritance.cs#UseClasses)]

## <a name="abstract-and-virtual-methods"></a>Abstraktní a virtuální metody

Když základní třída deklaruje metodu jako [`virtual`](../../language-reference/keywords/virtual.md) , odvozená třída může být [`override`](../../language-reference/keywords/override.md) metodou s vlastní implementací. Pokud základní třída deklaruje člena jako [`abstract`](../../language-reference/keywords/abstract.md) , musí být tato metoda přepsána v jakékoli neabstraktní třídě, která přímo dědí z této třídy. Pokud je odvozená třída sama o sobě abstraktní, dědí abstraktní členy bez jejich implementace. Abstraktní a virtuální členové jsou základem pro polymorfismus, což je druhá primární charakteristika objektově orientovaného programování. Další informace najdete v tématu [polymorfismus](./polymorphism.md).

## <a name="abstract-base-classes"></a>Abstraktní základní třídy

Třídu můžete deklarovat jako [abstraktní](../../language-reference/keywords/abstract.md) , pokud chcete zabránit přímému vytváření instancí pomocí operátoru [New](../../language-reference/operators/new-operator.md) . Abstraktní třída se dá použít jenom v případě, že je z ní odvozená nová třída. Abstraktní třída může obsahovat jeden nebo více signatur metod, které jsou deklarovány jako abstraktní. Tyto signatury určují parametry a návratovou hodnotu, ale nemají žádnou implementaci (tělo metody). Abstraktní třída nemusí obsahovat abstraktní členy; Pokud však třída obsahuje abstraktní člen, musí být samotná třída deklarována jako abstraktní. Odvozené třídy, které nejsou abstraktní, musí poskytovat implementaci pro všechny abstraktní metody z abstraktní základní třídy. Další informace naleznete v tématu [abstraktní a zapečetěné třídy a členy třídy](abstract-and-sealed-classes-and-class-members.md).

## <a name="interfaces"></a>Rozhraní

*Rozhraní* je odkazový typ, který definuje sadu členů. Všechny třídy a struktury, které implementují toto rozhraní, musí implementovat tuto sadu členů. Rozhraní může definovat výchozí implementaci pro některé nebo všechny tyto členy. Třída může implementovat více rozhraní, i když může odvozovat pouze z jediné přímé základní třídy.

Rozhraní slouží k definování specifických možností pro třídy, které nemají nutně mít relaci "je". <xref:System.IEquatable%601?displayProperty=nameWithType>Rozhraní může být například implementováno jakoukoliv třídou nebo strukturou pro určení, zda jsou dva objekty typu ekvivalent (ale typ definuje ekvivalenci). <xref:System.IEquatable%601>neznamená, že stejný druh vztahu "je", který existuje mezi základní třídou a odvozenou třídou (například `Mammal` je a `Animal` ). Další informace naleznete v tématu [rozhraní](../interfaces/index.md).

## <a name="preventing-further-derivation"></a>Zabránit dalšímu odvození  

Třída může zabránit jiným třídám dědit z ní nebo z některého z jejích členů deklarací samotného nebo členu jako [`sealed`](../../language-reference/keywords/sealed.md) . Další informace naleznete v tématu [abstraktní a zapečetěné třídy a členy třídy](./abstract-and-sealed-classes-and-class-members.md).

## <a name="derived-class-hiding-of-base-class-members"></a>Odvozená třída skrývání členů základní třídy  

Odvozená třída může skrýt členy základní třídy deklarováním členů se stejným názvem a signaturou. Pomocí [`new`](../../language-reference/keywords/new-modifier.md) modifikátoru lze explicitně označit, že člen není určen jako přepsání základního člena. Použití [`new`](../../language-reference/keywords/new-modifier.md) není vyžadováno, ale pokud se nepoužije, bude vygenerováno upozornění kompilátoru [`new`](../../language-reference/keywords/new-modifier.md) . Další informace naleznete v tématu [Správa verzí pomocí klíčových slov override a New](./versioning-with-the-override-and-new-keywords.md) a [znalost, kdy použít klíčová slova override a New](./knowing-when-to-use-override-and-new-keywords.md).

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Třídy a struktury](./index.md)
- [Deník](../../language-reference/keywords/class.md)
