---
title: Dědičnost - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- abstract methods [C#]
- abstract classes [C#]
- inheritance [C#]
- derived classes [C#]
- virtual methods [C#]
- C# language, inheritance
ms.assetid: 81d64ee4-50f9-4d6c-a8dc-257c348d2eea
ms.openlocfilehash: a6e9e095caaa8c0e4330df3f766dbef927c5acd2
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202350"
---
# <a name="inheritance-c-programming-guide"></a>Dědičnost (Průvodce programováním v C#)

Dědičnost, společně s zapouzdření a polymorfismu, je jednou tři primární charakteristiky objektově orientované programování. Dědičnost umožňuje vytvořit nové třídy, které opakovaně používat, rozšířit a upravovat chování, které je definováno v jiné třídy. Třídy, jejíž členové jsou zdědění, se nazývá *základní třída*, a názvem třídy, která dědí tyto členy *odvozené třídy*. Odvozená třída může mít pouze jednu přímou základní třídu. Dědičnost je však tranzitivní. Pokud ClassC je odvozeno od ClassB a ClassB je odvozen z ClassA, ClassC dědí členy deklarované v ClassB a nakonec.  
  
> [!NOTE]
>  Struktury nepodporují dědičnosti, ale mohou implementovat rozhraní. Další informace najdete v tématu [rozhraní](../../../csharp/programming-guide/interfaces/index.md).  
  
 Koncepčně odvozené třídy je specializací třídy base. Například, pokud máte základní třídu `Animal`, bude pravděpodobně jedné odvozené třídy, který je pojmenován `Mammal` a jiné odvozené třídy, který je pojmenován `Reptile`. A `Mammal` je `Animal`a `Reptile` je `Animal`, ale každá odvozená třída představuje různé specializace základní třídy.  
  
 Při definování třídy odvozovat z jiné třídy odvozené třídy implicitně získá všechny členy základní třídy, s výjimkou jejích konstruktorů a finalizační metody. Odvozená třída tak můžete znovu použít kód v základní třídě bez nutnosti znovu implementovat. V odvozené třídě můžete přidat více členů. Tímto způsobem rozšiřuje odvozené třídy funkce základní třídy.  
  
 Následující obrázek ukazuje třídu `WorkItem` , která představuje položky práce v některých obchodních procesů. Stejně jako všechny třídy je odvozen z <xref:System.Object?displayProperty=nameWithType> a dědí její metody. `WorkItem` Přidá pět členů své vlastní. Patří mezi ně konstruktor, protože nejsou zděděných konstruktorů. Třída `ChangeRequest` dědí z `WorkItem` a představuje konkrétní typ pracovní položky. `ChangeRequest` Přidá dva další členy, které dědí z členů `WorkItem` a z <xref:System.Object>. Je nutné přidat vlastní konstruktor a také přidá `originalItemID`. Vlastnost `originalItemID` umožňuje `ChangeRequest` instance má být přidružena k původní `WorkItem` pro kterou platí žádost o změnu.  
  
 ![Dědičnost třídy](../../../csharp/programming-guide/classes-and-structs/media/class_inheritance.png "Class_Inheritance")  
Dědičnost tříd  
  
 Následující příklad ukazuje, jak relace tříd jsme vám ukázali v předchozí ilustraci jsou vyjádřeny v jazyce C#. Příklad také ukazuje, jak `WorkItem` přepisuje metodu virtuální <xref:System.Object.ToString%2A?displayProperty=nameWithType>a jak `ChangeRequest` třída dědí `WorkItem` implementace metody.  
  
 [!code-csharp[csProgGuideInheritance#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#49)]  
  
## <a name="abstract-and-virtual-methods"></a>Abstraktní a virtuální metody  
 Pokud základní třída deklaruje metodu jako [virtuální](../../../csharp/language-reference/keywords/virtual.md), mohou odvozené třídy [přepsat](../../../csharp/language-reference/keywords/override.md) metoda vlastní implementací. Pokud základní třída deklaruje člen jako [abstraktní](../../../csharp/language-reference/keywords/abstract.md), že metoda musí přepsat v neabstraktní třídě, který dědí přímo z této třídy. Pokud odvozené třídy je sama o sobě abstraktní, dědí abstraktní členové bez jejich implementaci. Abstraktní a virtuální členy jsou základem pro polymorfismus, což je druhým charakteristickým znakem primární objektově orientované programování. Další informace najdete v tématu [polymorfismus](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).  
  
## <a name="abstract-base-classes"></a>Abstraktní základní třídy  
 Je možné deklarovat třídu jako [abstraktní](../../../csharp/language-reference/keywords/abstract.md) Pokud chcete, aby se zabránilo přímé vytváření instancí pomocí [nové](../../../csharp/language-reference/keywords/new.md) – klíčové slovo. Pokud to uděláte, třídu lze použít pouze v případě, že nové třídy je odvozen z něj. Abstraktní třída může obsahovat jednu nebo více podpisy metod, že samotné jsou deklarovány jako abstraktní. Tyto podpisy zadejte parametry a vrátí hodnotu, ale nemají implementaci (tělo metody). Abstraktní třída nemá obsahovat abstraktní členy. Pokud třída obsahuje abstraktní člen, vlastní třídy musí deklarovat jako abstraktní. Odvozené třídy, které nejsou abstraktní sami musí poskytnout implementaci pro všechny abstraktní metody z abstraktní základní třídu. Další informace najdete v tématu [abstraktní a zapečetěné třídy a členové](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
## <a name="interfaces"></a>Rozhraní  
 *Rozhraní* je typem odkazu, který je poněkud podobně jako abstraktní základní třídu, která se skládá pouze abstraktní členy. Pokud třída implementuje rozhraní, se musí poskytnout implementaci pro všechny členy rozhraní. Třída může implementovat více rozhraní, i když lze odvodit z pouze jednu přímou základní třídu.  
  
 Rozhraní se používají k definování specifické možnosti pro třídy, které nutně nemusí "je" vztah. Například <xref:System.IEquatable%601?displayProperty=nameWithType> rozhraní může být implementována každá třída nebo struktura, která se má povolit klientský kód k určení, zda dva objekty typu jsou ekvivalentní (ale typ definuje ekvivalence). <xref:System.IEquatable%601> neznamená stejný druh "je" vztah, který existuje mezi základní a odvozenou třídu (například `Mammal` je `Animal`). Další informace najdete v tématu [rozhraní](../../../csharp/programming-guide/interfaces/index.md).  
  
## <a name="preventing-further-derivation"></a>Brání odvození další  
 Třída může zabránit dalším třídám dědění z něj nebo z některé z jejích členů deklarováním samotné nebo člena jako [zapečetěné](../../../csharp/language-reference/keywords/sealed.md). Další informace najdete v tématu [abstraktní a zapečetěné třídy a členové](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
## <a name="derived-class-hiding-of-base-class-members"></a>Skrývání odvozená třída členy základní třídy  
 Odvozené třídy lze skrýt členy základní třídy deklarací členů s týmž názvem a podpisem. [Nové](../../../csharp/language-reference/keywords/new.md) modifikátor lze explicitně určit, že člen není určena pro se přepíše základního člena. Použití [nové](../../../csharp/language-reference/keywords/new.md) není vyžadováno, ale upozornění kompilátoru se vygeneruje, pokud [nové](../../../csharp/language-reference/keywords/new.md) se nepoužívá. Další informace najdete v tématu [Správa verzí pomocí nových klíčových slov Override a](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) a [vědět, když pro použití přepsání a nových klíčových slov](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
- [class](../../../csharp/language-reference/keywords/class.md)
- [struct](../../../csharp/language-reference/keywords/struct.md)
