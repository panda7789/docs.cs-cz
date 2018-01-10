---
title: "Podpora pro aplikace pro web Windows Store a prostředí Windows Runtime v rozhraní .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Store apps, .NET Framework support for
- Windows Runtime, .NET Framework support for
- .NET for Windows Store apps
- .NET Framework, and Windows Store apps
- .NET Framework, and Windows Runtime
ms.assetid: 6fa7d044-ae12-4c54-b8ee-50915607a565
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f11daa93aa4e1cbddd0fa0e9f065295f42c820d5
ms.sourcegitcommit: 91691981897cf8451033cb01071d8f5d94017f97
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2018
---
# <a name="net-framework-support-for-windows-store-apps-and-windows-runtime"></a>Podpora pro aplikace pro web Windows Store a prostředí Windows Runtime v rozhraní .NET Framework
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Podporuje různé scénáře vývoj softwaru pomocí [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Tyto scénáře spadají do tří kategorií:  
  
-   Vývoj [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace s ovládacími prvky XAML, jak je popsáno v [aplikace plán pro Windows Store pomocí jazyka C# nebo Visual Basic](http://go.microsoft.com/fwlink/p/?LinkID=242212), [aplikace pro Windows Store rozvojových (VB / C# nebo C++ a XAML)](http://go.microsoft.com/fwlink/p/?LinkId=238311)a [Přehled aplikace .NET pro Windows Store](http://go.microsoft.com/fwlink/p/?LinkId=238312) ve službě Windows Dev Center.  
  
-   Vývoj knihovny tříd pro použití v [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace, které vytvoříte v rozhraní .NET Framework.  
  
-   Vývoj [!INCLUDE[wrt](../../../includes/wrt-md.md)] součásti, které jsou součástí. WinMD soubory, které mohou být využívána žádný programovací jazyk, který podporuje [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Například v tématu [vytváření součásti systému Windows Runtime v C# a Visual Basic](http://go.microsoft.com/fwlink/p/?LinkId=238313) ve službě Windows Dev Center.  
  
 Toto téma popisuje podporu, který poskytuje pro všechny tři kategorie rozhraní .NET Framework a popisuje scénáře pro [!INCLUDE[wrt](../../../includes/wrt-md.md)] součásti. První část obsahuje základní informace o vztahu mezi rozhraní .NET Framework a [!INCLUDE[wrt](../../../includes/wrt-md.md)]a vysvětluje některé oddities může dojít v systému nápovědy a rozhraní IDE. [Druhé části](#WindowsRuntimeComponents) popisuje scénáře pro vývoj [!INCLUDE[wrt](../../../includes/wrt-md.md)] součásti.  
  
## <a name="the-basics"></a>Základní informace  
 Rozhraní .NET Framework podporuje tři vývojové scénáře uvedena i výše tím, že poskytuje [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]a díky podpoře [!INCLUDE[wrt](../../../includes/wrt-md.md)] sám sebe.  
  
-   [Aplikace .NET pro Windows Store](http://go.microsoft.com/fwlink/p/?LinkId=247912) poskytuje zjednodušený přehled knihovny tříd rozhraní .NET Framework a obsahovat pouze typy a členy můžete použít k vytvoření [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace a [!INCLUDE[wrt](../../../includes/wrt-md.md)] součásti.  
  
    -   Pokud používáte Visual Studio ([!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] nebo novější) pro vývoj [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace nebo [!INCLUDE[wrt](../../../includes/wrt-md.md)] součást, sadu referenční sestavení zajistí, že vidíte jenom relevantní typy a členy.  
  
    -   Tato efektivní sada rozhraní API je jednodušší, ještě odebrání funkcí, které jsou duplikované v rozhraní .NET Framework nebo který duplicitní [!INCLUDE[wrt](../../../includes/wrt-md.md)] funkce. Například obsahuje pouze verze obecné typy kolekcí a modelu objektu dokumentu XML pro odstranění [!INCLUDE[wrt](../../../includes/wrt-md.md)] XML API nastavit.  
  
    -   Funkce, které jednoduše zabalit operační systém rozhraní API jsou také odebrat, protože [!INCLUDE[wrt](../../../includes/wrt-md.md)] je snadné volání ze spravovaného kódu.  
  
     Další informace o [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], najdete v článku [přehled aplikace .NET pro Windows Store](http://go.microsoft.com/fwlink/p/?LinkId=238312) v Center.To vývojáře systému Windows, přečtěte si informace o procesu výběru rozhraní API, najdete v článku [aplikace .NET pro Windows Store](http://go.microsoft.com/fwlink/p/?LinkId=251061) položku v rozhraní .NET blog.  
  
-   [Prostředí Windows Runtime](http://go.microsoft.com/fwlink/p/?LinkId=238319) poskytuje uživatele prvky rozhraní pro vytváření [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace a poskytuje přístup k funkce operačního systému. Rozhraní .NET Framework, jako [!INCLUDE[wrt](../../../includes/wrt-md.md)] obsahuje metadata, která umožňuje kompilátory jazyka C# a Visual Basic používat [!INCLUDE[wrt](../../../includes/wrt-md.md)] knihovny třídy, způsob jejich použití rozhraní .NET Framework. Rozhraní .NET Framework je jednodušší použít [!INCLUDE[wrt](../../../includes/wrt-md.md)] skrytím určité rozdíly:  
  
    -   Některé rozdíly v programování vzory mezi rozhraní .NET Framework a [!INCLUDE[wrt](../../../includes/wrt-md.md)], jako je například vzoru pro přidávání a odebírání obslužné rutiny událostí jsou skryté. Jednoduše použijte vzoru rozhraní .NET Framework.  
  
    -   Některé rozdíly v běžně používané typy (například primitivní typy a kolekce) jsou skryté. Jednoduše použijte typ rozhraní .NET Framework, jak je popsáno v [rozdíly, jsou viditelné v prostředí IDE](#DifferencesVisibleInIDE)dál v tomto článku.  
  
 Většinu času, podpora v rozhraní .NET Framework pro [!INCLUDE[wrt](../../../includes/wrt-md.md)] je transparentní. Další část popisuje některé zřejmá rozdíly mezi spravovaného kódu a [!INCLUDE[wrt](../../../includes/wrt-md.md)].  
  
<a name="AboutReferenceDocumentation"></a>   
### <a name="the-net-framework-and-the-includewrtincludeswrt-mdmd-reference-documentation"></a>Rozhraní .NET Framework a [!INCLUDE[wrt](../../../includes/wrt-md.md)] referenční dokumentace  
 V systému Windows a nastaví dokumentaci rozhraní .NET Framework jsou oddělené. Pokud jste po stisknutí klávesy F1 zobrazit nápovědu pro typ nebo člen, zobrazí se referenční dokumentaci k nástroji z příslušné sady. Ale když si zobrazíte [odkaz na prostředí Windows Runtime](http://go.microsoft.com/fwlink/p/?LinkId=238319) můžete setkat, příklady, které pravděpodobně puzzling:  
  
-   Témata, jako [IIterable rozhraní](http://go.microsoft.com/fwlink/p/?LinkId=238321) nemají syntaxe deklarace pro Visual Basic a C#. Místo toho Poznámka se zobrazí nad části Syntaxe (v tomto případě ".NET: Toto rozhraní se zobrazí jako System.Collections.Generic.IEnumerable\<T >"). Důvodem je, že rozhraní .NET Framework a [!INCLUDE[wrt](../../../includes/wrt-md.md)] poskytuje podobné funkce s jinou rozhraní. Kromě toho jsou chování rozdíly: `IIterable` má `First` metoda místo <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metoda vrátí enumerátor. Namísto nutnosti další jiný způsob provádění běžných úloh, podporuje rozhraní .NET Framework [!INCLUDE[wrt](../../../includes/wrt-md.md)] tím, že zobrazí chcete použít typ jste obeznámeni s spravovaného kódu. Neuvidíte `IIterable` rozhraní v prostředí IDE, a proto jediným způsobem, jak dojde k jeho [!INCLUDE[wrt](../../../includes/wrt-md.md)] referenční dokumentaci k nástroji je přímo procházením prostřednictvím této dokumentace.  
  
-   [SyndicationFeed konstruktor](http://go.microsoft.com/fwlink/p/?LinkId=238322) dokumentace znázorňuje úzce související problém: typy jejího parametr pravděpodobně lišit pro různé jazyky. Pro C# a Visual Basic, jsou typy parametrů <xref:System.String?displayProperty=nameWithType> a <xref:System.Uri?displayProperty=nameWithType>. Znovu, je to proto rozhraní .NET Framework má svou vlastní `String` a `Uri` typy a pro takové běžně používané typy ho nemá smysl vynutit uživatelů rozhraní .NET Framework další jiný způsob plnění úkolů. V prostředí IDE, rozhraní .NET Framework skryje odpovídající [!INCLUDE[wrt](../../../includes/wrt-md.md)] typy.  
  
-   V určitých případech, jako [Windows.UI.Xaml.GridLength](http://go.microsoft.com/fwlink/p/?LinkId=251059) struktury rozhraní .NET Framework poskytuje typ se stejným názvem, ale další funkce. Například jsou sadu témat konstruktor a vlastnosti přidružené `GridLength`, ale protože členů nejsou k dispozici pouze ve spravovaném kódu mají syntaxi bloky pouze pro Visual Basic a C#. V [!INCLUDE[wrt](../../../includes/wrt-md.md)], struktury obsahovat pouze pole. [!INCLUDE[wrt](../../../includes/wrt-md.md)] Vyžaduje pomocná třída, struktura [Windows.UI.Xaml.GridLengthHelper](http://go.microsoft.com/fwlink/p/?LinkId=251060), aby ekvivalentní funkce. Neuvidíte, že pomocná třída v integrovaném vývojovém prostředí při psaní spravovaného kódu.  
  
-   V prostředí IDE [!INCLUDE[wrt](../../../includes/wrt-md.md)] zobrazí typy odvození od <xref:System.Object?displayProperty=nameWithType>. Budou pravděpodobně členy zděděno z <xref:System.Object>, jako například <xref:System.Object.ToString%2A?displayProperty=nameWithType>. Tito členové pracovat stejně jako Pokud typy ve skutečnosti zděděn z <xref:System.Object>, a [!INCLUDE[wrt](../../../includes/wrt-md.md)] typy lze převést na <xref:System.Object>. Tato funkce je součástí poskytující rozhraní .NET Framework pro podporu [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Ale pokud zobrazit typy v [!INCLUDE[wrt](../../../includes/wrt-md.md)] referenční dokumentace, zobrazí žádné takové členy. V dokumentaci pro tyto zřejmá zděděné členy zajišťuje <xref:System.Object?displayProperty=nameWithType> referenční dokumentace.  
  
<a name="DifferencesVisibleInIDE"></a>   
### <a name="differences-that-are-visible-in-the-ide"></a>Rozdíly, které jsou viditelné v prostředí IDE  
 V další pokročilé scénáře programování, jako je třeba použití [!INCLUDE[wrt](../../../includes/wrt-md.md)] součásti, které jsou napsané v C# zajistit logiku aplikace pro [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace vytvořená pro systém Windows pomocí jazyka JavaScript, tyto rozdíly jsou zřejmá v prostředí IDE stejně jako v dokumentaci. Při vrácení příslušné součásti `IDictionary<int, string>` JavaScript a prohlédněte si ho v ladicím programu jazyka JavaScript, uvidíte metody `IMap<int, string>` protože používá JavaScript [!INCLUDE[wrt](../../../includes/wrt-md.md)] typu. Některé běžně používané kolekce, které v následující tabulce jsou uvedeny typy, které vypadat jinak, ve dvou jazycích:  
  
|[!INCLUDE[wrt](../../../includes/wrt-md.md)]Typ|Odpovídající typ rozhraní .NET Framework|  
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
  
 V [!INCLUDE[wrt](../../../includes/wrt-md.md)], `IMap<K, V>` a `IMapView<K, V>` jsou vstupní pomocí `IKeyValuePair`. Když je předat do spravovaného kódu, se zobrazí jako `IDictionary<TKey, TValue>` a `IReadOnlyDictionary<TKey, TValue>`, takže přirozeně použijete `System.Collections.Generic.KeyValuePair<TKey, TValue>` je výčet.  
  
 Rozhraní způsob, jak se zobrazí v ovlivňuje spravovaného kódu, objevit způsob typy, které implementují tato rozhraní. Například `PropertySet` třída implementuje `IMap<K, V>`, která se zobrazí ve spravovaném kódu jako `IDictionary<TKey, TValue>`. `PropertySet`se zobrazí, jako kdyby se implementovat `IDictionary<TKey, TValue>` místo `IMap<K, V>`, takže ve spravovaném kódu se zdá, že máte `Add` metodu, která se chová stejně jako `Add` metoda v rozhraní .NET Framework slovník. Nezobrazí tak, aby měl `Insert` metoda.  
  
 Další informace o vytváření pomocí rozhraní .NET Framework [!INCLUDE[wrt](../../../includes/wrt-md.md)] součásti a návod, který ukazuje, jak použít tyto součásti v jazyce JavaScript, najdete v části [vytváření součásti systému Windows Runtime v C# a Visual Basic](http://go.microsoft.com/fwlink/p/?LinkId=238313) v Centrum vývojářů pro Windows.  
  
### <a name="primitive-types"></a>Primitivní typy  
 Povolení přirozené použití [!INCLUDE[wrt](../../../includes/wrt-md.md)] ve spravovaném kódu, primitivní typy rozhraní .NET Framework se zobrazí místo [!INCLUDE[wrt](../../../includes/wrt-md.md)] primitivní typy v kódu. V rozhraní .NET Framework, primitivní typy, jako `Int32` struktura mít mnoho užitečné vlastnosti a metody, jako `Int32.TryParse` metoda. Naopak primitivní typy a struktury v [!INCLUDE[wrt](../../../includes/wrt-md.md)] obsahovat pouze pole. Pokud použijete primitiv ve spravovaném kódu, se zobrazí jako typy rozhraní .NET Framework a můžete vlastnosti a metody rozhraní .NET Framework typů běžným způsobem. Následující seznam obsahuje souhrn:  
  
-   Pro [!INCLUDE[wrt](../../../includes/wrt-md.md)] primitiv `Int32`, `Int64`, `Single`, `Double`, `Boolean`, `String` (neměnné kolekci znaky Unicode), `Enum`, `UInt32`, `UInt64`, a `Guid`, použijte typ se stejným názvem v `System` oboru názvů.  
  
-   Pro `UInt8`, použijte `System.Byte`.  
  
-   Pro `Char16`, použijte `System.Char`.  
  
-   Pro `IInspectable` rozhraní, použijte `System.Object`.  
  
-   Pro `HRESULT`, použijte strukturou s jedním `System.Int32` člen.  
  
 Stejně jako u rozhraní typy jenom jednou, může se zobrazit důkaz tento reprezentace je při projektu rozhraní .NET Framework je [!INCLUDE[wrt](../../../includes/wrt-md.md)] komponenty, která je používána [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace vytvořené pomocí jazyka JavaScript.  
  
 Další základní běžně používané [!INCLUDE[wrt](../../../includes/wrt-md.md)] typy, které se zobrazují v spravovaného kódu jako patří jejich ekvivalenty rozhraní .NET Framework `Windows.Foundation.DateTime` struktura, která se zobrazí ve spravovaném kódu jako <xref:System.DateTimeOffset?displayProperty=nameWithType> struktury a `Windows.Foundation.TimeSpan` struktury, která Zobrazí se jako <xref:System.TimeSpan?displayProperty=nameWithType> struktura.  
  
### <a name="other-differences"></a>Další rozdíly  
 V několika případech skutečnost, že typy rozhraní .NET Framework objeví ve vašem kódu místo [!INCLUDE[wrt](../../../includes/wrt-md.md)] typy vyžaduje akci z vaší strany. Například [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376) třídy se zobrazí jako <xref:System.Uri?displayProperty=nameWithType> v rozhraní .NET Framework kódu. <xref:System.Uri?displayProperty=nameWithType>Umožňuje relativní identifikátor URI, ale [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376) vyžaduje absolutní identifikátor URI. Proto když předávání identifikátorů URI [!INCLUDE[wrt](../../../includes/wrt-md.md)] metoda, ujistěte se, že je absolutní. (Viz [předávání identifikátorů URI do prostředí Windows Runtime](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md).)  
  
<a name="WindowsRuntimeComponents"></a>   
## <a name="scenarios-for-developing-windows-runtime-components"></a>Scénáře pro vývoj součásti systému Windows Runtime  
 Scénáře, které jsou podporovány pro spravované [!INCLUDE[wrt](../../../includes/wrt-md.md)] součásti závisí na následující obecné zásady:  
  
-   [!INCLUDE[wrt](../../../includes/wrt-md.md)]Součásti, které jsou vytvořené pomocí rozhraní .NET Framework máte zřejmá rozdíl v ničem z jiných [!INCLUDE[wrt](../../../includes/wrt-md.md)]knihovny. Například, pokud znovu implementovat nativní [!INCLUDE[wrt](../../../includes/wrt-md.md)] součást pomocí spravovaného kódu, dvě součásti jsou vně. Je skutečnost, že se příslušné součásti zapsané ve spravovaném kódu pro kód, který používá je skrytá, i když tento kód je sám spravovaného kódu. Interně, ale příslušné součásti je true spravovaného kódu a běží na modul CLR (CLR).  
  
-   Součástí může obsahovat typy, které implementují logiku aplikace [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uživatelského rozhraní ovládací prvky, nebo obojí.  
  
    > [!NOTE]
    >  Je dobrým zvykem jednotlivé prvky uživatelského rozhraní z logiky aplikace. Navíc nemůžete použít [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] ovládacích prvků do uživatelského rozhraní [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace vytvořená pro systém Windows pomocí jazyka JavaScript a HTML.  
  
-   Komponenta může být v rámci řešení sady Visual Studio pro projekt [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace nebo znovu použitelné komponentní, které můžete přidat do více řešení.  
  
    > [!NOTE]
    >  Pokud příslušné součásti se použije pouze s C# nebo Visual Basic, neexistuje žádný důvod, aby bylo [!INCLUDE[wrt](../../../includes/wrt-md.md)] součásti. Pokud provedete ho obyčejnou knihovna tříd rozhraní .NET Framework místo toho, nemusíte omezit prostor veřejné rozhraní API pro [!INCLUDE[wrt](../../../includes/wrt-md.md)] typy.  
  
-   Můžete vydání verzí opakovaně použitelné součásti pomocí [!INCLUDE[wrt](../../../includes/wrt-md.md)] [VersionAttribute](http://go.microsoft.com/fwlink/p/?LinkId=238563) atribut identifikovat, jaké typy (a které členy v rámci typu) byly přidány v různých verzích.  
  
-   Typy v příslušné součásti můžete odvozena od [!INCLUDE[wrt](../../../includes/wrt-md.md)] typy. Ovládací prvky můžete odvozena od typy primitivní ovládacích prvků v [Windows.UI.Xaml.Controls.Primitives](http://go.microsoft.com/fwlink/p/?LinkId=238564) oboru názvů nebo z více skončila ovládací prvky [tlačítko](http://go.microsoft.com/fwlink/p/?LinkId=238565).  
  
    > [!IMPORTANT]
    >  Počínaje [!INCLUDE[win8](../../../includes/win8-md.md)] a [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], všechny veřejné typy ve spravovaných [!INCLUDE[wrt](../../../includes/wrt-md.md)] součásti musí být zapečetěna. Typ v jiném [!INCLUDE[wrt](../../../includes/wrt-md.md)] komponentu nelze odvodit z nich. Pokud chcete zajistit polymorfní chování v příslušné součásti, můžete vytvořit rozhraní a implementovat v polymorfní typy.  
  
-   Musí být všechny typy parametrů a vraťte se na veřejné typy v příslušné součásti [!INCLUDE[wrt](../../../includes/wrt-md.md)] typy (včetně [!INCLUDE[wrt](../../../includes/wrt-md.md)] typy, které definuje příslušné součásti).  
  
 Následující části obsahují příklady běžné scénáře.  
  
### <a name="application-logic-for-a-includewin8appnamelongincludeswin8-appname-long-mdmd-app-with-javascript"></a>Aplikační logiku pro [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace v jazyce JavaScript  
 Když budete vyvíjet [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace pro systém Windows pomocí jazyka JavaScript, můžete zjistit, zda některé části aplikační logiku líp fungovat ve spravovaném kódu, nebo jsou usnadňují vývoj. JavaScript nemůže používat knihovny tříd rozhraní .NET Framework přímo, ale můžete použít knihovny tříd. WinMD soubor. V tomto scénáři [!INCLUDE[wrt](../../../includes/wrt-md.md)] součást je nedílnou součástí aplikace, takže nemá smysl zajistit verze atributy.  
  
### <a name="reusable-includewin8appnamelongincludeswin8-appname-long-mdmd-ui-controls"></a>Opakovaně použitelného [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] ovládacích prvků uživatelského rozhraní  
 Můžete balíček sadu související ovládacích prvků uživatelského rozhraní v opakovaně použitelného [!INCLUDE[wrt](../../../includes/wrt-md.md)] součásti. Na trh komponentu svoje vlastní nebo použít jako element v aplikacích, které vytvoříte. V tomto scénáři má smysl použít [!INCLUDE[wrt](../../../includes/wrt-md.md)] [VersionAttribute](http://go.microsoft.com/fwlink/p/?LinkId=238563) atribut zlepšit kompatibilitu.  
  
### <a name="reusable-application-logic-from-existing-net-framework-apps"></a>Znovu použitelné aplikační logiku z existující aplikací rozhraní .NET Framework  
 Spravovaný kód můžete balíček z existujících desktopových aplikací jako samostatná [!INCLUDE[wrt](../../../includes/wrt-md.md)] součásti. To umožňuje používat komponentu v [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace vytvořené pomocí C++ nebo JavaScript, stejně jako v [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace vytvořené pomocí jazyka C# nebo Visual Basic. Správa verzí je možnost, pokud existuje více scénářů opakované použití kódu.  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Přehled aplikace .NET pro Windows Store](http://go.microsoft.com/fwlink/p/?LinkId=238312)|Popisuje typy rozhraní .NET Framework a členy, které můžete použít k vytvoření [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace a [!INCLUDE[wrt](../../../includes/wrt-md.md)]součásti. (Na webu Windows Dev Center.)|  
|[Plán pro aplikace Windows Store pomocí jazyka C# nebo Visual Basic](http://go.microsoft.com/fwlink/p/?LinkId=242212)|Poskytuje klíče materiály, které vám pomůžou začít s vývojem [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikací pomocí jazyka C# nebo Visual Basic, včetně mnoha témata rychlý start, pokyny a osvědčené postupy. (Na webu Windows Dev Center.)|  
|[Vývoj aplikací pro Windows Store (VB / c / C++ a XAML)](http://go.microsoft.com/fwlink/p/?LinkId=238311)|Poskytuje klíče materiály, které vám pomůžou začít s vývojem [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikací pomocí jazyka C# nebo Visual Basic, včetně mnoha témata rychlý start, pokyny a osvědčené postupy. (Na webu Windows Dev Center.)|  
|[Vytváření modulu Runtime součásti systému Windows v C# a Visual Basic](http://go.microsoft.com/fwlink/p/?LinkId=238313)|Popisuje postup vytvoření [!INCLUDE[wrt](../../../includes/wrt-md.md)] komponenty pomocí rozhraní .NET Framework, vysvětluje, jak můžete použít jako součást [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace vytvořená pro systém Windows pomocí jazyka JavaScript a popisuje, jak ladit kombinace pomocí sady Visual Studio. (Na webu Windows Dev Center.)|  
|[Odkaz na prostředí Windows Runtime](/uwp/api/)|V referenční dokumentaci [!INCLUDE[wrt](../../../includes/wrt-md.md)]. (Na webu Windows Dev Center.)|  
|[Předávání identifikátorů URI do prostředí Windows Runtime](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md)|Popisuje problém, který mohou nastat při předání identifikátoru URI ze spravovaného kódu na [!INCLUDE[wrt](../../../includes/wrt-md.md)]a jak tomu zamezit.|
