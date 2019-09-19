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
ms.openlocfilehash: 4a0a6a00fc76a646b4295db726bd8ae67733e321
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053224"
---
# <a name="application-domains"></a>Aplikační domény

Operační systémy a běhová prostředí obvykle poskytují určitou formu izolace mezi aplikacemi. Například Windows používá procesy k izolaci aplikací. Tato izolace je nutná k zajištění toho, aby kód spuštěný v jedné aplikaci nepříznivě ovlivnil jiné nesouvisející aplikace.  
  
 Aplikační domény poskytují hranici izolace pro zabezpečení, spolehlivost a správu verzí a pro uvolňování sestavení. Domény aplikace jsou obvykle vytvářeny hostiteli modulu runtime, což zodpovídá za zavedení modulu CLR (Common Language Runtime) před spuštěním aplikace.  
  
## <a name="the-benefits-of-isolating-applications"></a>Výhody izolace aplikací

 Historické hranice procesů byly použity k izolaci aplikací spuštěných ve stejném počítači. Každá aplikace se načte do samostatného procesu, který izoluje aplikaci od ostatních aplikací běžících ve stejném počítači.  
  
 Aplikace jsou izolované, protože paměťové adresy jsou relativní vzhledem k procesu; ukazatel na paměť předaný z jednoho procesu na jiný nelze použít v smysluplném způsobu v cílovém procesu. Kromě toho nelze mezi dvěma procesy uskutečnit Přímá volání. Místo toho je nutné použít proxy servery, které poskytují úroveň nepřímých odkazů.  
  
 Spravovaný kód musí být před spuštěním ověřovacího procesu předán (Pokud správce neudělil oprávnění k přeskočení ověření). Proces ověřování určuje, zda se může kód pokusit o přístup k neplatným adresám paměti nebo provedení jiné akce, která by mohla způsobit, že proces, ve kterém je spuštěný, nefunguje správně. Kód, který projde ověřovacím testem, je označován jako typově bezpečný. Možnost ověřování kódu jako bezpečného typu umožňuje, aby modul CLR (Common Language Runtime) poskytoval jako skvělou úroveň izolace jako hranici procesu, a to s mnohem nižšími náklady na výkon.  
  
 Aplikační domény poskytují bezpečnější a všestrannou jednotku zpracování, kterou může modul CLR (Common Language Runtime) použít k zajištění izolace mezi aplikacemi. V jednom procesu můžete spustit několik aplikačních domén se stejnou úrovní izolace, která by existovala v samostatných procesech, ale bez dalších režijních procesů a přepínání mezi procesy. Možnost spouštět více aplikací v rámci jednoho procesu výrazně zvyšuje škálovatelnost serveru.  
  
 Izolace aplikací je také důležité pro zabezpečení aplikací. Můžete například spouštět ovládací prvky z několika webových aplikací v jednom procesu prohlížeče takovým způsobem, že ovládací prvky nemají přístup k datům a prostředkům druhé strany.  
  
 Izolace poskytovaná aplikačními doménami má následující výhody:  
  
- Chyby v jedné aplikaci nemohou ovlivnit jiné aplikace. Vzhledem k tomu, že kód zajišťující bezpečnost typů nemůže způsobit chyby paměti, může použití domén aplikací zajistit, aby kód spuštěný v jedné doméně neovlivnil jiné aplikace v tomto procesu.  
  
- Jednotlivé aplikace lze zastavit bez zastavení celého procesu. Použití aplikačních domén umožňuje uvolnit kód spuštěný v jedné aplikaci.  
  
    > [!NOTE]
    > Nelze uvolnit jednotlivá sestavení nebo typy. Pouze úplná doména může být uvolněna.  
  
- Kód spuštěný v jedné aplikaci nemůže přistupovat přímo k kódu nebo prostředkům z jiné aplikace. Modul CLR (Common Language Runtime) vynutil tuto izolaci tím, že zabraňuje přímému volání mezi objekty v různých aplikačních doménách. Objekty, které jsou předávány mezi doménami, jsou buď zkopírovány nebo otevřeny serverem proxy. Pokud je objekt zkopírován, volání objektu je místní. To znamená, že volající i odkazovaný objekt jsou ve stejné doméně aplikace. Pokud je objekt otevřen prostřednictvím proxy serveru, volání objektu je vzdálené. V tomto případě je volající a odkazovaný objekt v různých doménách aplikace. Volání mezi doménami používají stejnou infrastrukturu vzdáleného volání jako volání mezi dvěma procesy nebo mezi dvěma počítači. V takovém případě musí být metadata odkazovaného objektu k dispozici v obou doménách aplikace, aby bylo možné volání metody správně zkompilovat JIT. Pokud volající doména nemá přístup k metadatům pro objekt, který je volán, kompilace může selhat s výjimkou typu <xref:System.IO.FileNotFoundException>. Další informace najdete v tématu [vzdálené objekty](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100)). Mechanismus pro určení způsobu, jakým lze objekty používat napříč doménami, je určen objektem. Další informace naleznete v tématu <xref:System.MarshalByRefObject?displayProperty=nameWithType>.  
  
