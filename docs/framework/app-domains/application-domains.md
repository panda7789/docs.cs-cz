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
ms.openlocfilehash: a5c9f4248e060d231941269f39cadbc7147ce27f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399873"
---
# <a name="application-domains"></a>Aplikační domény

Operační systémy a runtime prostředí obvykle poskytují určitou formu izolace mezi aplikacemi. Systém Windows například používá procesy k izolování aplikací. Tato izolace je nezbytná k zajištění, že kód spuštěný v jedné aplikaci nemůže nepříznivě ovlivnit jiné nesouvisející aplikace.  
  
 Aplikační domény poskytují hranice izolace pro zabezpečení, spolehlivost a správu verzí a pro uvolnění sestavení. Domény aplikací jsou obvykle vytvářeny hostiteli runtime, kteří jsou zodpovědní za zasunutí modulu runtime společného jazyka před spuštěním aplikace.  
  
## <a name="the-benefits-of-isolating-applications"></a>Výhody izolace aplikací

 Historicky byly hranice procesu použity k izolátí aplikací spuštěných ve stejném počítači. Každá aplikace je načtena do samostatného procesu, který izoluje aplikaci od jiných aplikací spuštěných ve stejném počítači.  
  
 Aplikace jsou izolované, protože adresy paměti jsou relativní k procesu; ukazatel paměti předaný z jednoho procesu do druhého nelze použít žádným smysluplným způsobem v cílovém procesu. Kromě toho nelze provádět přímé volání mezi dvěma procesy. Místo toho je nutné použít proxy servery, které poskytují úroveň dereference.  
  
 Spravovaný kód musí být před spuštěním předán ověřovacím procesem (pokud správce neudělil oprávnění k přeskočení ověření). Proces ověření určuje, zda se kód může pokusit o přístup k neplatným adresám paměti nebo provést jinou akci, která by mohla způsobit, že proces, ve kterém je spuštěn, nebude správně fungovat. Kód, který projde ověřovací zkouškou, je považován za typově bezpečný. Možnost ověřit kód jako typově bezpečné umožňuje za běhu společného jazyka poskytnout stejně velkou úroveň izolace jako hranice procesu, při mnohem nižších nákladech na výkon.  
  
 Aplikační domény poskytují bezpečnější a univerzálnější jednotku zpracování, kterou může běžný jazyk runtime použít k zajištění izolace mezi aplikacemi. Můžete spustit několik aplikačních domén v jednom procesu se stejnou úrovní izolace, která by existovala v samostatných procesech, ale bez další režie provádění meziprocesových volání nebo přepínání mezi procesy. Možnost spouštět více aplikací v rámci jednoho procesu výrazně zvyšuje škálovatelnost serveru.  
  
 Izolace aplikací je také důležitá pro zabezpečení aplikací. Můžete například spustit ovládací prvky z několika webových aplikací v jednom procesu prohlížeče takovým způsobem, že ovládací prvky nemají přístup k datům a prostředkům ostatních.  
  
 Izolace poskytovaná aplikačními doménami má následující výhody:  
  
- Chyby v jedné aplikaci nemohou ovlivnit jiné aplikace. Vzhledem k tomu, že typově bezpečný kód nemůže způsobit chyby paměti, použití aplikačních domén zajišťuje, že kód spuštěný v jedné doméně nemůže ovlivnit jiné aplikace v procesu.  
  
- Jednotlivé aplikace lze zastavit bez zastavení celého procesu. Použití aplikačních domén umožňuje uvolnit kód spuštěný v jedné aplikaci.  
  
    > [!NOTE]
    > Nelze uvolnit jednotlivá sestavení nebo typy. Lze uvolnit pouze úplnou doménu.  
  
- Kód spuštěný v jedné aplikaci nemůže přímo přistupovat ke kódu nebo prostředkům z jiné aplikace. Běžný jazyk runtime vynucuje tuto izolaci tím, že brání přímé volání mezi objekty v různých aplikačních doménách. Objekty, které procházejí mezi doménami, jsou zkopírovány nebo přístupné prostřednictvím serveru proxy. Pokud je objekt zkopírován, volání objektu je místní. To znamená, že volající i objekt, na který se odkazuje, jsou ve stejné doméně aplikace. Pokud je objekt přístupný prostřednictvím proxy serveru, volání objektu je vzdálené. V tomto případě volající a objekt odkazuje jsou v různých doménách aplikace. Volání mezi doménami používají stejnou infrastrukturu vzdáleného volání jako volání mezi dvěma procesy nebo mezi dvěma počítači. Jako takové metadata pro odkazovaný objekt musí být k dispozici pro obě domény aplikace povolit volání metody, které mají být správně kompilovány JIT. Pokud volající doména nemá přístup k metadatům volaného objektu, může kompilace selhat s výjimkou typu <xref:System.IO.FileNotFoundException>. Další informace naleznete [v tématu Vzdálené objekty](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100)). Mechanismus pro určení, jak lze přistupovat k objektům napříč doménami, je určen objektem. Další informace naleznete v tématu <xref:System.MarshalByRefObject?displayProperty=nameWithType>.  
  
