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
ms.openlocfilehash: a51d8d77318685e4a4c8b90a793f2946de4a792b
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025538"
---
# <a name="net-framework-support-for-windows-store-apps-and-windows-runtime"></a>Podpora pro aplikace pro web Windows Store a prostředí Windows Runtime v rozhraní .NET Framework
Rozhraní .NET Framework 4.5 podporuje různé scénáře vývoje softwaru pomocí prostředí Windows Runtime. Tyto scénáře spadají do tří kategorií:

- Vývoj [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace s ovládacími prvky XAML, jak je popsáno v [aplikací plán pro Windows Store pomocí jazyka C# nebo Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10)), [jak tos (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10)), a [.NET pro Windows Store apps – přehled ](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)).

- Vývoj knihoven tříd pro použití v [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace, které vytváříte s použitím rozhraní .NET Framework.

- Vývoj komponent Windows Runtime, zabalené v. Soubory WinMD, které můžete používat programovací jazyk, který podporuje prostředí Windows Runtime. Viz například [vytváření komponent Windows Runtime v jazyce C# a Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).

 Toto téma popisuje podporu, že rozhraní .NET Framework poskytuje pro všechny tři kategorie a popisuje scénáře pro komponenty Windows Runtime. První část obsahuje základní informace o vztahu mezi rozhraní .NET Framework a prostředí Windows Runtime a vysvětluje některé oddities, které můžete narazit v systému nápovědy a integrovaného vývojového prostředí. [Druhé části](#WindowsRuntimeComponents) popisuje scénáře pro vývoj součástí prostředí Windows Runtime.

## <a name="the-basics"></a>Základní informace
 Rozhraní .NET Framework podporuje tři vývojové scénáře tím, že poskytuje výše uvedených [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]a díky podpoře samotný modul Runtime Windows.

- [Obory názvů rozhraní .NET framework a prostředí Windows Runtime](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)#net-framework-and-windows-runtime-namespaces) poskytuje zjednodušený pohled na knihovny tříd rozhraní .NET Framework a obsahovat pouze typy a členy, které můžete použít k vytvoření [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikací a součástí prostředí Windows Runtime.

    - Při použití sady Visual Studio (Visual Studio 2012 nebo novější) pro vývoj [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace nebo součásti prostředí Windows Runtime, sadu referenčních sestavení zajistí, že se zobrazí jenom odpovídající typy a členy.

    - Tato efektivní sada rozhraní API je zjednodušen odebráním funkcí, které jsou duplikovány v rámci rozhraní .NET Framework nebo který duplicitní modulu Windows Runtime funkce. Například obsahuje pouze verze obecné typy kolekcí a modelu objektu dokumentu XML se odstraní a místo toho použití rozhraní API architektury Windows Runtime XML nastaven.

    - Funkce, které jednoduše zabalit operačního systému rozhraní API jsou také odebrat, protože modul Windows Runtime je snadné je zavolat ze spravovaného kódu.

     Další informace o tom [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], najdete v článku [.NET pro Windows Store apps – přehled](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)). Přečtěte si informace o procesu výběru rozhraní API, najdete v článku [Metro style aplikace .NET pro](https://devblogs.microsoft.com/dotnet/net-for-metro-style-apps/) záznam v blogu .NET.

- [Modulu Windows Runtime](/uwp/api/) uživateli poskytuje prvky rozhraní pro vytváření [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace a poskytuje přístup k funkcím operačního systému. Například rozhraní .NET Framework má modul Windows Runtime metadata, která umožňuje C# a knihovny tříd kompilátory jazyka Visual Basic na využití modulu Windows Runtime způsob použití rozhraní .NET Framework. Rozhraní .NET Framework usnadňuje použití prostředí Windows Runtime tím, že skryjete některé rozdíly:

    - Určité rozdíly v programování vzory mezi rozhraní .NET Framework a modulu Windows Runtime, jako je například vzor pro přidávání a odebírání obslužných rutin událostí, jsou skryté. Stačí použít model rozhraní .NET Framework.

    - Určité rozdíly v běžně používané typy (například primitivní typy a kolekce) jsou skryté. Jednoduše použijte typ rozhraní .NET Framework, jak je popsáno v [rozdíly, že jsou viditelné v integrovaném vývojovém prostředí](#DifferencesVisibleInIDE)dále v tomto článku.

 Ve většině případů, podporu rozhraní .NET Framework pro prostředí Windows Runtime je transparentní. Další část popisuje některé zřejmé rozdíly mezi spravovaným kódem a prostředí Windows Runtime.

<a name="AboutReferenceDocumentation"></a>
### <a name="the-net-framework-and-the-windows-runtime-reference-documentation"></a>Rozhraní .NET Framework a Windows Runtime referenční dokumentaci
 Modul Windows Runtime a sady dokumentace rozhraní .NET Framework jsou oddělené. Pokud stisknete klávesu F1 pro zobrazení nápovědy na typ nebo člen, referenční dokumentaci k příslušné sady se zobrazí. Nicméně pokud při procházení [referenční příručka prostředí Windows Runtime](/uwp/api/) můžete narazit na příklady, které jsou zdánlivě nejasné:

- Témata, jako <xref:Windows.Foundation.Collections.IIterable%601> rozhraní nemají syntaxi deklarace pro Visual Basic nebo C#. Místo toho se nad oddílem syntaxe zobrazí poznámka (v tomto případě ".NET: Toto rozhraní se zobrazí jako System.Collections.Generic.IEnumerable\<T > "). Je to proto, že rozhraní .NET Framework a prostředí Windows Runtime poskytuje podobné funkce s různými rozhraními. Kromě toho existují rozdíly v chování: `IIterable` má `First` metoda místo <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metoda vrátí enumerátor. Místo vynucení a seznamte se jiný způsob provádění běžných úkolů, rozhraní .NET Framework podporuje modul Runtime Windows tak, že váš spravovaný kód zdá se, použijte typ, který už znáte. Neuvidíte `IIterable` rozhraní v rozhraní IDE, a proto je jediný způsob, jak se můžete setkat v referenční dokumentaci modulu Windows Runtime tak, že přejdete přímo do této dokumentace.

- <xref:Windows.Web.Syndication.SyndicationFeed.%23ctor(System.String,System.String,Windows.Foundation.Uri)> Dokumentaci ukazuje úzce související problém: Typy parametrů se zdají být pro různé jazyky. Pro C# a Visual Basic, jsou typy parametrů <xref:System.String?displayProperty=nameWithType> a <xref:System.Uri?displayProperty=nameWithType>. Znovu, důvodem je, že rozhraní .NET Framework má svůj vlastní `String` a `Uri` typů a pro takové běžně používané typy ho nemá smysl přinutit uživatele rozhraní .NET Framework se dozvíte jiný způsob plnění úkolů. V integrovaném vývojovém prostředí zobrazovat rozhraní .NET Framework odpovídající typy Windows Runtime.

- V několika případech, jako <xref:Windows.UI.Xaml.GridLength> strukturu, rozhraní .NET Framework poskytuje typ se stejným názvem, ale rozšířenou funkčností. Například sadu konstruktor a vlastnost témata jsou přidružené k `GridLength`, ale vzhledem k tomu, že členové jsou k dispozici jenom ve spravovaném kódu mají syntaxi bloky pouze pro Visual Basic a C#. V modulu Windows Runtime struktury mají pouze pole. Vyžaduje pomocná třída, struktura prostředí Windows Runtime <xref:Windows.UI.Xaml.GridLengthHelper>, odpovídá funkci zajistí. Neuvidíte, že pomocná třída v integrovaném vývojovém prostředí při psaní spravovaného kódu.

- V integrovaném vývojovém prostředí, se zobrazí typy Windows Runtime k odvození z <xref:System.Object?displayProperty=nameWithType>. Zobrazí mít členy zděděné z <xref:System.Object>, jako například <xref:System.Object.ToString%2A?displayProperty=nameWithType>. Tyto členy, fungovat jako typy ve skutečnosti zděděno z <xref:System.Object>, a typy Windows Runtime lze převést na <xref:System.Object>. Tato funkce je součástí podpoře, kterou rozhraní .NET Framework poskytuje pro prostředí Windows Runtime. Pokud však zobrazit typy v prostředí Windows Runtime referenční dokumentaci, bez těchto členů zobrazí. Poskytuje dokumentaci pro tyto zřejmý zděděných členů <xref:System.Object?displayProperty=nameWithType> referenční dokumentaci.

<a name="DifferencesVisibleInIDE"></a>
### <a name="differences-that-are-visible-in-the-ide"></a>Rozdíly, které jsou viditelné v prostředí IDE
 V další pokročilé scénáře programování, například pomocí komponenty Windows Runtime v C# poskytnout aplikační logiku pro [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace vytvořené pro Windows pomocí jazyka JavaScript, tyto rozdíly jsou zřejmé v také integrovaného vývojového prostředí ve dokumentace ke službě. Pokud vaše komponenta vrátí `IDictionary<int, string>` až po JavaScript a můžete prohlédnout v ladicím programu JavaScriptu, uvidíte metody `IMap<int, string>` vzhledem k tomu používá typ prostředí Windows Runtime jazyka JavaScript. Některé běžně používá kolekce, které typy, které v těchto dvou jazyků vypadat jinak, jsou uvedeny v následující tabulce:

|Typ prostředí Windows Runtime|Odpovídající typ rozhraní .NET Framework|
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

 V modulu Windows Runtime `IMap<K, V>` a `IMapView<K, V>` provést iteraci pomocí `IKeyValuePair`. Při jejich předání do spravovaného kódu, zobrazí se jako `IDictionary<TKey, TValue>` a `IReadOnlyDictionary<TKey, TValue>`, takže přirozeně použijete `System.Collections.Generic.KeyValuePair<TKey, TValue>` je výčet.

 Rozhraní způsob, jak se zobrazí ve spravovaném kódu ovlivňuje způsob, jak typy, které implementují tato rozhraní se zobrazí. Například `PropertySet` implementuje třída `IMap<K, V>`, která se zobrazí ve spravovaném kódu jako `IDictionary<TKey, TValue>`. `PropertySet` Zobrazí se jako by se implementovat `IDictionary<TKey, TValue>` místo `IMap<K, V>`, takže ve spravovaném kódu zřejmě má `Add` metodu, která se chová jako `Add` metoda v rozhraní .NET Framework slovníky. Nezobrazí mít `Insert` metody.

 Další informace o použití rozhraní .NET Framework pro vytváření součástí prostředí Windows Runtime a návod, který ukazuje, jak použít takové komponenty v jazyce JavaScript naleznete v tématu [vytváření komponent Windows Runtime v C# a Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).

### <a name="primitive-types"></a>Primitivní typy
 Povolit přirozené používání prostředí Windows Runtime ve spravovaném kódu, primitivní typy rozhraní .NET Framework se zobrazí místo primitivní typy Windows Runtime ve vašem kódu. V rozhraní .NET Framework, například primitivní typy `Int32` struktury mají mnoho užitečným vlastnostem a metodám, například `Int32.TryParse` metody. Pouze pole, mají oproti tomu primitivní typy a struktury v modulu Windows Runtime. Při použití primitivy ve spravovaném kódu zdají být typy rozhraní .NET Framework, můžete si vlastnosti a metody typy rozhraní .NET Framework jako obvykle. Následující seznam obsahuje souhrn:

- Pro prostředí Windows Runtime primitiv `Int32`, `Int64`, `Single`, `Double`, `Boolean`, `String` (neměnné kolekci znaků Unicode), `Enum`, `UInt32`, `UInt64`, a `Guid`, použijte typ se stejným názvem v `System` oboru názvů.

- Pro `UInt8`, použijte `System.Byte`.

- Pro `Char16`, použijte `System.Char`.

- Pro `IInspectable` rozhraní, použijte `System.Object`.

- Pro `HRESULT`, použití struktury s jednou `System.Int32` člena.

 Jak s typy rozhraní, může se zobrazit doklad o tento zápis je v případě rozhraní .NET Framework projektu se pouze komponenty prostředí Windows Runtime, která používá [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikaci sestavenou pomocí jazyka JavaScript.

 Jiné typy Windows Runtime základní, běžně používaném, které se zobrazují v spravovaného kódu obsahovat ekvivalenty rozhraní .NET Framework `Windows.Foundation.DateTime` struktura, která se zobrazí ve spravovaném kódu jako <xref:System.DateTimeOffset?displayProperty=nameWithType> strukturu a `Windows.Foundation.TimeSpan` struktury, která Zobrazí se jako <xref:System.TimeSpan?displayProperty=nameWithType> struktury.

### <a name="other-differences"></a>Další rozdíly
 V několika případech skutečnost, že ve svém kódu místo typy Windows Runtime se zobrazí typy rozhraní .NET Framework vyžaduje akci. Například <xref:Windows.Foundation.Uri?displayProperty=nameWithType> třída se objeví jako <xref:System.Uri?displayProperty=nameWithType> v kódu rozhraní .NET Framework. <xref:System.Uri?displayProperty=nameWithType> Umožňuje relativní identifikátor URI, ale <xref:Windows.Foundation.Uri?displayProperty=nameWithType> vyžaduje absolutní identifikátor URI. Proto při předání identifikátor URI metodě modulu Windows Runtime, musíte zajistit, že je absolutní. (Viz [předávání identifikátorů URI pro Windows Runtime](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md).)

<a name="WindowsRuntimeComponents"></a>
## <a name="scenarios-for-developing-windows-runtime-components"></a>Scénáře pro vývoj součástí prostředí Windows Runtime
 Scénáře, které jsou podporovány pro spravované komponenty Windows Runtime závisí na následující obecné zásady:

- Windows Runtime komponenty, které se vytvářejí pomocí rozhraní .NET Framework mít žádné zjevný rozdíl oproti jiných Runtimelibraries Windows. Například pokud se rozhodnete znovu implementovat nativní součást prostředí Windows Runtime pomocí spravovaného kódu, dvě součásti jsou vně odlišitelné. Je skutečnost, že vaše komponenta je zapsána ve spravovaném kódu pro kód, který používá je neviditelné, i v případě, že kód je samotný spravovaného kódu. Interně jsou však vaše komponenta je hodnota true, spravovaný kód a běží na common language runtime (CLR).

- Součástí může obsahovat typy, které implementují logiku aplikace [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uživatelského rozhraní ovládacích prvků, nebo obojí.

    > [!NOTE]
    >  Je vhodné oddělení prvky uživatelského rozhraní od logiky aplikace. Kromě toho nemůžete použít [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] ovládacích prvků uživatelského rozhraní v [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace vytvořené pro Windows pomocí jazyků JavaScript a HTML.

- Komponenta může být v rámci řešení sady Visual Studio pro projekt [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace nebo opětovně použitelnou komponentu, můžete přidat do více řešení.

    > [!NOTE]
    >  Pokud vaše komponenta se dá použít jenom s C# nebo Visual Basic neexistuje žádný důvod k němu komponenty prostředí Windows Runtime. Pokud ji nastavíte běžné knihovny tříd .NET Framework místo toho, není nutné omezit jeho veřejné ploše rozhraní API pro typy Windows Runtime.

- Pomocí prostředí Windows Runtime lze uvolnit verze opakovaně použitelné komponenty <xref:Windows.Foundation.Metadata.VersionAttribute> atribut k identifikaci typy, které (a členy v rámci typu) byly přidány v různých verzích.

- Typy v komponentě lze odvodit z typů modulu Windows Runtime. Ovládací prvky lze odvodit z primitivních typů ovládacích prvků v <xref:Windows.UI.Xaml.Controls.Primitives> oboru názvů nebo z úplnějších ovládacích prvků <xref:Windows.UI.Xaml.Controls.Button>.

    > [!IMPORTANT]
    >  Počínaje [!INCLUDE[win8](../../../includes/win8-md.md)] a rozhraní .NET Framework 4.5, všechny veřejné typy ve spravované součásti prostředí Windows Runtime musí být zapečetěný. Typ v jiné součásti prostředí Windows Runtime nelze odvodit z nich. Pokud chcete poskytnout tak polymorfní chování v komponentě, můžete vytvořit rozhraní a implementaci v polymorfních typů.

- Všechny parametry a návratovým typem ve veřejných typů v komponentě musí být typy Windows Runtime (včetně typy Windows Runtime, které definuje vaše komponenta).

 Následující části obsahují příklady běžným scénářům.

### <a name="application-logic-for-a-includewin8appnamelongincludeswin8-appname-long-mdmd-app-with-javascript"></a>Aplikace logiky pro [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace s použitím jazyka JavaScript
 Při vývoji [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace pro Windows pomocí jazyka JavaScript, může pro vás, že některé části aplikační logiky líp fungovat ve spravovaném kódu nebo usnadňuje vývoj. JavaScript nemůže používat knihovny tříd rozhraní .NET Framework přímo, ale může být knihovna tříd. Soubor WinMD. V tomto scénáři součást prostředí Windows Runtime je nedílnou součástí aplikace, takže nemá smysl poskytuje atributy verze.

### <a name="reusable-includewin8appnamelongincludeswin8-appname-long-mdmd-ui-controls"></a>Opakovaně použitelného [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] ovládacích prvků uživatelského rozhraní
 Můžete zabalit sadu souvisejících ovládacích prvků uživatelského rozhraní v opakovaně použitelné součásti prostředí Windows Runtime. Součást můžete uvádět na trh sama o sobě nebo použít jako prvek v aplikace, které vytvoříte. V tomto scénáři je vhodné použít modul Windows Runtime <xref:Windows.Foundation.Metadata.VersionAttribute> atributů pro zlepšení kompatibility.

### <a name="reusable-application-logic-from-existing-net-framework-apps"></a>Opakovaně použitelné aplikace logiky z existujících aplikací .NET Framework
 Spravovaný kód ze své stávající aplikace klasické pracovní plochy můžete zabalit jako samostatné komponenty prostředí Windows Runtime. To umožňuje používat komponenty v [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikací vytvořených pomocí jazyka C++ nebo JavaScript, stejně jako v [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikací vytvořených pomocí jazyka C# nebo Visual Basic. Správa verzí je možnost, pokud existuje více scénářů opakované použití kódu.

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[.NET pro Windows Store apps – přehled](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))|Popisuje typy rozhraní .NET Framework a členy, které můžete použít k vytvoření [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace a Windows RuntimeComponents. (Ve službě Windows Dev Center.)|
|[Plán pro aplikace pro Windows Store pomocí jazyka C# nebo Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10))|Poskytuje klíčové prostředky, které vám pomůžou začít vyvíjet [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikací pomocí C# nebo Visual Basic, včetně mnoha témat rychlý start, pokyny a osvědčené postupy. (Ve službě Windows Dev Center.)|
|[Jak tos (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10))|Poskytuje klíčové prostředky, které vám pomůžou začít vyvíjet [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikací pomocí C# nebo Visual Basic, včetně mnoha témat rychlý start, pokyny a osvědčené postupy. (Ve službě Windows Dev Center.)|
|[Vytváření komponent Windows Runtime v jazyce C# a Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)|Popisuje způsob vytváření komponent Windows Runtime s použitím rozhraní .NET Framework, vysvětluje, jak ho použít jako součást [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace vytvořené pro Windows pomocí JavaScriptu a popisuje, jak ladit kombinaci pomocí sady Visual Studio. (Ve službě Windows Dev Center.)|
|[Referenční příručka prostředí Windows Runtime](/uwp/api/)|Referenční dokumentace pro Windows Runtime. (Ve službě Windows Dev Center.)|
|[Předávání identifikátorů URI do prostředí Windows Runtime](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md)|Popisuje problém, který může nastat při předání identifikátor URI ze spravovaného kódu do prostředí Windows Runtime a jak tomu zamezit.|