- Chování kódu je vymezeno aplikací, ve které běží. Jinými slovy aplikační doména poskytuje nastavení konfigurace, jako jsou například zásady verze aplikace, umístění všech vzdálených sestavení, ke kterým přistupuje, a informace o tom, kde najít sestavení, která jsou načtena do domény.  
  
- Oprávnění udělená kódu mohou být řízena doménou aplikace, ve které kód běží.  
  
## <a name="application-domains-and-assemblies"></a>Aplikační domény a sestavení

 Tato část popisuje vztah mezi doménami aplikace a sestaveními. Před spuštěním kódu, který obsahuje, je nutné načíst sestavení do domény aplikace. Spuštění typické aplikace způsobí, že se do domény aplikace načtou několik sestavení.  
  
 Způsob, jakým je sestavení načteno, určuje, zda je jeho zkompilovaný kód just-in-time (JIT) sdílen více doménami aplikace v procesu a zda může být sestavení uvolněno z procesu.  
  
- Pokud je sestavení načteno jako doménově neutrální, všechny domény aplikace, které sdílejí stejnou sadu oprávnění zabezpečení, mohou sdílet stejný kód zkompilovaný JIT, což snižuje velikost paměti vyžadované aplikací. Sestavení ale nemůže být nikdy uvolněno z procesu.  
  
- Pokud sestavení není načteno jako doménově neutrální, musí být kompilována JIT v každé doméně aplikace, ve které je načtena. Sestavení lze však uvolnit z procesu uvolněním všech domén aplikace, ve kterých je načtena.  
  
 Hostitel modulu runtime určuje, zda mají být sestavení načtena jako doménově neutrální při načtení modulu runtime do procesu. U spravovaných aplikací použijte <xref:System.LoaderOptimizationAttribute> atribut pro metodu vstupního bodu pro proces a zadejte hodnotu z asociovaného <xref:System.LoaderOptimization> výčtu. U nespravovaných aplikací, které jsou hostiteli modulu CLR (Common Language Runtime), zadejte vhodný příznak při volání metody [CorBindToRuntimeEx – Function](../unmanaged-api/hosting/corbindtoruntimeex-function.md) .  
  
 Existují tři možnosti, jak načíst doménově neutrální sestavení:  
  
- <xref:System.LoaderOptimization.SingleDomain?displayProperty=nameWithType>nenačítá žádná sestavení jako doménově neutrální, s výjimkou mscorlib, která je vždy zavedena jako doménově neutrální. Toto nastavení se nazývá jediná doména, protože se běžně používá v případě, že je na hostiteli spuštěná jenom jedna aplikace v procesu.

- <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType>načte všechna sestavení jako doménově neutrální. Toto nastavení použijte v případě, že v procesu existuje více domén aplikace, z nichž každý spouští stejný kód.

- <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType>Načte sestavení se silným názvem jako doménově neutrální, pokud jsou a všechny jejich závislosti byly nainstalovány v globální mezipaměti sestavení (GAC). Další sestavení jsou načtena a kompilována JIT samostatně pro každou doménu aplikace, ve které jsou načtena, a proto mohou být z procesu uvolněna. Toto nastavení použijte při spuštění více než jedné aplikace v jednom procesu nebo v případě, že máte směs sestavení, která jsou sdílena mnoha doménami aplikace a sestaveními, které je potřeba z procesu uvolnit.
  
 Kód zkompilovaný JIT nelze sdílet pro sestavení, která jsou načtena do kontextu load-from, pomocí <xref:System.Reflection.Assembly.LoadFrom%2A> metody <xref:System.Reflection.Assembly> třídy nebo načtena z imagí pomocí přetížení <xref:System.Reflection.Assembly.Load%2A> metody, která určuje Bajtová pole.  
  
 Sestavení, která byla zkompilována do nativního kódu pomocí nástroje [Ngen. exe (generátor nativních bitových kopií)](../tools/ngen-exe-native-image-generator.md) , lze sdílet mezi doménami aplikace, pokud jsou při prvním načtení do procesu načtena doménově neutrální.  
  
 Kód zkompilovaný JIT pro sestavení, které obsahuje vstupní bod aplikace, je sdílen pouze v případě, že lze sdílet všechny jeho závislosti.  
  
 Sestavení neutrální v doméně může být kompilováno kompilátorem JIT více než jednou. Například pokud je sada udělení zabezpečení dvou aplikačních domén odlišná, nemůže sdílet stejný kód zkompilovaný JIT. Každá kopie sestavení zkompilovaného JIT však může být sdílena s ostatními aplikačními doménami, které mají stejnou sadu udělení.  
  
 Pokud se rozhodnete, zda mají být sestavení načtena jako doménově neutrální, je nutné provést kompromis mezi snížením využití paměti a dalšími faktory výkonu.  
  
