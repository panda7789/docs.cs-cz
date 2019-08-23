---
title: Obecné typy v .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5c9f15a7ff30d5647338bf1954aca441b47281b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948745"
---
# <a name="generics-in-net"></a>Obecné typy v .NET

<a name="top"></a>Obecné typy umožňují přizpůsobit metodu, třídu, strukturu nebo rozhraní na přesný datový typ, na kterém funguje. Například namísto použití <xref:System.Collections.Hashtable> třídy, která umožňuje klíčům a hodnotám být libovolného typu, můžete <xref:System.Collections.Generic.Dictionary%602> použít obecnou třídu a zadat typ povolený pro klíč a typ povolený pro hodnotu. Z výhod obecných typů se zvyšuje použitelnost kódu a bezpečnost typů.  
  
 Toto téma poskytuje přehled obecných typů v rozhraní .NET a souhrn obecných typů a metod. Obsahuje následující oddíly:  
  
- [Definování a použití generických typů](#defining_and_using_generics)  
  
- [Terminologie generických typů](#generics_terminology)  
  
- [Knihovna tříd a podpora jazyků](#class_library_and_language_support)  
  
- [Vnořené typy a obecné typy](#nested_types_and_generics)  
  
- [Příbuzná témata](#related_topics)  
  
- [Referenční informace](#reference)  
  
<a name="defining_and_using_generics"></a>   
## <a name="defining-and-using-generics"></a>Definování a použití generických typů  
 Obecné typy jsou třídy, struktury, rozhraní a metody, které mají zástupné symboly (parametry typu) pro jeden nebo více typů, které jsou uloženy nebo použity. Třída obecné kolekce může používat parametr typu jako zástupný symbol pro typ objektů, které úložiště ukládá; parametry typu se zobrazí jako typy polí a typy parametrů jejich metod. Obecná metoda může použít svůj parametr typu jako typ své návratové hodnoty nebo jako typ jednoho z jeho formálních parametrů. Následující kód ilustruje jednoduchou definici obecné třídy.  
  
 [!code-cpp[Conceptual.Generics.Overview#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#2)]
 [!code-csharp[Conceptual.Generics.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#2)]
 [!code-vb[Conceptual.Generics.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#2)]  
  
 Při vytváření instance obecné třídy zadáte skutečné typy, které mají být nahrazeny parametry typu. Tím se vytvoří nová Obecná třída označovaná jako konstruovaná obecná třída s vybranými typy, které jsou nahrazeny všude, kde se objeví parametry typu. Výsledkem je typově bezpečná třída, která je upravena podle vašeho výběru typů, jak ukazuje následující kód.  
  
 [!code-cpp[Conceptual.Generics.Overview#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#3)]
 [!code-csharp[Conceptual.Generics.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#3)]
 [!code-vb[Conceptual.Generics.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#3)]  
  
<a name="generics_terminology"></a>   
### <a name="generics-terminology"></a>Terminologie generických typů  
 Pro diskuzi o obecných typech v rozhraní .NET se používají následující výrazy:  
  
- *Definice obecného typu* je deklarace třídy, struktury nebo rozhraní, která funguje jako šablona, se zástupnými symboly pro typy, které může obsahovat nebo použít. <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> Třída může například obsahovat dva typy: klíče a hodnoty. Vzhledem k tomu, že definice obecného typu je pouze šablona, nelze vytvořit instance třídy, struktury nebo rozhraní, které je definicí obecného typu.  
  
- *Parametry obecného typu*nebo *parametry typu*jsou zástupné symboly v definici obecného typu nebo metody. Obecný typ má dva `TKey` parametry typu a `TValue`, které reprezentují typy jeho klíčů a hodnot. <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>  
  
- *Konstruovaný obecný typ*, neboli *konstruovaný typ*, je výsledkem určení typů pro parametry obecného typu definice obecného typu.  
  
- *Argument obecného typu* je libovolný typ, který je nahrazen parametrem obecného typu.  
  
- *Obecný typ* běžné podmínky zahrnuje konstruované typy i definice obecného typu.  
  
- *Kovariance* a *kontravariance* parametrů obecného typu umožňuje použít konstruované obecné typy, jejichž argumenty typu jsou více odvozené (kovariance) nebo méně odvozené (kontravariance) než cílový konstruovaný typ. Kovariance a kontravariance jsou souhrnně označovány jako *Variance*. Další informace najdete v tématu [kovariance a kontravariance](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
- *Omezení* jsou omezení pro parametry obecného typu. Například můžete omezit parametr typu na typy, které implementují <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> obecné rozhraní, aby bylo zajištěno, že lze seřadit instance daného typu. Můžete také omezit parametry typu na typy, které mají konkrétní základní třídu, která má konstruktor bez parametrů, nebo, které jsou odkazové typy nebo hodnoty. Uživatelé obecného typu nemohou dosadit argumenty typu, které nesplňují omezení.  
  
- *Obecná definice metody* je metoda se dvěma seznamy parametrů: seznam parametrů obecného typu a seznam formálních parametrů. Parametry typu se mohou zobrazit jako návratový typ nebo jako typy formálních parametrů, jak ukazuje následující kód.  
  
 [!code-cpp[Conceptual.Generics.Overview#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#4)]
 [!code-csharp[Conceptual.Generics.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#4)]
 [!code-vb[Conceptual.Generics.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#4)]  
  
 Obecné metody se můžou vyskytovat na obecných nebo neobecných typech. Je důležité si uvědomit, že metoda není obecná, protože patří do obecného typu, nebo i když má formální parametry, jejichž typy jsou obecné parametry nadřazeného typu. Metoda je obecná pouze v případě, že má svůj vlastní seznam parametrů typu. V následujícím kódu je pouze metoda `G` obecná.  
  
 [!code-cpp[Conceptual.Generics.Overview#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#5)]
 [!code-csharp[Conceptual.Generics.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#5)]
 [!code-vb[Conceptual.Generics.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#5)]  
  
 [Zpět na začátek](#top)  
  
<a name="advantages_limitations"></a>   
## <a name="advantages-and-disadvantages-of-generics"></a>Výhody a nevýhody obecných typů  
 Použití obecných kolekcí a delegátů má mnoho výhod:  
  
- Bezpečnost typů. Obecné typy posunou zatížení typu zabezpečení od vás do kompilátoru. Není nutné psát kód pro testování správného datového typu, protože je vynutila v době kompilace. Je potřeba snížit typ přetypování a možnost chyb za běhu.  
  
- Méně kód a kód je snazší znovu použít. Není nutné dědit ze základního typu a přepsat členy. Například <xref:System.Collections.Generic.LinkedList%601> je připraven k okamžitému použití. Můžete například vytvořit propojený seznam řetězců s následující deklarací proměnné:  
  
     [!code-cpp[HowToGeneric#24](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/source2.cpp#24)]
     [!code-csharp[HowToGeneric#24](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/source2.cs#24)]
     [!code-vb[HowToGeneric#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/source2.vb#24)]  
  
- Lepší výkon. Obecné typy kolekcí obecně poskytují lepší pro ukládání a manipulaci s typy hodnot, protože není nutné pole hodnot.  
  
- Obecné Delegáti umožňují typově bezpečná zpětná volání bez nutnosti vytvářet více tříd delegátů. Například <xref:System.Predicate%601> obecný delegát umožňuje vytvořit metodu, která implementuje vlastní kritéria hledání pro konkrétní typ a použít metodu s <xref:System.Array> metodami typu <xref:System.Array.Find%2A>, jako jsou, <xref:System.Array.FindLast%2A>a <xref:System.Array.FindAll%2A> . .  
  
- Obecné zjednodušují dynamicky generovaný kód. Použijete-li obecné typy s dynamicky generovaným kódem, nemusíte generovat typ. Tím se zvyšuje počet scénářů, ve kterých lze použít zjednodušené dynamické metody namísto generování celých sestavení. Další informace najdete v tématu [jak: Definujte a spusťte dynamické metody](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md) a <xref:System.Reflection.Emit.DynamicMethod>.  
  
 Níže jsou uvedena některá omezení obecných typů:  
  
- Obecné typy lze odvodit z většiny základních tříd, například <xref:System.MarshalByRefObject> (a omezení lze použít pro vyžadování, aby parametry obecného typu byly odvozeny ze základních tříd, jako <xref:System.MarshalByRefObject>). .NET Framework však nepodporuje obecné typy vázané na kontext. Obecný typ lze odvodit z <xref:System.ContextBoundObject>, ale při pokusu o vytvoření instance tohoto typu <xref:System.TypeLoadException>dojde k.  
  
- Výčty nemůžou mít parametry obecného typu. Výčet může být obecný pouze incident (například proto, že je vnořen do obecného typu, který je definován pomocí Visual Basic, C#nebo C++). Další informace naleznete v části "výčty" v [běžném typu systému](../../../docs/standard/base-types/common-type-system.md).  
  
- Jednoduché dynamické metody nemůžou být obecné.  
  
- V Visual Basic, C#a C++, nelze vytvořit instanci vnořeného typu, který je uzavřen v obecném typu, pokud typy nejsou přiřazeny k parametrům typu všech nadřazených typů. Dalším způsobem, jak to vyjádřit, je vnořený typ, který je definován pomocí těchto jazyků, obsahuje parametry typu všech nadřazených typů. To umožňuje, aby parametry typu nadřazených typů byly použity v definicích členů vnořeného typu. Další informace naleznete v části "vnořené typy" v <xref:System.Type.MakeGenericType%2A>tématu.  
  
    > [!NOTE]
    > Vnořený typ, který je definován vygenerováním kódu v dynamickém sestavení nebo pomocí nástroje [Ilasm. exe (IL Assembler)](../../../docs/framework/tools/ilasm-exe-il-assembler.md) , není vyžadován pro zahrnutí parametrů typu svých nadřazených typů. Pokud je však neobsahuje, parametry typu nejsou v oboru vnořené třídy.  
  
     Další informace naleznete v části "vnořené typy" v <xref:System.Type.MakeGenericType%2A>tématu.  
  
 [Zpět na začátek](#top)  
  
<a name="class_library_and_language_support"></a>   
## <a name="class-library-and-language-support"></a>Knihovna tříd a podpora jazyků  
 Rozhraní .NET poskytuje řadu obecných tříd kolekcí v následujících oborech názvů:  
  
- Obor názvů obsahuje většinu obecných typů kolekcí poskytovaných rozhraním .NET, <xref:System.Collections.Generic.List%601> jako jsou obecné třídy <xref:System.Collections.Generic.Dictionary%602>a. <xref:System.Collections.Generic>  
  
- Obor názvů obsahuje další typy obecných kolekcí, jako je <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> obecná třída, která je užitečná pro vystavení objektových modelů uživatelům vaší třídy. <xref:System.Collections.ObjectModel>  
  
 Obecná rozhraní pro implementaci porovnání řazení a rovnosti jsou k dispozici v <xref:System> oboru názvů společně s obecnými typy delegátů pro obslužné rutiny událostí, převody a predikáty vyhledávání.  
  
 Do <xref:System.Reflection> oboru názvů se přidala podpora pro obecné typy pro zkoumání obecných typů a obecných metod <xref:System.Reflection.Emit> , pro generování dynamických sestavení, která obsahují obecné typy <xref:System.CodeDom> a metody, a pro generování zdrojových grafů. které obsahují obecné typy.  
  
 Modul CLR (Common Language Runtime) poskytuje nové operační kódy a předpony pro podporu obecných typů v jazyce MSIL (Microsoft Intermediate <xref:System.Reflection.Emit.OpCodes.Stelem>Language <xref:System.Reflection.Emit.OpCodes.Ldelem>) <xref:System.Reflection.Emit.OpCodes.Unbox_Any>, <xref:System.Reflection.Emit.OpCodes.Constrained>včetně, <xref:System.Reflection.Emit.OpCodes.Readonly>,, a.  
  
 Visual C++, C#a Visual Basic vše poskytují plnou podporu pro definování a používání generických typů. Další informace o podpoře jazyků naleznete v tématu [Obecné typy v Visual Basic](../../visual-basic/programming-guide/language-features/data-types/generic-types.md), [Úvod do obecných](../../csharp/programming-guide/generics/index.md)hodnot a [Přehled obecných typů ve vizuálu C++ ](/cpp/windows/overview-of-generics-in-visual-cpp).  
  
 [Zpět na začátek](#top)  
  
<a name="nested_types_and_generics"></a>   
## <a name="nested-types-and-generics"></a>Vnořené typy a obecné typy  
 Typ, který je vnořen v obecném typu, může záviset na parametrech typu nadřazeného obecného typu. Modul CLR (Common Language Runtime) považuje vnořené typy za obecné, a to i v případě, že nemají vlastní parametry obecného typu. Při vytváření instance vnořeného typu je nutné zadat argumenty typu pro všechny nadřazené obecné typy.  
  
 [Zpět na začátek](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Obecné kolekce na platformě .NET](../../../docs/standard/generics/collections.md)|Popisuje třídy obecných kolekcí a jiné obecné typy v rozhraní .NET.|  
|[Obecné delegáty pro manipulaci s poli a seznamy](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)|Popisuje Obecné delegáty pro převody, predikáty hledání a akce, které mají být provedeny na prvcích pole nebo kolekce.|  
|[Obecná rozhraní](../../../docs/standard/generics/interfaces.md)|Popisuje Obecná rozhraní, která poskytují společné funkce napříč rodinami obecných typů.|  
|[Kovariance a kontravariance](../../../docs/standard/generics/covariance-and-contravariance.md)|Popisuje kovariance a kontravariance v parametrech obecného typu.|  
|[Běžně používané typy kolekcí](../../../docs/standard/collections/commonly-used-collection-types.md)|Obsahuje souhrnné informace o vlastnostech a scénářích použití typů kolekcí v rozhraní .NET, včetně obecných typů.|  
|[Kdy použít generické kolekce](../../../docs/standard/collections/when-to-use-generic-collections.md)|Popisuje obecná pravidla pro určení, kdy použít typy obecných kolekcí.|  
|[Postupy: Definování obecného typu pomocí generování reflexe](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)|Vysvětluje, jak generovat dynamická sestavení, která zahrnují obecné typy a metody.|  
|[Obecné typy v Visual Basic](../../visual-basic/programming-guide/language-features/data-types/generic-types.md)|Popisuje funkci Generics pro Visual Basic uživatele, včetně témat s postupy pro použití a definování obecných typů.|  
|[Úvod do obecných typů](../../csharp/programming-guide/generics/index.md)|Poskytuje přehled o definování a použití obecných typů pro C# uživatele.|  
|[Přehled obecných typů ve Visual C++](/cpp/windows/overview-of-generics-in-visual-cpp)|Popisuje funkci obecných typů pro C++ uživatele, včetně rozdílů mezi obecnými typy a šablonami.|  
  
<a name="reference"></a>   
## <a name="reference"></a>Reference  
 <xref:System.Collections.Generic>  
  
 <xref:System.Collections.ObjectModel>  
  
 <xref:System.Reflection.Emit.OpCodes?displayProperty=nameWithType>  
  
 [Zpět na začátek](#top)
