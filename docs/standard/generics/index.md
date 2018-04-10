---
title: Obecné typy v architektuře .NET Framework
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generic methods, type inference
- generics [.NET Framework], collections
- generic interfaces [.NET Framework]
- constructed generic types
- nested generic types
- generic type definitions
- generic classes [.NET Framework]
- generics [.NET Framework], interfaces
- generics [.NET Framework], about
- generics [.NET Framework]
- generic collections [.NET Framework]
- generic delegates [.NET Framework]
- generic type arguments
- generics [.NET Framework], delegates
- generics [.NET Framework], features
- constraints [.NET Framework]
- generic types
- generic type parameters
ms.assetid: 2994d786-c5c7-4666-ab23-4c83129fe39c
caps.latest.revision: 23
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d06c2ae074045ae750c079383f43c3d6aa6f726c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="generics-in-the-net-framework"></a>Obecné typy v architektuře .NET Framework
<a name="top"></a>Obecné typy umožňují přizpůsobit metoda, třída, struktura nebo rozhraní na přesné datový typ, kterým se pracuje. Například místo použití <xref:System.Collections.Hashtable> třídy, což umožňuje klíče a hodnoty k být jakéhokoli typu, můžete použít <xref:System.Collections.Generic.Dictionary%602> obecné třídy a zadat typ povolené pro klíč a typ povolené pro hodnotu. Mezi výhody obecných typů jsou vyšší kódu – opětovné použití a typ zabezpečení.  
  
 Toto téma obsahuje přehled obecných typů v rozhraní .NET Framework a souhrn obecná typů nebo metody. Obsahuje následující oddíly:  
  