- Chování kódu je vymezeno aplikací, ve které je spuštěn. Jinými slovy, doména aplikace poskytuje nastavení konfigurace, jako jsou zásady verze aplikace, umístění všech vzdálených sestavení, ke kterým přistupuje, a informace o tom, kde najít sestavení načtená do domény.  
  
- Oprávnění udělená kódu mohou být řízena doménou aplikace, ve které je kód spuštěn.  
  
## <a name="application-domains-and-assemblies"></a>Domény a sestavení aplikací

 Tato část popisuje vztah mezi aplikačními doménami a sestaveními. Před spuštěním kódu, který obsahuje, je nutné načíst sestavení do domény aplikace. Spuštění typické aplikace způsobí, že několik sestavení, které mají být načteny do domény aplikace.  
  
 Způsob, jakým je načten oseka sestavení určuje, zda jeho just-in-time (JIT) zkompilovaný kód může být sdílena více aplikačních domén v procesu a zda sestavení lze uvolnit z procesu.  
  
- Pokud je sestavení načteno neutrální z domény, všechny domény aplikace, které sdílejí stejnou sadu grantů zabezpečení, mohou sdílet stejný kód zkompilovaný JIT, což snižuje paměť požadovanou aplikací. Sestavení však nelze nikdy uvolnit z procesu.  
  
- Pokud sestavení není načteno neutrální domény, musí být kompilován JIT v každé doméně aplikace, ve které je načten. Sestavení však může být uvolněna z procesu uvolněním všech domén aplikace, ve kterém je načten.  
  
 Hostitel runtime určuje, zda má být načíst sestavení jako neutrální domény při načtení runtime do procesu. Pro spravované aplikace <xref:System.LoaderOptimizationAttribute> použijte atribut pro metodu vstupního bodu pro proces <xref:System.LoaderOptimization> a zadejte hodnotu z přidruženého výčtu. Pro nespravované aplikace, které jsou hostiteli za běhu společného jazyka, zadejte příslušný příznak při volání metody [Funkce CorBindToRuntimeEx.](../unmanaged-api/hosting/corbindtoruntimeex-function.md)  
  
 Existují tři možnosti pro načítání neutrálních sestavení domény:  
  
- <xref:System.LoaderOptimization.SingleDomain?displayProperty=nameWithType>načte žádná sestavení jako neutrální domény, s výjimkou Mscorlib, který je vždy načten domény neutrální. Toto nastavení se nazývá jedna doména, protože se běžně používá, když hostitel používá pouze jednu aplikaci v procesu.

- <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType>načte všechna sestavení jako neutrální z domény. Toto nastavení použijte, pokud je v procesu více aplikačních domén, které spouštějí stejný kód.

- <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType>načte sestavení se silným názvem jako neutrální domény, pokud byly nainstalovány oni a všechny jejich závislosti v globální mezipaměti sestavení. Ostatní sestavení jsou načteny a JIT kompilovány samostatně pro každou doménu aplikace, ve které jsou načteny, a proto mohou být uvolněny z procesu. Toto nastavení použijte při spuštění více než jedné aplikace ve stejném procesu nebo pokud máte směs sestavení, které jsou sdíleny mnoha aplikačních domén a sestavení, které je třeba uvolnit z procesu.
  
 Jit kompilovaný kód nelze sdílet pro sestavení načtená do <xref:System.Reflection.Assembly.LoadFrom%2A> kontextu load-from, pomocí metody <xref:System.Reflection.Assembly> třídy <xref:System.Reflection.Assembly.Load%2A> nebo načtená z bitových kopií pomocí přetížení metody, která určují bajtová pole.  
  
 Sestavení, která byla zkompilována do nativního kódu pomocí [ngen.exe (Native Image Generator),](../tools/ngen-exe-native-image-generator.md) mohou být sdílena mezi doménami aplikace, pokud jsou načteny neutrální domény při prvním načtení do procesu.  
  
 JIT kompilovaný kód pro sestavení, který obsahuje vstupní bod aplikace je sdílena pouze v případě, že všechny jeho závislosti lze sdílet.  
  
 Neutrální sestavení domény může být jit kompilován více než jednou. Například pokud se liší sady grantů zabezpečení dvou aplikačních domén, nemohou sdílet stejný kód zkompilovaný JIT. Každá kopie sestavení zkompilovaného JIT však může být sdílena s jinými aplikačními doménami, které mají stejnou sadu grantů.  
  
 Při rozhodování, zda načíst sestavení jako neutrální domény, je nutné provést kompromis mezi sníženívyužití paměti a další faktory výkonu.  
  