- Přístup ke statickým datům a metodám je pro doménově neutrální sestavení pomalejší, protože je potřeba izolovat sestavení. Každá doména aplikace, která přistupuje k sestavení, musí mít samostatnou kopii statických dat, aby se zabránilo odkazům na objekty ve statických polích z překročení hranice domény. V důsledku toho modul runtime obsahuje další logiku pro přesměrování volajícího na příslušnou kopii statických dat nebo metody. Tato dodatečná logika zpomaluje volání.  
  
- Všechny závislosti sestavení musí být umístěny a načteny, když je sestavení načteno jako doménově neutrální, protože závislost, která nemůže být načtena doménově neutrální, zabraňuje sestavení v načtení domény-neutrální.  
  
## <a name="application-domains-and-threads"></a>Domény aplikace a vlákna

 Aplikační doména tvoří hranici izolace pro zabezpečení, správu verzí, spolehlivost a uvolňování spravovaného kódu. Vlákno je konstrukce operačního systému používaná modulem CLR (Common Language Runtime) ke spouštění kódu. V době běhu se všechen spravovaný kód načte do aplikační domény a spustí se v jednom nebo více spravovaných vláknech.  
  
 Mezi doménami a vlákny aplikace neexistuje korelace 1:1. V jednom okamžiku může být několik vláken spuštěno v jedné doméně aplikace a určité vlákno není omezeno na jednu doménu aplikace. To znamená, že vlákna jsou volna mezi hranice aplikační domény. pro každou doménu aplikace se nevytvoří nové vlákno.  
  
 V každém okamžiku se každé vlákno spustí v doméně aplikace. Nula, jedno nebo více vláken může být spuštěno v jakékoli dané doméně aplikace. Modul runtime uchovává přehled o tom, která vlákna jsou spuštěna, v nichž jsou domény aplikace spuštěny. Doménu, ve které je vlákno spuštěno, můžete najít kdykoli voláním <xref:System.Threading.Thread.GetDomain%2A?displayProperty=nameWithType> metody.

### <a name="application-domains-and-cultures"></a>Domény a jazykové verze aplikace

 Jazyková verze, která je reprezentována <xref:System.Globalization.CultureInfo> objektem, je přidružena k vláknům. Můžete získat jazykovou verzi, která je přidružená k aktuálně spuštěnému vláknu <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> pomocí vlastnosti, a můžete získat nebo nastavit jazykovou verzi, která je přidružená k aktuálně spuštěnému vláknu <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> pomocí vlastnosti. Pokud je jazyková verze, která je přidružena k vláknu, explicitně nastavena pomocí <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> vlastnosti, je nadále přidružena k danému vláknu, pokud vlákno překračuje hranice aplikační domény. V opačném případě je jazyková verze, která je přidružena k vláknu v daném čase, určena hodnotou <xref:System.Globalization.CultureInfo.DefaultThreadCurrentCulture%2A?displayProperty=nameWithType> vlastnosti v doméně aplikace, ve které je vlákno spuštěno:  
  
- Pokud hodnota vlastnosti `null`není, jazyková verze, která je vrácena vlastností, je přidružena k vláknu (a tedy vráceny <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> pomocí vlastností a <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> ).  
  
- Pokud je `null`hodnota vlastnosti, je aktuální jazyková verze systému přidružena k vláknu.  
  
## <a name="programming-with-application-domains"></a>Programování s aplikačními doménami

 Domény aplikace jsou obvykle vytvářeny a manipulují programově pomocí hostitelů modulu runtime. Někdy však může aplikace chtít pracovat i s doménami aplikace. Například program aplikace může načíst součást aplikace do domény, aby bylo možné uvolnit doménu (a komponentu) bez nutnosti zastavit celou aplikaci.  
  
 <xref:System.AppDomain> Je programové rozhraní k aplikačním doménám. Tato třída obsahuje metody pro vytváření a uvolňování domén, k vytvoření instancí typů v doménách a k registraci různých oznámení, jako je například uvolnění domény aplikace. V následující tabulce jsou uvedeny běžně <xref:System.AppDomain> používané metody.  
  
