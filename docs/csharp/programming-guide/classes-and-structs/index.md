---
title: Třídy a struktury (Průvodce programováním v C#)
description: Popisuje použití třídy a struktury (struktury) v jazyce C#.
ms.date: 01/17/2016
helpviewer_keywords:
- structs [C#], about structs
- classes [C#], overview
- C# language, structs
- C# language, objects
- objects [C#]
- C# language, classes
ms.assetid: cc39dbda-8754-423e-b5b1-16a1db0734c0
ms.openlocfilehash: 801f8e64bf64ee55651521ba53915000cc326303
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33327356"
---
# <a name="classes-and-structs-c-programming-guide"></a>Třídy a struktury (Průvodce programováním v C#)
Třídy a struktury jsou dva základní konstrukce z obecný systém typů v rozhraní .NET Framework. Každá je v podstatě struktura dat, který zapouzdřuje sadu dat a chování, které patří společně jako logickou jednotku. Data a chování jsou *členy* třídy nebo struktura, a obsahují metody, vlastnosti a události a podobně, jak je uvedeno dále v tomto tématu.  
  
 Deklaraci třídě nebo struktuře je jako matrici, která se používá k vytvoření instance nebo objekty v době běhu. Pokud definujete třídě nebo struktuře názvem `Person`, `Person` je název typu. Pokud deklarace a inicializace proměnné `p` typu `Person`, `p` říká, že je na objekt nebo instanci `Person`. Více instancí stejného `Person` typ lze vytvořit, a každá instance může mít různé hodnoty v její vlastnosti a pole.  
  
 Třída je typu odkazu. Když je vytvořen objekt třídy, obsahuje proměnnou, do kterého daný objekt je přiřazen pouze odkaz na tuto paměť. Pokud reference objektu je přiřazen k nové proměnné, nové proměnné odkazuje na původní objekt. Změny provedené prostřednictvím jednu proměnnou se projeví v jiné proměnné, protože obě odkazují ke stejným datům.  
  
 Struktury je typ hodnoty. Když je vytvořen struktury, obsahuje proměnnou, ke kterému je přiřazena struct struktura na skutečná data. Když struktura je přiřazen k nové proměnné, je zkopírována. Novou proměnnou a původní proměnná proto obsahovat dvě samostatné kopie stejná data. Změny provedené v jedné kopie nemají vliv na jiné kopie.  
  
 Třídy se obecně používají pro modelování složitější chování nebo data, která má být změnit po vytvoření objektu třídy. Struktury jsou nejvhodnější pro malé datové struktury, které obsahují hlavně data, která není určena pro změnit po vytvoření struct.  
  
 Další informace najdete v tématu [třídy](../../../csharp/programming-guide/classes-and-structs/classes.md), [objekty](../../../csharp/programming-guide/classes-and-structs/objects.md), a [struktury](../../../csharp/programming-guide/classes-and-structs/structs.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `CustomClass` v `ProgrammingGuide` oboru názvů má tři členy: konstruktoru instance, vlastnost s názvem `Number`a metodu s názvem `Multiply`. `Main` Metoda v `Program` třída vytvoří instance (objekt) `CustomClass`, a metod a vlastností objektu přistupují pomocí zápisu s tečkou.
  
 [!code-csharp[csProgGuideObjects#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/class1.cs#1)]  
  
## <a name="encapsulation"></a>Zapouzdření  
 *Zapouzdření* se někdy označuje jako první pilíře nebo Princip objektově orientované programování. Podle principu zapouzdření třídě nebo struktuře můžete určit způsob přístupné každý ze členů bude kód mimo třídě nebo struktuře. Metody a proměnné, které nejsou určeny k použití v mimo třídu nebo sestavení může být skryté omezit potenciální pro kódování škodlivý zneužití nebo chyby.  
  
 Další informace o třídách najdete v tématu [třídy](../../../csharp/programming-guide/classes-and-structs/classes.md) a [objekty](../../../csharp/programming-guide/classes-and-structs/objects.md).  
  
### <a name="members"></a>Členové  
 Všechny metody, pole, konstanty, vlastnosti a události musí být deklarován v rámci typu; Toto nastavení se nazývá *členy* typu. V jazyce C# neexistují žádné globální proměnné nebo metod, protože v některých dalších jazycích. I programu vstupního bodu, `Main` metodu, musí být deklarován v třídě nebo struktuře. Následující seznam obsahuje různé typy členů, které může být deklarován v třídě nebo struktuře.  
  
-   [Pole](../../../csharp/programming-guide/classes-and-structs/fields.md)  
  
-   [Konstanty](../../../csharp/programming-guide/classes-and-structs/constants.md)  
  
-   [Vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)  
  
-   [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [Události](../../../csharp/programming-guide/events/index.md)  
  
-   [Finalizační metody](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
  
-   [Indexery](../../../csharp/programming-guide/indexers/index.md)  
  
-   [Operátory](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
  
-   [Vnořené typy](../../../csharp/programming-guide/classes-and-structs/nested-types.md)  
  
### <a name="accessibility"></a>Usnadnění  
 Některé metody a vlastnosti mají být volána nebo k němu přistupovat z kódu mimo vaší třídě nebo struktuře, označuje jako *kód klienta*. Jiné metody a vlastnosti, může být pouze pro použití ve třídě nebo struktuře, sám sebe. Je důležité omezit usnadnění kódu tak, aby pouze kód určený klientský dosáhnout. Zadejte jak přístupné vaše typy a jejich členové mají kód klienta pomocí modifikátory přístupu [veřejné](../../../csharp/language-reference/keywords/public.md), [chráněné](../../../csharp/language-reference/keywords/protected.md), [interní](../../../csharp/language-reference/keywords/internal.md), [ chráněné interní](../../../csharp/language-reference/keywords/protected-internal.md), [privátní](../../../csharp/language-reference/keywords/private.md) a [privátní chráněné](../../../csharp/language-reference/keywords/private-protected.md). Je výchozí usnadnění `private`. Další informace najdete v tématu [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
### <a name="inheritance"></a>Dědičnost  
 Třídy (ale ne struktury) podporují koncept dědění. Třída odvozená z jiné třídy ( *základní třída*) automaticky obsahuje všechny veřejné, chráněné a vnitřní členy základní třídy, s výjimkou jeho konstruktory a finalizační metody. Další informace najdete v tématu [dědičnosti](../../../csharp/programming-guide/classes-and-structs/inheritance.md) a [polymorfismus](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).  
  
 Třídy mohou být deklarována jako [abstraktní](../../../csharp/language-reference/keywords/abstract.md), což znamená, že jeden nebo více své metody nemají implementaci. I když abstraktní třídy nelze vytvořit instanci přímo, může sloužit jako základní třídy pro jiné třídy, které poskytují chybějící implementace. Třídy lze deklarovat také jako [zapečetěné](../../../csharp/language-reference/keywords/sealed.md) zabránit jiné třídy, která dědí z nich. Další informace najdete v tématu [abstraktní a zapečetěné třídy a jejich členové](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
### <a name="interfaces"></a>Rozhraní  
 Třídy a struktury může dědit vlastnosti více rozhraní. Dědění z rozhraní znamená, že typ implementuje všechny metody, které jsou definované v rozhraní. Další informace najdete v tématu [rozhraní](../../../csharp/programming-guide/interfaces/index.md).  
  
### <a name="generic-types"></a>Obecné typy  
 Třídy a struktury lze definovat se jeden nebo více parametrů typu. Kód klienta poskytuje typ, když se vytváří instanci typu. Například <xref:System.Collections.Generic.List%601> třídy v <xref:System.Collections.Generic> obor názvů je definován s jeden typ parametru. Vytvoří instanci kód klienta `List<string>` nebo `List<int>` k určení typu, který bude obsahovat seznam. Další informace najdete v tématu [obecné typy](../../../csharp/programming-guide/generics/index.md).  
  
### <a name="static-types"></a>Statické typy  
 Třídy (ale ne struktury) lze deklarovat jako [statické](../../../csharp/language-reference/keywords/static.md). Statická třída může obsahovat pouze statické členy a nelze vytvořit instanci s new – klíčové slovo. Jedna kopie třídy je načten do paměti při načtení program a jeho členové jsou přístupné prostřednictvím název třídy. Třídy a struktury může obsahovat statické členy. Další informace najdete v tématu [statické třídy a statické členy třídy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
### <a name="nested-types"></a>Vnořené typy  
 Třídě nebo struktuře lze začlenit do jiné třídě nebo struktuře. Další informace najdete v tématu [vnořené typy](../../../csharp/programming-guide/classes-and-structs/nested-types.md).  
  
### <a name="partial-types"></a>Částečné typy  
 Část třída, struktura nebo metoda v jednom souboru kódu a další část můžete definovat v samostatném souboru kódu. Další informace najdete v tématu [částečné třídy a metody](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
### <a name="object-initializers"></a>Inicializátory objektů  
 Můžete vytvořit instanci a inicializaci třídy nebo struktura objekty a kolekce objektů, bez nutnosti explicitně volání jejich konstruktor. Další informace najdete v tématu [inicializátory objektu a kolekce](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
### <a name="anonymous-types"></a>Anonymní typy  
 V situacích, kdy není praktické nebo potřebné pro vytvoření třídy s názvem například když jsou naplnění seznamu s daty struktur, není nutné zachovat nebo předejte na jinou metodu, můžete použít anonymní typy. Další informace najdete v tématu [anonymní typy](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
### <a name="extension-methods"></a>Metody rozšíření  
 Můžete "rozšířit" třídu bez vytvoření odvozené třídy tak, že vytvoříte samostatné typu, jejíž metody lze volat jako v případě, kdyby patřily do původní typ. Další informace najdete v tématu [rozšiřující metody](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  
  
### <a name="implicitly-typed-local-variables"></a>Implicitně typované lokální proměnné  
 Ve třídě nebo struktuře metodu můžete implicitní zadáním kompilátoru k určení správného typu v době kompilace. Další informace najdete v tématu [implicitně typované lokální proměnné](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
