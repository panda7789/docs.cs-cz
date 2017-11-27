---
title: "Dědičnost (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- abstract methods [C#]
- abstract classes [C#]
- inheritance [C#]
- derived classes [C#]
- virtual methods [C#]
- C# language, inheritance
ms.assetid: 81d64ee4-50f9-4d6c-a8dc-257c348d2eea
caps.latest.revision: "38"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dc3d448d311fe0a67839757fa43a209d92141214
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="inheritance-c-programming-guide"></a>Dědičnost (Průvodce programováním v C#)

Dědičnost, společně s zapouzdření a polymorfismus, je jedna z vlastností objektově orientované programování s tři primární. Dědičnost umožňuje vytvořit nové třídy, které znovu použít, rozšířit nebo změnit chování, která je definována v jiné třídy. Je volána třídu, jejíž členové jsou děděné *základní třída*, a třídu, která dědí členů, se nazývá *odvozené třídy*. Odvozená třída může mít pouze jeden přímé základní třídy. Je však přenositelné dědičnosti. Pokud ClassC je odvozený od ClassB a ClassB je odvozený od ClassA, dědí ClassC členy v ClassB a ClassA deklarován.  
  
> [!NOTE]
>  Struktury nepodporují dědičnosti, ale jejich můžete implementovat rozhraní. Další informace najdete v tématu [rozhraní](../../../csharp/programming-guide/interfaces/index.md).  
  
 Odvozené třídy je koncepčně, specializace základní třídy. Například, pokud máte základní třídu `Animal`, může mít jeden odvozené třídy, který je pojmenován `Mammal` a jiné odvozené třídy, která je s názvem `Reptile`. A `Mammal` je `Animal`a `Reptile` je `Animal`, ale každý odvozené třídy představuje různé specializací základní třídy.  
  
 Když definujete třídu k odvozování z jiné třídy, odvozené třídy získá implicitně všechny členy základní třídy, s výjimkou jeho konstruktory a finalizační metody. Odvozené třídy a tím můžete znovu použít kód v základní třídě bez nutnosti znovu implementaci. V odvozené třídě můžete přidat více členů. Odvozená třída tímto způsobem rozšiřuje funkce základní třídy.  
  
 Následující obrázek znázorňuje třídu `WorkItem` představující položku práce v některé obchodní proces. Všechny třídy, jako je odvozena z <xref:System.Object?displayProperty=nameWithType> a dědí všechny její metody. `WorkItem`Přidá svůj vlastní pět členy. Patří mezi ně konstruktor, protože nejsou zděděno konstruktory. Třída `ChangeRequest` dědí z `WorkItem` a představuje konkrétní typ pracovní položky. `ChangeRequest`Přidá dva členy více členů, které dědí z `WorkItem` a z <xref:System.Object>. Je nutné přidat vlastní konstruktor a také přidá `originalItemID`. Vlastnost `originalItemID` umožňuje `ChangeRequest` instance, která má být přidružen k původní `WorkItem` pro kterou platí žádost o změnu.  
  
 ![Třídy dědičnosti](../../../csharp/programming-guide/classes-and-structs/media/class_inheritance.png "Class_Inheritance")  
Dědičnost třídy  
  
 Následující příklad ukazuje, jak vztahy tříd ukázáno v předchozí ilustraci jsou vyjádřeny v jazyce C#. Příklad také ukazuje, jak `WorkItem` potlačí metodu virtuální <xref:System.Object.ToString%2A?displayProperty=nameWithType>a jak `ChangeRequest` třída dědí `WorkItem` implementace metody.  
  
 [!code-csharp[csProgGuideInheritance#49](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/inheritance_1.cs)]  
  
## <a name="abstract-and-virtual-methods"></a>Abstraktní a virtuální metody  
 Když základní třídu deklaruje jako metodu [virtuální](../../../csharp/language-reference/keywords/virtual.md), můžete do odvozené třídy [přepsat](../../../csharp/language-reference/keywords/override.md) metodu vlastní implementací. Pokud základní třídu deklaruje člena jako [abstraktní](../../../csharp/language-reference/keywords/abstract.md), že metoda musí být přepsána nastaveními v neabstraktní třídy, která přímo dědí z třídy. Pokud odvozené třídy je sám abstraktní, dědí abstraktní členy bez jejich implementaci. Abstraktní a virtuální členy jsou základem pro polymorfismus, což je druhý primární vlastnosti objektově orientované programování. Další informace najdete v tématu [polymorfismus](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).  
  
## <a name="abstract-base-classes"></a>Abstraktní třídy Base  
 Je možné deklarovat třídu jako [abstraktní](../../../csharp/language-reference/keywords/abstract.md) Pokud chcete, aby se zabránilo přímé vytváření instancí pomocí [nové](../../../csharp/language-reference/keywords/new.md) – klíčové slovo. Pokud to uděláte, třídy lze použít pouze v případě, že je z něj odvozenou novou třídu. Abstraktní třídy může obsahovat jednu nebo více metoda podpisy, že sami jsou deklarované jako abstraktní. Tyto podpisy zadejte parametry a vrátí hodnotu, ale nemají implementaci (metoda textu). Abstraktní třída nemusí obsahovat abstraktní členy; ale pokud třídu neobsahuje člena abstraktní, vlastní třídy musí být deklarován jako abstraktní. Odvozené třídy, které nejsou abstraktní sami musí poskytovat implementace pro žádné abstraktní metody z abstraktní základní třídu. Další informace najdete v tématu [abstraktní a zapečetěné třídy a jejich členové](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
## <a name="interfaces"></a>Rozhraní  
 *Rozhraní* je odkaz na typ, který je trochu podobné abstraktní základní třída, která se skládá z jenom abstraktní členy. Pokud třída implementuje rozhraní, je třeba poskytnout implementaci pro všechny členy rozhraní. Třída může implementovat více rozhraní, i když lze odvozovat pouze jediné přímé základní třídy.  
  
 Rozhraní slouží k určení specifické možnosti pro třídy, které není nezbytně nutné "je" relace. Například <xref:System.IEquatable%601?displayProperty=nameWithType> rozhraní může být implementováno všechny třídy nebo struktura, která má k povolení kód klienta k určení, zda dva objekty typu jsou ekvivalentní (ale typ definuje ekvivalenční). <xref:System.IEquatable%601>neznamená stejný druh "je" vztah, který existuje mezi základní třídou a odvozené třídy (například `Mammal` je `Animal`). Další informace najdete v tématu [rozhraní](../../../csharp/programming-guide/interfaces/index.md).  
  
## <a name="preventing-further-derivation"></a>Brání další odvození  
 Třída zabránit jiné třídy, která dědí z něj nebo z jakéhokoli z jejích členů, deklarováním sám sebe nebo jako člen [zapečetěné](../../../csharp/language-reference/keywords/sealed.md). Další informace najdete v tématu [abstraktní a zapečetěné třídy a jejich členové](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
## <a name="derived-class-hiding-of-base-class-members"></a>Skrytí odvozené třídy základní třídy členů  
 Odvozené třídy můžete skrýt členy základní třídy deklarace členy se stejným názvem a podpis. [Nové](../../../csharp/language-reference/keywords/new.md) modifikátor umožňuje explicitně znamenat, že člen není určen jako přepsání základní člena. Použití [nové](../../../csharp/language-reference/keywords/new.md) není vyžadována, ale pokud se budou generovat upozornění kompilátoru [nové](../../../csharp/language-reference/keywords/new.md) nepoužívá. Další informace najdete v tématu [Správa verzí pomocí nové klíčových slov Override a](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) a [zároveň budete vědět, při použití přepsání a nová klíčová slova](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [– Třída](../../../csharp/language-reference/keywords/class.md)  
 [Struktura](../../../csharp/language-reference/keywords/struct.md)