-   [Definování a použití obecných typů](#defining_and_using_generics)  
  
-   [Terminologie obecných typů](#generics_terminology)  
  
-   [Knihovny tříd a jazyková podpora](#class_library_and_language_support)  
  
-   [Vnořené typy a obecné typy](#nested_types_and_generics)  
  
-   [Související témata](#related_topics)  
  
-   [Referenční informace](#reference)  
  
<a name="defining_and_using_generics"></a>   
## <a name="defining-and-using-generics"></a>Definování a použití obecných typů  
 Obecné typy jsou třídy, struktury, rozhraní a metody, které mají zástupné symboly (parametry typu) pro jeden nebo více typů, které ukládají nebo používají. Třída obecné kolekce může použít parametr typu jako zástupný symbol pro typ objektů, které uchovává; parametry typu se zobrazí jako typy jeho polí a typy parametrů jeho metod. Obecná metoda může používat jeho parametr typu jako typ hodnoty nebo jako typ jeden z jeho formální parametrů. Následující kód ukazuje definici jednoduchého obecná třída.  
  
 [!code-cpp[Conceptual.Generics.Overview#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#2)]
 [!code-csharp[Conceptual.Generics.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#2)]
 [!code-vb[Conceptual.Generics.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#2)]  
  
 Když vytvoříte instanci obecné třídy, zadáte skutečné typy k nahrazení parametrů typu. To vytváří nová obecná třída, označuje jako sestavené obecné třídy, s vašimi vybranými typy nahrazena všude, kde parametrů. Výsledkem je třída bezpečnost typů, přesně podle svého výběru typů, jak ukazuje následující kód.  
  
 [!code-cpp[Conceptual.Generics.Overview#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#3)]
 [!code-csharp[Conceptual.Generics.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#3)]
 [!code-vb[Conceptual.Generics.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#3)]  
  
<a name="generics_terminology"></a>   
### <a name="generics-terminology"></a>Terminologie obecných typů  
 K popisu obecných typů v rozhraní .NET Framework se používají následující termíny:  
  
-   A *definice obecného typu* je třída, struktura nebo deklarace rozhraní, která funguje jako šablona, se zástupnými symboly pro typy, které může obsahovat nebo použít. Například <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> třídy může obsahovat dva typy: klíče a hodnoty. Vzhledem k definici obecného typu je pouze šablonu, nelze vytvořit instance třídy, struktury nebo rozhraní, které je definice obecného typu.  
  
-   *Parametry obecného typu*, nebo *parametry typu*, jsou zástupné symboly v definici obecný typ nebo metoda. <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> Obecného typu má dva parametry typu `TKey` a `TValue`, které představují typy klíčů a hodnot.  
  
-   A *sestavený obecného typu*, nebo *sestavený typ*, je výsledkem určení typů parametrů obecného typu definice obecného typu.  
  
-   A *argument obecného typu* je žádný typ, který je nahrazena pro parametr obecného typu.  
  
-   Obecný termín *obecného typu* zahrnuje sestavené typy a definice obecného typu.  
  
-   *Kovariance* a *kontravariance* typu obecné parametry umožňují používat sestavené obecné typy, jejichž typ argumenty jsou více odvozené (kovariance) nebo méně odvozené (kontravariance) než cílový sestavený typ. Kovariance a kontravariance se souhrnně označují jako *odchylky*. Další informace najdete v tématu [kovariance a kontravariance](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
-   *Omezení* omezení umísťují na parametry obecného typu. Například může omezit parametry typu na typy, které implementují <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> obecná rozhraní, ujistěte se, že lze provést řazení instance typu. Můžete také omezit parametry typu na typy, které mají určité základní třídy, které mají výchozí konstruktor nebo odkazové typy nebo typy hodnot, které jsou. Uživatelé obecného typu nelze nahradit argumenty typu, které nesplňují omezení.  
  
-   A *obecná metoda definice* je metoda se dvěma seznamy parametrů: seznam parametry obecného typu a formální parametry. Parametry typu se může zobrazit jako návratový typ nebo typy formální parametry, jak je znázorněno v následujícím kódu.  
  
 [!code-cpp[Conceptual.Generics.Overview#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#4)]
 [!code-csharp[Conceptual.Generics.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#4)]
 [!code-vb[Conceptual.Generics.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#4)]  
  
 Obecné metody se může zobrazit na obecné nebo neobecné typy. Je důležité si uvědomit, že metoda není obecná právě, protože patří do obecného typu nebo i, protože má formální parametry jejichž typy jsou obecné parametry nadřazeného typu. Metoda je obecná pouze v případě, že má svou vlastní seznam parametrů typu. V následujícím kódu, pouze metoda `G` je obecná.  
  
 [!code-cpp[Conceptual.Generics.Overview#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#5)]
 [!code-csharp[Conceptual.Generics.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#5)]
 [!code-vb[Conceptual.Generics.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#5)]  
  
 [Zpět na začátek](#top)  
  
<a name="advantages_limitations"></a>   
## <a name="advantages-and-disadvantages-of-generics"></a>Výhody a nevýhody obecných typů  
 Existuje mnoho výhod pomocí obecné kolekce a delegáti:  
  
-   Bezpečnost typů. Obecné typy posunutí zatížení bezpečnost typů od vás kompilátoru. Není nutné napsat kód pro testování pro správného datového typu, protože je vyžadována v době kompilace. Potřeba přetypování a možnost běhové chyby jsou omezeny.  
  
-   Snadno znovu použít menší kód a kód. Není nutné přepsat členy a dědí ze základního typu. Například <xref:System.Collections.Generic.LinkedList%601> je připravený k okamžitému použití. Například můžete vytvořit seznam řetězců propojené s následující deklarace proměnné:  
  
     [!code-cpp[HowToGeneric#24](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/source2.cpp#24)]
     [!code-csharp[HowToGeneric#24](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/source2.cs#24)]
     [!code-vb[HowToGeneric#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/source2.vb#24)]  
  
-   Lepší výkon. Obecné typy kolekcí obecně poskytují lepší výkon pro ukládání a manipulace s typy hodnot, protože není potřeba pole hodnoty typů.  
  
-   Obecní delegáti povolit bezpečnost typů zpětná volání, aniž by bylo nutné vytvořit více delegát třídy. Například <xref:System.Predicate%601> obecný delegát umožňuje vytvoření metody, která implementuje vlastních kritérií vyhledávání pro konkrétní typ a použít metodu pomocí metod <xref:System.Array> zadejte například <xref:System.Array.Find%2A>, <xref:System.Array.FindLast%2A>, a <xref:System.Array.FindAll%2A> .  
  
-   Obecné typy zjednodušit dynamicky generovaného kódu. Při použití obecných typů pomocí dynamicky generovaném kódu není potřeba generovat typu. Tím se zvyšuje počet scénáře ve kterých se dá použít zjednodušené dynamické metody namísto generování celý sestavení. Další informace najdete v tématu Postupy: definování a spouštět dynamické metody a DynamicMethod.  
  
 Tady jsou některá omezení obecných typů:  
  
-   Obecné typy může být odvozen od většiny základních tříd, jako například <xref:System.MarshalByRefObject> (a omezení může být použita pro požadavek, aby se parametry obecného typu odvozeny od základní třídy jako <xref:System.MarshalByRefObject>). Ale [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] nepodporuje obecné typy vázané na kontextu. Obecný typ může být odvozen od <xref:System.ContextBoundObject>, ale pokusu o vytvoření instance tohoto typu příčiny <xref:System.TypeLoadException>.  
  
-   Výčty nemohou mít parametry obecného typu. Výčet může být generický pouze náhodou (například proto je vnořený v obecného typu, který je definován pomocí jazyka Visual Basic, c nebo C++). Další informace najdete v tématu "Výčty" v [obecný systém typů](../../../docs/standard/base-types/common-type-system.md).  
  
-   Zjednodušené dynamické metody nesmí být obecný.  
  
-   V jazyce Visual Basic, C# a C++ typu, který je součástí obecného typu nejde vytvořit instance, pokud typy byly přiřazeny parametry typu všech nadřazených typů. Jinými slovy to je, že v reflexe, obsahuje vnořené typ, který je definován pomocí těchto jazycích parametry typu všech nadřazených typů. To umožňuje uzavření typy, který se má použít v definicích člen vnořené typy parametrů typu. Další informace najdete v části "Vnořené typy" v <xref:System.Type.MakeGenericType%2A>.  
  
    > [!NOTE]
    >  Vnořené typ, který je definován pomocí vytváření kódu v dynamickém sestavení nebo pomocí [Ilasm.exe (IL assembleru)](../../../docs/framework/tools/ilasm-exe-il-assembler.md) není potřeba zahrnovat parametry typu z jeho nadřazených typů; ale pokud neobsahuje je parametry typu nejsou v oboru ve vnořené třídy.  
  
     Další informace najdete v části "Vnořené typy" v <xref:System.Type.MakeGenericType%2A>.  
  
 [Zpět na začátek](#top)  
  
<a name="class_library_and_language_support"></a>   
## <a name="class-library-and-language-support"></a>Knihovny tříd a jazyková podpora  
 Rozhraní .NET Framework poskytuje řadu obecné třídy kolekcí v následujících oborů názvů:  
  
-   <xref:System.Collections.Generic> Obor názvů obsahuje většinu typů obecnou kolekci, poskytuje rozhraní .NET Framework, jako <xref:System.Collections.Generic.List%601> a <xref:System.Collections.Generic.Dictionary%602> obecné třídy.  
  
-   <xref:System.Collections.ObjectModel> Obor názvů katalogizuje další obecné typy kolekcí, jako <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> obecná třída, která se hodí pro zpřístupnění objektové modely uživatelům vaší třídy.  
  
 Obecná rozhraní pro provádění porovnání rovnosti a řazení jsou součástí <xref:System> oboru názvů, společně s obecný delegát typy obslužných rutin událostí, převody a predikáty vyhledávání.  
  
 K byla přidána podpora pro obecné typy <xref:System.Reflection> obor názvů pro zkoumání obecné typy a metod, na <xref:System.Reflection.Emit> pro Emitování dynamických sestavení, které obsahují obecné typy a metody a <xref:System.CodeDom> pro generování zdroje grafů které zahrnují obecné typy.  
  
 Modul common language runtime poskytuje nové operační kódy a předpony pro podporu obecné typy v Microsoft (MSIL intermediate language), včetně <xref:System.Reflection.Emit.OpCodes.Stelem>, <xref:System.Reflection.Emit.OpCodes.Ldelem>, <xref:System.Reflection.Emit.OpCodes.Unbox_Any>, <xref:System.Reflection.Emit.OpCodes.Constrained>, a <xref:System.Reflection.Emit.OpCodes.Readonly>.  
  
 Visual C++, C# a Visual Basic všechny poskytují plnou podporu pro definování a použití obecných typů. Další informace o podpoře jazyků naleznete v tématu [obecné typy v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/data-types/generic-types.md), [Úvod do obecných typů](~/docs/csharp/programming-guide/generics/introduction-to-generics.md), a [přehled obecné typy v jazyce Visual C++](/cpp/windows/overview-of-generics-in-visual-cpp).  
  
 [Zpět na začátek](#top)  
  
<a name="nested_types_and_generics"></a>   
## <a name="nested-types-and-generics"></a>Vnořené typy a obecné typy  
 Typ, který je vnořených v obecného typu mohou záviset na typu parametry nadřazeného obecného typu. Modul common language runtime zvažuje vnořené typy jako obecný, i když nemají vlastní parametry obecného typu. Při vytváření instance typu vnořené, musíte zadat argumenty typu pro všechny nadřazené obecné typy.  
  
 [Zpět na začátek](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Generování kolekcí v architektuře .NET Framework](../../../docs/standard/generics/collections.md)|Popisuje obecnou kolekci třídy a jiné obecné typy v rozhraní .NET Framework.|  
|[Obecné delegáty pro manipulaci s poli a seznamy](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)|Popisuje obecní delegáti převody, predikáty vyhledávání a akce, které budou provedeny na elementy pole nebo kolekce.|  
|[Obecná rozhraní](../../../docs/standard/generics/interfaces.md)|Popisuje obecná rozhraní, které tvoří běžné funkce celé řady obecných typů.|  
|[Kovariance a kontravariance](../../../docs/standard/generics/covariance-and-contravariance.md)|Popisuje kovariance a kontravariance v parametry obecného typu.|  
|[Běžně používané typy kolekcí](../../../docs/standard/collections/commonly-used-collection-types.md)|Poskytuje souhrnné informace o vlastnostech a scénáře použití typy kolekcí v rozhraní .NET Framework, včetně obecné typy.|  
|[Kdy použít generické kolekce](../../../docs/standard/collections/when-to-use-generic-collections.md)|Popisuje obecná pravidla pro určování, kdy použít obecné typy kolekcí.|  
|[Postupy: Definování obecného typu pomocí generování reflexe](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)|Vysvětluje, jak vygenerovat dynamická sestavení, které zahrnují obecné typy a metody.|  
|[Obecné typy v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/data-types/generic-types.md)|Popisuje funkce obecných typů pro uživatele, Visual Basic, včetně témat s postupy pro používání a definice obecných typů.|  
|[Úvod do obecných typů](~/docs/csharp/programming-guide/generics/introduction-to-generics.md)|Poskytuje přehled o definice a použití obecných typů pro C# uživatele.|  
|[Přehled obecných typů ve Visual C++](/cpp/windows/overview-of-generics-in-visual-cpp)|Popisuje funkce obecných typů pro uživatele, C++, včetně rozdíly mezi obecné typy a šablony.|  
  
<a name="reference"></a>   
## <a name="reference"></a>Odkaz  
 <xref:System.Collections.Generic>  
  
 <xref:System.Collections.ObjectModel>  
  
 <xref:System.Reflection.Emit.OpCodes?displayProperty=nameWithType>  
  
 [Zpět na začátek](#top)