- Přístup ke statickým datům a metodám je pomalejší pro sestavení neutrální z domény z důvodu nutnosti izolovat sestavení. Každá aplikační doména, která přistupuje k sestavení, musí mít samostatnou kopii statických dat, aby odkazy na objekty ve statických polích nepřekročily hranice domény. V důsledku toho runtime obsahuje další logiku nasměrovat volajícího na příslušnou kopii statických dat nebo metody. Tato další logika zpomaluje volání.  
  
- Všechny závislosti sestavení musí být lokalizovány a načteny při načítání sestavení neutrální domény, protože závislost, která nemůže být načtena neutrální domény zabraňuje načtení neutrální ho sestavení domény.  
  
## <a name="application-domains-and-threads"></a>Aplikační domény a vlákna

 Doména aplikace tvoří hranici izolace pro zabezpečení, správu verzí, spolehlivost a uvolnění spravovaného kódu. Vlákno je konstrukce operačního systému používaná běžným jazykem runtime ke spuštění kódu. Za běhu je veškerý spravovaný kód načten do domény aplikace a je spuštěn jedním nebo více spravovanými vlákny.  
  
 Neexistuje korelace 1:1 mezi doménami aplikace a vlákny. Několik podprocesů lze spustit v jedné doméně aplikace v daném okamžiku a konkrétní vlákno není omezena na jednu doménu aplikace. To znamená, že vlákna mohou volně překračovat hranice domény aplikace; nové vlákno není vytvořeno pro každou doménu aplikace.  
  
 V každém okamžiku se každé vlákno spustí v doméně aplikace. Nula, jeden nebo více vláken může být provádění v dané doméně aplikace. Runtime sleduje, která vlákna jsou spuštěna ve kterých aplikačních doménách. Můžete vyhledat doménu, ve které je vlákno spuštěno <xref:System.Threading.Thread.GetDomain%2A?displayProperty=nameWithType> kdykoli voláním metody.

### <a name="application-domains-and-cultures"></a>Aplikační domény a jazykové verze

 Jazyková verze, která <xref:System.Globalization.CultureInfo> je reprezentována objektem, je přidružena k vláknům. Můžete získat jazykovou verzi, která je přidružena k <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> aktuálně spuštěné vlákno pomocí vlastnosti a můžete získat nebo nastavit <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> jazykovou verzi, která je přidružena k aktuálně spuštěné vlákno pomocí vlastnosti. Pokud jazyková verze, která je přidružena k <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> podprocesu byla explicitně nastavena pomocí vlastnosti, bude i nadále přidružena k tomuto vláknu, když vlákno překročí hranice domény aplikace. V opačném případě je jazyková verze, která je přidružena <xref:System.Globalization.CultureInfo.DefaultThreadCurrentCulture%2A?displayProperty=nameWithType> k podprocesu v daném okamžiku, určena hodnotou vlastnosti v doméně aplikace, ve které je vlákno spuštěno:  
  
- Pokud hodnota vlastnosti není `null`, jazyková verze, která je vrácena vlastností je <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> přidružena k podprocesu (a proto vrácena vlastnostmi a).  
  
- Pokud je `null`hodnota vlastnosti , aktuální jazyková verze systému je přidružena k vláknu.  
  
## <a name="programming-with-application-domains"></a>Programování s aplikačními doménami

 Aplikační domény jsou obvykle vytvářeny a řízeny programově hostiteli za běhu. Někdy však může aplikační program také chtít pracovat s aplikačními doménami. Aplikační program může například načíst součást aplikace do domény, aby bylo možné uvolnit doménu (a komponentu), aniž by bylo třeba zastavit celou aplikaci.  
  
 Jedná <xref:System.AppDomain> se o programové rozhraní k aplikačním doménám. Tato třída zahrnuje metody pro vytváření a uvolňování domén, k vytvoření instancí typů v doménách a k registraci různých oznámení, jako je například uvolnění domény aplikace. V následující tabulce jsou <xref:System.AppDomain> uvedeny běžně používané metody.  
  
