---
title: Migrace aplikace pro Windows Store do .NET Native
ms.date: 03/30/2017
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3909855db109938794fad3e0afc99d492009b81c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43461784"
---
# <a name="migrating-your-windows-store-app-to-net-native"></a>Migrace aplikace pro Windows Store do .NET Native
.NET native poskytuje statické kompilace aplikací ve Windows Store nebo v počítači vývojáře. Tím se liší od dynamická kompilace provádí kompilátor just-in-time (JIT) pro aplikace Windows Store nebo [Native Image Generator (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) na zařízení. Bez ohledu na rozdíly, .NET Native snaží udržovat kompatibilitu s [.NET pro Windows Store apps](https://msdn.microsoft.com/library/windows/apps/br230302.aspx). Ve většině případů věcí, které fungují v aplikacích .NET pro Windows Store také pracovat s .NET Native.  Nicméně v některých případech může dojít k nějaké změny. Tento dokument popisuje tyto rozdíly mezi standardní aplikace .NET pro Windows Store a .NET Native v následujících oblastech:  
  
-   [Obecné runtime rozdíly](#Runtime)  
  
-   [Dynamické programování rozdílů](#Dynamic)  
  
-   [Další související reflexe rozdíly](#Reflection)  
  
-   [Nepodporované scénáře a rozhraní API](#Unsupported)  
  
-   [Visual Studio rozdíly](#VS)  
  
<a name="Runtime"></a>   
## <a name="general-runtime-differences"></a>Obecné runtime rozdíly  
  
-   Výjimky, jako například <xref:System.TypeLoadException>, která jsou vyvolány pomocí kompilátoru JIT, když je aplikace spuštěna ve společné language runtime (CLR) obecně vést k chybám kompilace při zpracování v .NET Native.  
  
-   Nevolejte <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> metoda z vlákna uživatelského rozhraní aplikace. To může způsobit zablokování v .NET Native.  
  
-   Nemusíte spoléhat na pořadí vyvolání konstruktoru statické třídy. V rozhraní .NET Native se liší od pořadí v modulu runtime standardní pořadí volání. (I s standardní modulu runtime, neměli byste spoléhat pořadí spuštění statické třídy konstruktory.)  
  
-   Nekonečné smyčky bez volání (například `while(true);`) v libovolném vlákně může přenést aplikaci do zastavení. Obdobně čeká velký nebo nekonečné podat aplikace zastavení.  
  
-   Některé obecné inicializace cykly není vyvolat výjimky v .NET Native. Například následující kód vyvolá výjimku <xref:System.TypeLoadException> výjimky na standardní modulu CLR. V .NET Native nepodporuje.  
  
     [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]  
  
-   V některých případech poskytuje různé implementace knihovny tříd rozhraní .NET Framework .NET Native. Objekt vrácený z metody vždy členy vrácený typ implementuje. Ale protože jeho základní implementaci se liší, je nemusí být schopné provést přetypování na stejnou sadu typů, jako by na jiných platformách rozhraní .NET Framework. Například v některých případech se vám nemusí být schopné provést přetypování <xref:System.Collections.Generic.IEnumerable%601> vrácena metodami, jako objekt rozhraní <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> nebo <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> k `T[]`.  
  
-   Ve výchozím nastavení pro aplikace .NET pro Windows Store není povolené mezipaměti rozhraní WinInet, ale je v .NET Native. To zvyšuje výkon, ale má pracujícího důsledky sady. Není nutná žádná akce pro vývojáře.  
  
<a name="Dynamic"></a>   
## <a name="dynamic-programming-differences"></a>Dynamické programování rozdílů  
 .NET native staticky odkazuje v kódu z rozhraní .NET Framework, aby kód aplikace místní pro maximální výkon. Binární velikosti je však nutné zůstanou malé, takže celé rozhraní .NET Framework není možné připojit v. Toto omezení kompilátoru .NET Native řeší pomocí závislost redukční funkci, která odebere odkazy na nepoužitý kód. Však .NET Native nemusí udržovat nebo vytvořit některé informace o typu a kód při informace nelze odvodit staticky v době kompilace, ale místo toho se dynamicky načíst za běhu.  
  
 .NET native povolení reflexe a dynamické programování. Ne všechny typy však může být označený pro reflexi, protože by velikost generovaného kódu moc velká (zejména protože odráží v rámci veřejných API v rozhraní .NET Framework je podporováno). Kompilátor .NET Native díky inteligentní možnosti, které typy by měly podporovat reflexe a uchovává metadata a generuje kód jenom pro tyto typy.  
  
 Například datová vazba vyžaduje aplikaci umožnit názvy vlastností namapovat na funkce. V aplikacích .NET pro Windows Store modul common language runtime automaticky používá reflexi pro tuto možnost poskytnout pro spravované typy a veřejně dostupné nativní typy. V rozhraní .NET Native kompilátor automaticky zahrnuje jejich metadata pro typy, na které svázat data.  
  
 .NET Native kompilátoru zvládne také běžně používá obecné typy, jako <xref:System.Collections.Generic.List%601> a <xref:System.Collections.Generic.Dictionary%602>, což práce bez vyžadování jakéhokoli pomocné parametry nebo direktivy. [Dynamické](~/docs/csharp/language-reference/keywords/dynamic.md) – klíčové slovo je podporováno také v rámci určitá omezení.  
  
> [!NOTE]
>  Při přenesení aplikace do .NET Native měli důkladně otestujte všech cestách kódu. dynamické.  
  
 Výchozí konfigurace pro .NET Native stačí pro většinu vývojářů, ale někteří vývojáři mohou chtít jemné ladit jejich konfigurace s použitím direktivy modulu runtime (. rd.xml) soubor. Kromě toho v některých případech se kompilátoru .NET Native nelze určit, která metadata musí být k dispozici pro účely reflexe a spoléhá na pomocné parametry, zejména v následujících případech:  
  
-   Některé konstrukce, jako jsou <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> a <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> nemůže být určeno staticky.  
  
-   Obecný typ, který chcete zhodnocení, protože kompilátor nemůže určit, instancí, musí být zadaný pomocí direktivy modulu runtime. Nejedná se o to, že veškerý kód musí být zahrnut, ale protože odraz na obecných typech mohl vytvořit nekonečné cyklus (například, když obecné metody se vyvolá u obecného typu).  
  
> [!NOTE]
>  Direktivy modulu runtime jsou definovány v direktivy modulu runtime (. rd.xml) soubor. Obecné informace o použití tohoto souboru najdete v tématu [Začínáme](../../../docs/framework/net-native/getting-started-with-net-native.md). Informace o direktivy modulu runtime naleznete v tématu [direktivy modulu Runtime (rd.xml) odkaz na soubor konfigurace](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
 .NET native také zahrnuje profilování nástroje, které pomůžou vývojářům určit, jaké typy mimo výchozí sadu by měla podporovat reflexe.  
  
<a name="Reflection"></a>   
## <a name="other-reflection-related-differences"></a>Další související reflexe rozdíly  
 Existuje mnoho dalších jednotlivé související reflexe rozdíly v chování mezi aplikacemi .NET pro Windows Store a .NET Native.  
  
 V .NET Native:  
  
-   Privátní reflexe přes typy a členy v knihovně tříd rozhraní .NET Framework není podporováno. Můžete však reflexi vlastní privátní typy a členy, jakož i typy a členy v knihovnách třetích stran.  
  
-   <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> Správně vrátí vlastnost `false` pro <xref:System.Reflection.ParameterInfo> objekt, který reprezentuje návratovou hodnotu. V aplikacích .NET pro Windows Store, vrátí `true`. Převodní jazyk (IL) nepodporuje tento přímo a výkladu je ponecháno na jazyk.  
  
-   Veřejné členy na <xref:System.RuntimeFieldHandle> a <xref:System.RuntimeMethodHandle> struktury nejsou podporovány. Tyto typy jsou podporovány pouze pro LINQ, stromy výrazů a inicializace statické pole.  
  
-   <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> a <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> zahrnout skryté členy základních tříd a může proto přepsat bez explicitního přepsání. To platí také pro jiné [RuntimeReflectionExtensions.GetRuntime*](https://msdn.microsoft.com/library/system.reflection.runtimereflectionextensions_methods.aspx) metody.  
  
-   <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> a <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> není selhání při pokusu o vytvoření určité kombinace (například pole Parametry ByRef).  
  
-   Reflexe nelze použít k vyvolání členy, které mají parametry ukazatele.  
  
-   Reflexe nelze použít k získání nebo nastavení pole ukazatel.  
  
-   Když je nesprávný počet argumentů a typ jednoho z argumentů není správný, .NET Native vyvolá <xref:System.ArgumentException> místo <xref:System.Reflection.TargetParameterCountException>.  
  
-   Binární serializace výjimek není obecně podporována. V důsledku toho nejsou objekty mohou být přidány do <xref:System.Exception.Data%2A?displayProperty=nameWithType> slovníku.  
  
<a name="Unsupported"></a>   
## <a name="unsupported-scenarios-and-apis"></a>Nepodporované scénáře a rozhraní API  
 V následujících částech nepodporované scénáře a rozhraní API pro obecný vývoj, spolupráce a technologie, jako je HTTPClient a Windows Communication Foundation (WCF):  
  
-   [Obecný vývoj](#General)  
  
-   [HttpClient](#HttpClient)  
  
-   [Interop](#Interop)  
  
-   [Nepodporované rozhraní API](#APIs)  
  
<a name="General"></a>   
### <a name="general-development-differences"></a>Obecný vývoj rozdíly  
 **Typy hodnot**  
  
-   Pokud přepíšete <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> a <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> metody pro typ hodnoty, nevolejte implementace základní třídy. V aplikacích .NET pro Windows Store tyto metody závisí na reflexi. V době kompilace .NET Native generuje implementace, která se nemusí spoléhat na reflexe runtime. To znamená, že pokud nepřepíšete tyto dvě metody, budou fungovat podle očekávání, protože implementace v době kompilace .NET Native generuje. Ale přepsání těchto metod ale volání implementace základní třídy za následek výjimku.  
  
-   Typy hodnot, které jsou větší než jeden megabajt, ale nejsou podporovány.  
  
-   Typy hodnot nemohou mít výchozí konstruktor v .NET Native. (C# a Visual Basic zakázat výchozí konstruktory na hodnotách. Nicméně ty lze vytvořit v IL.)  
  
 **Pole**  
  
-   Pole s dolní hranicí jinou než nula, nejsou podporována. Obvykle se tato pole vytvářejí voláním <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> přetížení.  
  
-   Dynamické vytváření vícerozměrných polí není podporováno. Takové pole jsou obvykle vytvořeny voláním přetížení <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> metoda, která zahrnuje `lengths` parametr, nebo voláním <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> metoda.  
  
-   Vícerozměrná pole, které mají čtyři nebo více dimenzí nejsou podporovány. To znamená, že jejich <xref:System.Array.Rank%2A?displayProperty=nameWithType> hodnotu vlastnosti, jsou čtyři nebo vyšší. Použití [Vícenásobná pole](~/docs/csharp/programming-guide/arrays/jagged-arrays.md) (pole polí) místo toho. Například `array[x,y,z]` není platný, ale `array[x][y][z]` není.  
  
-   Variance pro vícerozměrná pole se nepodporuje a způsobí, že <xref:System.InvalidCastException> výjimka za běhu.  
  
 **Obecné typy**  
  
-   Nekonečné rozšíření generického typu způsobí chybu kompilátoru. Tento kód například selže při kompilaci:  
  
     [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]  
  
 **Ukazatele**  
  
-   Pole ukazatelů nejsou podporovány.  
  
-   Reflexe nelze použít k získání nebo nastavení pole ukazatel.  
  
 **Serializace**  
  
 <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> Atribut není podporován. Použití <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> místo atributu.  
  
 **Prostředky**  
  
 Používání lokalizované prostředky <xref:System.Diagnostics.Tracing.EventSource> třída není podporována. <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> Vlastnost nedefinuje lokalizované prostředky.  
  
 **Delegáti**  
  
 `Delegate.BeginInvoke` a `Delegate.EndInvoke` nejsou podporovány.  
  
 **Ostatní rozhraní API**  
  
-   <xref:System.Reflection.TypeInfo.GUID%2A?displayProperty=nameWithType> Vlastnost vyvolá <xref:System.PlatformNotSupportedException> výjimka pokud <xref:System.Runtime.InteropServices.GuidAttribute> není použit atribut typu. Identifikátor GUID slouží především pro podporu modelu COM.  
  
-   <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> Metoda správně Parsuje řetězce, které obsahují krátký kalendářní data v .NET Native. Ale se nebude udržovat kompatibilitu s změny v datum a čas analýzy je popsáno v článcích znalostní báze Microsoft Knowledge Base [KB2803771](https://support.microsoft.com/kb/2803771) a [KB2803755](https://support.microsoft.com/kb/2803755).  
  
-   <xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType> `("E")` poloměr zaoblení správně v .NET Native. V některých verzích CLR je výsledný řetězec zkrácen místo zaokrouhleno.  
  
<a name="HttpClient"></a>   
### <a name="httpclient-differences"></a>Rozdíly HttpClient  
 V rozhraní .NET Native <xref:System.Net.Http.HttpClientHandler> třída interně používá rozhraní WinINet (prostřednictvím [HttpBaseProtocolFilter](https://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) třídy) namísto <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> třídy používané ve standardní aplikace .NET pro Windows Store.  WinINet nepodporuje všechny možnosti konfigurace, pro které <xref:System.Net.Http.HttpClientHandler> třídy podporuje.  Výsledek:  
  
-   Některé vlastnosti funkce na <xref:System.Net.Http.HttpClientHandler> vrátit `false` v .NET Native, že vrátí `true` ve standardní aplikace .NET pro Windows Store.  
  
-   Některé vlastnosti konfigurace `get` přistupující objekty vždy vrátí pevnou hodnotu v .NET Native, která je jiná než výchozí hodnotu konfigurovatelné v aplikacích .NET pro Windows Store.  
  
 Některé další rozdíly jsou popsané v následujících oddílech.  
  
 **Proxy server**  
  
 [HttpBaseProtocolFilter](https://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) třída nepodporuje konfiguraci nebo přepsání proxy serveru na základě žádosti.  To znamená, že všechny žádosti na .NET Native používat systému nakonfigurovaný proxy server nebo žádný proxy server, v závislosti na hodnotu <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> vlastnost.  V aplikacích .NET pro Windows Store, je definován proxy serveru <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> vlastnost.  V .NET Native, nastavení <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> hodnotu jinou než `null` vyvolá <xref:System.PlatformNotSupportedException> výjimky.  <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> Vrátí vlastnost `false` v .NET Native, že ji vrací `true` ve standardní aplikace rozhraní .NET Framework pro Windows Store.  
  
 **Automatické přesměrování**  
  
 [HttpBaseProtocolFilter](https://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) třídy neumožňuje maximálního počtu automatické přesměrování nakonfigurovat.  Hodnota <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> vlastnost je 50 ve výchozím nastavení standardní aplikace .NET pro Windows Store a je možné upravit. V .NET Native, tato vlastnost hodnotu 10 a upravit ji vyvolá výjimku při pokusu <xref:System.PlatformNotSupportedException> výjimky.  <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> Vrátí vlastnost `false` v .NET Native, že ji vrací `true` v aplikacích .NET pro Windows Store.  
  
 **Automatická dekomprese**  
  
 .NET pro Windows Store apps vám umožní nastavit <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> vlastnost <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, obě <xref:System.Net.DecompressionMethods.Deflate> a <xref:System.Net.DecompressionMethods.GZip>, nebo <xref:System.Net.DecompressionMethods.None>.  .NET native podporuje pouze <xref:System.Net.DecompressionMethods.Deflate> spolu s <xref:System.Net.DecompressionMethods.GZip>, nebo <xref:System.Net.DecompressionMethods.None>.  Pokoušíte se nastavit <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> vlastnost buď <xref:System.Net.DecompressionMethods.Deflate> nebo <xref:System.Net.DecompressionMethods.GZip> samostatně tiše nastaví na obě <xref:System.Net.DecompressionMethods.Deflate> a <xref:System.Net.DecompressionMethods.GZip>.  
  
 **Soubory cookie**  
  
 Zpracování souborů cookie najednou pomocí provádí <xref:System.Net.Http.HttpClient> a rozhraní WinINet.  Soubory cookie z <xref:System.Net.CookieContainer> spolu se soubory cookie do mezipaměti rozhraní WinINet souboru cookie.  Odebírá se soubor cookie z <xref:System.Net.CookieContainer> brání <xref:System.Net.Http.HttpClient> odesílání souboru cookie, ale pokud soubor cookie již viděla WinINet a soubory cookie nedošlo k odstranění tohoto uživatele z rozhraní WinINet odešle.  Není možné programově odebrat soubor cookie z rozhraní WinINet pomocí <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>, nebo <xref:System.Net.CookieContainer> rozhraní API.  Nastavení <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> vlastnost `false` způsobí, že pouze <xref:System.Net.Http.HttpClient> aby přestalo odesílat soubory cookie. Wininet – může obsahovat stále její soubory cookie v požadavku.  
  
 **Přihlašovací údaje**  
  
 V aplikacích .NET pro Windows Store <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> a <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> vlastnosti pracovat nezávisle.  Kromě toho <xref:System.Net.Http.HttpClientHandler.Credentials%2A> vlastnost přijímá libovolný objekt, který implementuje <xref:System.Net.ICredentials> rozhraní.  V rozhraní .NET Native, nastavení <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> vlastnost `true` způsobí, že <xref:System.Net.Http.HttpClientHandler.Credentials%2A> vlastnost `null`.  Kromě toho <xref:System.Net.Http.HttpClientHandler.Credentials%2A> vlastnost lze nastavit pouze na `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>, nebo objekt typu <xref:System.Net.NetworkCredential>.  Přiřazení jiného <xref:System.Net.ICredentials> objektu, nejoblíbenější z nich je <xref:System.Net.CredentialCache>do <xref:System.Net.Http.HttpClientHandler.Credentials%2A> vlastnost vyvolá <xref:System.PlatformNotSupportedException>.  
  
 **Další funkce nepodporované nebo unconfigurable**  
  
 V .NET Native:  
  
-   Hodnota <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> vlastnost je vždy <xref:System.Net.Http.ClientCertificateOption.Automatic>.  V aplikacích .NET pro Windows Store, výchozí hodnota je <xref:System.Net.Http.ClientCertificateOption.Manual>.  
  
-   <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> Vlastnost není konfigurovatelné.  
  
-   <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> Vlastnost je vždy `true`.  V aplikacích .NET pro Windows Store, výchozí hodnota je `false`.  
  
-   `SetCookie2` Hlaviček v odpovědi se ignoruje jako zastaralé.  
  
<a name="Interop"></a>   
### <a name="interop-differences"></a>Spolupráce rozdíly  
 **Zastaralé rozhraní API**  
  
 Počet zřídka používaný rozhraní API pro interoperabilitu se spravovaným kódem se již nepoužívají. Při použití s .NET Native, může vyvolat tato rozhraní API <xref:System.NotImplementedException> nebo <xref:System.PlatformNotSupportedException> výjimky nebo vyústí v chybu kompilátoru. V aplikacích .NET pro Windows Store tato rozhraní API jsou označeny jako zastaralé, i když jejich volání generuje kompilátor varování spíše než chybu kompilátoru.  
  
 Zastaralá rozhraní API pro `VARIANT` zařazování:  
  
||  
|-|  
|<xref:System.Runtime.InteropServices.BStrWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.VariantWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.VarEnum?displayProperty=nameWithType>|  
  
 <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> je podporováno, ale vyvolá výjimku v některých případech, například při použití s [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) nebo varianty byref.  
  
 Zastaralá rozhraní API pro [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) podporují:  
  
|Typ|Člen|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch>|  
|<xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual>|  
|<xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>|Atribut není podporovaný.|  
  
 Zastaralé rozhraní API classic událostí modelu COM:  
  
||  
|-|  
|<xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>|  
  
 Zastaralá rozhraní API v <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> rozhraní, což není podporováno v .NET Native:  
  
|Typ|Člen|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType>|Všichni členové.|  
|<xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType>|Všichni členové.|  
|<xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType>|Všichni členové.|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=nameWithType>|  
  
 Nepodporované spolupráce funkce:  
  
|Typ|Člen|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType>|Všichni členové.|  
|<xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType>|Všichni členové.|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.Currency>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.AnsiBStr>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.AsAny>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.CustomMarshaler>|  
  
 Zřídka se používá sběrného systému rozhraní API:  
  
|Typ|Člen|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadByte%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadInt16%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadInt32%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadInt64%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadIntPtr%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteByte%28System.Object%2CSystem.Int32%2CSystem.Byte%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteInt16%28System.Object%2CSystem.Int32%2CSystem.Int16%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteInt32%28System.Object%2CSystem.Int32%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteInt64%28System.Object%2CSystem.Int32%2CSystem.Int64%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteIntPtr%28System.Object%2CSystem.Int32%2CSystem.IntPtr%29>|  
  
 **Vyvolání platformy a kompatibilita vzájemné spolupráce COM**  
  
 Většina nespravovaného kódu a modelu COM interop scénáře jsou stále podporovány v .NET Native. Konkrétně se podporuje všechny interoperability s modulem Windows Runtime (WinRT) rozhraní API a zařazování požadované pro prostředí Windows Runtime. To zahrnuje podporu pro zařazování:  
  
-   Pole (včetně <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)  
  
-   `BStr`  
  
-   Delegáty  
  
-   Řetězce (kódování Unicode, Ansi a HSTRING)  
  
-   Struktury (`byref` a `byval`)  
  
-   Sjednocení  
  
-   Obslužné rutiny Win32  
  
-   Všechny konstruktory WinRT  
  
-   Částečně se podporuje pro zařazování typů variant. Jsou podporovány následující:  
  
    -   <xref:System.Boolean>  
  
    -   <xref:System.Byte>  
  
    -   <xref:System.Decimal>  
  
    -   <xref:System.Double>  
  
    -   <xref:System.Int16>  
  
    -   <xref:System.Int32>  
  
    -   <xref:System.Int64>  
  
    -   <xref:System.SByte>  
  
    -   <xref:System.Single>  
  
    -   <xref:System.UInt16>  
  
    -   <xref:System.UInt32>  
  
    -   <xref:System.UInt64>  
  
    -   `BStr`  
  
    -   [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)  
  
 Ale .NET Native nepodporuje následující:  
  
-   Použití klasického událostí modelu COM  
  
-   Implementace <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> na spravovaný typ rozhraní  
  
-   Implementace [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) rozhraní pro spravovaný typ prostřednictvím <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> atribut. Mějte však na paměti, že nelze volat COM objekty prostřednictvím `IDispatch`, a spravovaný objekt nemůže implementovat `IDispatch`.  
  
 Použití reflexe pro vyvolání platformy volání metody není podporováno. Toto omezení můžete obejít obtékání volání metody v jiné metody a místo toho Obálka volání pomocí reflexe.  
  
<a name="APIs"></a>   
### <a name="other-differences-from-net-apis-for-windows-store-apps"></a>Další rozdíly v rozhraní .NET API pro Windows Store apps  
 Tato část uvádí zbývající rozhraní API, která se v .NET Native nepodporují. Největší sada nepodporované rozhraní API je Windows Communication Foundation (WCF) rozhraní API.  
  
 **DataAnnotations (System.ComponentModel.DataAnnotations)**  
  
 Typy v <xref:System.ComponentModel.DataAnnotations> a <xref:System.ComponentModel.DataAnnotations.Schema> obory názvů v .NET Native nepodporují. Patří mezi ně následující typy, které se nacházejí v aplikacích .NET pro Windows Store pro Windows 8:  
  
||  
|-|  
|<xref:System.ComponentModel.DataAnnotations.AssociationAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ConcurrencyCheckAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.CustomValidationAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DataType?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DataTypeAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayColumnAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayFormatAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.EditableAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.EnumDataTypeAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.FilterUIHintAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.KeyAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.RangeAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.RegularExpressionAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.RequiredAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.StringLengthAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.TimestampAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.UIHintAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationContext?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationResult?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.Validator?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedOption?displayProperty=nameWithType>|  
  
 **Visual Basic**  
  
 Visual Basic se v .NET Native momentálně nepodporuje. Následující typy, které do <xref:Microsoft.VisualBasic> a <xref:Microsoft.VisualBasic.CompilerServices> obory názvů nejsou k dispozici v .NET Native:  
  
||  
|-|  
|<xref:Microsoft.VisualBasic.CallType?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.Constants?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Conversions?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.DesignerGeneratedAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.IncompleteInitialization?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl.ForLoopControl?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Operators?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.OptionCompareAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.OptionTextAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ProjectData?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.StandardModuleAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.StaticLocalInitFlag?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Utils?displayProperty=nameWithType>|  
  
 **Kontext odrazu (obor názvů System.Reflection.Context)**  
  
 <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> Třída není podporována v .NET Native.  
  
 **RTC (System.Net.Http.Rtc)**  
  
 <xref:System.Net.Http.RtcRequestFactory?displayProperty=nameWithType> Třída není podporována v .NET Native.  
  
 **Windows Communication Foundation (WCF) (System.ServiceModel.\*)**  
  
 Typy v [obory názvů System.ServiceModel.*](https://msdn.microsoft.com/library/gg145010.aspx) v .NET Native nepodporují. To zahrnuje následující typy:  
  
||  
|-|  
|<xref:System.ServiceModel.ActionNotSupportedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpMessageCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpSecurityMode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.BeginOperationDelegate?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.ChannelBase%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.EndOperationDelegate?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.InvokeAsyncCompletedEventArgs?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationState?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DataContractFormatAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DnsEndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointAddress?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointAddressBuilder?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EnvelopeVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ExceptionDetail?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultCode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultReason?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultReasonText?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.HttpBindingBase?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.HttpClientCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.HttpTransportSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IDefaultCommunicationTimeouts?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IExtension%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IExtensionCollection%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.InvalidMessageContractException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageBodyMemberAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageContractMemberAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageHeader%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageHeaderException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageSecurityOverTcp?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageSecurityVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetHttpBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetHttpMessageEncoding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetTcpSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationContext?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationContextScope?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationFormatStyle?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ProtocolException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.QuotaExceededException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServerTooBusyException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServiceActivationException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServiceKnownTypeAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.SpnEndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.TcpClientCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.TcpTransportSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.TransferMode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.UnknownMessageReceivedEventArgs?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.UpnEndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.AddressHeader?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.AddressHeaderCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.AddressingVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ChannelManagerBase?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ChannelParameterCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.CommunicationObject?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.FaultConverter?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpRequestMessageProperty?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpResponseMessageProperty?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpsTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IChannelFactory?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IChannelFactory%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IDuplexChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IDuplexSession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IDuplexSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IHttpCookieContainerManager?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IInputChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IInputSession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IInputSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IMessageProperty?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IOutputChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IOutputSession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IOutputSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IRequestSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ISession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.LocalClientSecuritySettings?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageBuffer?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageEncoder?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageEncoderFactory?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageHeader?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageHeaderInfo?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageHeaders?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageProperties?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageState?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.RequestContext?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.SecurityHeaderLayout?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TcpConnectionPoolSettings?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TransportSecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.WebSocketTransportSettings?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.WebSocketTransportUsage?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.ClientCredentials?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.FaultDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.FaultDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageBodyDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageDirection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageHeaderDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageHeaderDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePartDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePartDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePropertyDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePropertyDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.OperationDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.OperationDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.ClientOperation?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.ClientRuntime?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.DispatchOperation?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.DispatchRuntime?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.EndpointDispatcher?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IClientOperationSelector?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.BasicSecurityProfileVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.HttpDigestClientCredential?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecureConversationVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecurityAccessDeniedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecurityPolicyVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecurityVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.TrustVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.UserNamePasswordClientCredential?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.WindowsClientCredential?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.UserNameSecurityTokenParameters?displayProperty=nameWithType>|  
  
### <a name="differences-in-serializers"></a>Rozdíly v serializátorů  
 Tyto věci se týkají serializace a deserializace pomocí <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, a <xref:System.Xml.Serialization.XmlSerializer> třídy:  
  
-   V rozhraní .NET Native <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> selhání k serializaci nebo deserializaci odvozenou třídu, která má člena základní třídy, jejíž typ není kořenový typ serializace. Například v následujícím kódu pokusu o serializaci nebo deserializaci `Y` způsobí chybu:  
  
     [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]  
  
     Typ `InnerType` nezná serializátor, protože se během serializace procházet členy základní třídy.  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> selhání k serializaci třídy nebo struktury, která implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní. Například následující typy selhání k serializaci nebo deserializaci:  
  
  
  
-   <xref:System.Xml.Serialization.XmlSerializer> selže při serializaci následující hodnotu objektu, protože nemá specifické znalosti přesného typu objekt, který má být serializován:  
  
  
  
-   <xref:System.Xml.Serialization.XmlSerializer> k serializaci nebo deserializaci, pokud je typ serializovaný objekt se nezdaří <xref:System.Xml.XmlQualifiedName>.  
  
-   Všechny serializátory (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, a <xref:System.Xml.Serialization.XmlSerializer>) nepovedlo se generovat Serializační kód pro typ <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> nebo pro typ, který obsahuje <xref:System.Xml.Linq.XElement>. Místo toho zobrazí chyby sestavení.  
  
-   Následující konstruktory typů serializace nemusí fungovat podle očekávání:  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.DataContractSerializerSettings%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Xml.XmlDictionaryString%2CSystem.Xml.XmlDictionaryString%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.Json.DataContractJsonSerializerSettings%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.String%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlRootAttribute%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%2CSystem.Type%5B%5D%2CSystem.Xml.Serialization.XmlRootAttribute%2CSystem.String%29?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Serialization.XmlSerializer> selhání pro generování kódu pro typ, který obsahuje metody s některou z následujících atributů:  
  
    -   <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
-   <xref:System.Xml.Serialization.XmlSerializer> nebude respektovat <xref:System.Xml.Serialization.IXmlSerializable> vlastní serializace rozhraní. Pokud máte třídu, která implementuje toto rozhraní <xref:System.Xml.Serialization.XmlSerializer> bere v úvahu typ prostý původní typ objektu (POCO) CLR a serializuje pouze veřejné vlastností.  
  
-   Serializace prostý <xref:System.Exception> objektu, například následující příkaz, nebude fungovat s <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:  
  
  
  
<a name="VS"></a>   
## <a name="visual-studio-differences"></a>Visual Studio rozdíly  
 **Ladění a výjimek**  
  
 Pokud používáte aplikace kompilované pomocí .NET Native v ladicím programu, výjimkách first-chance jsou povolené pro následující typy výjimek:  
  
-   <xref:System.MemberAccessException>  
  
-   <xref:System.TypeAccessException>  
  
 **Vytváření aplikací**  
  
 Použít x86 sestavení nástroje, které se používají ve výchozím nastavení sada Visual Studio. Nedoporučujeme ale používat nástroje AMD64 MSBuild, které jsou součástí C:\Program Files (x86)\MSBuild\12.0\bin\amd64; To může způsobit problémy sestavení.  
  
 **Profilovací programy**  
  
-   Profiler procesoru Visual Studio a Profiler paměti XAML nezobrazují pouze můj kód správně.  
  
-   Profiler paměti XAML nebude přesně zobrazovat data spravované haldy.  
  
-   Profiler procesoru není správně identifikovat moduly a zobrazí předponou názvy funkcí.  
  
 **Projekty knihovny testů jednotek**  
  
 Povolení .NET Native v knihovna testů jednotek pro projekt aplikace Windows Store se nepodporuje a způsobí, že projekt tak, aby se nesestaví.  
  
## <a name="see-also"></a>Viz také  
 [Začínáme](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [.NET pro Windows Store apps – přehled](https://msdn.microsoft.com/library/windows/apps/br230302.aspx)  
 [Podpora pro aplikace pro web Windows Store a prostředí Windows Runtime v rozhraní .NET Framework](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
