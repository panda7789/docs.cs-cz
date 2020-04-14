---
title: Migrace aplikace pro Windows Store do .NET Native
ms.date: 03/30/2017
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
ms.openlocfilehash: 36f9ac4647b349ff379869f3415a5fb9e55228e3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81241942"
---
# <a name="migrate-your-windows-store-app-to-net-native"></a>Migrace aplikace pro Windows Store do nativní ho storu .NET

.NET Native poskytuje statickou kompilaci aplikací ve Windows Storu nebo v počítači vývojáře. To se liší od dynamické kompilace prováděné pro aplikace pro Windows Store kompilátorem just-in-time (JIT) nebo [native image generator (Ngen.exe)](../tools/ngen-exe-native-image-generator.md) v zařízení. Navzdory rozdílům se nativní rozhraní .NET snaží zachovat kompatibilitu s [rozhraním .NET pro aplikace pro Windows Store](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29). Z větší části věci, které fungují na .NET pro aplikace pro Windows Store také pracovat s .NET Native.  V některých případech však může dojít ke změnám chování. Tento dokument popisuje tyto rozdíly mezi standardní .NET pro aplikace pro Windows Store a .NET Native v následujících oblastech:

- [Obecné rozdíly za běhu](#Runtime)

- [Rozdíly dynamického programování](#Dynamic)

- [Další rozdíly související s reflexí](#Reflection)

- [Nepodporované scénáře a api](#Unsupported)

- [Rozdíly v sadě Visual Studio](#VS)

<a name="Runtime"></a>

## <a name="general-runtime-differences"></a>Obecné rozdíly za běhu

- Výjimky, jako <xref:System.TypeLoadException>je například , které jsou vyvolány kompilátorem JIT při spuštění aplikace na clr (COMMON Language) obecně za následek chyby v době kompilace při zpracování .NET Native.

- Nevolejte metodu <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> z vlákna uživatelského rozhraní aplikace. To může mít za následek zablokování na .NET Native.

- Nespoléhejte na statické třídy konstruktoru vyvolání řazení. V .NET Native pořadí vyvolání se liší od pořadí na standardní runtime. (I při standardním běhu za běhu byste neměli spoléhat na pořadí provádění konstruktorů statické třídy.)

- Nekonečné opakování bez volání `while(true);`(například) v libovolném vlákně může zastavit aplikaci. Podobně velké nebo nekonečné čekání může zastavit aplikaci.

- Některé obecné inicializační cykly nevyvolání výjimky v .NET Native. Například následující kód vyvolá <xref:System.TypeLoadException> výjimku na standardní CLR. V .NET Native, není.

  [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]

- V některých případech .NET Native poskytuje různé implementace knihoven tříd rozhraní .NET Framework. Objekt vrácený z metody bude vždy implementovat členy vráceného typu. Však vzhledem k tomu, že jeho zálohování implementace je jiný, nemusí být možné přetypovat do stejné sady typů, jako byste mohli na jiných platformách rozhraní .NET Framework. Například v některých případech nemusí být možné <xref:System.Collections.Generic.IEnumerable%601> přetypovat objekt <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> rozhraní <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> `T[]`vrácené metody, jako je například nebo na .

- Mezipaměť WinInet není ve výchozím nastavení povolena v rozhraní .NET pro aplikace pro Windows Store, ale je na nativní .NET. To zlepšuje výkon, ale má pracovní sadu důsledky. Není nutná žádná akce vývojáře.

<a name="Dynamic"></a>

## <a name="dynamic-programming-differences"></a>Rozdíly dynamického programování

.NET Native staticky odkazy v kódu z rozhraní .NET Framework, aby kód aplikace místní pro maximální výkon. Binární velikosti však musí zůstat malé, takže nelze dovést celý rozhraní .NET Framework. Nativní kompilátor .NET řeší toto omezení pomocí reduktoru závislostí, který odebere odkazy na nepoužívaný kód. Nativní .NET však nemusí udržovat nebo generovat některé informace o typu a kód, pokud tyto informace nelze odvodit staticky v době kompilace, ale místo toho je načten dynamicky za běhu.

Nativní rozhraní .NET umožňuje reflexi a dynamické programování. Však ne všechny typy mohou být označeny pro reflexi, protože by to generované velikostkódu příliš velké (zejména proto, že odráží na veřejné rozhraní API v rozhraní .NET Framework je podporována). Nativní kompilátor .NET provádí inteligentní volby o tom, které typy by měly podporovat reflexi a udržuje metadata a generuje kód pouze pro tyto typy.

Například datová vazba vyžaduje, aby aplikace mohla mapovat názvy vlastností na funkce. V rozhraní .NET pro aplikace pro Windows Store používá běžný jazykový běh automaticky reflexe k poskytování této funkce pro spravované typy a veřejně dostupné nativní typy. V nativním rozhraní .NET kompilátor automaticky obsahuje metadata pro typy, ke kterým vázáte data.

Kompilátor .NET Native může také zpracovávat <xref:System.Collections.Generic.List%601> běžně <xref:System.Collections.Generic.Dictionary%602>používané obecné typy, jako jsou a , které fungují bez nutnosti jakékoli rady nebo direktivy. Klíčové slovo [dynamické](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) je také podporováno v určitých mezích.

> [!NOTE]
> Při přenosu aplikace do nativního rozhraní .NET byste měli důkladně otestovat všechny cesty dynamického kódu.

Výchozí konfigurace pro .NET Native je dostatečná pro většinu vývojářů, ale někteří vývojáři mohou chtít doladit své konfigurace pomocí souboru direktiv runtime (.rd.xml). Kromě toho v některých případech kompilátor .NET Native není schopen určit, která metadata musí být k dispozici pro reflexi a spoléhá na rady, zejména v následujících případech:

- Některé konstrukce <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> jako <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> a nelze určit staticky.

- Vzhledem k tomu, že kompilátor nemůže určit instance, obecný typ, který chcete uvažovat, musí být určen direktivy za běhu. Není to jen proto, že musí být zahrnut veškerý kód, ale protože reflexe obecných typů může tvořit nekonečný cyklus (například když je obecná metoda vyvolána u obecného typu).

> [!NOTE]
> Direktivy runtime jsou definovány v souboru direktiv runtime (.rd.xml). Obecné informace o použití tohoto souboru naleznete v [tématu Začínáme](getting-started-with-net-native.md). Informace o direktivách runtime naleznete v [tématu Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).

.NET Native také obsahuje profilovací nástroje, které pomáhají vývojáři určit, které typy mimo výchozí sadu by měly podporovat reflexi.

<a name="Reflection"></a>

## <a name="other-reflection-related-differences"></a>Další rozdíly související s reflexí

Existuje řada dalších rozdílů v chování souvisejících s odrazem mezi rozhraním .NET pro aplikace pro Windows Store a nativním rozhraním .NET.

V nativním rozhraní .NET:

- Privátní reflexe nad typy a členy v knihovně tříd rozhraní .NET Framework není podporována. Můžete však uvažovat o vlastních soukromých typech a členech, stejně jako o typech a členech v knihovnách třetích stran.

- Vlastnost <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> správně `false` vrátí <xref:System.Reflection.ParameterInfo> pro objekt, který představuje vrácenou hodnotu. V rozhraní .NET pro aplikace `true`pro Windows Store vrátí . Zprostředkující jazyk (IL) nepodporuje přímo a tlumočení je ponecháno na jazyku.

- Veřejné členy <xref:System.RuntimeFieldHandle> na <xref:System.RuntimeMethodHandle> a struktury nejsou podporovány. Tyto typy jsou podporovány pouze pro LINQ, stromy výrazů a inicializaci statického pole.

- <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType>a <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> zahrnout skryté členy do základních tříd a proto mohou být přepsány bez explicitních přepsání. To platí také pro jiné metody [RuntimeReflectionExtensions.GetRuntime*.](xref:System.Reflection.RuntimeReflectionExtensions)

- <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType>a <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> neselhat při pokusu o vytvoření určité kombinace (například pole byrefs).

- Reflexe nelze použít k vyvolání členů, které mají parametry ukazatele.

- Odraz nelze použít k získání nebo nastavení pole ukazatele.

- Pokud je počet argumentů chybný a typ jednoho z argumentů je <xref:System.ArgumentException> nesprávný, nativní .NET vyvolá místo <xref:System.Reflection.TargetParameterCountException>.

- Binární serializace výjimek není obecně podporována. V důsledku toho mohou být do slovníku <xref:System.Exception.Data%2A?displayProperty=nameWithType> přidány neserializovatelné objekty.

<a name="Unsupported"></a>

## <a name="unsupported-scenarios-and-apis"></a>Nepodporované scénáře a api

V následujících částech jsou uvedeny nepodporované scénáře a api pro obecný vývoj, interop a technologie, jako je httpclient a Windows Communication Foundation (WCF):

- [Obecný vývoj](#General)

- [HttpClient](#HttpClient)

- [Interop](#Interop)

- [Nepodporovaná api](#APIs)

<a name="General"></a>

### <a name="general-development-differences"></a>Obecné rozdíly ve vývoji

**Typy hodnot**

- Pokud přepíšete <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> metody a pro typ hodnoty, nevolejte implementace základní třídy. V rozhraní .NET pro aplikace pro Windows Store tyto metody spoléhají na reflexi. V době kompilace .NET Native generuje implementaci, která nespoléhá na odraz za běhu. To znamená, že pokud tyto dvě metody nepřepíšete, budou fungovat podle očekávání, protože nativní rozhraní .NET generuje implementaci v době kompilace. Však přepsání těchto metod, ale volání implementace základní třídy výsledky výjimky.

- Typy hodnot větší než jeden megabajt nejsou podporovány.

- Typy hodnot nemůže mít konstruktor bez parametrů v .NET Native. (C# a Visual Basic zakázat konstruktory bez parametrů na typy hodnot. Ty však mohou být vytvořeny v IL.)

**Pole**

- Pole s nižší mezí než nula nejsou podporovány. Obvykle tato pole jsou vytvořeny voláním <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> přetížení.

- Dynamické vytváření vícerozměrných polí není podporováno. Tato pole jsou obvykle vytvořeny voláním <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> přetížení metody, `lengths` která obsahuje parametr, nebo voláním <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> metody.

- Vícerozměrná pole, která mají čtyři nebo více dimenzí, nejsou podporována; to znamená, <xref:System.Array.Rank%2A?displayProperty=nameWithType> že jejich hodnota vlastnosti je čtyři nebo vyšší. Místo toho použijte [zubaté pole](../../csharp/programming-guide/arrays/jagged-arrays.md) (pole polí). Například `array[x,y,z]` je neplatný, ale `array[x][y][z]` není.

- Odchylka pro vícerozměrná pole není podporována a způsobuje výjimku <xref:System.InvalidCastException> za běhu.

**Obecné typy**

- Nekonečné rozšíření obecného typu má za následek chybu kompilátoru. Například tento kód se nepodaří zkompilovat:

  [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]

**Ukazatele**

- Pole ukazatelů nejsou podporována.

- Odraz nelze použít k získání nebo nastavení pole ukazatele.

**Serializace**

Atribut <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> není podporován. Místo <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> toho použijte atribut.

**Materiály**

Použití lokalizovaných prostředků <xref:System.Diagnostics.Tracing.EventSource> s třídou není podporováno. Vlastnost <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> nedefinuje lokalizované prostředky.

**Delegáty**

`Delegate.BeginInvoke`a `Delegate.EndInvoke` nejsou podporovány.

**Ostatní rozhraní API**

- Vlastnost [TypeInfo.GUID](xref:System.Type.GUID) vyvolá <xref:System.PlatformNotSupportedException> výjimku, <xref:System.Runtime.InteropServices.GuidAttribute> pokud atribut není použit pro typ. Identifikátor GUID se používá především pro podporu com.

- Metoda <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> správně analyzuje řetězce, které obsahují krátká data v .NET Native. Nezachovává však kompatibilitu se změnami analýzy data a času popsanými v článcích znalostní báze [KB2803771](https://support.microsoft.com/kb/2803771) a [KB2803755](https://support.microsoft.com/kb/2803755).

- <xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType>`("E")` je správně zaokrouhlena v nativním rozhraní .NET. V některých verzích CLR je výsledný řetězec zkrácen namísto zaokrouhlení.

<a name="HttpClient"></a>

### <a name="httpclient-differences"></a>Rozdíly mezi klienty HttpClient

V .NET Native <xref:System.Net.Http.HttpClientHandler> třída interně používá WinINet (prostřednictvím <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> třídy) namísto <xref:System.Net.WebRequest> třídy a <xref:System.Net.WebResponse> používané ve standardním rozhraní .NET pro aplikace pro Windows Store.  WinINet nepodporuje všechny možnosti konfigurace, které <xref:System.Net.Http.HttpClientHandler> třída podporuje.  Výsledek:

- Některé vlastnosti schopností <xref:System.Net.Http.HttpClientHandler> `false` při návratu na .NET `true` Native, zatímco se vrátí ve standardní .NET pro aplikace pro Windows Store.

- Některé přistupující objekty vlastností `get` konfigurace vždy vrátí pevnou hodnotu na .NET Native, která se liší od výchozí konfigurovatelné hodnoty v rozhraní .NET pro aplikace pro Windows Store.

Některé další rozdíly chování jsou zahrnuty v následujících podsekcích.

**Proxy server**

Třída <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> nepodporuje konfiguraci nebo přepsání proxy serveru na základě požadavku.  To znamená, že všechny požadavky na .NET Native používají systémově nakonfigurovaný <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> proxy server nebo žádný proxy server, v závislosti na hodnotě vlastnosti.  V rozhraní .NET pro aplikace pro Windows <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> Store je proxy server definován vlastností.  Na .NET Native, <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> nastavení na `null` hodnotu <xref:System.PlatformNotSupportedException> jinou než vyvolá výjimku.  Vlastnost <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> vrátí `false` na .NET Native, `true` vzhledem k tomu, že se vrátí ve standardním rozhraní .NET Framework pro aplikace pro Windows Store.

**Automatické přesměrování**

Třída <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> neumožňuje konfiguraci maximálního počtu automatických přesměrování.  Hodnota vlastnosti <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> je ve výchozím nastavení 50 ve standardní mj. Na .NET Native hodnota této vlastnosti je 10 a pokus <xref:System.PlatformNotSupportedException> u jeho změny vyvolá výjimku.  Vlastnost <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> vrátí `false` na .NET Native, `true` vzhledem k tomu, že se vrátí v .NET pro aplikace pro Windows Store.

**Automatická dekomprese**

Rozhraní .NET pro aplikace pro <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> Windows <xref:System.Net.DecompressionMethods.Deflate>Store <xref:System.Net.DecompressionMethods.GZip>umožňuje <xref:System.Net.DecompressionMethods.Deflate> <xref:System.Net.DecompressionMethods.GZip>nastavit <xref:System.Net.DecompressionMethods.None>vlastnost na , , jak nebo .  Nativní rozhraní <xref:System.Net.DecompressionMethods.Deflate> .NET <xref:System.Net.DecompressionMethods.GZip>podporuje <xref:System.Net.DecompressionMethods.None>pouze společně s rozhraním . nebo .  Pokuso o <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> nastavení <xref:System.Net.DecompressionMethods.Deflate> vlastnosti buď nebo <xref:System.Net.DecompressionMethods.GZip> samostatně <xref:System.Net.DecompressionMethods.Deflate> <xref:System.Net.DecompressionMethods.GZip>tiše nastaví na obě a .

**Soubory cookie**

Zpracování souborů cookie se <xref:System.Net.Http.HttpClient> provádí současně a WinINet.  Cookies z <xref:System.Net.CookieContainer> těchto souborů jsou kombinovány se soubory cookie v mezipaměti souborů cookie WinINet.  Odebrání souboru <xref:System.Net.CookieContainer> cookie <xref:System.Net.Http.HttpClient> z brání odeslání souboru cookie, ale pokud soubor cookie byl již vidět WinINet, a soubory cookie nebyly odstraněny uživatelem, WinINet odešle.  Není možné programově odebrat soubor cookie z WinINet <xref:System.Net.Http.HttpClient> <xref:System.Net.Http.HttpClientHandler>pomocí <xref:System.Net.CookieContainer> rozhraní , nebo API.  Nastavení <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> vlastnosti `false` způsobí <xref:System.Net.Http.HttpClient> pouze zastavit odesílání souborů cookie; WinINet může stále obsahovat své cookies v žádosti.

**Přihlašovací údaje**

V rozhraní .NET pro <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> aplikace <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> pro Windows Store fungují vlastnosti a vlastnosti nezávisle.  Navíc <xref:System.Net.Http.HttpClientHandler.Credentials%2A> vlastnost přijímá libovolný objekt, který <xref:System.Net.ICredentials> implementuje rozhraní.  V nativní .NET <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> nastavení `true` vlastnosti způsobí, že <xref:System.Net.Http.HttpClientHandler.Credentials%2A> vlastnost stane `null`.  Kromě toho <xref:System.Net.Http.HttpClientHandler.Credentials%2A> lze vlastnost nastavit `null`pouze <xref:System.Net.CredentialCache.DefaultCredentials%2A>na , nebo <xref:System.Net.NetworkCredential>objekt typu .  Přiřazení jakýkoli <xref:System.Net.ICredentials> jiný objekt, nejoblíbenější z <xref:System.Net.CredentialCache>nich <xref:System.Net.Http.HttpClientHandler.Credentials%2A> je , <xref:System.PlatformNotSupportedException>vlastnost hází .

**Jiné nepodporované nebo nekonfigurovatelné funkce**

V nativním rozhraní .NET:

- Hodnota vlastnosti <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> je <xref:System.Net.Http.ClientCertificateOption.Automatic>vždy .  V rozhraní .NET pro aplikace <xref:System.Net.Http.ClientCertificateOption.Manual>pro Windows Store je výchozí hodnota .

- Vlastnost <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> není konfigurovatelná.

- Vlastnost <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> je `true`vždy .  V rozhraní .NET pro aplikace `false`pro Windows Store je výchozí hodnota .

- Záhlaví `SetCookie2` v odpovědích je ignorováno jako zastaralé.

<a name="Interop"></a>
### <a name="interop-differences"></a>Interop rozdíly
 **Zastaralá api**

 Počet zřídka používaných api pro interoperabilitu se spravovaným kódem byly zastaralé. Při použití s .NET Native, tato <xref:System.NotImplementedException> <xref:System.PlatformNotSupportedException> rozhraní API může vyvolat nebo výjimku nebo způsobit chybu kompilátoru. V rozhraní .NET pro aplikace pro Windows Store jsou tato rozhraní API označena jako zastaralá, i když jejich volání generuje upozornění kompilátoru spíše než chybu kompilátoru.

 Zastaralá api pro `VARIANT` zařazování zahrnují:

- <xref:System.Runtime.InteropServices.BStrWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VariantWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VarEnum?displayProperty=nameWithType>

 <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType>je podporována, ale vyvolá výjimku v některých scénářích, například při použití s [variantami IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) nebo byref.

 Mezi zastaralá api pro podporu [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) patří:

- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>

Mezi zastaralá api pro klasické události COM patří:

- <xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>

Zastaralá rozhraní API <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> v rozhraní, která nejsou v nativním rozhraní .NET podporována, zahrnují:

- <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType>(všichni členové)
- <xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType>(všichni členové)
- <xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType>(všichni členové)
- <xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=fullName>

Mezi další nepodporované funkce interop patří:

- <xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType>(všichni členové)
- <xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType>(všichni členové)
- <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.AnsiBStr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.AsAny?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.CustomMarshaler?displayProperty=fullName>

 Zřídka používané zařazování API:

- <xref:System.Runtime.InteropServices.Marshal.ReadByte%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt16%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt32%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt64%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadIntPtr%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteByte%28System.Object%2CSystem.Int32%2CSystem.Byte%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt16%28System.Object%2CSystem.Int32%2CSystem.Int16%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt32%28System.Object%2CSystem.Int32%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt64%28System.Object%2CSystem.Int32%2CSystem.Int64%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteIntPtr%28System.Object%2CSystem.Int32%2CSystem.IntPtr%29?displayProperty=fullName>

 **Vyvolání platformy a kompatibilita interopu COM**

 Většina scénářů vyvolání platformy a interop com jsou stále podporovány v .NET Native. Zejména je podporována veškerá interoperabilita s windows runtime (WinRT) API a všechny zařazování požadované pro prostředí Windows Runtime je podporována. To zahrnuje zařazování podporu pro:

- Pole (včetně <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)

- `BStr`

- Delegáty

- Řetězce (Unicode, Ansi a HSTRING)

- Structs`byref` ( `byval`a )

- Sjednocení

- Popisovače Win32

- Všechny konstrukce WinRT

- Částečná podpora pro zařazování typů variant. Podporované systémy:

  - <xref:System.Boolean>

  - <xref:System.Byte>

  - <xref:System.Decimal>

  - <xref:System.Double>

  - <xref:System.Int16>

  - <xref:System.Int32>

  - <xref:System.Int64>

  - <xref:System.SByte>

  - <xref:System.Single>

  - <xref:System.UInt16>

  - <xref:System.UInt32>

  - <xref:System.UInt64>

  - `BStr`

  - [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)

Nativní rozhraní .NET však nepodporuje následující:

- Použití klasických událostí com

- Implementace rozhraní <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> spravovaného typu

- Implementace rozhraní [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) na spravovaném <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> typu prostřednictvím atributu. Všimněte si však, že nelze `IDispatch`volat objekty COM prostřednictvím a spravovaný objekt nelze implementovat `IDispatch`.

Použití reflexe k vyvolání metody vyvolání platformy není podporováno. Toto omezení můžete obejít zabalením volání metody v jiné metodě a pomocí reflexe místo toho volat obálku.

<a name="APIs"></a>

### <a name="other-differences-from-net-apis-for-windows-store-apps"></a>Další rozdíly oproti rozhraním API .NET pro aplikace pro Windows Store

V této části jsou uvedeny zbývající rozhraní API, která nejsou podporována v nativním rozhraní .NET. Největší sada nepodporovaných api jsou Windows Communication Foundation (WCF) API.

**DataAnnotations (System.ComponentModel.DataAnnotations)**

Typy v <xref:System.ComponentModel.DataAnnotations> oborech názvů a <xref:System.ComponentModel.DataAnnotations.Schema> nejsou v nativním rozhraní .NET podporovány. Patří mezi ně následující typy, které jsou k dispozici v rozhraní .NET pro aplikace pro Windows Store pro Windows 8:

- <xref:System.ComponentModel.DataAnnotations.AssociationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ConcurrencyCheckAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.CustomValidationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DataType?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DataTypeAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayColumnAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayFormatAttribute>
- <xref:System.ComponentModel.DataAnnotations.EditableAttribute>
- <xref:System.ComponentModel.DataAnnotations.EnumDataTypeAttribute>
- <xref:System.ComponentModel.DataAnnotations.FilterUIHintAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.KeyAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RangeAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RegularExpressionAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RequiredAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.StringLengthAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.TimestampAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.UIHintAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationContext?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationResult?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Validator?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedOption?displayProperty=nameWithType>

 **Visual Basic**

Visual Basic není aktuálně podporován v .NET Native. Následující typy v <xref:Microsoft.VisualBasic> <xref:Microsoft.VisualBasic.CompilerServices> oborech názvů a nejsou v nativním rozhraní .NET k dispozici:

- <xref:Microsoft.VisualBasic.CallType?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Constants?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.HideModuleNameAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Conversions?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.DesignerGeneratedAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.IncompleteInitialization?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl.ForLoopControl?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Operators?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.OptionCompareAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.OptionTextAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ProjectData?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.StandardModuleAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.StaticLocalInitFlag?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Utils?displayProperty=nameWithType>

**Kontext reflexe (system.reflection.context obor názvů)**

Třída <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> není podporována v .NET Native.

**RTC (System.Net.Http.Rtc)**

Třída `System.Net.Http.RtcRequestFactory` není podporována v .NET Native.

**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**

Typy v [oborech názvů System.ServiceModel.*](xref:System.ServiceModel) nejsou v nativním rozhraní .NET podporovány. Patří mezi ně následující typy:

- <xref:System.ServiceModel.ActionNotSupportedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpMessageCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpSecurityMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.BeginOperationDelegate?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.ChannelBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.EndOperationDelegate?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.InvokeAsyncCompletedEventArgs?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationState?displayProperty=nameWithType>
- <xref:System.ServiceModel.DataContractFormatAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.DnsEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointAddress?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointAddressBuilder?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType>
- <xref:System.ServiceModel.EnvelopeVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.ExceptionDetail?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultCode?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultReason?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultReasonText?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpBindingBase?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpClientCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpTransportSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType>
- <xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.IDefaultCommunicationTimeouts?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtension%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtensionCollection%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.InvalidMessageContractException?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageBodyMemberAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageContractMemberAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageHeader%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageHeaderException?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityOverTcp?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetHttpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetHttpMessageEncoding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetTcpSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContextScope?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationFormatStyle?displayProperty=nameWithType>
- <xref:System.ServiceModel.ProtocolException?displayProperty=nameWithType>
- <xref:System.ServiceModel.QuotaExceededException?displayProperty=nameWithType>
- <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServerTooBusyException?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceActivationException?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceKnownTypeAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.SpnEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpClientCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpTransportSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.TransferMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.UnknownMessageReceivedEventArgs?displayProperty=nameWithType>
- <xref:System.ServiceModel.UpnEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressHeader?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressingVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ChannelManagerBase?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ChannelParameterCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CommunicationObject?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.FaultConverter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpRequestMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpResponseMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannelFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IHttpCookieContainerManager?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IRequestSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ISession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageBuffer?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncoder?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncoderFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeader?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeaderInfo?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeaders?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageProperties?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageState?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.RequestContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SecurityHeaderLayout?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WebSocketTransportSettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WebSocketTransportUsage?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ClientCredentials?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.FaultDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.FaultDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageBodyDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDirection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageHeaderDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageHeaderDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePartDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePartDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePropertyDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePropertyDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.OperationDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.OperationDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.ClientOperation?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.ClientRuntime?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.DispatchOperation?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.DispatchRuntime?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.EndpointDispatcher?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientOperationSelector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.BasicSecurityProfileVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecureConversationVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityAccessDeniedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityPolicyVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.TrustVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.WindowsClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.UserNameSecurityTokenParameters?displayProperty=nameWithType>

### <a name="differences-in-serializers"></a>Rozdíly v serializátorech

Následující rozdíly se týkají serializace a <xref:System.Runtime.Serialization.DataContractSerializer>deserializace pomocí , <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>a <xref:System.Xml.Serialization.XmlSerializer> tříd:

- V .NET <xref:System.Runtime.Serialization.DataContractSerializer> Native <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> a nepodaří serializovat nebo rekonstruovat odvozenou třídu, která má člen základní třídy, jehož typ není typ kořenové serializace. Například v následujícím kódu, pokus o serializaci nebo `Y` deserializovat má za následek chybu:

  [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]

  Typ `InnerType` není znám serializátoru, protože členy základní třídy nejsou provázány během serializace.

- <xref:System.Runtime.Serialization.DataContractSerializer>a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nepodaří serializovat třídu nebo strukturu, která implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní. Například následující typy se nezdaří serializovat nebo rekonstruovat:

- <xref:System.Xml.Serialization.XmlSerializer>nepodaří serializovat následující hodnotu objektu, protože nezná přesný typ objektu, který má být serializován:

- <xref:System.Xml.Serialization.XmlSerializer>nepodaří serializovat nebo rekonstruovat, pokud je <xref:System.Xml.XmlQualifiedName>typ serializovaného objektu .

- Všechny serializátory <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>( <xref:System.Xml.Serialization.XmlSerializer><xref:System.Runtime.Serialization.DataContractSerializer>, , a ) <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> nepodaří generovat kód <xref:System.Xml.Linq.XElement>serializace pro typ nebo pro typ, který obsahuje . Místo toho zobrazují chyby v době sestavení.

- Následující konstruktory serializace typy nejsou zaručena pracovat podle očekávání:

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.DataContractSerializerSettings%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Xml.XmlDictionaryString%2CSystem.Xml.XmlDictionaryString%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.Json.DataContractJsonSerializerSettings%29>

  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.String%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlRootAttribute%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%2CSystem.Type%5B%5D%2CSystem.Xml.Serialization.XmlRootAttribute%2CSystem.String%29>

- <xref:System.Xml.Serialization.XmlSerializer>nepodaří generovat kód pro typ, který má metody přiřazené s některou z následujících atributů:

  - <xref:System.Runtime.Serialization.OnSerializingAttribute>

  - <xref:System.Runtime.Serialization.OnSerializedAttribute>

  - <xref:System.Runtime.Serialization.OnDeserializingAttribute>

  - <xref:System.Runtime.Serialization.OnDeserializedAttribute>

- <xref:System.Xml.Serialization.XmlSerializer>nerespektuje <xref:System.Xml.Serialization.IXmlSerializable> vlastní serializační rozhraní. Pokud máte třídu, která implementuje toto rozhraní, <xref:System.Xml.Serialization.XmlSerializer> považuje typ prostého starého typu CLR (POCO) a serializuje pouze jeho veřejné vlastnosti.

- Serializace prostého <xref:System.Exception> objektu nefunguje <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>dobře s a .

<a name="VS"></a>

## <a name="visual-studio-differences"></a>Rozdíly v sadě Visual Studio

**Výjimky a ladění**

Při spuštění aplikací zkompilovaných pomocí .NET Native v ladicím programu jsou povoleny výjimky první šance pro následující typy výjimek:

- <xref:System.MemberAccessException>

- <xref:System.TypeAccessException>

**Vytváření aplikací**

Použijte nástroje sestavení x86, které se používají ve výchozím nastavení visual studio. Nedoporučujeme používat nástroje AMD64 MSBuild, které se nacházejí v c:\programových souborech (x86)\MSBuild\12.0\bin\amd64; Ty mohou způsobit problémy sestavení.

**Profilovací programy**

- Profiler procesoru Visual Studio a profiler paměti XAML nezobrazují just-my-code správně.

- Paměť Ový profilování XAML nezobrazuje přesně spravovaná data haldy.

- Profiler procesoru neidentifikuje správně moduly a zobrazuje předponové názvy funkcí.

**Projekty knihovny testování částí**

Povolení nativního rozhraní .NET v knihovně testování částí pro projekt aplikací pro Windows Store není podporováno a způsobí, že se projekt nepodaří sestavit.

## <a name="see-also"></a>Viz také

- [Začínáme](getting-started-with-net-native.md)
- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Přehled aplikace .NET pro Windows Store](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29)
- [Podpora pro aplikace pro web Windows Store a prostředí Windows Runtime v rozhraní .NET Framework](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