|AppDomain – metoda|Popis|  
|----------------------|-----------------|  
|<xref:System.AppDomain.CreateDomain%2A>|Vytvoří novou doménu aplikace. Doporučuje se použít přetížení této metody, která určuje <xref:System.AppDomainSetup> objekt. Toto je upřednostňovaný způsob, jak nastavit vlastnosti nové domény, jako je například základ aplikace nebo kořenový adresář aplikace. umístění konfiguračního souboru pro doménu; a cestu pro hledání, kterou modul CLR (Common Language Runtime) používá k načtení sestavení do domény.|  
|<xref:System.AppDomain.ExecuteAssembly%2A> a <xref:System.AppDomain.ExecuteAssemblyByName%2A>|Spustí sestavení v doméně aplikace. Toto je metoda instance, takže ji lze použít ke spouštění kódu v jiné doméně aplikace, ke které máte odkaz.|  
|<xref:System.AppDomain.CreateInstanceAndUnwrap%2A>|Vytvoří instanci zadaného typu v doméně aplikace a vrátí proxy. Tuto metodu použijte, chcete-li zabránit načtení sestavení obsahujícího typ do volajícího sestavení.|  
|<xref:System.AppDomain.Unload%2A>|Provede řádné vypnutí domény. Aplikační doména není uvolněna, dokud nebudou všechny podprocesy spuštěné v doméně buď zastaveny, nebo již nejsou v doméně.|  
  
> [!NOTE]
> Modul CLR (Common Language Runtime) nepodporuje serializaci globálních metod, takže delegáty nelze použít ke spouštění globálních metod v jiných doménách aplikace.  
  
 Nespravovaná rozhraní, která jsou popsána ve specifikaci rozhraní hostování Common Language Runtime, poskytují také přístup k doménám aplikace. Hostitelé modulu runtime mohou používat rozhraní z nespravovaného kódu k vytvoření a získání přístupu k doménám aplikace v rámci procesu.  
  
## <a name="the-complus_loaderoptimization-environment-variable"></a>Proměnná prostředí COMPLUS_LoaderOptimization

 Proměnná prostředí, která nastavuje výchozí zásady optimalizace zavaděče spustitelné aplikace.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
COMPLUS_LoaderOptimization = 1  
```  
  
### <a name="remarks"></a>Poznámky

 Typická aplikace načítá několik sestavení do aplikační domény před tím, než je kód, který obsahují, lze spustit.  
  
 Způsob, jakým je sestavení načteno, určuje, zda je jeho zkompilovaný kód JIT (just-in-time) sdílen více doménami aplikace v rámci procesu.  
  
- Pokud je sestavení načteno jako doménově neutrální, všechny domény aplikace, které sdílejí stejnou sadu oprávnění zabezpečení, mohou sdílet stejný kód zkompilovaný JIT. Tím se zmenší paměť požadovaná aplikací.  
  
- Pokud sestavení není načteno jako doménově neutrální, musí být kompilována JIT v každé doméně aplikace, ve které je načtena, a zavaděč nesmí sdílet interní prostředky mezi doménami aplikace.  
  
 Pokud je nastavena na hodnotu 1, příznak prostředí COMPLUS_LoaderOptimization vynutí, aby hostitel modulu runtime načetl všechna sestavení v nedoménově neutrálním tvaru známém jako SingleDomain. SingleDomain nenačítá žádná sestavení jako doménově neutrální, s výjimkou mscorlib, která je vždy zavedena jako doménově neutrální. Toto nastavení se nazývá jediná doména, protože se běžně používá v případě, že je na hostiteli spuštěná jenom jedna aplikace v procesu.  
  
> [!CAUTION]
> Příznak prostředí COMPLUS_LoaderOptimization byl navržen pro použití v diagnostických a testovacích scénářích. Pokud je příznak zapnutý, může dojít k závažnému zpomalení a zvýšení využití paměti.  
  
### <a name="code-example"></a>Příklad kódu

 Chcete-li vynutit, aby se všechna sestavení nenačítala jako doménově neutrální pro službu IISADMIN, je možné `COMPLUS_LoaderOptimization=1` dosáhnout připojením k hodnotě s více řetězci v prostředí HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\IISADMIN klíče.  
  
```  
Key = HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\IISADMIN  
Name = Environment  
Type = REG_MULTI_SZ  
Value (to append) = COMPLUS_LoaderOptimization=1  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.AppDomain?displayProperty=nameWithType>
- <xref:System.MarshalByRefObject?displayProperty=nameWithType>
- [Programování s aplikačními doménami a sestaveními](index.md)
- [Používání domén aplikací](use.md)
