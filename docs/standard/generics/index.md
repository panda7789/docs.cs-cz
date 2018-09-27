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
ms.openlocfilehash: 104a0018896eb95255cf4054f9402ce5160b95f7
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47236264"
---
# <a name="generics-in-net"></a>Obecné typy v .NET

<a name="top"></a> Obecné typy umožňují přizpůsobit metodu, třídy, struktury nebo rozhraní pro přesný datový typ, který je pracováno. Například místo použití <xref:System.Collections.Hashtable> třídy, která umožňuje klíče a hodnoty být libovolného typu, můžete použít <xref:System.Collections.Generic.Dictionary%602> obecné třídy a určit typ povolené pro klíč a typ povolené hodnoty. Mezi výhody obecných typů se zvýšenou kód a typová bezpečnost.  
  
 Toto téma obsahuje přehled obecných typů v rozhraní .NET a souhrn obecné typy a metody. Obsahuje následující oddíly:  
  
-   [Definování a použití obecných typů](#defining_and_using_generics)  
  
-   [Terminologie obecných typů](#generics_terminology)  
  
-   [Knihovna tříd a podpora jazyků](#class_library_and_language_support)  
  
-   [Vnořené typy a obecné typy](#nested_types_and_generics)  
  
-   [Související témata](#related_topics)  
  
-   [Referenční informace](#reference)  
  
<a name="defining_and_using_generics"></a>   
## <a name="defining-and-using-generics"></a>Definování a použití obecných typů  
 Obecné typy jsou třídy, struktury, rozhraní a metody, které obsahovaly zástupné symboly (parametry typu) pro jeden nebo více typů, které uložit nebo použít. Obecné kolekce tříd může být parametr typu použít jako zástupný symbol pro typ objektů, které uchovává; parametry typu se zobrazí jako typy polí a typů parametrů metody. Jako typ hodnoty nebo typ jednoho z jejích formálních parametrů Obecné metody použít jeho typu parametru. Následující kód znázorňuje definici jednoduchou obecnou třídu.  
  
 [!code-cpp[Conceptual.Generics.Overview#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#2)]
 [!code-csharp[Conceptual.Generics.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#2)]
 [!code-vb[Conceptual.Generics.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#2)]  
  
 Při vytváření instance generické třídy zadejte skutečné typy nelze nahradit pro parametry typu. Tím se vytvoří nová obecná třída, nazývá konstruované obecné třídy, se vaše vybrané typy všude, kde se zobrazí parametry typu nahrazeny. Výsledkem je typově bezpečný třídu, která je vytvořený na míru zadaným hodnotám typů, jak ukazuje následující kód.  
  
 [!code-cpp[Conceptual.Generics.Overview#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#3)]
 [!code-csharp[Conceptual.Generics.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#3)]
 [!code-vb[Conceptual.Generics.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#3)]  
  
<a name="generics_terminology"></a>   
### <a name="generics-terminology"></a>Terminologie obecných typů  
 O obecných typů v .NET se používají následující termíny:  
  
-   A *definice obecného typu* je třída, struktura nebo deklaraci rozhraní, která funguje jako šablona, se zástupnými symboly pro typy, které může obsahovat nebo použít. Například <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> třídy mohou obsahovat dva typy: klíče a hodnoty. Definice obecného typu je pouze šablony, nelze vytvořit instance třídy, struktury nebo rozhraní, které je definice obecného typu.  
  
-   *Parametry obecného typu*, nebo *parametry typu*, jsou zástupné symboly v definici obecného typu nebo metody. <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> Obecného typu má dva parametry typu `TKey` a `TValue`, které představují typy klíčů a hodnot.  
  
-   A *Konstruovaný obecný typ*, nebo *konstruovaný typ.*, je výsledkem určení typů pro parametry obecného typu v definici obecného typu.  
  
-   A *argument obecného typu* libovolný typ, který nahrazuje parametr obecného typu.  
  
-   Obecný termín *obecného typu* zahrnuje sestavené typy a definice obecného typu.  
  
-   *Kovariance* a *kontravariance* obecného typu parametry umožňují používat konstruované obecné typy, jejichž typ argumenty jsou více odvozeného (kovariance) nebo méně odvozené (kontravariance) než cílový vytvořen Zadejte. Kovariance a kontravariance se souhrnně označují jako *variance*. Další informace najdete v tématu [kovariance a kontravariance](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
-   *Omezení* omezení jsou umístěny v parametrech obecného typu. Například může být omezen na typy, které implementují parametr typu <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> obecná rozhraní, ujistěte se, že lze provést řazení instance daného typu. Lze také omezit parametry typu pro typy, které mají určité základní třídy, které mají výchozí konstruktor, nebo které jsou odkazové typy nebo typy hodnot. Uživatelé obecný typ nelze nahradit argumenty typu, které nesplňují omezení.  
  
-   A *definice obecné metody* představuje metodu se dvěma seznamy parametrů: seznam parametrů obecného typu a seznam formálních parametrů. Parametry typu se může zobrazit jako návratový typ nebo typy formálních parametrů, jak ukazuje následující kód.  
  
 [!code-cpp[Conceptual.Generics.Overview#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#4)]
 [!code-csharp[Conceptual.Generics.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#4)]
 [!code-vb[Conceptual.Generics.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#4)]  
  
 Obecné metody se může objevit v obecnému nebo neobecnému typy. Je důležité si uvědomit, že metoda není obecná, to, že patří obecnému typu nebo dokonce, protože má formální parametry, jejichž typy jsou obecným parametrům nadřazeného typu. Metoda je obecná pouze v případě, že má svůj vlastní seznam parametrů typu. V následujícím kódu metoda pouze `G` je obecný.  
  
 [!code-cpp[Conceptual.Generics.Overview#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#5)]
 [!code-csharp[Conceptual.Generics.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#5)]
 [!code-vb[Conceptual.Generics.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#5)]  
  
 [Zpět na začátek](#top)  
  
<a name="advantages_limitations"></a>   
## <a name="advantages-and-disadvantages-of-generics"></a>Výhody a nevýhody obecných typů  
 Existuje mnoho výhody použití obecných kolekcí a delegáti:  
  
-   Bezpečnost typů. Obecné typy shift si museli dělat starosti bezpečnost typů od vás kompilátoru. Není nutné napsat kód pro testování správného datového typu, protože ho zajišťují v době kompilace. Jsou snižuje potřebu přetypování typu a možnost chyby za běhu.  
  
-   Mnohem snazší znovu použít méně kódu a kódu. Není nutné přepsat členy a dědit ze základního typu. Například <xref:System.Collections.Generic.LinkedList%601> je připravená k okamžitému použití. Například můžete vytvořit propojený seznam řetězců s následující deklaraci proměnné:  
  
     [!code-cpp[HowToGeneric#24](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/source2.cpp#24)]
     [!code-csharp[HowToGeneric#24](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/source2.cs#24)]
     [!code-vb[HowToGeneric#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/source2.vb#24)]  
  
-   Lepší výkon. Obecné typy kolekcí obecně poskytují lepší výkon pro ukládání a manipulaci s typy hodnot, protože není nutné pro typy hodnot pole.  
  
-   Obecní delegáti povolit zajišťující bezpečnost typů zpětná volání, aniž by bylo nutné vytvořit delegáta více tříd. Například <xref:System.Predicate%601> obecného delegátu umožňuje vytvořit metodu, která implementuje vlastní kritérií vyhledávání pro konkrétní typ a použít metodu s metodami <xref:System.Array> jako <xref:System.Array.Find%2A>, <xref:System.Array.FindLast%2A>, a <xref:System.Array.FindAll%2A> .  
  
-   Obecné typy Zjednodušte dynamicky generovaném kódu. Při použití obecných typů pomocí není potřeba generovat typ dynamicky generovaném kódu. Tím se zvyšuje počet scénáře, ve které můžete použít jednoduchý dynamických metod místo aby generovala celé sestavení. Další informace najdete v tématu [postupy: definování a spouštět dynamické metody](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md) a <xref:System.Reflection.Emit.DynamicMethod>.  
  
 Toto jsou některá omezení obecných typů:  
  
-   Obecné typy mohou být odvozeny z Většina základních tříd, například <xref:System.MarshalByRefObject> (a omezení je možné, že parametry obecného typu jsou odvozeny od základní třídy jako vyžadování <xref:System.MarshalByRefObject>). Ale [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] nepodporuje obecné typy vázané na kontext. Obecný typ může být odvozena z <xref:System.ContextBoundObject>, ale při pokusu o vytvoření instance, která způsobí typ <xref:System.TypeLoadException>.  
  
-   Výčty nemůžou mít parametry obecného typu. Výčet může být obecný pouze mimochodem (například, protože je vnořená v obecném typu, který je definován pomocí jazyka Visual Basic, C# nebo C++). Další informace najdete v tématu "Výčty" [obecný systém typů](../../../docs/standard/base-types/common-type-system.md).  
  
-   Zjednodušené dynamické metody nemohou být obecné.  
  
-   V jazyce Visual Basic, C# a C++ vnořený typ, který je uzavřen v obecném typu nelze vytvořit instanci Pokud typy byly přiřazeny parametry typu všech ohraničujících typů. Jinými slovy to je, že v reflexi, vnořený typ, který je definován pomocí těchto jazyků obsahuje parametry typu všech ohraničujících typů. To umožňuje parametry typu nadřazené typy pro použití v definicích členů vnořeného typu. Další informace najdete v tématu "Vnořené typy" <xref:System.Type.MakeGenericType%2A>.  
  
    > [!NOTE]
    >  Vnořený typ, který je definován pomocí generování kódu v dynamickém sestavení nebo [Ilasm.exe (IL Assembler)](../../../docs/framework/tools/ilasm-exe-il-assembler.md) nemusí obsahovat parametry typu jeho nadřazené typy; ale pokud ho neobsahuje, parametry typu nejsou v oboru vnořené třídy.  
  
     Další informace najdete v tématu "Vnořené typy" <xref:System.Type.MakeGenericType%2A>.  
  
 [Zpět na začátek](#top)  
  
<a name="class_library_and_language_support"></a>   
## <a name="class-library-and-language-support"></a>Knihovna tříd a podpora jazyků  
 .NET nabízí celou řadu obecné kolekce tříd v následující obory názvů:  
  
-   <xref:System.Collections.Generic> Obor názvů obsahuje typy obecné kolekce poskytované rozhraní .NET, například <xref:System.Collections.Generic.List%601> a <xref:System.Collections.Generic.Dictionary%602> obecné třídy.  
  
-   <xref:System.Collections.ObjectModel> Obor názvů obsahuje další obecné typy kolekcí, jako <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> obecná třída, která se hodí pro zpřístupnění objektové modely uživatelům vaší třídy.  
  
 Jsou k dispozici v obecné rozhraní pro provádění porovnání rovnosti a řazení <xref:System> obor názvů, spolu s obecnými typy delegátu obslužné rutiny událostí, převodů a predikáty vyhledávání.  
  
 Byla přidaná podpora pro obecné typy <xref:System.Reflection> obor názvů pro zkoumání obecných typů a obecných metod na <xref:System.Reflection.Emit> Emitování dynamických sestavení, které obsahují obecné typy a metody a do <xref:System.CodeDom> pro generování grafů zdroje které zahrnují obecné typy.  
  
 Modul common language runtime poskytuje nové operačních kódů a předpony pro podporu obecných typů v jazyce Microsoft intermediate language (MSIL), včetně <xref:System.Reflection.Emit.OpCodes.Stelem>, <xref:System.Reflection.Emit.OpCodes.Ldelem>, <xref:System.Reflection.Emit.OpCodes.Unbox_Any>, <xref:System.Reflection.Emit.OpCodes.Constrained>, a <xref:System.Reflection.Emit.OpCodes.Readonly>.  
  
 Visual C++, C# a Visual Basic všechny poskytují plnou podporu pro definování a použití obecných typů. Další informace o podpoře jazyků naleznete v tématu [obecné typy v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/data-types/generic-types.md), [Úvod do obecných typů](~/docs/csharp/programming-guide/generics/introduction-to-generics.md), a [přehled obecných typů v jazyce Visual C++](/cpp/windows/overview-of-generics-in-visual-cpp).  
  
 [Zpět na začátek](#top)  
  
<a name="nested_types_and_generics"></a>   
## <a name="nested-types-and-generics"></a>Vnořené typy a obecné typy  
 Typ, který je vnořená v obecném typu může záviset na parametry typu nadřazeným obecným typem. Modul common language runtime bere v úvahu vnořených typů je obecný, i v případě, že nemají vlastní parametry obecného typu. Při vytváření instance vnořeného typu, musíte zadat argumenty typu všech ohraničujících obecných typů.  
  
 [Zpět na začátek](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Obecné kolekce na platformě .NET](../../../docs/standard/generics/collections.md)|Popisuje obecné třídy kolekcí a jiné obecné typy v rozhraní .NET.|  
|[Obecné delegáty pro manipulaci s poli a seznamy](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)|Popisuje obecné delegáty pro převody, predikáty vyhledávání a akce mají být provedeny na elementy pole nebo kolekce.|  
|[Obecná rozhraní](../../../docs/standard/generics/interfaces.md)|Popisuje obecná rozhraní, které poskytují společné funkce napříč řady obecných typů.|  
|[Kovariance a kontravariance](../../../docs/standard/generics/covariance-and-contravariance.md)|Popisuje kovariance a kontravariance v parametrech obecného typu.|  
|[Běžně používané typy kolekcí](../../../docs/standard/collections/commonly-used-collection-types.md)|Poskytuje souhrnné informace o vlastnostech a scénáře použití kolekci typů v .NET, včetně obecných typů.|  
|[Kdy použít generické kolekce](../../../docs/standard/collections/when-to-use-generic-collections.md)|Popisuje obecná pravidla pro určení, kdy použití obecných typů kolekce.|  
|[Postupy: Definování obecného typu pomocí generování reflexe](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)|Vysvětluje, jak ke generování dynamických sestavení, které zahrnují obecné typy a metody.|  
|[Obecné typy v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/data-types/generic-types.md)|Popisuje funkci obecných typů pro uživatele jazyka Visual Basic, včetně témat s návody pro použití a definice obecných typů.|  
|[Úvod do obecných typů](~/docs/csharp/programming-guide/generics/introduction-to-generics.md)|Poskytuje přehled o definice a používání obecných typů pro uživatele jazyka C#.|  
|[Přehled obecných typů ve Visual C++](/cpp/windows/overview-of-generics-in-visual-cpp)|Popisuje funkci obecných typů pro uživatele jazyka C++, jaký je rozdíl mezi obecnými typy a šablony.|  
  
<a name="reference"></a>   
## <a name="reference"></a>Odkaz  
 <xref:System.Collections.Generic>  
  
 <xref:System.Collections.ObjectModel>  
  
 <xref:System.Reflection.Emit.OpCodes?displayProperty=nameWithType>  
  
 [Zpět na začátek](#top)
