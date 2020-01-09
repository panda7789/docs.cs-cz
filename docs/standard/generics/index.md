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
ms.openlocfilehash: f04b6fcd1641a53efe75d38ab7122967bff6a58d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708368"
---
# <a name="generics-in-net"></a>Obecné typy v .NET

Obecné typy umožňují přizpůsobit metodu, třídu, strukturu nebo rozhraní na přesný datový typ, na kterém funguje. Například namísto použití třídy <xref:System.Collections.Hashtable>, která umožňuje klíčům a hodnotám být libovolného typu, můžete použít obecnou třídu <xref:System.Collections.Generic.Dictionary%602> a zadat typ povolený pro klíč a typ povolený pro hodnotu. Z výhod obecných typů se zvyšuje použitelnost kódu a bezpečnost typů.  

## <a name="defining-and-using-generics"></a>Definování a použití generických typů
 Obecné typy jsou třídy, struktury, rozhraní a metody, které mají zástupné symboly (parametry typu) pro jeden nebo více typů, které jsou uloženy nebo použity. Třída obecné kolekce může používat parametr typu jako zástupný symbol pro typ objektů, které úložiště ukládá; parametry typu se zobrazí jako typy polí a typy parametrů jejich metod. Obecná metoda může použít svůj parametr typu jako typ své návratové hodnoty nebo jako typ jednoho z jeho formálních parametrů. Následující kód ilustruje jednoduchou definici obecné třídy.  
  
 [!code-cpp[Conceptual.Generics.Overview#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#2)]
 [!code-csharp[Conceptual.Generics.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#2)]
 [!code-vb[Conceptual.Generics.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#2)]  
  
 Při vytváření instance obecné třídy zadáte skutečné typy, které mají být nahrazeny parametry typu. Tím se vytvoří nová Obecná třída označovaná jako konstruovaná obecná třída s vybranými typy, které jsou nahrazeny všude, kde se objeví parametry typu. Výsledkem je typově bezpečná třída, která je upravena podle vašeho výběru typů, jak ukazuje následující kód.  
  
 [!code-cpp[Conceptual.Generics.Overview#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#3)]
 [!code-csharp[Conceptual.Generics.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#3)]
 [!code-vb[Conceptual.Generics.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#3)]  

### <a name="generics-terminology"></a>Terminologie generických typů  
 Pro diskuzi o obecných typech v rozhraní .NET se používají následující výrazy:  
  
- *Definice obecného typu* je deklarace třídy, struktury nebo rozhraní, která funguje jako šablona, se zástupnými symboly pro typy, které může obsahovat nebo použít. Například třída <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> může obsahovat dva typy: klíče a hodnoty. Vzhledem k tomu, že definice obecného typu je pouze šablona, nelze vytvořit instance třídy, struktury nebo rozhraní, které je definicí obecného typu.  
  
- *Parametry obecného typu*nebo *parametry typu*jsou zástupné symboly v definici obecného typu nebo metody. <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> obecný typ má dva parametry typu, `TKey` a `TValue`, které reprezentují typy jeho klíčů a hodnot.  
  
- *Konstruovaný obecný typ*, neboli *konstruovaný typ*, je výsledkem určení typů pro parametry obecného typu definice obecného typu.  
  
- *Argument obecného typu* je libovolný typ, který je nahrazen parametrem obecného typu.  
  
- *Obecný typ* běžné podmínky zahrnuje konstruované typy i definice obecného typu.  
  
- *Kovariance* a *kontravariance* parametrů obecného typu umožňuje použít konstruované obecné typy, jejichž argumenty typu jsou více odvozené (kovariance) nebo méně odvozené (kontravariance) než cílový konstruovaný typ. Kovariance a kontravariance jsou souhrnně označovány jako *Variance*. Další informace najdete v tématu [kovariance a kontravariance](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
- *Omezení* jsou omezení pro parametry obecného typu. Například můžete omezit parametr typu na typy, které implementují obecné rozhraní <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType>, aby bylo zajištěno, že lze seřadit instance daného typu. Můžete také omezit parametry typu na typy, které mají konkrétní základní třídu, která má konstruktor bez parametrů, nebo, které jsou odkazové typy nebo hodnoty. Uživatelé obecného typu nemohou dosadit argumenty typu, které nesplňují omezení.  
  
- *Obecná definice metody* je metoda se dvěma seznamy parametrů: seznam parametrů obecného typu a seznam formálních parametrů. Parametry typu se mohou zobrazit jako návratový typ nebo jako typy formálních parametrů, jak ukazuje následující kód.  
  
 [!code-cpp[Conceptual.Generics.Overview#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#4)]
 [!code-csharp[Conceptual.Generics.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#4)]
 [!code-vb[Conceptual.Generics.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#4)]  
  
 Obecné metody se můžou vyskytovat na obecných nebo neobecných typech. Je důležité si uvědomit, že metoda není obecná, protože patří do obecného typu, nebo i když má formální parametry, jejichž typy jsou obecné parametry nadřazeného typu. Metoda je obecná pouze v případě, že má svůj vlastní seznam parametrů typu. V následujícím kódu je pouze metoda `G` obecná.  
  
 [!code-cpp[Conceptual.Generics.Overview#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#5)]
 [!code-csharp[Conceptual.Generics.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#5)]
 [!code-vb[Conceptual.Generics.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#5)]  
  
## <a name="advantages-and-disadvantages-of-generics"></a>Výhody a nevýhody obecných typů
 Použití obecných kolekcí a delegátů má mnoho výhod:  
  
- Bezpečnost typů. Obecné typy posunou zatížení typu zabezpečení od vás do kompilátoru. Není nutné psát kód pro testování správného datového typu, protože je vynutila v době kompilace. Je potřeba snížit typ přetypování a možnost chyb za běhu.  
  
- Méně kód a kód je snazší znovu použít. Není nutné dědit ze základního typu a přepsat členy. Například <xref:System.Collections.Generic.LinkedList%601> je připravena k okamžitému použití. Můžete například vytvořit propojený seznam řetězců s následující deklarací proměnné:  
  
     [!code-cpp[HowToGeneric#24](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/source2.cpp#24)]
     [!code-csharp[HowToGeneric#24](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/source2.cs#24)]
     [!code-vb[HowToGeneric#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/source2.vb#24)]  
  
- Vyšší výkon. Obecné typy kolekcí obecně poskytují lepší pro ukládání a manipulaci s typy hodnot, protože není nutné pole hodnot.  
  
- Obecné Delegáti umožňují typově bezpečná zpětná volání bez nutnosti vytvářet více tříd delegátů. Například obecný delegát <xref:System.Predicate%601> umožňuje vytvořit metodu, která implementuje vlastní kritéria hledání pro konkrétní typ a použít metodu s metodami <xref:System.Array> typu, jako jsou <xref:System.Array.Find%2A>, <xref:System.Array.FindLast%2A>a <xref:System.Array.FindAll%2A>.  
  
- Obecné zjednodušují dynamicky generovaný kód. Použijete-li obecné typy s dynamicky generovaným kódem, nemusíte generovat typ. Tím se zvyšuje počet scénářů, ve kterých lze použít zjednodušené dynamické metody namísto generování celých sestavení. Další informace naleznete v tématu [How to: Define and Execute Dynamic Methods](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md) and <xref:System.Reflection.Emit.DynamicMethod>.  
  
 Níže jsou uvedena některá omezení obecných typů:  
  
- Obecné typy lze odvodit z většiny základních tříd, jako je například <xref:System.MarshalByRefObject> (a omezení lze použít pro vyžadování, aby parametry obecného typu byly odvozeny ze základních tříd, jako je <xref:System.MarshalByRefObject>). .NET Framework však nepodporuje obecné typy vázané na kontext. Obecný typ lze odvodit z <xref:System.ContextBoundObject>, ale pokus o vytvoření instance tohoto typu způsobí <xref:System.TypeLoadException>.  
  
- Výčty nemůžou mít parametry obecného typu. Výčet může být obecný pouze incident (například proto, že je vnořen do obecného typu, který je definován pomocí Visual Basic, C#nebo C++). Další informace naleznete v části "výčty" v [běžném typu systému](../../../docs/standard/base-types/common-type-system.md).  
  
- Jednoduché dynamické metody nemůžou být obecné.  
  
- V Visual Basic, C#a C++, nelze vytvořit instanci vnořeného typu, který je uzavřen v obecném typu, pokud typy nejsou přiřazeny k parametrům typu všech nadřazených typů. Dalším způsobem, jak to vyjádřit, je vnořený typ, který je definován pomocí těchto jazyků, obsahuje parametry typu všech nadřazených typů. To umožňuje, aby parametry typu nadřazených typů byly použity v definicích členů vnořeného typu. Další informace naleznete v tématu "vnořené typy" v <xref:System.Type.MakeGenericType%2A>.  
  
    > [!NOTE]
    > Vnořený typ, který je definován vygenerováním kódu v dynamickém sestavení nebo pomocí nástroje [Ilasm. exe (IL Assembler)](../../../docs/framework/tools/ilasm-exe-il-assembler.md) , není vyžadován pro zahrnutí parametrů typu svých nadřazených typů. Pokud je však neobsahuje, parametry typu nejsou v oboru vnořené třídy.  
  
     Další informace naleznete v tématu "vnořené typy" v <xref:System.Type.MakeGenericType%2A>.  

## <a name="class-library-and-language-support"></a>Knihovna tříd a podpora jazyků  
 Rozhraní .NET poskytuje řadu obecných tříd kolekcí v následujících oborech názvů:  
  
- Obor názvů <xref:System.Collections.Generic> obsahuje většinu obecných typů kolekcí poskytovaných rozhraním .NET, jako jsou obecné třídy <xref:System.Collections.Generic.List%601> a <xref:System.Collections.Generic.Dictionary%602>.  
  
- Obor názvů <xref:System.Collections.ObjectModel> obsahuje další typy obecných kolekcí, jako je například <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> obecná třída, která je užitečná pro vystavení objektových modelů uživatelům vaší třídy.  
  
 Obecná rozhraní pro implementaci porovnání řazení a rovnosti jsou k dispozici v oboru názvů <xref:System> společně s obecnými typy delegátů pro obslužné rutiny událostí, převody a predikáty vyhledávání.  
  
 Byla přidána podpora pro obecné typy do oboru názvů <xref:System.Reflection> pro zkoumání obecných typů a obecných metod, pro <xref:System.Reflection.Emit> pro generování dynamických sestavení, která obsahují obecné typy a metody, a pro <xref:System.CodeDom> pro generování zdrojových grafů, které obsahují obecné typy.  
  
 Modul CLR (Common Language Runtime) poskytuje nové operační kódy a předpony pro podporu obecných typů v jazyce MSIL (Microsoft Intermediate Language), včetně <xref:System.Reflection.Emit.OpCodes.Stelem>, <xref:System.Reflection.Emit.OpCodes.Ldelem>, <xref:System.Reflection.Emit.OpCodes.Unbox_Any>, <xref:System.Reflection.Emit.OpCodes.Constrained>a <xref:System.Reflection.Emit.OpCodes.Readonly>.  
  
 Visual C++, C#a Visual Basic vše poskytují plnou podporu pro definování a používání generických typů. Další informace o podpoře jazyků naleznete v tématu [Obecné typy v Visual Basic](../../visual-basic/programming-guide/language-features/data-types/generic-types.md), [Úvod do obecných](../../csharp/programming-guide/generics/index.md)hodnot a [Přehled obecných typů ve vizuálu C++ ](/cpp/windows/overview-of-generics-in-visual-cpp). 

## <a name="nested-types-and-generics"></a>Vnořené typy a obecné typy  
 Typ, který je vnořen v obecném typu, může záviset na parametrech typu nadřazeného obecného typu. Modul CLR (Common Language Runtime) považuje vnořené typy za obecné, a to i v případě, že nemají vlastní parametry obecného typu. Při vytváření instance vnořeného typu je nutné zadat argumenty typu pro všechny nadřazené obecné typy.  

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

## <a name="reference"></a>Odkaz  
 <xref:System.Collections.Generic>  
  
 <xref:System.Collections.ObjectModel>  
  
 <xref:System.Reflection.Emit.OpCodes?displayProperty=nameWithType>  