|Metoda Domény aplikace|Popis|  
|----------------------|-----------------|  
|<xref:System.AppDomain.CreateDomain%2A>|Vytvoří novou doménu aplikace. Doporučuje se použít přetížení této metody, která <xref:System.AppDomainSetup> určuje objekt. Toto je upřednostňovaný způsob nastavení vlastností nové domény, jako je například základ aplikace nebo kořenový adresář aplikace. umístění konfiguračního souboru pro doménu; a vyhledávací cestu, která je za běhu společného jazyka použít k načtení sestavení do domény.|  
|<xref:System.AppDomain.ExecuteAssembly%2A> a <xref:System.AppDomain.ExecuteAssemblyByName%2A>|Spustí sestavení v doméně aplikace. Jedná se o metodu instance, takže ji lze použít ke spuštění kódu v jiné doméně aplikace, na kterou máte odkaz.|  
|<xref:System.AppDomain.CreateInstanceAndUnwrap%2A>|Vytvoří instanci zadaného typu v doméně aplikace a vrátí proxy server. Tuto metodu použijte, abyste se vyhnuli načítání sestavení obsahujícího vytvořený typ do volajícího sestavení.|  
|<xref:System.AppDomain.Unload%2A>|Provede řádné vypnutí domény. Doména aplikace není uvolněna, dokud se všechna vlákna spuštěná v doméně nezastavila nebo již nejsou v doméně.|  
  
> [!NOTE]
> Běžný jazyk runtime nepodporuje serializaci globálních metod, takže delegáti nelze použít ke spuštění globálních metod v jiných aplikačních doménách.  
  
 Nespravovaná rozhraní popsaná ve specifikaci common language runtime hosting interfaces také poskytují přístup k aplikačním doménám. Hostitelé runtime mohou používat rozhraní z nespravovaného kódu k vytvoření a získání přístupu k aplikačním doménám v rámci procesu.  
  
## <a name="the-complus_loaderoptimization-environment-variable"></a>Proměnná prostředí COMPLUS_LoaderOptimization

 Proměnná prostředí, která nastavuje výchozí zásadu optimalizace zavaděče spustitelné aplikace.  
  
### <a name="syntax"></a>Syntaxe  
  
```env  
COMPLUS_LoaderOptimization = 1  
```  
  
### <a name="remarks"></a>Poznámky

 Typická aplikace načte několik sestavení do domény aplikace před kód, který obsahují mohou být provedeny.  
  
 Způsob, jakým je načten oseka, určuje, zda jeho kompilovaný kód za čase (JIT) může být sdílen více aplikačními doménami v procesu.  
  
- Pokud je sestavení načteno neutrální z domény, všechny domény aplikace, které sdílejí stejnou sadu grantů zabezpečení, mohou sdílet stejný kód zkompilovaný JIT. To snižuje paměť požadovanou aplikací.  
  
- Pokud sestavení není načteno neutrální domény, musí být kompilován JIT v každé doméně aplikace, ve které je načteno, a zavaděč nesmí sdílet interní prostředky mezi doménami aplikace.  
  
 Pokud je nastavena na 1, příznak prostředí COMPLUS_LoaderOptimization vynutí hostitele runtime načíst všechna sestavení v nedomény neutrální způsobem známý jako SingleDomain. SingleDomain načte žádná sestavení jako neutrální domény, s výjimkou Mscorlib, který je vždy načten domény neutrální. Toto nastavení se nazývá jedna doména, protože se běžně používá, když hostitel používá pouze jednu aplikaci v procesu.  
  
> [!CAUTION]
> Příznak prostředí COMPLUS_LoaderOptimization byl navržen pro použití v diagnostických a testovacích scénářích. Zapnutí příznaku může způsobit výrazné zpomalení a zvýšení využití paměti.  
  
### <a name="code-example"></a>Příklad kódu

 Vynutit, aby všechna sestavení nebyla načtena jako neutrální pro službu `COMPLUS_LoaderOptimization=1` IISADMIN neutrální, lze dosáhnout připojením k multiřetězcové hodnotě prostředí v klíči HKEY_LOCAL_MACHINE\CURRENTControlSet\services\IISADMIN.  
  
```env  
Key = HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\IISADMIN  
Name = Environment  
Type = REG_MULTI_SZ  
Value (to append) = COMPLUS_LoaderOptimization=1  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.AppDomain?displayProperty=nameWithType>
- <xref:System.MarshalByRefObject?displayProperty=nameWithType>
- [Programování s doménami aplikací a sestaveními](index.md)
- [Používání domén aplikací](use.md)
