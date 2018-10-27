---
title: Aplikační domény
ms.date: 03/30/2017
helpviewer_keywords:
- process boundaries for isolation
- application isolation
- application domains, about
- common language runtime, application domains
- application domains
- runtime, application domains
- isolation between applications
- code, verification process
- verification testing code
ms.assetid: 113a8bbf-6875-4a72-a49d-ca2d92e19cc8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e1db5447be5f46873b6648fc6791426b2886a75
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192613"
---
# <a name="application-domains"></a>Aplikační domény

Operační systémy a běhová prostředí obvykle poskytují určitou formu izolace mezi aplikacemi. Například Windows používá procesy k izolaci aplikací. Tato izolace je nezbytná k zajištění, že kód spuštěný v jedné aplikaci nemohl nepříznivě ovlivnit jiné nesouvisející aplikace.  
  
 Aplikační domény poskytují izolační hranici pro zabezpečení, spolehlivosti a správy verzí a pro uvolňování sestavení. Aplikační domény jsou obvykle vytvářeny hostitelská prostředí modulu runtime, která jsou odpovědná za spuštění modul common language runtime, před spuštěním aplikace.  
  
## <a name="the-benefits-of-isolating-applications"></a>Výhody izolace aplikací

 V minulosti byly hranice procesů použity k izolaci aplikací spuštěných na stejném počítači. Každá aplikace je načtena jako samostatný proces, který ji izoluje od jiných aplikací spuštěných na stejném počítači.  
  
 Aplikace jsou izolovány vzhledem k tomu, že adresy paměti jsou procesně relativní; ukazatel paměti předaný z jednoho procesu nelze žádným smysluplným způsobem v cílovém procesu. Kromě toho nemůžete provádět přímá volání mezi dvěma procesy. Místo toho musíte použít proxy servery, které zajišťují určitou úroveň dereference.  
  
 Spravovaný kód musí být předán skrz ověřovací proces před spuštěním (pokud správce udělil oprávnění k přeskočení ověření). Ověřovací proces určuje, zda kód může pokusit o přístup k neplatné adrese paměti nebo provede nějakou jinou akci, která by mohla způsobit procesu, ve kterém je spuštěna nesprávné fungování. Kód, který projde ověřovacím testem je označen jako typově bezpečný. Schopnost ověřit kód jako typově bezpečný umožňuje poskytovat tak skvělou úroveň izolace, jako je hranice procesu a za mnohem nižší výkon, modul common language runtime.  
  
 Aplikační domény poskytují bezpečnější a všestrannější jednotky zpracování, které modul common language runtime můžete použít k poskytnutí izolace mezi aplikacemi. Můžete spustit několik domén aplikace v jediném procesu se stejnou úrovní izolace, která by existovala v oddělených procesech, ale bez další režie mezi procesní volání nebo přepínání mezi procesy. Umožňuje spustit několik aplikací v rámci jediného procesu výrazně zvyšuje škálovatelnost serveru.  
  
 Izolování aplikace je také důležité kvůli jejímu zabezpečení. Například můžete spustit ovládací prvky z několika webových aplikací v jediném procesu prohlížeče takovým způsobem, že ovládací prvky nelze přistupovat k datům a prostředkům.  
  
 Izolace poskytovaná aplikačními doménami má následující výhody:  
  
-   Chyby v jedné aplikaci nemůžou ovlivnit jiné aplikace. Vzhledem k tomu, že kód zajišťující bezpečnost typů nemůže způsobit chyby paměti, pomocí aplikačních domén zajišťuje, že kód spuštěný v jedné doméně nemohl ovlivnit jiné aplikace v procesu.  
  
-   Jednotlivé aplikace mohou být ukončeny bez ukončení celého procesu. Používání domén aplikací umožňuje uvolnit kód spuštěný v jedné aplikaci.  
  
    > [!NOTE]
    >  Není možné uvolnit samostatná sestavení nebo typy. Pouze úplná doména může být uvolněna.  
  
