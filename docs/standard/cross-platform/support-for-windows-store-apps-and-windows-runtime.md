---
title: Podpora pro aplikace pro web Windows Store a prostředí Windows Runtime v rozhraní .NET Framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Windows Store apps, .NET Framework support for
- Windows Runtime, .NET Framework support for
- .NET for Windows Store apps
- .NET Framework, and Windows Store apps
- .NET Framework, and Windows Runtime
ms.assetid: 6fa7d044-ae12-4c54-b8ee-50915607a565
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15d6262fb5e7dfb99759f0f85c9a197157713300
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204945"
---
# <a name="net-framework-support-for-windows-store-apps-and-windows-runtime"></a>Podpora pro aplikace pro web Windows Store a prostředí Windows Runtime v rozhraní .NET Framework

.NET Framework 4,5 podporuje několik scénářů vývoje softwaru s prostředí Windows Runtime. Tyto scénáře spadají do tří kategorií:

- Vývoj aplikací pro Windows 8. x ze Storu pomocí ovládacích prvků XAML, jak je popsáno v tématu [Průvodce C# pro aplikace pro Windows Store s využitím nebo Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10)), [postupy (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10))a [.NET pro aplikace pro Windows Store – přehled](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)).

- Vývoj knihoven tříd pro použití v aplikacích Windows 8. x Store, které vytvoříte pomocí .NET Framework.

- Vývoj komponent prostředí Windows Runtime v balení. Soubory WinMD, které mohou být používány jakýmkoli programovacím jazykem, který podporuje prostředí Windows Runtime. Příklad najdete v tématu [vytváření prostředí Windows runtimech komponent C# v a Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).

Toto téma popisuje podporu, kterou .NET Framework poskytuje pro všechny tři kategorie, a popisuje scénáře pro prostředí Windows Runtime součásti. První část obsahuje základní informace o vztahu mezi .NET Framework a prostředí Windows Runtime a vysvětluje některé oddities, se kterými se můžete setkat v systému help a integrovaném vývojovém prostředí (IDE). [Druhá část](#WindowsRuntimeComponents) popisuje scénáře pro vývoj komponent prostředí Windows Runtime.

## <a name="the-basics"></a>Základní informace

.NET Framework podporuje tři vývojové scénáře, které jsou uvedeny dříve, poskytováním [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]a podporou samotného prostředí Windows Runtime.

- [Obory názvů .NET Framework a prostředí Windows Runtime](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)#net-framework-and-windows-runtime-namespaces) poskytují zjednodušené zobrazení knihoven tříd .NET Framework a zahrnují pouze typy a členy, které můžete použít k vytvoření aplikací pro Store systému Windows 8. x a prostředí Windows Runtime komponent.

  - Při použití sady Visual Studio (Visual Studio 2012 nebo novější) pro vývoj aplikace Windows 8. x Store nebo prostředí Windows Runtime komponenty, sada referenčních sestavení zajišťuje, aby se zobrazily pouze relevantní typy a členy.

  - Tato zjednodušená sada API je dále zjednodušená odebráním funkcí, které jsou duplikovány v rámci .NET Framework nebo duplicitních prostředí Windows Runtime funkcí. Například obsahuje pouze obecné verze typů kolekce a model objektu dokumentu XML je odstraněn ve prospěch prostředí Windows Runtime sadě XML API.

  - Také se odeberou funkce, které jednoduše zabalí rozhraní API operačního systému, protože prostředí Windows Runtime je snadné volat ze spravovaného kódu.

  Další informace o [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]najdete v tématu [Přehled rozhraní .NET pro aplikace pro Windows Store](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)). Informace o procesu výběru rozhraní API najdete v tématu věnovaném záznamu .NET [pro aplikace stylu Metro](https://devblogs.microsoft.com/dotnet/net-for-metro-style-apps/) na blogu .NET.

- [Prostředí Windows Runtime](/uwp/api/) poskytuje prvky uživatelského rozhraní pro vytváření aplikací pro Windows 8. x Store a poskytuje přístup k funkcím operačního systému. Podobně jako .NET Framework má prostředí Windows Runtime metadata, která umožňují kompilátorům C# a Visual Basic použít prostředí Windows Runtime způsobem, který používají knihovny tříd .NET Framework. .NET Framework usnadňuje používání prostředí Windows Runtime skrytím některých rozdílů:

  - Některé rozdíly v programovacích vzorech mezi .NET Framework a prostředí Windows Runtime, jako je například vzor pro přidávání a odebírání obslužných rutin událostí, jsou skryté. Stačí použít vzor .NET Framework.

  - Některé rozdíly v běžně používaných typech (například primitivní typy a kolekce) jsou skryté. Jednoduše použijete typ .NET Framework, jak je popsáno v [rozdílech, které jsou viditelné v integrovaném vývojovém prostředí (IDE](#DifferencesVisibleInIDE)) dále v tomto článku.

Ve většině případů je .NET Framework podpora prostředí Windows Runtime transparentní. V další části jsou popsány některé z zdánlivých rozdílů mezi spravovaným kódem a prostředí Windows Runtime.

<a name="AboutReferenceDocumentation"></a>

### <a name="the-net-framework-and-the-windows-runtime-reference-documentation"></a>.NET Framework a referenční dokumentace k prostředí Windows Runtime

Prostředí Windows Runtime a dokumentace sady .NET Framework jsou oddělené. Pokud stisknete klávesu F1 pro zobrazení nápovědu pro určitý typ nebo člen, zobrazí se referenční dokumentace z příslušné sady. Pokud však procházíte [prostředí Windows Runtime odkazem](/uwp/api/) , může dojít k příkladům, které se jeví jako nejasné:

- Témata, jako například rozhraní <xref:Windows.Foundation.Collections.IIterable%601>, nemají syntaxi deklarace pro Visual Basic nebo C#. Místo toho se zobrazí Poznámka nad oddílem syntaxe (v tomto případě ".NET: Toto rozhraní se zobrazuje jako System. Collections. Generic. IEnumerable\<T >"). Důvodem je to, že .NET Framework a prostředí Windows Runtime poskytují podobné funkce s různými rozhraními. Kromě toho existují rozdíly v chování: `IIterable` má `First` metodu namísto metody <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>, která vrací enumerátor. Místo toho, abyste se dozvěděli o různých způsobech provádění běžné úlohy, .NET Framework podporuje prostředí Windows Runtime tím, že váš spravovaný kód bude používat typ, který znáte. V integrovaném vývojovém prostředí se nezobrazuje rozhraní `IIterable`, a proto jediným způsobem, kterým se v dokumentaci k prostředí Windows Runtime referenční dokumentaci setkáte, je procházení této dokumentace přímo.

- Dokumentace k <xref:Windows.Web.Syndication.SyndicationFeed.%23ctor(System.String,System.String,Windows.Foundation.Uri)> znázorňuje úzce související problém: jeho typy parametrů se budou lišit pro různé jazyky. Pro C# a Visual Basic jsou typy parametrů <xref:System.String?displayProperty=nameWithType> a <xref:System.Uri?displayProperty=nameWithType>. Důvodem je to, že .NET Framework má vlastní `String` a `Uri` typy a pro tyto běžně používané typy nemá smysl vynutit .NET Framework uživatele, aby se dozvěděli jiným způsobem. V integrovaném vývojovém prostředí .NET Framework skryje odpovídající prostředí Windows Runtime typy.

- V několika případech, jako je například struktura <xref:Windows.UI.Xaml.GridLength>, .NET Framework poskytuje typ se stejným názvem, ale více funkcí. Například sada témat konstruktoru a vlastností jsou spojeny s `GridLength`, ale mají bloky syntaxe pouze pro Visual Basic a C# protože členové jsou k dispozici pouze ve spravovaném kódu. V prostředí Windows Runtime mají struktury pouze pole. Prostředí Windows Runtime struktura vyžaduje pomocnou třídu <xref:Windows.UI.Xaml.GridLengthHelper>, aby poskytovala ekvivalentní funkce. Při psaní spravovaného kódu se tato pomocná třída nezobrazuje v integrovaném vývojovém prostředí.

- V integrovaném vývojovém prostředí se prostředí Windows Runtime typy odvodit od <xref:System.Object?displayProperty=nameWithType>. Zdá se, že mají členy děděné z <xref:System.Object>, jako je například <xref:System.Object.ToString%2A?displayProperty=nameWithType>. Tito členové fungují tak, jak by kdyby byly typy skutečně zděděné z <xref:System.Object>, a prostředí Windows Runtime typy lze přetypovat na <xref:System.Object>. Tato funkce je součástí podpory, kterou .NET Framework poskytuje pro prostředí Windows Runtime. Pokud však zobrazíte typy v referenční dokumentaci prostředí Windows Runtime, žádní tito členové se nezobrazí. Dokumentace pro tyto zjevné zděděné členy je k dispozici v dokumentaci <xref:System.Object?displayProperty=nameWithType> reference.

<a name="DifferencesVisibleInIDE"></a>

### <a name="differences-that-are-visible-in-the-ide"></a>Rozdíly, které jsou viditelné v integrovaném vývojovém prostředí

V pokročilejších programovacích scénářích, jako je například použití komponenty prostředí Windows Runtime C# napsané v systému k poskytnutí aplikační logiky pro Windows 8. x Store, sestavené pro Windows pomocí JavaScriptu, jsou tyto rozdíly zjevné v integrovaném vývojovém prostředí i v dokumentaci. Pokud vaše komponenta vrátí `IDictionary<int, string>` do JavaScriptu a zobrazí se v ladicím programu JavaScriptu, zobrazí se metody `IMap<int, string>`, protože JavaScript používá typ prostředí Windows Runtime. Některé běžně používané typy kolekcí, které se v těchto dvou jazycích zobrazují odlišně, jsou uvedené v následující tabulce:

|Typ prostředí Windows Runtime|Odpovídající typ .NET Framework|
|--------------------------------------------------------------|---------------------------------------|
|`IIterable<T>`|`IEnumerable<T>`|
|`IIterator<T>`|`IEnumerator<T>`|
|`IVector<T>`|`IList<T>`|
|`IVectorView<T>`|`IReadOnlyList<T>`|
|`IMap<K, V>`|`IDictionary<TKey, TValue>`|
|`IMapView<K, V>`|`IReadOnlyDictionary<TKey, TValue>`|
|`IBindableIterable`|`IEnumerable`|
|`IBindableVector`|`IList`|
|`Windows.UI.Xaml.Data.INotifyPropertyChanged`|`System.ComponentModel.INotifyPropertyChanged`|
|`Windows.UI.Xaml.Data.PropertyChangedEventHandler`|`System.ComponentModel.PropertyChangedEventHandler`|
|`Windows.UI.Xaml.Data.PropertyChangedEventArgs`|`System.ComponentModel.PropertyChangedEventArgs`|

V prostředí Windows Runtime se `IMap<K, V>` a `IMapView<K, V>` iterovat pomocí `IKeyValuePair`. Když je předáte spravovanému kódu, zobrazí se jako `IDictionary<TKey, TValue>` a `IReadOnlyDictionary<TKey, TValue>`, takže přirozeně používáte `System.Collections.Generic.KeyValuePair<TKey, TValue>` k jejich vytvoření výčtu.

Způsob zobrazení rozhraní ve spravovaném kódu ovlivňuje způsob, jakým se zobrazí typy, které implementují tato rozhraní. Například třída `PropertySet` implementuje `IMap<K, V>`, která se zobrazí ve spravovaném kódu jako `IDictionary<TKey, TValue>`. `PropertySet` se zobrazí jako při implementaci `IDictionary<TKey, TValue>` namísto `IMap<K, V>`, takže ve spravovaném kódu se zdá, že mají `Add` metodu, která se chová jako metoda `Add` na .NET Frameworkch slovnících. Zdá se, že neexistuje metoda `Insert`.

Další informace o použití .NET Framework k vytvoření komponenty prostředí Windows Runtime a návod, který ukazuje, jak použít takovou komponentu s JavaScriptem naleznete v tématu [Creating prostředí Windows Runtime Components C# in a Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).

### <a name="primitive-types"></a>Primitivní typy

Chcete-li povolit přirozené použití prostředí Windows Runtime ve spravovaném kódu, zobrazí se .NET Framework primitivních typů namísto prostředí Windows Runtime primitivních typů ve vašem kódu. V .NET Framework primitivní typy, jako je například struktura `Int32`, obsahují mnoho užitečných vlastností a metod, jako je například metoda `Int32.TryParse`. Naopak primitivní typy a struktury v prostředí Windows Runtime mají pouze pole. Při použití primitivních hodnot ve spravovaném kódu se jeví jako .NET Framework typy a můžete použít vlastnosti a metody .NET Framework typů jako obvykle. Následující seznam poskytuje souhrn:

- Pro prostředí Windows Runtime primitivních `Int32`, `Int64`, `Single`, `Double`, `Boolean`, `String` (neměnné kolekce znaků Unicode), `Enum`, `UInt32`, `UInt64`a `Guid`, použijte v oboru názvů `System` typ se stejným názvem.

- Pro `UInt8`použijte `System.Byte`.

- Pro `Char16`použijte `System.Char`.

- Pro rozhraní `IInspectable` použijte `System.Object`.

- Pro `HRESULT`použijte strukturu s jedním `System.Int32` členem.

Stejně jako u typů rozhraní se může zobrazit legitimace této reprezentace pouze v případě, že váš .NET Framework projekt je prostředí Windows Runtime komponenta, kterou používá aplikace Windows 8. x Store sestavená pomocí JavaScriptu.

Další základní, běžně používané prostředí Windows Runtime typy, které se zobrazí ve spravovaném kódu jako jejich .NET Framework ekvivalenty, zahrnují strukturu `Windows.Foundation.DateTime`, která se zobrazuje ve spravovaném kódu jako struktura <xref:System.DateTimeOffset?displayProperty=nameWithType> a struktura `Windows.Foundation.TimeSpan`, která se zobrazí jako struktura <xref:System.TimeSpan?displayProperty=nameWithType>.

### <a name="other-differences"></a>Jiné rozdíly

V několika případech fakt, že .NET Framework typy se zobrazí ve vašem kódu, místo prostředí Windows Runtime typy vyžaduje akci na vaší straně. Například třída <xref:Windows.Foundation.Uri?displayProperty=nameWithType> se zobrazí jako <xref:System.Uri?displayProperty=nameWithType> v kódu .NET Framework. <xref:System.Uri?displayProperty=nameWithType> povoluje relativní identifikátor URI, ale <xref:Windows.Foundation.Uri?displayProperty=nameWithType> vyžaduje absolutní identifikátor URI. Proto Pokud předáte identifikátor URI metodě prostředí Windows Runtime, je nutné zajistit, aby byl absolutní. Viz [předání identifikátoru URI prostředí Windows Runtime](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md).

<a name="WindowsRuntimeComponents"></a>

## <a name="scenarios-for-developing-windows-runtime-components"></a>Scénáře pro vývoj komponent prostředí Windows Runtime

Scénáře podporované komponentami spravované prostředí Windows Runtime závisí na následujících obecných zásadách:

- Prostředí Windows Runtime komponenty sestavené pomocí .NET Framework nemají žádné zjevné rozdíly oproti jiným systémům Windows Runtimelibraries. Například pokud znovu implementujete nativní prostředí Windows Runtime komponentu pomocí spravovaného kódu, jsou tyto dvě komponenty mimo jiné. Skutečnost, že vaše komponenta je napsána ve spravovaném kódu, je neviditelná pro kód, který ho používá, i v případě, že se jedná o spravovaný kód. Nicméně interně je vaše komponenta skutečný spravovaný kód a běží v modulu CLR (Common Language Runtime).

- Komponenty mohou obsahovat typy, které implementují logiku aplikace, ovládací prvky uživatelského rozhraní systému Windows 8. x nebo obojí.

  > [!NOTE]
  > Je vhodné oddělit prvky uživatelského rozhraní od logiky aplikace. Nemůžete také použít ovládací prvky uživatelského rozhraní Windows 8. x Store v aplikaci Windows 8. x Store sestavené pro Windows pomocí JavaScriptu a HTML.

- Komponenta může být projekt v rámci řešení sady Visual Studio pro aplikaci Windows 8. x Store nebo opakovaně použitelná součást, kterou můžete přidat do více řešení.

  > [!NOTE]
  > Pokud se vaše komponenta použije jenom s C# nebo Visual Basic, neexistuje žádný důvod, proč ji vytvořit prostředí Windows Runtime komponentu. Pokud místo toho použijete obvyklou .NET Framework knihovnu tříd, nemusíte omezovat jeho veřejnou plochu rozhraní API na prostředí Windows Runtime typy.

- Verze opakovaně použitelných komponent můžete vydávat pomocí atributu prostředí Windows Runtime <xref:Windows.Foundation.Metadata.VersionAttribute> k určení, které typy (a kteří členy v rámci typu) byly přidány v různých verzích.

- Typy v komponentě mohou být odvozeny z prostředí Windows Runtime typů. Ovládací prvky lze odvozovat z primitivních typů ovládacích prvků v oboru názvů <xref:Windows.UI.Xaml.Controls.Primitives> nebo z více dokončených ovládacích prvků, jako je například <xref:Windows.UI.Xaml.Controls.Button>.

  > [!IMPORTANT]
  > Počínaje [!INCLUDE[win8](../../../includes/win8-md.md)] a .NET Framework 4,5 musí být všechny veřejné typy v spravované prostředí Windows Runtime komponentě zapečetěné. Typ v jiné součásti prostředí Windows Runtime nelze z nich odvodit. Pokud chcete ve své komponentě poskytnout polymorfní chování, můžete vytvořit rozhraní a implementovat ho v polymorfních typech.

- Všechny parametry a návratové typy na veřejných typech ve vaší komponentě musí být prostředí Windows Runtime typy (včetně prostředí Windows Runtimech typů, které vaše komponenta definuje).

V následujících částech jsou uvedeny příklady běžných scénářů.

### <a name="application-logic-for-a-windows-8x-store-app-with-javascript"></a>Aplikační logika pro aplikaci Windows 8. x Store s jazykem JavaScript

Když vyvíjíte aplikaci Windows 8. x Store pro systém Windows pomocí JavaScriptu, můžete zjistit, že některé části logiky aplikace fungují lépe ve spravovaném kódu nebo je lze snadněji vyvíjet. JavaScript nemůže použít .NET Framework knihovny tříd přímo, ale můžete vytvořit knihovnu tříd a. Soubor WinMD. V tomto scénáři je součást prostředí Windows Runtime nedílnou součástí aplikace, takže nedává smysl poskytovat atributy verze.

### <a name="reusable-windows-8x-store-ui-controls"></a>Opakovaně použitelné ovládací prvky uživatelského rozhraní Windows 8. x Store

Můžete zabalit sadu souvisejících ovládacích prvků uživatelského rozhraní do opakovaně použitelné součásti prostředí Windows Runtime. Komponentu lze uvádět na trh samostatně nebo použít jako prvek v aplikacích, které vytvoříte. V tomto scénáři má smysl použít atribut prostředí Windows Runtime <xref:Windows.Foundation.Metadata.VersionAttribute> ke zvýšení kompatibility.

### <a name="reusable-application-logic-from-existing-net-framework-apps"></a>Opakovaně použitelná logika aplikace z existujících aplikací .NET Framework

Spravovaný kód můžete zabalit z vaší stávající desktopové aplikace jako samostatnou součást prostředí Windows Runtime. To vám umožňuje používat komponentu v aplikacích Windows 8. x Store, které jsou sestavené pomocí C++ jazyka nebo JavaScript, a také v aplikacích pro Windows 8. x C# Store sestavených pomocí nebo Visual Basic. Správa verzí je možnost, pokud existuje více scénářů opakovaného použití kódu.

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Přehled aplikace .NET pro Windows Store](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))|Popisuje typy .NET Framework a členy, které můžete použít k vytváření aplikací pro Windows 8. x Store a Windows RuntimeComponents. (Na stránce Windows Dev Center.)|
|[Plán pro aplikace pro Windows Store C# s využitím nebo Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10))|Poskytuje klíčové materiály, které vám pomůžou začít s vývojem aplikací pro Windows 8. C# x ze Storu pomocí nebo Visual Basic, včetně mnoha témat pro rychlý Start, pokynů a osvědčených postupů. (Na stránce Windows Dev Center.)|
|[Jak TOS (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10))|Poskytuje klíčové materiály, které vám pomůžou začít s vývojem aplikací pro Windows 8. C# x ze Storu pomocí nebo Visual Basic, včetně mnoha témat pro rychlý Start, pokynů a osvědčených postupů. (Na stránce Windows Dev Center.)|
|[Vytváření komponent prostředí Windows Runtime v C# nástroji a Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)|Popisuje, jak vytvořit prostředí Windows Runtime komponentu pomocí .NET Framework, vysvětluje, jak ji použít jako součást aplikace Windows 8. x Store vytvořená pro systém Windows pomocí JavaScriptu a popisuje, jak ladit kombinaci se sadou Visual Studio. (Na stránce Windows Dev Center.)|
|[Odkaz na prostředí Windows Runtime](/uwp/api/)|Referenční dokumentace pro prostředí Windows Runtime. (Na stránce Windows Dev Center.)|
|[Předávání identifikátorů URI do prostředí Windows Runtime](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md)|Popisuje problém, který může nastat při předání identifikátoru URI ze spravovaného kódu do prostředí Windows Runtime a jeho zabránění.|
