---
title: Třídy a struktury – C# Průvodce programováním
ms.custom: seodec18
description: Popisuje použití tříd a struktur (struktur) v C#.
ms.date: 01/17/2016
helpviewer_keywords:
- structs [C#], about structs
- classes [C#], overview
- C# language, structs
- C# language, objects
- objects [C#]
- C# language, classes
ms.assetid: cc39dbda-8754-423e-b5b1-16a1db0734c0
ms.openlocfilehash: c0b7e52cbbf0b49dee3598239f96e113ba929a80
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922260"
---
# <a name="classes-and-structs-c-programming-guide"></a>Třídy a struktury (Průvodce programováním v C#)
Třídy a struktury jsou dva ze základních konstrukcí systému obecného typu v .NET Framework. Každá z nich je v podstatě datová struktura, která zapouzdřuje sadu dat a chování, které patří dohromady jako logická jednotka. Data a chování jsou *členy* třídy nebo struktury a obsahují její metody, vlastnosti a události a tak dále, jak je uvedeno dále v tomto tématu.  
  
 Deklarace třídy nebo struktury je jako podrobný plán, který slouží k vytváření instancí nebo objektů za běhu. Pokud definujete třídu nebo strukturu s názvem `Person`, `Person` je název typu. Pokud deklarujete a inicializujete proměnnou `p` typu `Person`, `p` je `Person`označována jako objekt nebo instance. Lze vytvořit více instancí stejného `Person` typu a každá instance může mít v jeho vlastnostech a polích jiné hodnoty.  
  
 Třída je odkazový typ. Při vytvoření objektu třídy obsahuje proměnná, do které je objekt přiřazen, pouze odkaz na tuto paměť. Když je odkaz na objekt přiřazen nové proměnné, nová proměnná odkazuje na původní objekt. Změny provedené přes jednu proměnnou se projeví v jiné proměnné, protože obě odkazují na stejná data.  
  
 Struktura je typ hodnoty. Při vytvoření struktury obsahuje proměnná, ke které je přiřazena struktura, vlastní data struktury. Když je struktura přiřazena nové proměnné, je zkopírována. Nová proměnná a původní proměnná proto obsahují dvě samostatné kopie stejných dat. Změny provedené v jedné kopii nemají vliv na ostatní kopírování.  
  
 Obecně třídy jsou používány k modelování složitějšího chování nebo dat, která mají být upravena po vytvoření objektu třídy. Struktury jsou nejvhodnější pro malé datové struktury, které obsahují hlavně data, která nejsou určena k úpravám po vytvoření struktury.  
  
 Další informace naleznete v tématu [třídy](./classes.md), [objekty](./objects.md)a [struktury](./structs.md).  
  
## <a name="example"></a>Příklad  
 V `CustomClass` následujícím příkladu `ProgrammingGuide` má obor názvů tři členy: konstruktor instance, vlastnost s názvem `Number`a metodu s názvem `Multiply`. Metoda ve třídě vytvoří`CustomClass`instanci (objekt) a metoda objektu a vlastnost je k dispozici pomocí zápisu `Program`stečkou `Main` .
  
 [!code-csharp[csProgGuideObjects#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/class1.cs#1)]  
  
## <a name="encapsulation"></a>Zapouzdření  
 *Zapouzdření* se někdy označuje jako první pilíř nebo Princip objektově orientovaného programování. V souladu s principem zapouzdření může třída nebo struktura určit, jak přístupný každé z jejích členů je kód mimo třídu nebo strukturu. Metody a proměnné, které nejsou určeny pro použití vně třídy nebo sestavení, mohou být skryty pro omezení potenciálu chyb kódování nebo škodlivých zneužití.  
  
 Další informace o třídách naleznete v tématu [třídy](./classes.md) a [objekty](./objects.md).  
  
### <a name="members"></a>Členové  
 Všechny metody, pole, konstanty, vlastnosti a události musí být deklarovány v rámci typu; Tyto prvky se nazývají *členy* typu. V C#neexistují žádné globální proměnné ani metody, protože jsou v některých jiných jazycích. Dokonce i vstupní bod programu, `Main` metoda, musí být deklarována v rámci třídy nebo struktury. Následující seznam obsahuje všechny různé druhy členů, které mohou být deklarovány ve třídě nebo struktuře.  
  
- [Pole](./fields.md)  
  
- [Konstanty](./constants.md)  
  
- [Vlastnosti](./properties.md)  
  
- [Metody](./methods.md)  
  
- [Konstruktory](./constructors.md)  
  
- [Události](../events/index.md)  
  
- [Finalizační metody](./destructors.md)  
  
- [Indexery](../indexers/index.md)  
  
- [Operátory](../../language-reference/operators/index.md)  
  
- [Vnořené typy](./nested-types.md)  
  
### <a name="accessibility"></a>Usnadnění  
 Některé metody a vlastnosti mají být volány nebo dostupné z kódu mimo vaši třídu nebo strukturu, označované jako *kód klienta*. Jiné metody a vlastnosti mohou být použity pouze v samotné třídě nebo struktuře. Je důležité omezit přístupnost kódu, aby k němu mohl získat pouze zamýšlený kód klienta. Určíte, jak budou přístupné vaše typy a jejich členové klientskému kódu pomocí modifikátorů přístupu [Public](../../language-reference/keywords/public.md), [Protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [Protected Internal](../../language-reference/keywords/protected-internal.md), [Private](../../language-reference/keywords/private.md) a [Private Protected](../../language-reference/keywords/private-protected.md). Výchozí přístupnost je `private`. Další informace najdete v tématu [modifikátory přístupu](./access-modifiers.md).  
  
### <a name="inheritance"></a>Dědičnost  
 Třídy (ale ne struktury) podporují koncept dědičnosti. Třída, která je odvozena z jiné třídy ( *základní třída*), automaticky obsahuje všechny veřejné, chráněné a interní členy základní třídy s výjimkou jejich konstruktorů a finalizační metody. Další informace naleznete v tématu [Dědičnost](./inheritance.md) a [polymorfismus](./polymorphism.md).  
  
 Třídy mohou být deklarovány jako [abstraktní](../../language-reference/keywords/abstract.md), což znamená, že jedna nebo více jejich metod nemají žádnou implementaci. I když abstraktní třídy nemohou být vytvořeny přímo, mohou sloužit jako základní třídy pro jiné třídy, které poskytují chybějící implementaci. Třídy lze také deklarovat jako [zapečetěné](../../language-reference/keywords/sealed.md) , aby nedocházelo k dědění jiných tříd. Další informace naleznete v tématu [abstraktní a zapečetěné třídy a členy třídy](./abstract-and-sealed-classes-and-class-members.md).  
  
### <a name="interfaces"></a>Rozhraní  
 Třídy a struktury mohou dědit více rozhraní. Pro dědění z rozhraní znamená, že typ implementuje všechny metody definované v rozhraní. Další informace naleznete v tématu [rozhraní](../interfaces/index.md).  
  
### <a name="generic-types"></a>Obecné typy  
 Třídy a struktury lze definovat s jedním nebo více parametry typu. Klientský kód dodává typ při vytváření instance typu. Například <xref:System.Collections.Generic.List%601> Třída<xref:System.Collections.Generic> v oboru názvů je definována s jedním parametrem typu. Klientský kód vytvoří instanci `List<string>` nebo `List<int>` k určení typu, který bude obsahovat seznam. Další informace najdete v tématu [Obecné typy](../generics/index.md).  
  
### <a name="static-types"></a>Statické typy  
 Třídy (ale ne struktury) lze deklarovat jako [statické](../../language-reference/keywords/static.md). Statická třída může obsahovat pouze statické členy a nelze vytvořit instanci s klíčovým slovem New. Jedna kopie třídy je načtena do paměti, když se program načte a její členové jsou k dispozici prostřednictvím názvu třídy. Třídy i struktury mohou obsahovat statické členy. Další informace naleznete v tématu [statické třídy a statické členy třídy](./static-classes-and-static-class-members.md).  
  
### <a name="nested-types"></a>Vnořené typy  
 Třída nebo struktura může být vnořena do jiné třídy nebo struktury. Další informace naleznete v tématu [vnořené typy](./nested-types.md).  
  
### <a name="partial-types"></a>Částečné typy  
 Můžete definovat část třídy, struktury nebo metody v jednom souboru kódu a další části v samostatném souboru kódu. Další informace naleznete v tématu [částečné třídy a metody](./partial-classes-and-methods.md).  
  
### <a name="object-initializers"></a>Inicializátory objektů  
 Můžete vytvářet instance a inicializovat objekty třídy nebo struktury a kolekce objektů bez explicitního volání jejich konstruktoru. Další informace naleznete v tématu [Inicializátory objektů a kolekcí](./object-and-collection-initializers.md).  
  
### <a name="anonymous-types"></a>Anonymní typy  
 V situacích, kdy není vhodné nebo nutné vytvořit pojmenovanou třídu, například při sestavování seznamu pomocí datových struktur, které není nutné uchovávat nebo předávat jiné metodě, použijete anonymní typy. Další informace najdete v tématu [anonymní typy](./anonymous-types.md).  
  
### <a name="extension-methods"></a>Metody rozšíření  
 Můžete "rozšiřuje" třídu bez vytváření odvozené třídy vytvořením samostatného typu, jehož metody lze volat, jako by patřily k původnímu typu. Další informace naleznete v tématu [metody rozšíření](./extension-methods.md).  
  
### <a name="implicitly-typed-local-variables"></a>Implicitně typované lokální proměnné  
 V rámci metody třídy nebo struktury lze pomocí implicitního zápisu instruovat kompilátor, aby určil správný typ v době kompilace. Další informace naleznete v tématu [implicitně typované lokální proměnné](./implicitly-typed-local-variables.md).  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
