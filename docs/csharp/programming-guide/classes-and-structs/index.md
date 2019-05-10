---
title: Třídy a struktury - C# Průvodce programováním
ms.custom: seodec18
description: Popisuje použití tříd a struktur (struktury) v jazyce C#.
ms.date: 01/17/2016
helpviewer_keywords:
- structs [C#], about structs
- classes [C#], overview
- C# language, structs
- C# language, objects
- objects [C#]
- C# language, classes
ms.assetid: cc39dbda-8754-423e-b5b1-16a1db0734c0
ms.openlocfilehash: 9c26b8deb6036c13a9a61d8929b4cabba5f3ef67
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64584543"
---
# <a name="classes-and-structs-c-programming-guide"></a>Třídy a struktury (Průvodce programováním v C#)
Třídy a struktury jsou dvě základní konstrukce obecný systém typů v rozhraní .NET Framework. Každá je v podstatě datová struktura, která zapouzdřuje sadu dat a chování, které patří k sobě jako logická jednotka. Data a chování jsou *členy* třídy nebo struktury, a zahrnují metody, vlastnosti a události a tak dále, jak je uvedeno dále v tomto tématu.  
  
 Deklarace třídy nebo struktury je jako matrice, který slouží k vytváření instancí nebo objektů za běhu. Pokud definujete třídu nebo strukturu nazvanou `Person`, `Person` je název typu. Pokud deklarujete a inicializujete proměnnou `p` typu `Person`, `p` se říká, že objekt nebo instance `Person`. Více instancí stejného `Person` typu je možné vytvořit, a každá instance může mít různé hodnoty v její vlastnosti a pole.  
  
 Třída je typem odkazu. Když je vytvořen objekt třídy, proměnné, ke kterému je přiřazen objekt obsahuje pouze odkaz na tuto paměť. Pokud je odkaz na objekt přiřazen nové proměnné, Nová proměnná odkazuje na původní objekt. Změny provedené prostřednictvím jedné proměnné se projeví v jiné proměnné, protože obě odkazují na stejná data.  
  
 Struktura je typ hodnoty. Když se vytvoří struktura, obsahuje proměnné, ke kterému je přiřazena struktura, obsahovat skutečná data. Když je struktura přiřazena nové proměnné, zkopíruje se. Nové proměnné a původní proměnné proto obsahují dvě oddělené kopie stejných dat. Změny provedené v jedné kopii neovlivní druhou kopii.  
  
 Obecně třídy slouží k modelování složitějšího chování nebo dat, která se mají být změněna po vytvoření objektu třídy. Struktury jsou nejvhodnější pro malé datové struktury, které obsahují především data, které se mají být změněna po vytvoření struktury.  
  
 Další informace najdete v tématu [třídy](../../../csharp/programming-guide/classes-and-structs/classes.md), [objekty](../../../csharp/programming-guide/classes-and-structs/objects.md), a [struktury](../../../csharp/programming-guide/classes-and-structs/structs.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `CustomClass` v `ProgrammingGuide` obor názvů má tři členy: konstruktor instance, vlastnost s názvem `Number`a metodu s názvem `Multiply`. `Main` Metodu `Program` třída vytvoří instance (objekt) `CustomClass`, a metody a vlastnosti objektu jsou přístupné pomocí zápisu s tečkou.
  
 [!code-csharp[csProgGuideObjects#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/class1.cs#1)]  
  
## <a name="encapsulation"></a>Zapouzdření  
 *Zapouzdření* se někdy označuje jako první pilíř nebo Princip objektově orientované programování. Podle principu zapouzdření třídy nebo struktury můžete určit jak přístupný, každý z jejích členů je pro kód mimo třídy nebo struktury. Metody a proměnné, které nejsou určeny k použití mimo třídy nebo sestavení, lze skrýt a omezit tak potenciální kódování chyby nebo škodlivých exploitů.  
  
 Další informace o třídách naleznete v tématu [třídy](../../../csharp/programming-guide/classes-and-structs/classes.md) a [objekty](../../../csharp/programming-guide/classes-and-structs/objects.md).  
  
### <a name="members"></a>Členové  
 Všechny metody, pole, konstanty, vlastnosti a události musí být deklarována v rámci typu; Toto nastavení se nazývá *členy* typu. V jazyce C# nejsou žádné globální proměnné ani metody jako v některých jiných jazycích. Dokonce i vstupní bod programu, `Main` metodu, musí být deklarována v rámci třídy nebo struktury. Následující seznam obsahuje všechny různé druhy členů, které mohou být deklarovány ve třídě nebo struktuře.  
  
- [Pole](../../../csharp/programming-guide/classes-and-structs/fields.md)  
  
- [Konstanty](../../../csharp/programming-guide/classes-and-structs/constants.md)  
  
- [Vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)  
  
- [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
- [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
- [Události](../../../csharp/programming-guide/events/index.md)  
  
- [Finalizační metody](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
  
- [Indexery](../../../csharp/programming-guide/indexers/index.md)  
  
- [Operátory](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
  
- [Vnořené typy](../../../csharp/programming-guide/classes-and-structs/nested-types.md)  
  
### <a name="accessibility"></a>Usnadnění  
 Některé metody a vlastnosti jsou určeny k volání nebo přístupu z kódu mimo vaši třídu nebo strukturu a jsou známé jako *klientský kód*. Jiné metody a vlastnosti může být pouze pro použití v dané třídy nebo struktury samotné. Je důležité omezit dostupnost vašeho kódu tak, aby k němu lze přistoupit pouze zamýšlený klientský kód. Můžete upřesnit, jak počítačové vaše typy a členové pro klientský kód pomocí přístupu modifikátory přístupu [veřejné](../../../csharp/language-reference/keywords/public.md), [chráněné](../../../csharp/language-reference/keywords/protected.md), [interní](../../../csharp/language-reference/keywords/internal.md), [ interní chráněné](../../../csharp/language-reference/keywords/protected-internal.md), [privátní](../../../csharp/language-reference/keywords/private.md) a [private, protected](../../../csharp/language-reference/keywords/private-protected.md). Výchozí dostupnost je `private`. Další informace najdete v tématu [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
### <a name="inheritance"></a>Dědičnost  
 Třídy (ale ne struktury) podporují koncept dědičnosti. Třída, která je odvozena od jiné třídy ( *základní třída*) automaticky obsahuje všechny veřejné, chráněné a interní členy základní třídy s výjimkou jejích konstruktorů a finalizační metody. Další informace najdete v tématu [dědičnosti](../../../csharp/programming-guide/classes-and-structs/inheritance.md) a [polymorfismus](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).  
  
 Třídy mohou být deklarovány jako [abstraktní](../../../csharp/language-reference/keywords/abstract.md), což znamená, že jeden nebo více z jejich metod nemají implementaci. I když abstraktní třídy nelze přímo vytvořit instanci, mohou sloužit jako základní třídy pro jiné třídy, které tuto chybějící implementaci poskytují. Třídy lze také deklarovat jako [zapečetěné](../../../csharp/language-reference/keywords/sealed.md) zabránit tak jejich dědění jiné třídy. Další informace najdete v tématu [abstraktní a zapečetěné třídy a členové](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
### <a name="interfaces"></a>Rozhraní  
 Třídy a struktury mohou dědit více rozhraní. Chcete-li dědit z rozhraní znamená, že typ implementuje všechny metody definované v rozhraní. Další informace najdete v tématu [rozhraní](../../../csharp/programming-guide/interfaces/index.md).  
  
### <a name="generic-types"></a>Obecné typy  
 Třídy a struktury lze definovat pomocí jednoho nebo více parametrů typu. Klientský kód poskytuje typ při vytváření instance daného typu. Například <xref:System.Collections.Generic.List%601> třídy v <xref:System.Collections.Generic> obor názvů je definované s jedním parametrem typu. Klientský kód vytvoří instanci `List<string>` nebo `List<int>` k určení typu, který bude obsahovat seznam. Další informace najdete v tématu [obecných typů](../../../csharp/programming-guide/generics/index.md).  
  
### <a name="static-types"></a>Statické typy  
 Třídy (ale ne struktury) mohou být deklarovány jako [statické](../../../csharp/language-reference/keywords/static.md). Statická třída může obsahovat pouze statické členy a nelze vytvořit instanci pomocí klíčového slova new. Jedna kopie třídy, je načten do paměti v momentě načtení programu a její členové budou přístupní prostřednictvím názvu třídy. Třídy a struktury mohou obsahovat statické členy. Další informace najdete v tématu [statické třídy a statické členy třídy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
### <a name="nested-types"></a>Vnořené typy  
 Třídy nebo struktury může být vnořena do jiné třídy nebo struktury. Další informace najdete v tématu [vnořené typy](../../../csharp/programming-guide/classes-and-structs/nested-types.md).  
  
### <a name="partial-types"></a>Částečné typy  
 Můžete definovat část třídy, struktury nebo metody v jediném souboru kódu a jiné části v samostatném souboru kódu. Další informace najdete v tématu [částečné třídy a metody](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
### <a name="object-initializers"></a>Inicializátory objektů  
 Můžete konkretizovat a inicializovat třídu nebo strukturu objektů a kolekce objektů, bez explicitního volání jejich konstruktoru. Další informace najdete v tématu [inicializátory objektu a kolekce](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
### <a name="anonymous-types"></a>Anonymní typy  
 V situacích, kdy není vhodné nebo nezbytné vytvořit třídu s názvem například když plníte seznam datovými struktur, není potřeba přetrvat ani být předány jiné metodě, použijte anonymní typy. Další informace najdete v tématu [anonymní typy](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
### <a name="extension-methods"></a>Metody rozšíření  
 Můžete "rozšířit" třídu bez vytvoření odvozené třídy vytvořením samostatného typu, jejíž metody lze volat, jakoby příslušely k původnímu typu. Další informace najdete v tématu [rozšiřující metody](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  
  
### <a name="implicitly-typed-local-variables"></a>Implicitně typované lokální proměnné  
 V rámci metody třídy nebo struktury vám pomůže implicitního zápisu instruovali kompilátor k určení správného typu v době kompilace. Další informace najdete v tématu [implicitně typované lokální proměnné](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
