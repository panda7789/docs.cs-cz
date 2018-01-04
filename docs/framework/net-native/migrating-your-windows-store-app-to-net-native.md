---
title: Migrace aplikace pro Windows Store do .NET Native
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
caps.latest.revision: "29"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ce23d66f79f94af74250cff137499f6c8b1582ac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="migrating-your-windows-store-app-to-net-native"></a>Migrace aplikace pro Windows Store do .NET Native
[!INCLUDE[net_native](../../../includes/net-native-md.md)]poskytuje statické kompilace aplikací ve službě Windows Store nebo na počítači pro vývojáře. Tím se liší od dynamická kompilace provádí kompilátoru v běhu (JIT) pro aplikace Windows Store nebo [generátor (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) na zařízení. Bez ohledu rozdíly [!INCLUDE[net_native](../../../includes/net-native-md.md)] pokusí zachování kompatibility s [aplikace .NET pro Windows Store](http://msdn.microsoft.com/library/windows/apps/br230302.aspx). Ve většině případů věcí, které fungují v aplikacích .NET pro Windows Store se taky pracovat s [!INCLUDE[net_native](../../../includes/net-native-md.md)].  Ale v některých případech se můžete setkat s nějaké změny. Tento dokument popisuje tyto rozdíly mezi standardní aplikace .NET pro Windows Store a [!INCLUDE[net_native](../../../includes/net-native-md.md)] v těchto oblastech:  
  
-   [Rozdíly obecné runtime](#Runtime)  
  
-   [Dynamické programování rozdílů](#Dynamic)  
  
-   [Další související reflexe rozdíly](#Reflection)  
  
-   [Nepodporované scénáře a rozhraní API](#Unsupported)  
  
-   [Rozdíly Visual Studio](#VS)  
  
<a name="Runtime"></a>   
## <a name="general-runtime-differences"></a>Rozdíly obecné runtime  
  
-   Výjimky, jako například <xref:System.TypeLoadException>, která jsou vyvolané kompilátoru za běhu, když aplikace běží na nejběžnější language runtime (CLR) obecně mít za následek chyby při kompilaci při zpracování [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
-   Nemůžete volat <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> metoda z vlákna uživatelského rozhraní aplikace. Může dojít k zablokování na [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
-   Nemusíte spoléhat na statická třída konstruktor volání řazení. V [!INCLUDE[net_native](../../../includes/net-native-md.md)], se liší od pořadí na standardní runtime pořadí volání. (I s standardní modul runtime, neměli byste tedy spoléhat v řádu provádění statická třída konstruktory.)  
  
-   Nekonečné opakování ve smyčce bez provedení volání (například `while(true);`) na všechny přístup z více vláken, mohou způsobit aplikace zastavení. Podobně velké soubory nebo nekonečné počká, mohou způsobit aplikace zastavení.  
  
-   Některé obecné inicializace cykly nemáte generování výjimek [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Například následující kód vrátí <xref:System.TypeLoadException> výjimky na standardní CLR. V [!INCLUDE[net_native](../../../includes/net-native-md.md)], nepodporuje.  
  
     [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]  
  
-   V některých případech [!INCLUDE[net_native](../../../includes/net-native-md.md)] poskytuje různé implementace knihovny tříd rozhraní .NET Framework. Objekt, vrátí metoda bude vždy implementovat členy vráceného typu. Ale vzhledem k tomu, že jeho implementace zálohování se liší, nelze přetypovat na stejnou sadu typy, jako by na jiných platformách rozhraní .NET Framework. Například v některých případech nelze přetypovat <xref:System.Collections.Generic.IEnumerable%601> rozhraní objektů vrácené objektem metody, jako <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> nebo <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> k `T[]`.  
  
-   Mezipaměť WinInet není povolená ve výchozím nastavení pro aplikace .NET pro Windows Store, ale je na [!INCLUDE[net_native](../../../includes/net-native-md.md)]. To zvyšuje výkon, ale má pracujícího sadu dopad. Není nutná žádná akce developer.  
  
<a name="Dynamic"></a>   
## <a name="dynamic-programming-differences"></a>Dynamické programování rozdílů  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)]staticky odkazuje kód rozhraní .NET Framework, chcete-li kód místní aplikace pro maximální výkon. Binární velikosti je však nutné zůstávají malé, takže celý rozhraní .NET Framework není možné připojit v. [!INCLUDE[net_native](../../../includes/net-native-md.md)] Kompilátoru přeloží toto omezení pomocí reduktorem závislost, která odebere odkazy na nepoužívané kódu. Ale [!INCLUDE[net_native](../../../includes/net-native-md.md)] nemusí údržbě nebo při informace nelze odvodit staticky v době kompilace, ale místo toho se dynamicky načíst za běhu generovat některé informace o typu a kódu.  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)]Povolit reflexe a dynamické programování. Ne všechny typy lze však označit pro reflexe, protože by velikost generovaného kódu příliš velký (hlavně proto odrážející na veřejné rozhraní API v rozhraní .NET Framework je podporuje). [!INCLUDE[net_native](../../../includes/net-native-md.md)] Kompilátoru umožňuje inteligentní možností, které typy by měly podporovat reflexe, a udržuje metadata a generuje kód jenom pro tyto typy.  
  
 Datová vazba například vyžaduje aplikaci, abyste mohli mapovat názvy vlastností na funkce. V aplikacích .NET pro Windows Store modul common language runtime automaticky používá reflexe zajišťující tuto možnost pro veřejně dostupné typy nativní a spravované typy. V [!INCLUDE[net_native](../../../includes/net-native-md.md)], kompilátor automaticky zahrne metadata pro typy, pro které vázat data.  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] Kompilátoru může také zpracovat běžně používané obecné typy, jako <xref:System.Collections.Generic.List%601> a <xref:System.Collections.Generic.Dictionary%602>, které pracovní bez nutnosti jakékoli pomocné parametry nebo direktivy. [Dynamické](~/docs/csharp/language-reference/keywords/dynamic.md) – klíčové slovo je podporováno také v rámci určitá omezení.  
  
> [!NOTE]
>  Měli byste otestovat všechny cesty kódu dynamické důkladně při portování aplikaci [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
 Výchozí konfiguraci pro [!INCLUDE[net_native](../../../includes/net-native-md.md)] je dostatečné pro většinu vývojáři, ale někteří vývojáři chtít jemnou optimalizace jejich konfigurace počítače pomocí direktivy modulu runtime (. rd.xml) souboru. Kromě toho, v některých případech [!INCLUDE[net_native](../../../includes/net-native-md.md)] kompilátoru se nepodařilo určit, které metadata musí být k dispozici pro reflexi a spoléhá na pomocné parametry, zejména v následujících případech:  
  
-   Některé konstrukce, jako <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> a <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> nelze určit staticky.  
  
-   Protože kompilátor nemůže zjistit, konkretizací, obecného typu, který chcete, aby odpovídala v musí být určena direktivy modulu runtime. Tato akce není právě, protože všechny kód musí být zahrnut, ale důvodu reflexe v obecných typech, můžete nekonečné cyklus (například když obecná metoda je volána, obecného typu).  
  
> [!NOTE]
>  Direktivy modulu runtime jsou definovány v direktivy modulu runtime (. rd.xml) souboru. Obecné informace o použití tohoto souboru najdete v tématu [Začínáme](../../../docs/framework/net-native/getting-started-with-net-native.md). Informace o direktivy modulu runtime najdete v tématu [direktivy modulu Runtime (rd.xml) referenci na konfigurační soubor](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)]zahrnuje taky profilace nástroje, které pomáhají určit, jaké typy mimo výchozí sadu by měla podporovat reflexe vývojář.  
  
<a name="Reflection"></a>   
## <a name="other-reflection-related-differences"></a>Další související reflexe rozdíly  
 Existuje několik dalších jednotlivých související reflexe rozdíly v chování mezi aplikace .NET pro Windows Store a [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
 V [!INCLUDE[net_native](../../../includes/net-native-md.md)]:  
  
-   Privátní reflexe přes typy a členy v knihovně tříd rozhraní .NET Framework není podporována. Můžete, ale projeví přes vlastní privátní typy a členy, jakož i typy a členy v knihovnách třetích stran.  
  
-   <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> Vlastnost správně vrací `false` pro <xref:System.Reflection.ParameterInfo> objekt, který reprezentuje návratovou hodnotu. V aplikacích .NET pro Windows Store, vrátí `true`. Převodní jazyk (IL) nepodporuje tento přímo a výkladu je ponechán jazyk.  
  
-   Veřejné členy na <xref:System.RuntimeFieldHandle> a <xref:System.RuntimeMethodHandle> struktury nejsou podporovány. Tyto typy jsou podporovány pouze u LINQ, stromy výrazů a inicializace statické pole.  
  
-   <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType>a <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> zahrnout skryté členy základní třídy a proto může být přepsána bez explicitní přepsání. To platí i jiné [RuntimeReflectionExtensions.GetRuntime*](http://msdn.microsoft.com/library/system.reflection.runtimereflectionextensions_methods.aspx) metody.  
  
-   <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType>a <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> nemáte selhání při pokusu o vytvoření určité kombinace (například pole byrefs).  
  
-   Reflexe nelze použít k vyvolání členy, které mají parametry ukazatele.  
  
-   Reflexe nelze použít k získání nebo nastavení pole ukazatele.  
  
-   Když je nesprávný počet argumentů a typ jednoho z argumentů je nesprávný, [!INCLUDE[net_native](../../../includes/net-native-md.md)] vyvolá <xref:System.ArgumentException> místo <xref:System.Reflection.TargetParameterCountException>.  
  
-   Binární serializace výjimek obecně není podporována. V důsledku toho nejsou objekty mohou být přidány do <xref:System.Exception.Data%2A?displayProperty=nameWithType> slovníku.  
  
<a name="Unsupported"></a>   
## <a name="unsupported-scenarios-and-apis"></a>Nepodporované scénáře a rozhraní API  
 Následující části uvádějí nepodporované scénáře a rozhraní API pro obecné vývoj, zprostředkovatel komunikace s objekty a technologie, jako je například HTTPClient a Windows Communication Foundation (WCF):  
  
-   [Obecné vývoj](#General)  
  
-   [HttpClient](#HttpClient)  
  
-   [Zprostředkovatel komunikace s objekty](#Interop)  
  
-   [Nepodporované rozhraní API](#APIs)  
  
<a name="General"></a>   
### <a name="general-development-differences"></a>Vývoj pro obecné rozdíly  
 **Typy hodnot**  
  
-   Pokud přepíšete <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> a <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> metody pro typ hodnoty, nemůžete volat implementace základní třídy. V aplikacích .NET pro Windows Store tyto metody závisí na reflexi. Při kompilaci [!INCLUDE[net_native](../../../includes/net-native-md.md)] generuje implementace, která není závisí na reflexi modulu runtime. To znamená, že pokud nemáte přepsat tyto dvě metody, budou fungovat podle očekávání, protože [!INCLUDE[net_native](../../../includes/net-native-md.md)] generuje implementace v době kompilace. Přepsání těchto metod, ale volání implementaci základní třídy výsledkem však výjimku.  
  
-   Typy hodnot, které jsou větší než 1 MB nejsou podporovány.  
  
-   Typy hodnot nemůže mít výchozí konstruktor v [!INCLUDE[net_native](../../../includes/net-native-md.md)]. (C# a Visual Basic zakázat výchozí konstruktory u typů hodnot. Ale ty lze vytvořit v IL.)  
  
 **Pole**  
  
-   Pole s dolní mez než nulu nejsou podporována. Obvykle jsou tato pole vytvořena voláním <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> přetížení.  
  
-   Dynamické vytváření vícerozměrná pole není podporováno. Takovými poli se obvykle vytvářejí voláním přetížení <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> metoda, která zahrnuje `lengths` parametr, nebo při volání <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> metoda.  
  
-   Vícerozměrná pole, které mají čtyři nebo více dimenzí nejsou podporovány; To znamená jejich <xref:System.Array.Rank%2A?displayProperty=nameWithType> hodnota vlastnosti je 4 nebo vyšší. Použití [Vícenásobná pole](~/docs/csharp/programming-guide/arrays/jagged-arrays.md) (pole polí) místo. Například `array[x,y,z]` je neplatná, ale `array[x][y][z]` není.  
  
-   Odchylky pro vícerozměrná pole nepodporuje a způsobí, že <xref:System.InvalidCastException> výjimky za běhu.  
  
 **Obecné typy**  
  
-   Chyba kompilátoru za následek rozšíření nekonečné obecného typu. Například tento kód se nepovede zkompilovat:  
  
     [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]  
  
 **Ukazatele**  
  
-   Pole ukazatele nejsou podporována.  
  
-   Reflexe nelze použít k získání nebo nastavení pole ukazatele.  
  
 **Serializace**  
  
 <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> Atribut není podporován. Použití <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> atribut místo.  
  
 **Prostředky**  
  
 Použití lokalizované prostředky s <xref:System.Diagnostics.Tracing.EventSource> třída není podporována. <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> Nedefinuje vlastnost lokalizované prostředky.  
  
 **Delegáti**  
  
 `Delegate.BeginInvoke`a `Delegate.EndInvoke` nejsou podporovány.  
  
 **Async**  
  
 Dělení na vlákna logiku přetížení IAsync úloh není podporována.  
  
 **Ostatní rozhraní API**  
  
-   <xref:System.Reflection.TypeInfo.GUID%2A?displayProperty=nameWithType> Vlastnost vyvolává <xref:System.PlatformNotSupportedException> výjimka pokud <xref:System.Runtime.InteropServices.GuidAttribute> není použit atribut typu. Identifikátor GUID slouží především pro podporu modelu COM.  
  
-   <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> Metoda správně analyzuje řetězce, které obsahují krátká data v [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Ale ho nebude zachování kompatibility s změny v datum a čas analýza popsané v článcích znalostní báze Microsoft Knowledge Base [KB2803771](http://support.microsoft.com/kb/2803771) a [KB2803755](http://support.microsoft.com/kb/2803755).  
  
-   <xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType>`("E")` se správně zaokrouhlí v [!INCLUDE[net_native](../../../includes/net-native-md.md)]. V některé verze modulu CLR se zkrátí na výsledný řetězec místo zaokrouhlené.  
  
<a name="HttpClient"></a>   
### <a name="httpclient-differences"></a>Rozdíly HttpClient  
 V [!INCLUDE[net_native](../../../includes/net-native-md.md)], <xref:System.Net.Http.HttpClientHandler> třída se používá interně WinINet (prostřednictvím [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) třída) místo <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> třídy používané ve standardní aplikace .NET pro Windows Store.  WinINet nepodporuje všechny možnosti konfigurace, který <xref:System.Net.Http.HttpClientHandler> třídy podporuje.  Výsledek:  
  
-   Některé vlastnosti schopností na <xref:System.Net.Http.HttpClientHandler> vrátit `false` na [!INCLUDE[net_native](../../../includes/net-native-md.md)], vzhledem k tomu, že budou vracet `true` v standardní aplikace .NET pro Windows Store.  
  
-   Některé vlastnosti konfigurace `get` přístupové objekty vždy vrátit pevnou hodnotu na [!INCLUDE[net_native](../../../includes/net-native-md.md)] , je jiná než výchozí hodnota konfigurovat v aplikacích .NET pro Windows Store.  
  
 Některé další chování rozdíly jsou popsané v následující témata.  
  
 **Proxy server**  
  
 [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) třída nepodporuje konfiguraci nebo přepsání proxy serveru na základě požadavků.  To znamená, že všechny požadavky na [!INCLUDE[net_native](../../../includes/net-native-md.md)] používat systém nakonfigurován server proxy server nebo žádný proxy server, v závislosti na hodnotě <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> vlastnost.  V aplikacích .NET pro Windows Store je definované proxy serveru <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> vlastnost.  Na [!INCLUDE[net_native](../../../includes/net-native-md.md)], nastavení <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> hodnotu jinou než `null` vyvolá <xref:System.PlatformNotSupportedException> výjimka.  <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> Vlastnost vrátí `false` na [!INCLUDE[net_native](../../../includes/net-native-md.md)], zatímco vrátí `true` v standardní aplikace rozhraní .NET Framework pro Windows Store.  
  
 **Automatické přesměrování**  
  
 [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) třída neumožňuje maximální počet automatické přesměrování nakonfigurovat.  Hodnota <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> vlastnost je 50 ve výchozím nastavení v standardní aplikace .NET pro Windows Store a nelze jej změnit. Na [!INCLUDE[net_native](../../../includes/net-native-md.md)], hodnota této vlastnosti je 10 a upravit ho generuje při pokusu <xref:System.PlatformNotSupportedException> výjimka.  <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> Vlastnost vrátí `false` na [!INCLUDE[net_native](../../../includes/net-native-md.md)], zatímco vrátí `true` v aplikacích .NET pro Windows Store.  
  
 **Automatickou dekompresi**  
  
 Aplikace .NET pro Windows Store můžete nastavit <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> vlastnost <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, oba <xref:System.Net.DecompressionMethods.Deflate> a <xref:System.Net.DecompressionMethods.GZip>, nebo <xref:System.Net.DecompressionMethods.None>.  [!INCLUDE[net_native](../../../includes/net-native-md.md)]podporuje pouze <xref:System.Net.DecompressionMethods.Deflate> společně s <xref:System.Net.DecompressionMethods.GZip>, nebo <xref:System.Net.DecompressionMethods.None>.  Pokusu o nastavení <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> vlastnost, která má buď <xref:System.Net.DecompressionMethods.Deflate> nebo <xref:System.Net.DecompressionMethods.GZip> samostatně bezobslužně nastaví na obě <xref:System.Net.DecompressionMethods.Deflate> a <xref:System.Net.DecompressionMethods.GZip>.  
  
 **Soubory cookie**  
  
 Zpracování souborů cookie se provádí současně pomocí <xref:System.Net.Http.HttpClient> a WinINet.  Soubory cookie z <xref:System.Net.CookieContainer> spolu se soubory cookie v mezipaměti souborů cookie WinINet.  Odebrání souborů cookie z <xref:System.Net.CookieContainer> brání <xref:System.Net.Http.HttpClient> odesílání souboru cookie, ale pokud WinINet už zobrazila souboru cookie a uživatelem, nebyly odstraněny soubory cookie z WinINet odešle ji.  Není možné programově odebrat soubor cookie z WinINet pomocí <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>, nebo <xref:System.Net.CookieContainer> rozhraní API.  Nastavení <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> vlastnost `false` způsobí, že pouze <xref:System.Net.Http.HttpClient> zastavit odesílání soubory cookie. WinINet stále mohou zahrnovat jeho soubory cookie v požadavku.  
  
 **Přihlašovací údaje**  
  
 V aplikacích .NET pro Windows Store <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> a <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> vlastnosti pracují nezávisle.  Kromě toho <xref:System.Net.Http.HttpClientHandler.Credentials%2A> tato vlastnost přijímá parametry libovolný objekt, který implementuje <xref:System.Net.ICredentials> rozhraní.  V [!INCLUDE[net_native](../../../includes/net-native-md.md)], nastavení <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> vlastnost `true` způsobí, že <xref:System.Net.Http.HttpClientHandler.Credentials%2A> vlastnost `null`.  Kromě toho <xref:System.Net.Http.HttpClientHandler.Credentials%2A> vlastnost lze nastavit pouze na `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>, nebo objekt typu <xref:System.Net.NetworkCredential>.  Přiřazení jakékoliv <xref:System.Net.ICredentials> objekt, nejoblíbenější z nich je <xref:System.Net.CredentialCache>do <xref:System.Net.Http.HttpClientHandler.Credentials%2A> vlastnost vyvolává <xref:System.PlatformNotSupportedException>.  
  
 **Další funkce nepodporované nebo unconfigurable**  
  
 V [!INCLUDE[net_native](../../../includes/net-native-md.md)]:  
  
-   Hodnota <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> vlastnost je vždy <xref:System.Net.Http.ClientCertificateOption.Automatic>.  V aplikacích .NET pro Windows Store, výchozí hodnota je <xref:System.Net.Http.ClientCertificateOption.Manual>.  
  
-   <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> Vlastnost není konfigurovatelné.  
  
-   <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> Vlastnost je vždy `true`.  V aplikacích .NET pro Windows Store, výchozí hodnota je `false`.  
  
-   `SetCookie2` Záhlaví v odpovědi se ignoruje jako zastaralé.  
  
<a name="Interop"></a>   
### <a name="interop-differences"></a>Rozdílech spolupráce  
 **Zastaralá rozhraní API**  
  
 Počet zřídka používaný rozhraní API pro spolupráci se spravovaným kódem jsou zastaralé. Při použití s [!INCLUDE[net_native](../../../includes/net-native-md.md)], může tato rozhraní API throw <xref:System.NotImplementedException> nebo <xref:System.PlatformNotSupportedException> výjimky nebo vést k chybě kompilátoru. V aplikacích .NET pro Windows Store tato rozhraní API jsou označeny jako zastaralé, i když je volání vygeneruje upozornění kompilátoru, nikoli k chybě kompilátoru.  
  
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
  
 <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType>je podporováno, ale vyvolá výjimku, v některých případech, například při použití s [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) nebo byref variant.  
  
 Zastaralá rozhraní API pro [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) podporují:  
  
|Typ|Člen|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch>|  
|<xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual>|  
|<xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>|Atribut není podporován.|  
  
 Zastaralá rozhraní API pro classic COM události:  
  
||  
|-|  
|<xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>|  
  
 Zastaralá rozhraní API v <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> rozhraní, což není podporováno v [!INCLUDE[net_native](../../../includes/net-native-md.md)]:  
  
|Typ|Člen|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType>|Všechny členy.|  
|<xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType>|Všechny členy.|  
|<xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType>|Všechny členy.|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=nameWithType>|  
  
 Jiné nepodporované funkce zprostředkovatele komunikace s objekty:  
  
|Typ|Člen|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType>|Všechny členy.|  
|<xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType>|Všechny členy.|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.Currency>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.AnsiBStr>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.AsAny>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.CustomMarshaler>|  
  
 Je používána zřídka mezipaměti sdružených dat rozhraní API:  
  
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
  
 **Vyvolání platformy a kompatibility zprostředkovatele komunikace s objekty COM**  
  
 Vyvolání platformy většina a scénáře zprostředkovatele komunikace s objekty COM jsou stále podporovány v [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Konkrétně je podporována všechny interoperabilitu se prostředí Windows Runtime (WinRT) rozhraní API a zařazování požadované pro prostředí Windows Runtime. To zahrnuje podporu pro zařazování:  
  
-   Pole (včetně <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)  
  
-   `BStr`  
  
-   Delegáty  
  
-   Řetězce (znakové sady Unicode, Ansi a HSTRING)  
  
-   Struktury (`byref` a `byval`)  
  
-   Sjednocení  
  
-   Obslužné rutiny Win32  
  
-   Všechny WinRT konstrukce  
  
-   Částečná podpora zařazování typů variant. Jsou podporovány následující:  
  
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
  
    -   [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509.aspx)  
  
 Ale [!INCLUDE[net_native](../../../includes/net-native-md.md)] nepodporuje následující:  
  
-   Pomocí klasického modelu COM události  
  
-   Implementace <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> rozhraní na spravovaného typu  
  
-   Implementace [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) rozhraní pro spravovaný typ prostřednictvím <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> atribut. Ale Všimněte si, že nelze volat objekty modelu COM pomocí `IDispatch`, a spravovaného objektu nelze implementovat, `IDispatch`.  
  
 Pomocí reflexe k vyvolání platformu vyvolání metody se nepodporuje. Toto omezení můžete obejít tak zabalení volání metody v jiné metody a místo toho volejte obálku pomocí reflexe.  
  
<a name="APIs"></a>   
### <a name="other-differences-from-net-apis-for-windows-store-apps"></a>Další rozdíly z aplikace rozhraní API .NET pro Windows Store  
 Tato část uvádí zbývající rozhraní API, které nejsou podporovány v [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Největší sadu nepodporované rozhraní API jsou Windows Communication Foundation (WCF) rozhraní API.  
  
 **DataAnnotations (System.ComponentModel.DataAnnotations)**  
  
 Typy v <xref:System.ComponentModel.DataAnnotations> a <xref:System.ComponentModel.DataAnnotations.Schema> obory názvů nejsou podporovány v [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Mezi ně patří následující typy, které se nacházejí v aplikacích .NET pro Windows Store pro systém Windows 8:  
  
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
  
 Visual Basic není podporován v [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Následující typy, které do <xref:Microsoft.VisualBasic> a <xref:Microsoft.VisualBasic.CompilerServices> obory názvů nejsou k dispozici v [!INCLUDE[net_native](../../../includes/net-native-md.md)]:  
  
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
  
 **Kontext reflexe (obor názvů System.Reflection.Context)**  
  
 <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> Třída není podporována v [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
 **RTC (System.Net.Http.Rtc)**  
  
 <xref:System.Net.Http.RtcRequestFactory?displayProperty=nameWithType> Třída není podporována v [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
 **Windows Communication Foundation (WCF) (System.ServiceModel.\*)**  
  
 Typy v [obory názvů System.ServiceModel.*](http://msdn.microsoft.com/library/gg145010.aspx) nejsou podporovány v [!INCLUDE[net_native](../../../includes/net-native-md.md)]. To zahrnuje následující typy:  
  
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
 Následující rozdíly týkají serializace a deserializace pomocí <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, a <xref:System.Xml.Serialization.XmlSerializer> třídy:  
  
-   V [!INCLUDE[net_native](../../../includes/net-native-md.md)], <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> k serializaci nebo deserializaci odvozené třídy, která má základní třída člena, jehož typ není typu serializace kořenové nezdaří. Například následující kód, pokusu o serializaci nebo deserializaci `Y` vede k chybě:  
  
     [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]  
  
     Typ `InnerType` nezná serializátor, protože nejsou členy základní třídy provázán během serializace.  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer>a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nepodaří serializovat třídu nebo strukturu, která implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní. Například následující typy selhat k serializaci nebo deserializaci:  
  
  
  
-   <xref:System.Xml.Serialization.XmlSerializer>selže k serializaci následující hodnotu objektu, protože neví přesný typ objektu k serializaci:  
  
  
  
-   <xref:System.Xml.Serialization.XmlSerializer>selže k serializaci nebo deserializaci, pokud je typ serializovaný objekt <xref:System.Xml.XmlQualifiedName>.  
  
-   Všechny serializátorů (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, a <xref:System.Xml.Serialization.XmlSerializer>) se nepodařilo vygenerovat kód serializace typu <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> nebo typu, který obsahuje <xref:System.Xml.Linq.XElement>. Místo toho se zobrazit chyby čase vytvoření buildu.  
  
-   Těchto konstruktorů typy serializace nemusí fungovat podle očekávání:  
  
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
  
-   <xref:System.Xml.Serialization.XmlSerializer>Nepodařilo se generovat kód pro typ, který má metody s atributy s žádným z následujících atributů:  
  
    -   <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
-   <xref:System.Xml.Serialization.XmlSerializer>není respektovat <xref:System.Xml.Serialization.IXmlSerializable> vlastní serializace rozhraní. Pokud máte třídu, která toto rozhraní implementuje <xref:System.Xml.Serialization.XmlSerializer> považovat za typ prostý starý typ objektu (objektů POCO) CLR a serializuje jenom jeho veřejné vlastnosti.  
  
-   Serializace prostý <xref:System.Exception> objektu, například následující příkaz, nebude fungovat správně s <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:  
  
  
  
<a name="VS"></a>   
## <a name="visual-studio-differences"></a>Rozdíly Visual Studio  
 **Výjimky a ladění**  
  
 Pokud používáte aplikace, kompilovat s použitím [!INCLUDE[net_native](../../../includes/net-native-md.md)] v ladicím programu, první možnosti výjimky jsou povolené pro následující typy výjimka:  
  
-   <xref:System.MemberAccessException>  
  
-   <xref:System.TypeAccessException>  
  
 **Vytváření aplikací**  
  
 Použijte x86 sestavení nástroje, které se používají ve výchozím nastavení Visual Studio. Nedoporučujeme používat nástroje AMD64 MSBuild, které se nacházejí v C:\Program Files (x86)\MSBuild\12.0\bin\amd64; To může způsobit problémy s sestavení.  
  
 **Profilery**  
  
-   Visual Studio Profiler procesoru a paměti profileru XAML nezobrazí pouze můj kód správně.  
  
-   XAML paměti profileru nebude přesně zobrazovat data spravovaná halda.  
  
-   Procesor profileru není správně identifikovat moduly a zobrazí předponu názvy funkcí.  
  
 **Projekty knihovny testů jednotek**  
  
 Povolení [!INCLUDE[net_native](../../../includes/net-native-md.md)] na knihovně testů jednotek pro Windows Store projekt aplikace se nepodporuje a způsobí, že projekt nepovede.  
  
## <a name="see-also"></a>Viz také  
 [Začínáme](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Přehled aplikace .NET pro Windows Store](http://msdn.microsoft.com/library/windows/apps/br230302.aspx)  
 [Podpora pro aplikace pro web Windows Store a prostředí Windows Runtime v rozhraní .NET Framework](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
