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
ms.openlocfilehash: 7f20e5108ad8bff602f5b761e65f093d987f2608
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78156306"
---
# <a name="generics-in-net"></a>Obecné typy v .NET

Obecné typy umožňují přizpůsobit metodu, třídu, strukturu nebo rozhraní přesnému datovému typu, se kterými pracuje. Například namísto použití <xref:System.Collections.Hashtable> třídy, která umožňuje klíče a hodnoty, které <xref:System.Collections.Generic.Dictionary%602> mají být libovolného typu, můžete použít obecné třídy a určit typ povolený pro klíč a typ povolený pro hodnotu. Mezi výhody generik patří zvýšená opětovná použitelnost kódu a bezpečnost typů.  

## <a name="defining-and-using-generics"></a>Definování a používání obecných typů
 Obecné typy jsou třídy, struktury, rozhraní a metody, které mají zástupné symboly (parametry typu) pro jeden nebo více typů, které ukládají nebo používají. Obecná třída kolekce může použít parametr typu jako zástupný symbol pro typ objektů, které ukládá; parametry typu se zobrazí jako typy jeho polí a typy parametrů jeho metod. Obecná metoda může použít jeho parametr typu jako typ jeho vrácené hodnoty nebo jako typ jednoho z jeho formálních parametrů. Následující kód ilustruje jednoduchou definici obecné třídy.  
  
 [!code-cpp[Conceptual.Generics.Overview#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#2)]
 [!code-csharp[Conceptual.Generics.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#2)]
 [!code-vb[Conceptual.Generics.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#2)]  
  
 Při vytváření instance obecné třídy určíte skutečné typy, které nahradí parametry typu. Tím se vytvoří nová obecná třída, označovaná jako vytvořená obecná třída, s vybranými typy nahrazenými všude, kde se zobrazí parametry typu. Výsledkem je typově bezpečná třída, která je přizpůsobena vašemu výběru typů, jak ukazuje následující kód.  
  
 [!code-cpp[Conceptual.Generics.Overview#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#3)]
 [!code-csharp[Conceptual.Generics.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#3)]
 [!code-vb[Conceptual.Generics.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#3)]  

### <a name="generics-terminology"></a>Terminologie generických léčiv  
 Následující termíny se používají k diskusi o obecných typů v rozhraní .NET:  
  
- *Definice obecného typu* je deklarace třídy, struktury nebo rozhraní, která funguje jako šablona se zástupnými symboly pro typy, které může obsahovat nebo používat. <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> Například třída může obsahovat dva typy: klíče a hodnoty. Vzhledem k tomu, že definice obecného typu je pouze šablona, nelze vytvořit instance třídy, struktury nebo rozhraní, které je definicí obecného typu.  
  
- *Parametry obecného typu*nebo *parametry typu*jsou zástupnými symboly v definici obecného typu nebo metody. Obecný <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> typ má dva parametry typu `TKey` a `TValue`, které představují typy jeho klíče a hodnoty.  
  
- *Vytvořený obecný typ*nebo *konstruovaný typ*je výsledkem určení typů parametrů obecného typu definice obecného typu.  
  
- *Obecný argument typu* je libovolný typ, který je nahrazen parametrem obecného typu.  
  
- Obecný termín *obecný typ* zahrnuje jak konstruované typy, tak definice obecného typu.  
  
- *Kovariance* a *kontravariát* parametrů obecného typu umožňují použít konstruované obecné typy, jejichž argumenty typu jsou více odvozené (kovariance) nebo méně odvozené (kontravariance) než cílový konstruovaný typ. Kovariance a kontravariance se souhrnně označují jako *rozptyl*. Další informace naleznete [v tématu Kovariance a Contravariance](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
- *Omezení* jsou omezení umístěná na parametry obecného typu. Můžete například omezit parametr typu na typy, které implementují <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> obecné rozhraní, abyste zajistili, že instance typu lze objednat. Parametry typu můžete také omezit na typy, které mají určitou základní třídu, které mají konstruktor bez parametrů nebo které jsou typy odkazů nebo typy hodnot. Uživatelé obecného typu nemohou nahradit argumenty typu, které nesplňují omezení.  
  
- Definice *obecné metody* je metoda se dvěma seznamy parametrů: seznam parametrů obecného typu a seznam formálních parametrů. Parametry typu se mohou zobrazit jako návratový typ nebo jako typy formálních parametrů, jak ukazuje následující kód.  
  
 [!code-cpp[Conceptual.Generics.Overview#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#4)]
 [!code-csharp[Conceptual.Generics.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#4)]
 [!code-vb[Conceptual.Generics.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#4)]  
  
 Obecné metody se mohou objevit u obecných nebo neobecných typů. Je důležité si uvědomit, že metoda není obecná jen proto, že patří k obecnému typu, nebo dokonce proto, že má formální parametry, jejichž typy jsou obecné parametry ohraničujícího typu. Metoda je obecná pouze v případě, že má vlastní seznam parametrů typu. V následujícím kódu je `G` pouze metoda obecná.  
  
 [!code-cpp[Conceptual.Generics.Overview#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#5)]
 [!code-csharp[Conceptual.Generics.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#5)]
 [!code-vb[Conceptual.Generics.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#5)]  
  
## <a name="advantages-and-disadvantages-of-generics"></a>Výhody a nevýhody generik
 Použití obecných kolekcí a delegátů má mnoho výhod:  
  
- Bezpečnost typů. Obecné typy přesunout zatížení bezpečnosti typů z vás kompilátoru. Není nutné psát kód k testování správného datového typu, protože je vynuceno v době kompilace. Snižuje se potřeba typového lití a možnost chyb za běhu.  
  
- Méně kódu a kódu je snadněji znovu použít. Není třeba dědit ze základního typu a přepsat členy. Například je <xref:System.Collections.Generic.LinkedList%601> připraven k okamžitému použití. Můžete například vytvořit propojený seznam řetězců s následující deklarací proměnné:  
  
     [!code-cpp[HowToGeneric#24](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/source2.cpp#24)]
     [!code-csharp[HowToGeneric#24](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/source2.cs#24)]
     [!code-vb[HowToGeneric#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/source2.vb#24)]  
  
- Lepší výkon. Obecné typy kolekcí obecně provádět lépe pro ukládání a manipulaci s typy hodnot, protože není nutné zaokřovat typy hodnot.  
  
- Obecné delegáty umožňují typově bezpečná zpětná volání bez nutnosti vytvářet více tříd delegátů. <xref:System.Predicate%601> Obecný delegát například umožňuje vytvořit metodu, která implementuje vlastní kritéria vyhledávání pro určitý typ <xref:System.Array> a <xref:System.Array.Find%2A>použít <xref:System.Array.FindLast%2A>metodu s metodami typu , jako jsou , a <xref:System.Array.FindAll%2A>.  
  
- Obecné typy zjednodušují dynamicky generovaný kód. Při použití obecných typů s dynamicky generovaným kódem není nutné generovat typ. Tím se zvyšuje počet scénářů, ve kterých můžete použít zjednodušené dynamické metody namísto generování celých sestavení. Další informace naleznete v [tématu How to: Define and Execute Dynamic Methods](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md) and <xref:System.Reflection.Emit.DynamicMethod>.  
  
 Následují některá omezení obecných typů:  
  
- Obecné typy lze odvodit z <xref:System.MarshalByRefObject> většiny základních tříd, například (a omezení lze použít <xref:System.MarshalByRefObject>k vyžadování, že parametry obecného typu jsou odvozeny ze základních tříd, jako je ). Rozhraní .NET Framework však nepodporuje kontextové obecné typy. Obecný typ lze odvodit z <xref:System.ContextBoundObject>, ale pokus o <xref:System.TypeLoadException>vytvoření instance tohoto typu způsobí .  
  
- Výčty nemohou mít parametry obecného typu. Výčet může být obecný pouze incidentně (například proto, že je vnořen v obecném typu, který je definován pomocí jazyka Visual Basic, C# nebo C++). Další informace naleznete v tématu "Výčet" v [běžném systému typu](../../../docs/standard/base-types/common-type-system.md).  
  
- Zjednodušené dynamické metody nemohou být obecné.  
  
- V jazyce Visual Basic, C# a C++ nelze vytvořit instanci vnořeného typu, který je uzavřen v obecném typu, pokud nebyly přiřazeny typy parametrů typu všech ohraničujících typů. Dalším způsobem, jak to říct, je, že v reflexi vnořený typ, který je definován pomocí těchto jazyků, zahrnuje parametry typu všech jeho ohraničujících typů. To umožňuje parametry typu ohraničující typy, které mají být použity v definicích členů vnořeného typu. Další informace naleznete v tématu <xref:System.Type.MakeGenericType%2A>"Vnořené typy" v .  
  
    > [!NOTE]
    > Vnořený typ, který je definován vyzařováním kódu v dynamickém sestavení nebo pomocí [souboru Ilasm.exe (IL Assembler),](../../../docs/framework/tools/ilasm-exe-il-assembler.md) není nutné zahrnout parametry typu jeho ohraničujících typů; však pokud je neobsahuje, parametry typu nejsou v oboru v vnořené třídě.  
  
     Další informace naleznete v tématu <xref:System.Type.MakeGenericType%2A>"Vnořené typy" v .  

## <a name="class-library-and-language-support"></a>Knihovna tříd a jazyková podpora  
 Rozhraní .NET poskytuje řadu obecných tříd kolekce v následujících oborech názvů:  
  
- Obor <xref:System.Collections.Generic> názvů obsahuje většinu typů obecných kolekcí poskytovaných <xref:System.Collections.Generic.List%601> rozhraním .NET, například obecné třídy a. <xref:System.Collections.Generic.Dictionary%602>  
  
- Obor <xref:System.Collections.ObjectModel> názvů obsahuje další obecné typy <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> kolekcí, jako je například obecná třída, které jsou užitečné pro vystavení objektových modelů uživatelům vašich tříd.  
  
 Obecná rozhraní pro implementaci porovnání řazení a rovnosti <xref:System> jsou k dispozici v oboru názvů spolu s obecnými typy delegátů pro obslužné rutiny událostí, převody a predikáty hledání.  
  
 Podpora pro obecné typy byly <xref:System.Reflection> přidány do oboru názvů pro zkoumání <xref:System.Reflection.Emit> obecných typů a obecných metod, pro <xref:System.CodeDom> emitování dynamických sestavení, které obsahují obecné typy a metody, a pro generování zdrojových grafů, které obsahují obecné typy.  
  
 Běžný jazyk runtime poskytuje nové opcodes a předpony pro podporu obecných <xref:System.Reflection.Emit.OpCodes.Stelem> <xref:System.Reflection.Emit.OpCodes.Ldelem>typů <xref:System.Reflection.Emit.OpCodes.Unbox_Any> <xref:System.Reflection.Emit.OpCodes.Constrained>v zprostředkujícím jazyce Microsoft (MSIL), včetně , , a <xref:System.Reflection.Emit.OpCodes.Readonly>.  
  
 Visual C++, C# a Visual Basic poskytují plnou podporu pro definování a používání obecných typů. Další informace o jazykové podpoře naleznete [v tématu Obecné typy v jazyce Visual Basic](../../visual-basic/programming-guide/language-features/data-types/generic-types.md), Úvod do [obecných typů](../../csharp/programming-guide/generics/index.md)a Přehled [obecných typů v jazyce Visual C++](/cpp/windows/overview-of-generics-in-visual-cpp).

## <a name="nested-types-and-generics"></a>Vnořené typy a obecné typy  
 Typ, který je vnořen do obecného typu, může záviset na parametrech typu ohraničujícího obecného typu. Běžný jazyk runtime považuje vnořené typy za obecné, i v případě, že nemají vlastní parametry obecného typu. Při vytváření instance vnořeného typu je nutné zadat argumenty typu pro všechny ohraničující obecné typy.  

## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[Obecné kolekce na platformě .NET](../../../docs/standard/generics/collections.md)|Popisuje obecné třídy kolekce a další obecné typy v rozhraní .NET.|  
|[Obecní delegáty pro manipulaci s poli a seznamy](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)|Popisuje obecné delegáty pro převody, predikáty hledání a akce, které mají být přijata na prvky pole nebo kolekce.|  
|[Obecná rozhraní](../../../docs/standard/generics/interfaces.md)|Popisuje obecná rozhraní, která poskytují běžné funkce napříč rodinami obecných typů.|  
|[Kovariance a kontravariance](../../../docs/standard/generics/covariance-and-contravariance.md)|Popisuje kovariance a kontravariance v parametrech obecného typu.|  
|[Běžně používané typy kolekcí](../../../docs/standard/collections/commonly-used-collection-types.md)|Obsahuje souhrnné informace o charakteristikách a scénářích použití typů kolekcí v rozhraní .NET, včetně obecných typů.|  
|[Kdy použít generické kolekce](../../../docs/standard/collections/when-to-use-generic-collections.md)|Popisuje obecná pravidla pro určení, kdy použít obecné typy kolekcí.|  
|[Postupy: Definování obecného typu pomocí generování reflexe](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)|Vysvětluje, jak generovat dynamická sestavení, která obsahují obecné typy a metody.|  
|[Obecné typy v jazyce Visual Basic](../../visual-basic/programming-guide/language-features/data-types/generic-types.md)|Popisuje funkci obecných typů pro uživatele jazyka Visual Basic, včetně témat s postupy pro použití a definování obecných typů.|  
|[Úvod do obecných typů](../../csharp/programming-guide/generics/index.md)|Obsahuje přehled definování a používání obecných typů pro uživatele jazyka C#.|  
|[Přehled obecných typů ve Visual C++](/cpp/windows/overview-of-generics-in-visual-cpp)|Popisuje funkci obecných typů pro uživatele jazyka C++, včetně rozdílů mezi obecnými typy a šablonami.|  

## <a name="reference"></a>Referenční informace  
 <xref:System.Collections.Generic>  
  
 <xref:System.Collections.ObjectModel>  
  
 <xref:System.Reflection.Emit.OpCodes?displayProperty=nameWithType>  
