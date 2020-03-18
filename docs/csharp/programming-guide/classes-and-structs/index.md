---
title: Třídy a struktury - C# Programovací průvodce
description: Popisuje použití tříd a struktur (struktur) v c#.
ms.date: 01/17/2016
helpviewer_keywords:
- structs [C#], about structs
- classes [C#], overview
- C# language, structs
- C# language, objects
- objects [C#]
- C# language, classes
ms.assetid: cc39dbda-8754-423e-b5b1-16a1db0734c0
ms.openlocfilehash: afd9e688bd716375bafb370fad4af082a9498411
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399852"
---
# <a name="classes-and-structs-c-programming-guide"></a>Třídy a struktury (Průvodce programováním v C#)
Třídy a struktury jsou dvě základní konstrukce společného systému typů v rozhraní .NET Framework. Každý z nich je v podstatě datová struktura, která zapouzdřuje sadu dat a chování, které patří k sobě jako logická jednotka. Data a chování jsou *členy* třídy nebo struktury a zahrnují jeho metody, vlastnosti a události a tak dále, jak je uvedeno dále v tomto tématu.  
  
 Deklarace třídy nebo struktury je jako podrobný plán, který se používá k vytvoření instancí nebo objektů za běhu. Pokud definujete třídu nebo `Person` `Person` strukturu s názvem , je název typu. Pokud deklarujete `p` a `Person`inicializujete proměnnou typu , `p` znamená to, že je objekt nebo instance aplikace `Person`. Lze vytvořit více `Person` instancí stejného typu a každá instance může mít ve svých vlastnostech a polích různé hodnoty.  
  
 Třída je typ odkazu. Při vytvoření objektu třídy proměnná, ke které je objekt přiřazen, obsahuje pouze odkaz na tuto paměť. Když je odkaz na objekt přiřazen nové proměnné, nová proměnná odkazuje na původní objekt. Změny provedené prostřednictvím jedné proměnné se projeví v druhé proměnné, protože obě odkazují na stejná data.  
  
 Struktura je typ hodnoty. Při vytvoření struktury, proměnná, ke které je přiřazena struktura obsahuje aktuální data struktury. Když je struktura přiřazena nové proměnné, zkopíruje se. Nová proměnná a původní proměnná proto obsahují dvě samostatné kopie stejných dat. Změny provedené v jedné kopii nemají vliv na druhou kopii.  
  
 Obecně platí, že třídy se používají k modelování složitější chování nebo data, která je určena k úpravě po vytvoření objektu třídy. Struktury jsou nejvhodnější pro malé datové struktury, které obsahují především data, která není určena k úpravě po vytvoření struktury.  
  
 Další informace naleznete v [tématu Třídy](./classes.md), [Objekty](./objects.md)a [Structure typy](../../language-reference/builtin-types/struct.md).  
  
## <a name="example"></a>Příklad  
 V `CustomClass` následujícím příkladu `ProgrammingGuide` má v oboru názvů tři členy: konstruktor instance, vlastnost s názvem `Number`a metodu s názvem `Multiply`. Metoda `Main` ve `Program` třídě vytvoří instanci `CustomClass`(objekt) aplikace a metoda a vlastnost objektu jsou přístupné pomocí tečkového zápisu.
  
 [!code-csharp[csProgGuideObjects#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/class1.cs#1)]  
  
## <a name="encapsulation"></a>Zapouzdření  
 *Zapouzdření* se někdy označuje jako první pilíř nebo princip objektově orientovaného programování. Podle principu zapouzdření může třída nebo struktura určit, jak je každý z jeho členů přístupný kódu mimo třídu nebo strukturu. Metody a proměnné, které nejsou určeny k použití mimo třídu nebo sestavení, mohou být skryty, aby se omezilpotenciál chyb kódování nebo škodlivých zneužití.  
  
 Další informace o třídách naleznete v [tématu Třídy](./classes.md) a [objekty](./objects.md).  
  
### <a name="members"></a>Členové  
 Všechny metody, pole, konstanty, vlastnosti a události musí být deklarovány v rámci typu; tyto se nazývají *členy* typu. V jazyce C# neexistují žádné globální proměnné nebo metody, jako jsou v některých jiných jazycích. I vstupní bod programu, `Main` metoda, musí být deklarován v rámci třídy nebo struktury. Následující seznam obsahuje všechny různé druhy členů, které mohou být deklarovány ve třídě nebo struktuře.  
  
- [Pole](./fields.md)  
  
- [Konstanty](./constants.md)  
  
- [Vlastnosti](./properties.md)  
  
- [Metody](./methods.md)  
  
- [Konstruktory](./constructors.md)  
  
- [Akce](../events/index.md)  
  
- [Finalizační metody](./destructors.md)  
  
- [Indexery](../indexers/index.md)  
  
- [Operátory](../../language-reference/operators/index.md)  
  
- [Vnořené typy](./nested-types.md)  
  
### <a name="accessibility"></a>Přístupnost  
 Některé metody a vlastnosti jsou určeny k volání nebo přístup z kódu mimo vaši třídu nebo strukturu, známé jako *klientský kód*. Jiné metody a vlastnosti mohou být pouze pro použití ve třídě nebo struktuře samotné. Je důležité omezit přístupnost kódu tak, aby k němu mohl dosáhnout pouze zamýšlený klientský kód. Můžete určit, jak přístupné jsou vaše typy a jejich členy klientského kódu pomocí modifikátorů přístupu [veřejné](../../language-reference/keywords/public.md), [chráněné](../../language-reference/keywords/protected.md), [interní](../../language-reference/keywords/internal.md), [chráněné interní,](../../language-reference/keywords/protected-internal.md) [soukromé](../../language-reference/keywords/private.md) a [soukromé chráněné](../../language-reference/keywords/private-protected.md). Výchozí usnadnění `private`přístupu je . Další informace naleznete [v tématu Access Modifiers](./access-modifiers.md).  
  
### <a name="inheritance"></a>Dědičnost  
 Třídy (ale ne struktury) podporují koncept dědičnosti. Třída, která je odvozena z jiné třídy *(základní třída)* automaticky obsahuje všechny veřejné, chráněné a interní členy základní třídy s výjimkou jejích konstruktorů a finalizačních metod. Další informace naleznete v [tématu Dědičnost](./inheritance.md) a [polymorfismus](./polymorphism.md).  
  
 Třídy mohou být deklarovány jako [abstraktní](../../language-reference/keywords/abstract.md), což znamená, že jedna nebo více jejich metod nemá žádnou implementaci. Přestože abstraktní třídy nelze vytvořit instanci přímo, mohou sloužit jako základní třídy pro jiné třídy, které poskytují chybějící implementaci. Třídy mohou být také deklarovány jako [zapečetěné,](../../language-reference/keywords/sealed.md) aby se zabránilo dědění jiných tříd z nich. Další informace naleznete [v tématu Abstract and Sealed Classes and Class Members](./abstract-and-sealed-classes-and-class-members.md).  
  
### <a name="interfaces"></a>Rozhraní  
 Třídy a struktury mohou dědit více rozhraní. Chcete-li dědit z rozhraní znamená, že typ implementuje všechny metody definované v rozhraní. Další informace naleznete v [tématu Rozhraní](../interfaces/index.md).  
  
### <a name="generic-types"></a>Obecné typy  
 Třídy a struktury lze definovat pomocí jednoho nebo více parametrů typu. Kód klienta dodává typ při vytváření instance typu. Například <xref:System.Collections.Generic.List%601> Třída v <xref:System.Collections.Generic> oboru názvů je definována s jedním parametrem typu. Kód klienta vytvoří `List<string>` instanci nebo `List<int>` určit typ, který bude obsahovat seznam. Další informace naleznete [v tématu Generics](../generics/index.md).  
  
### <a name="static-types"></a>Statické typy  
 Třídy (ale ne struktury) lze deklarovat jako [statické](../../language-reference/keywords/static.md). Statická třída může obsahovat pouze statické členy a nelze vytvořit instanci s novým klíčovým slovem. Jedna kopie třídy je načtena do paměti při načtení programu a jeho členové jsou přístupné prostřednictvím názvu třídy. Třídy i struktury mohou obsahovat statické členy. Další informace naleznete [v tématu Statické třídy a statické členy třídy](./static-classes-and-static-class-members.md).  
  
### <a name="nested-types"></a>Vnořené typy  
 Třídu nebo strukturu lze vnořit do jiné třídy nebo struktury. Další informace naleznete v [tématu Vnořené typy](./nested-types.md).  
  
### <a name="partial-types"></a>Částečné typy  
 Můžete definovat část třídy, struktury nebo metody v jednom souboru kódu a další část v samostatném souboru kódu. Další informace naleznete [v tématu Částečné třídy a metody](./partial-classes-and-methods.md).  
  
### <a name="object-initializers"></a>Inicializátory objektů  
 Můžete vytvořit inkonializovat a inicializovat třídy nebo struktury objekty a kolekce objektů, aniž by explicitně volat jejich konstruktor. Další informace naleznete v [tématu Objekt a kolekce Initializers](./object-and-collection-initializers.md).  
  
### <a name="anonymous-types"></a>Anonymní typy  
 V situacích, kdy není vhodné nebo nutné vytvořit pojmenovanou třídu, například při vyplnění seznamu datovými strukturami, které není nutné zachovat nebo předat jiné metodě, použijete anonymní typy. Další informace naleznete [v tématu Anonymní typy](./anonymous-types.md).  
  
### <a name="extension-methods"></a>Metody rozšíření  
 Třídu můžete "rozšířit" bez vytvoření odvozené třídy vytvořením samostatného typu, jehož metody lze volat, jako by patřily k původnímu typu. Další informace naleznete v [tématu Metody rozšíření](./extension-methods.md).  
  
### <a name="implicitly-typed-local-variables"></a>Implicitně typované lokální proměnné  
 V rámci metody třídy nebo struktury můžete použít implicitní psaní k instruování kompilátoru k určení správného typu v době kompilace. Další informace naleznete [v tématu Implicitně zadané místní proměnné](./implicitly-typed-local-variables.md).  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