-   Kód spuštěný v jedné aplikaci nemůže přímo přistupovat ke kódu nebo prostředkům jiné aplikace. Modul common language runtime vynucuje tuto izolaci, aby zabránil přímým voláním mezi objekty v různých aplikačních doménách. Objekty, které prochází mezi doménami jsou buď zkopírovány nebo zpřístupněny pomocí proxy serveru. Pokud je objekt zkopírován, volání objektu je lokální. To znamená volající a odkazovaný objekt jsou ve stejné doméně aplikace. Pokud je objekt zpřístupněný prostřednictvím proxy serveru, je volání objektu vzdálené. V takovém případě volající a odkazovaný objekt jsou v různých aplikačních doménách. Volání mezi doménami používat stejnou infrastrukturu vzdáleného volání jako volání mezi dvěma procesy nebo mezi dvěma počítači. Metadata pro objekt, který se odkazuje v důsledku toho musí být k dispozici pro obě domény aplikace. Chcete-li povolit volání metody, které chcete být JIT kompilován správně. Pokud volající doména nemá přístup k metadatům pro volaný objekt, kompilace může selhat s výjimkou typu **System.IO.FileNotFound**. Zobrazit [vzdálené objekty](https://msdn.microsoft.com/library/515686e6-0a8d-42f7-8188-73abede57c58) další podrobnosti. Mechanismus pro stanovení toho, jak mohou být objekty přístupné napříč doménami je určen objektem. Další informace naleznete v tématu <xref:System.MarshalByRefObject?displayProperty=nameWithType>.  
  
-   Chování kódu je určeno aplikací, ve kterém běží. Jinými slovy aplikační doména poskytuje nastavení konfigurace, například zásady stanovování verzí aplikace, umístění jakýchkoliv vzdálených sestavení, k nimž přistupuje a informace o tom, kde nalézt sestavení, která jsou načtena do domény.  
  
-   Oprávnění udělená kódu mohou být řízena domény aplikace, ve kterém kód běží.  
  
## <a name="application-domains-and-assemblies"></a>Doménám a sestavením aplikací

 Tato část popisuje vztah mezi doménami aplikací a sestaveními. Předtím, než může spustit kód, který ho obsahuje, je nutné načíst sestavení do domény aplikace. Spuštění Typická aplikace způsobí, že několik sestavení mají být načtena do domény aplikace.  
  
 Způsob, jakým je sestavení načteno Určuje, zda jeho just-in-time (JIT) kompilaci kódu může být sdílen více aplikačními doménami v procesu, a zda může být uvolněna z procesu sestavení.  
  
-   Pokud je sestavení načteno jako doménově neutrální, všechny aplikační domény, které sdílejí stejné zabezpečení udělují sady můžete sdílet stejný kód zkompilovaný pomocí kompilátoru JIT, který je sníženo množství paměti požadované aplikací. Nicméně sestavení může nikdy být uvolněna z procesu.  
  
-   Pokud sestavení není načteno jako doménově neutrální, musí být JIT kompilován v každé aplikační doméně, ve které je načten. Sestavení však může být uvolněna z procesu uvolnění všech aplikačních doménách, ve kterých je načíst.  
  
 Hostitelský modul runtime určuje, jestli se má načíst sestavení jako doménově neutrální, když ho načítá modul runtime do procesu. Spravované aplikace, použijte <xref:System.LoaderOptimizationAttribute> atribut do metody vstupního bodu pro proces a zadejte hodnotu od přidruženého <xref:System.LoaderOptimization> výčtu. Nespravované aplikace, které jsou hostiteli společného jazykového modulu runtime, zadejte odpovídající příznak při volání [CorBindToRuntimeEx – funkce](../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) metody.  
  
 Existují tři možnosti načtení doménově neutrální sestavení:  
  
- <xref:System.LoaderOptimization.SingleDomain?displayProperty=nameWithType> nenačítá žádné sestavení jako doménově neutrální, s výjimkou Mscorlib, které je vždy načteno jako doménově neutrální. Toto nastavení se nazývá jediná doména, protože se běžně používá, když na hostiteli běží pouze jednu aplikaci v procesu.

- <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType> načte všechna sestavení jako doménově neutrální. Toto nastavení použijte, pokud existuje více domén aplikace v procesu, z nichž všechny spustit stejný kód.

- <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType> načte sestavení se silným názvem jako doménově neutrální, pokud byly nainstalovány a jejich závislosti v globální mezipaměti sestavení. Jiná sestavení jsou načtena a JIT kompilován samostatně pro každou doménu aplikace, ve kterém jsou načteny a proto mohou být uvolněna z procesu. Pomocí tohoto nastavení při spuštění více než jednu aplikaci ve stejném procesu, nebo pokud máte různé sestavení, které sdílí mnoho aplikačních doménách a sestavení, které musí být uvolněna z procesu.
  
 Nelze sdílet kód zkompilovaný kompilátorem JIT pro sestavení, které načítají do kontextu načtení z pomocí <xref:System.Reflection.Assembly.LoadFrom%2A> metodu <xref:System.Reflection.Assembly> třídy nebo načíst z imagí pomocí přetížení <xref:System.Reflection.Assembly.Load%2A> metody, které specifikují pole bajtů.  
  
 Sestavení, která byla zkompilována do nativního kódu s použitím [Ngen.exe (Generátor nativních obrázků)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) je možné sdílet mezi doménami aplikace, že jsou načtena jako doménově neutrální prvním načtením do procesu.  
  
 Kód zkompilovaný kompilátorem JIT pro sestavení, který obsahuje vstupní bod aplikace se sdílí jenom v případě, že je možné sdílet jeho závislosti.  
  
 Sestavení nezávislá na doméně může být JIT kompilován více než jednou. Například při zabezpečení udělit sady z obou aplikačních doménách se liší, nemůžou ale sdílet stejný kód zkompilovaný kompilátorem JIT. Každá kopie JIT kompilaci sestavení však, mohou být sdíleny s dalšími doménami aplikace, které mají stejná sada udělení oprávnění.  
  
 Při rozhodování, jestli se má načíst sestavení jako doménově neutrální, je třeba kompromis mezi snížení využití paměti a dalších faktorů výkonu.  
  
-   Přístup ke statickým datům a metodám je kvůli potřebě izolovat sestavení pomalejší pro sestavení jako doménově neutrální. Každá doména aplikace, který přistupuje k sestavení musí mít samostatnou kopii statická data, aby se zabránilo odkazy na objekty v statická pole z přes hranice domén. V důsledku toho modul runtime obsahuje další logiku ke směrování volajícímu odpovídající kopii statická data nebo metody. Tuto logiku navíc může zpomalit volání.  
  
-   Všechny závislosti sestavení musí být umístěn a načíst, když je sestavení načteno jako doménově neutrální, protože závislost, která nemůže být načtena jako doménově neutrální, brání sestavení jsou načtena jako doménově neutrální.  
  
## <a name="application-domains-and-threads"></a>Domény aplikace a vlákna

 Domény aplikace tvoří hranici izolace zabezpečení, správy verzí, spolehlivost a uvolňování spravovaného kódu. Vlákno je konstrukce operační systém používá modul common language runtime k provádění kódu. Veškerého spravovaného kódu v době běhu, je načteno do domény aplikace a běží na jeden nebo více spravovaných vláken.  
  
 Není k dispozici 1: 1 korelace mezi doménami aplikace a vlákna. V jediné doméně aplikace v daném okamžiku můžete spustit několik vláken a konkrétní vlákno nejsou omezené na jedné aplikace domény aplikace. To znamená, že jsou zdarma přes hranice aplikační domény; vláken nové vlákno není vytvořena pro každou doménu aplikace.  
  
 V daném okamžiku každé vlákno spustí v doméně aplikace. Žádného, jednoho nebo více vláken může být spuštěno v libovolné doméně aplikace. Uchovává informace o modulu runtime, která vlákna jsou spuštěny v které domény aplikace. Můžete najít doménu, ve kterém je vlákno provádění v každém okamžiku voláním <xref:System.Threading.Thread.GetDomain%2A?displayProperty=nameWithType> metody.

### <a name="application-domains-and-cultures"></a>Aplikační domény a jazykové verze

 Jazykové verze, která je reprezentována <xref:System.Globalization.CultureInfo> objektu, je spojen s vlákny. Můžete získat jazykovou verzi, která souvisí s aktuálně spuštěné vlákno s použitím <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> vlastnosti kde můžete získat nebo nastavit jazykovou verzi, která souvisí s aktuálně spuštěné vlákno s použitím <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> vlastnost. Pokud jazykovou verzi, která souvisí s vláknem explicitně nastavené pomocí <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> vlastnost, pokračuje souviset s tímto vláknem po vlákno překročí hranice domény aplikace. V opačném případě určení jazykové verze, která souvisí s vláknem v daném okamžiku hodnotou <xref:System.Globalization.CultureInfo.DefaultThreadCurrentCulture%2A?displayProperty=nameWithType> vlastnost v aplikační doméně, ve kterém je spuštěn vlákna:  
  
-   Pokud hodnota vlastnosti není `null`, jazykovou verzi, která je vrácena vlastností je přidružené vlákno (a tedy vrácené <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> a <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> vlastnosti).  
  
-   Pokud je hodnota vlastnosti `null`, je spojen s vláknem aktuální systémovou kulturu.  
  
## <a name="programming-with-application-domains"></a>Programování pomocí domén aplikace

 Aplikační domény jsou obvykle vytvořit a spravovat prostřednictvím kódu programu pomocí hostitelská prostředí modulu runtime. Ale někdy programu aplikace může být také vhodné pro práci s doménami aplikace. Programu aplikace může například načíst součásti do domény, aby bylo možné uvolnění domény aplikace (a komponenta) bez nutnosti zastavení celé aplikace.  
  
 <xref:System.AppDomain> Je programové rozhraní do domény aplikace. Tato třída obsahuje metody pro vytvoření a uvolnění domény, chcete-li vytvořit instance typů v doménách a k registraci pro různá upozornění, jako je například uvolnění domény aplikace. Následující tabulce jsou uvedeny běžně používané <xref:System.AppDomain> metody.  
  
|Metoda třídy AppDomain|Popis|  
|----------------------|-----------------|  
|<xref:System.AppDomain.CreateDomain%2A>|Vytvoří novou doménu aplikace. Je doporučeno používat přetížení této metody, které určuje <xref:System.AppDomainSetup> objektu. Toto je upřednostňovaný způsob, jak nastavit vlastnosti nové domény, jako je například základ cesty aplikace nebo kořenového adresáře pro aplikaci. umístění konfiguračního souboru pro domény. a vyhledávací cestu, modul common language runtime, je použít k načtení sestavení do domény.|  
|<xref:System.AppDomain.ExecuteAssembly%2A> a <xref:System.AppDomain.ExecuteAssemblyByName%2A>|Spustí sestavení v doméně aplikace. Toto je metoda instance, takže ho můžete použít ke spouštění kódu vytvořeného v jiné doméně aplikace, ke kterému budete mít odkaz na.|  
|<xref:System.AppDomain.CreateInstanceAndUnwrap%2A>|Vytvoří instanci zadaného typu v aplikační doméně a vrátí proxy server. Pomocí této metody můžete předejít sestavení obsahující typ vytvořeného do volajícího sestavení.|  
|<xref:System.AppDomain.Unload%2A>|Provádí řádné vypnutí domény. Doména aplikace není uvolněn, dokud všechna vlákna spuštěná v doméně, byla buď zastavena nebo už nejsou v doméně.|  
  
> [!NOTE]
>  Modul common language runtime nepodporuje serializace globálních metod, takže delegáty nelze použít k provedení globálních metod v jiných doménách aplikace.  
  
 Nespravovaná rozhraní, je popsáno v modulu common language runtime hostování specifikace rozhraní také poskytnout přístup k aplikační domény. Hostitelská prostředí modulu runtime slouží k vytvoření a získat přístup do domény aplikace uvnitř procesu rozhraní z nespravovaného kódu.  
  
## <a name="the-complusloaderoptimization-environment-variable"></a>Complus_loaderoptimization – proměnná prostředí

 Proměnné prostředí, která nastaví výchozí zásady optimalizace zavaděče spustitelného souboru.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
COMPLUS_LoaderOptimization = 1  
```  
  
### <a name="remarks"></a>Poznámky

 Typická aplikace několik sestavení načte do domény aplikace předtím, než mohou být provedeny v kódu, které obsahují.  
  
 Způsob, jakým je načteno sestavení určuje, zda jeho just-in-time (JIT) kompilaci kódu může být sdílen více aplikačními doménami v procesu.  
  
-   Pokud je sestavení načteno jako doménově neutrální, všechny aplikační domény, které sdílejí stejnou sadu zabezpečení můžete sdílet stejný kód zkompilovaný kompilátorem JIT. Tím je sníženo množství paměti požadované aplikací.  
  
-   Pokud sestavení není načteno jako doménově neutrální, musí být JIT kompilován v každé aplikační doméně, ve které je načten a zavaděč nesmí sdílet interní prostředky mezi doménami aplikace.  
  
 Při natavení na 1 příznak prostředí COMPLUS_LoaderOptimization vynutí hostitelský modul runtime načtení všech sestavení způsobem domény neutrální označované jako SingleDomain. SingleDomain nenačítá žádné sestavení jako doménově neutrální, s výjimkou Mscorlib, které je vždy načteno jako doménově neutrální. Toto nastavení se nazývá jediná doména, protože se běžně používá, když na hostiteli běží pouze jednu aplikaci v procesu.  
  
> [!CAUTION]
>  Příznak prostředí COMPLUS_LoaderOptimization byl navržen pro použití v rámci diagnostiky a testovací scénáře. S se zapnutým příznakem můžete způsobit vážné zpomalování a zvýšení využití paměti.  
  
### <a name="code-example"></a>Příklad kódu

 K vynucení všechna sestavení zavedeny jako doménově neutrální pro IISADMIN, připojte service můžete dosáhnout přidáním `COMPLUS_LoaderOptimization=1` víceřetězcovou hodnotu prostředí v klíči HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\IISADMIN.  
  
```  
Key = HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\IISADMIN  
Name = Environment  
Type = REG_MULTI_SZ  
Value (to append) = COMPLUS_LoaderOptimization=1  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.AppDomain?displayProperty=nameWithType>
- <xref:System.MarshalByRefObject?displayProperty=nameWithType>
- [Programování s doménami aplikací a sestaveními](index.md)
- [Používání domén aplikací](use.md)
