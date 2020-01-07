---
title: Zápis vlastního hostitele modulu runtime .NET Core
description: Naučte se hostovat modul runtime .NET Core z nativního kódu pro podporu pokročilých scénářů, které vyžadují řízení fungování modulu runtime .NET Core.
author: mjrousos
ms.date: 12/21/2018
ms.custom: seodec18
ms.openlocfilehash: b4d36d1ded3af1c6f1181712080e9fcd18a5a468
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75339725"
---
# <a name="write-a-custom-net-core-host-to-control-the-net-runtime-from-your-native-code"></a>Zápis vlastního hostitele .NET Core pro řízení modulu .NET runtime z vašeho nativního kódu

Stejně jako všechny spravované kódy jsou aplikace .NET Core spouštěny hostitelem. Hostitel zodpovídá za spuštění modulu runtime (včetně součástí, jako je například JIT a systém uvolňování paměti) a vyvolává spravované vstupní body.

Hostování modulu runtime .NET Core je pokročilý scénář a ve většině případů se vývojáři .NET Core nemusejí starat o hostování, protože procesy sestavení .NET Core poskytují výchozímu hostiteli spouštění aplikací .NET Core. V některých specializovaných případech může být užitečné explicitně hostovat modul runtime .NET Core, a to buď jako způsob vyvolání spravovaného kódu v nativním procesu, nebo aby bylo možné získat větší kontrolu nad tím, jak funguje modul runtime.

Tento článek obsahuje přehled kroků nezbytných ke spuštění modulu runtime .NET Core z nativního kódu a spuštění spravovaného kódu.

## <a name="prerequisites"></a>Požadavky

Vzhledem k tomu, že hostitelé jsou nativní aplikace, tento C++ kurz popisuje vytvoření aplikace pro hostování .NET Core. Budete potřebovat C++ vývojové prostředí (například to, které poskytuje [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)).

Budete také chtít, aby hostitel v rámci aplikace .NET Core otestoval hostitele. proto byste měli nainstalovat [.NET Core SDK](https://dotnet.microsoft.com/download) a [vytvořit malou testovací aplikaci .NET Core](with-visual-studio.md) (například aplikaci Hello World). Je dostačující aplikace Hello World vytvořená novou šablonou projektu konzoly .NET Core.

## <a name="hosting-apis"></a>Hostování rozhraní API
Existují tři různá rozhraní API, která lze použít k hostování .NET Core. Tento článek (a jeho přidružené [ukázky](https://github.com/dotnet/samples/tree/master/core/hosting)) se zabývá všemi možnostmi.

* Upřednostňovanou metodou hostování modulu runtime .NET Core v rozhraní .NET Core 3,0 a vyšším je rozhraní API `nethost` a `hostfxr` knihovny. Tyto vstupní body zpracovávají složitost hledání a nastavení modulu runtime pro inicializaci a umožňují spouštění spravované aplikace a volání do statické spravované metody.
* Upřednostňovanou metodou hostování modulu runtime .NET Core před rozhraním .NET Core 3,0 je rozhraní API [CoreClrHost. h](https://github.com/dotnet/coreclr/blob/master/src/coreclr/hosts/inc/coreclrhost.h) . Toto rozhraní API zpřístupňuje funkce pro snadné spouštění a zastavování modulu runtime a vyvolání spravovaného kódu (buď spuštěním spravovaného souboru exe, nebo voláním statických spravovaných metod).
* Rozhraní .NET Core lze také hostovat s rozhraním `ICLRRuntimeHost4` v [knihovně Mscoree. h](https://github.com/dotnet/coreclr/blob/master/src/pal/prebuilt/inc/mscoree.h). Toto rozhraní API bylo asi delší než CoreClrHost. h, takže jste se mohli setkat s jeho staršími hostiteli. Pořád funguje a umožňuje nad hostitelským procesem větší kontrolu než CoreClrHost. U většiny scénářů se ale CoreClrHost. h upřednostňuje teď z důvodu jednodušších rozhraní API.

## <a name="sample-hosts"></a>Ukázkové hostitele
[Příklady hostitelů](https://github.com/dotnet/samples/tree/master/core/hosting) , které demonstrují kroky popsané v následujících kurzech, jsou k dispozici v úložišti GitHub/Samples GitHub. Komentáře v ukázkách jasně přiřazují očíslované kroky z těchto kurzů s tím, kde jsou provedeny v ukázce. Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Mějte na paměti, že Ukázkoví hostitelé se mají použít ke studijním účelům, takže mají světlou kontrolu chyb a jsou navržené pro zdůraznění čitelnosti v průběhu efektivity.

## <a name="create-a-host-using-nethosth-and-hostfxrh"></a>Vytvoření hostitele pomocí NetHost. h a HostFxr. h

Následující kroky podrobně popisují, jak pomocí knihoven `nethost` a `hostfxr` spustit modul runtime .NET Core v nativní aplikaci a volat do spravované statické metody. [Ukázka](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithHostFxr) používá hlavičku `nethost` a knihovnu nainstalovanou se sadou .NET SDK a kopie [`coreclr_delegates.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/coreclr_delegates.h) a [`hostfxr.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/hostfxr.h) souborů z úložiště [dotnet/Core-Setup](https://github.com/dotnet/core-setup) .

### <a name="step-1---load-hostfxr-and-get-exported-hosting-functions"></a>Krok 1 – načtení HostFxr a získání exportovaných funkcí hostování

Knihovna `nethost` poskytuje funkci `get_hostfxr_path` pro vyhledání knihovny `hostfxr`. Knihovna `hostfxr` zpřístupňuje funkce pro hostování modulu runtime .NET Core. Úplný seznam funkcí najdete v [`hostfxr.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/hostfxr.h) a v [nativním dokumentu návrhu hostování](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/native-hosting.md). Ukázka a tento kurz používá následující:

* `hostfxr_initialize_for_runtime_config`: inicializuje hostitelský kontext a připraví inicializaci modulu runtime .NET Core pomocí zadané konfigurace modulu runtime.
* `hostfxr_get_runtime_delegate`: Získá delegáta pro běhovou funkčnost.
* `hostfxr_close`: zavře hostitelský kontext.

Knihovna `hostfxr` se našla pomocí `get_hostfxr_path`. Pak se načte a jeho exporty se načtou.

[!code-cpp[HostFxrHost#LoadHostFxr](~/samples/core/hosting/HostWithHostFxr/src/NativeHost/nativehost.cpp#LoadHostFxr)]

### <a name="step-2---initialize-and-start-the-net-core-runtime"></a>Krok 2 – inicializace a spuštění modulu runtime .NET Core

Funkce `hostfxr_initialize_for_runtime_config` a `hostfxr_get_runtime_delegate` Inicializuje a spustí modul runtime .NET Core pomocí konfigurace modulu runtime pro spravovanou komponentu, která bude načtena. Funkce `hostfxr_get_runtime_delegate` slouží k získání delegáta modulu runtime, který umožňuje načíst spravované sestavení a získat ukazatel funkce na statickou metodu v tomto sestavení.

[!code-cpp[HostFxrHost#Initialize](~/samples/core/hosting/HostWithHostFxr/src/NativeHost/nativehost.cpp#Initialize)]

### <a name="step-3---load-managed-assembly-and-get-function-pointer-to-a-managed-method"></a>Krok 3 – načtení spravovaného sestavení a získání ukazatele na spravovanou metodu

Delegát modulu runtime je volán pro načtení spravovaného sestavení a získání ukazatele na funkci spravované metody. Delegát vyžaduje cestu sestavení, název typu a název metody jako vstupy a vrátí ukazatel na funkci, který lze použít k vyvolání spravované metody.

[!code-cpp[HostFxrHost#LoadAndGet](~/samples/core/hosting/HostWithHostFxr/src/NativeHost/nativehost.cpp#LoadAndGet)]

Předáním `nullptr` jako názvu typu delegáta při volání delegáta modulu runtime používá ukázka výchozí signaturu pro spravovanou metodu:

```csharp
public delegate int ComponentEntryPoint(IntPtr args, int sizeBytes);
```

Jiný podpis lze použít zadáním názvu typu delegáta při volání delegáta modulu runtime.

### <a name="step-4---run-managed-code"></a>Krok 4 – spuštění spravovaného kódu

Nativní hostitel teď může zavolat spravovanou metodu a předat jí požadované parametry.

[!code-cpp[HostFxrHost#CallManaged](~/samples/core/hosting/HostWithHostFxr/src/NativeHost/nativehost.cpp#CallManaged)]

## <a name="create-a-host-using-coreclrhosth"></a>Vytvoření hostitele pomocí CoreClrHost. h

Následující kroky podrobně popisují, jak pomocí rozhraní API CoreClrHost. h spustit modul runtime .NET Core v nativní aplikaci a volat do spravované statické metody. Fragmenty kódu v tomto dokumentu používají některá rozhraní API specifická pro systém Windows, ale [úplný Ukázkový hostitel](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithCoreClrHost) zobrazuje cesty kódu pro Windows i Linux.

Hostitel spolupracujícího s platformou [UNIX](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts/unixcorerun) obsahuje složitější příklad hostování v reálném čase pomocí coreclrhost. h.

### <a name="step-1---find-and-load-coreclr"></a>Krok 1 – vyhledání a načtení CoreCLR

Rozhraní API modulu runtime .NET Core jsou v *CoreCLR. dll* (ve Windows), v *Libcoreclr.so* (na platformě Linux) nebo v *Libcoreclr. DYLIB* (na MacOS). Prvním krokem pro hostování .NET Core je načtení knihovny CoreCLR. Někteří hostitelé prohledají různé cesty nebo používají vstupní parametry k nalezení knihovny, zatímco jiné vědí, že ji načítají z určité cesty (vedle hostitele, například nebo z umístění v rámci počítače).

Po nalezení se knihovna načte s `LoadLibraryEx` (ve Windows) nebo `dlopen` (na platformě Linux/macOS).

[!code-cpp[CoreClrHost#1](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#1)]

### <a name="step-2---get-net-core-hosting-functions"></a>Krok 2 – získání hostujících funkcí .NET Core

CoreClrHost má několik důležitých metod, které jsou užitečné pro hostování .NET Core:

* `coreclr_initialize`: spustí modul runtime .NET Core a nastaví výchozí (a pouze) doménu AppDomain.
* `coreclr_execute_assembly`: spustí spravované sestavení.
* `coreclr_create_delegate`: Vytvoří ukazatel na funkci spravované metody.
* `coreclr_shutdown`: ukončí modul runtime .NET Core.
* `coreclr_shutdown_2`: jako `coreclr_shutdown`, ale také načte ukončovací kód spravovaného kódu.

Po načtení knihovny CoreCLR je dalším krokem získat odkazy na tyto funkce pomocí `GetProcAddress` (ve Windows) nebo `dlsym` (na platformě Linux/macOS).

[!code-cpp[CoreClrHost#2](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#2)]

### <a name="step-3---prepare-runtime-properties"></a>Krok 3 – Příprava vlastností modulu runtime

Než začnete s modulem runtime, je nutné připravit některé vlastnosti k určení chování (zejména týkající se zavaděče sestavení).

Mezi běžné vlastnosti patří:

* `TRUSTED_PLATFORM_ASSEMBLIES` Toto je seznam cest sestavení (oddělený znakem '; ' ve Windows a ': ' v systému Linux), který bude ve výchozím nastavení schopný vyřešit. Někteří hostitelé mají pevně kódované manifesty se seznamem sestavení, která lze načíst. Ostatní budou do tohoto seznamu vkládat všechny knihovny v určitých umístěních (například vedle *CoreCLR. dll*).
* `APP_PATHS` se jedná o seznam cest k testování pro sestavení, pokud se nenalezne v seznamu důvěryhodných platforem sestavení (TPA). Vzhledem k tomu, že hostitel má větší kontrolu nad tím, která sestavení jsou načtena pomocí seznamu TPA, je osvědčeným postupem pro hostitele k určení, která sestavení chtějí načíst a jejich seznam explicitně. Pokud je tato vlastnost potřebná ke zjišťování za běhu, může tento scénář povolit.
* `APP_NI_PATHS` tento seznam se podobá APP_PATHS s tím rozdílem, že se jedná o cesty, které budou zjišťovány pro nativní bitové kopie.
* `NATIVE_DLL_SEARCH_DIRECTORIES` Tato vlastnost je seznam cest, které by měl zavaděč při hledání nativních knihoven volaných prostřednictvím volání nespravovaného testu otestovat.
* `PLATFORM_RESOURCE_ROOTS` tento seznam obsahuje cesty ke sondám pro satelitní sestavení prostředků (v podadresářích závislých na jazykové verzi).

V tomto ukázkovém hostiteli je seznam TPA vytvořený pouhým seznamem všech knihoven v aktuálním adresáři:

[!code-cpp[CoreClrHost#7](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#7)]

Vzhledem k tomu, že je ukázka jednoduchá, potřebuje pouze vlastnost `TRUSTED_PLATFORM_ASSEMBLIES`:

[!code-cpp[CoreClrHost#3](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#3)]

### <a name="step-4---start-the-runtime"></a>Krok 4 – spuštění modulu runtime

Na rozdíl od rozhraní API pro hostování aplikace Mscoree. h (popsané níže), rozhraní API CoreCLRHost. h spustí modul runtime a vytvoří výchozí doménu AppDomain s jediným voláním. Funkce `coreclr_initialize` přebírá základní cestu, název a vlastnosti popsané dříve a vrací zpětnou obslužnou rutinu na hostitele prostřednictvím parametru `hostHandle`.

[!code-cpp[CoreClrHost#4](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#4)]

### <a name="step-5---run-managed-code"></a>Krok 5 – spuštění spravovaného kódu

Při spuštění modulu runtime může hostitel volat spravovaný kód. To lze provést několika různými způsoby. Vzorový kód spojený s tímto kurzem používá funkci `coreclr_create_delegate` k vytvoření delegáta staticky spravované metody. Toto rozhraní API přebírá [název sestavení](../../standard/assembly/names.md), kvalifikovaný název oboru názvů a název metody jako vstupy a vrací delegáta, který může být použit k vyvolání metody.

[!code-cpp[CoreClrHost#5](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#5)]

V této ukázce může hostitel nyní volat `managedDelegate` ke spuštění metody `ManagedWorker.DoWork`.

Alternativně lze funkci `coreclr_execute_assembly` použít ke spuštění spravovaného spustitelného souboru. Toto rozhraní API přebírá cestu sestavení a pole argumentů jako vstupní parametry. Načte sestavení na této cestě a vyvolá jeho metodu Main.

```C++
int hr = executeAssembly(
        hostHandle,
        domainId,
        argumentCount,
        arguments,
        "HelloWorld.exe",
        (unsigned int*)&exitCode);
```

### <a name="step-6---shutdown-and-clean-up"></a>Krok 6 – vypnutí a vyčištění

Nakonec, když se hostitel spustí se spravovaným kódem, modul runtime .NET Core se vypne s `coreclr_shutdown` nebo `coreclr_shutdown_2`.

[!code-cpp[CoreClrHost#6](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#6)]

CoreCLR nepodporuje opětovnou inicializaci ani uvolnění. Nevolejte `coreclr_initialize` znovu ani uvolněte knihovnu CoreCLR.

## <a name="create-a-host-using-mscoreeh"></a>Vytvoření hostitele pomocí knihovny MSCOREE. h

Jak bylo zmíněno dříve, CoreClrHost. h je nyní upřednostňovanou metodou hostování modulu runtime .NET Core. Rozhraní `ICLRRuntimeHost4` lze přesto použít, i když rozhraní CoreClrHost. h nejsou dostatečná (pokud jsou třeba nestandardní spouštěcí příznaky, například nebo pokud je AppDomainManager nutné ve výchozí doméně). Tyto pokyny vás provede hostováním .NET Core pomocí Mscoree. h.

Hostitel spoluopětovného [spuštění](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts/corerun) zobrazuje složitější, reálný příklad hostování pomocí Mscoree. h.

### <a name="a-note-about-mscoreeh"></a>Poznámka o knihovně Mscoree. h
Rozhraní pro hostování `ICLRRuntimeHost4` .NET Core je definováno v [knihovně Mscoree. IDL](https://github.com/dotnet/coreclr/blob/master/src/inc/MSCOREE.IDL). Verze hlavičky tohoto souboru (mscoree. h), kterou váš hostitel bude potřebovat odkazovat, je vytvořena prostřednictvím MIDL při sestavení [modulu runtime .NET Core](https://github.com/dotnet/coreclr/) . Pokud nechcete sestavit modul runtime .NET Core, Mscoree. h je také k dispozici jako [předem sestavená hlavička](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc) v úložišti dotnet/CoreCLR. [Pokyny k vytvoření modulu runtime .NET Core](https://github.com/dotnet/coreclr#building-the-repository) najdete v úložišti GitHub.

### <a name="step-1---identify-the-managed-entry-point"></a>Krok 1 – určení spravovaného vstupního bodu
Po odkazování na potřebné hlavičky (například[Mscoree. h](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc/mscoree.h) a stdio. h) jedna z prvních věcí, kterou musí hostitel .NET Core udělat, je najít spravovaný vstupní bod, který bude používat. V našem ukázkovém hostiteli je to provedeno pouhým prvním argumentem příkazového řádku pro hostitele jako cestu ke spravovanému binárnímu souboru, jehož metoda `main` bude provedena.

[!code-cpp[NetCoreHost#1](~/samples/core/hosting/HostWithMscoree/host.cpp#1)]

### <a name="step-2---find-and-load-coreclr"></a>Krok 2 – vyhledání a načtení CoreCLR
Rozhraní API modulu runtime .NET Core jsou v *CoreCLR. dll* (ve Windows). Chcete-li získat naše hostující rozhraní (`ICLRRuntimeHost4`), je nutné najít a načíst *CoreCLR. dll*. Pro definování konvence, jak bude vyhledána *Knihovna CoreCLR. dll*, je k dis na hostitele. Někteří hostitelé očekávají, že se soubor nachází v dobře známém umístění v rámci počítače (například *%ProgramFiles%\dotnet\shared\Microsoft.NETCore.App\2.1.6*). Ostatní očekávají, že *CoreCLR. dll* se načte z umístění vedle samotného hostitele nebo aplikace, která se má hostovat. I když ostatní můžou najít knihovnu v proměnné prostředí.

V systému Linux nebo macOS je základní běhová knihovna *libcoreclr.so* nebo *libcoreclr. DYLIB*, v uvedeném pořadí.

Náš Ukázkový hostitel sonduje několik běžných umístění pro *CoreCLR. dll*. Po nalezení je nutné ji načíst prostřednictvím `LoadLibrary` (nebo `dlopen` v systému Linux/macOS).

[!code-cpp[NetCoreHost#2](~/samples/core/hosting/HostWithMscoree/host.cpp#2)]

### <a name="step-3---get-an-iclrruntimehost4-instance"></a>Krok 3 – získání instance ICLRRuntimeHost4
Rozhraní `ICLRRuntimeHost4` hostování je načteno voláním `GetProcAddress` (nebo `dlsym` na Linux/macOS) na `GetCLRRuntimeHost`a následným vyvoláním této funkce.

[!code-cpp[NetCoreHost#3](~/samples/core/hosting/HostWithMscoree/host.cpp#3)]

### <a name="step-4---set-startup-flags-and-start-the-runtime"></a>Krok 4 – nastavení příznaků spuštění a spuštění modulu runtime
S `ICLRRuntimeHost4` teď můžeme zadat spouštěcí příznaky pro celé prostředí a spustit modul runtime. Příznaky při spuštění určují, který systém uvolňování paměti (GC) se má použít (souběžný nebo Server), jestli budeme používat jednu doménu AppDomain nebo více doménových sad a jaké zásady optimalizace zavaděče použít (pro doménové nezávislé načítání sestavení).

[!code-cpp[NetCoreHost#4](~/samples/core/hosting/HostWithMscoree/host.cpp#4)]

Modul runtime je spuštěn s voláním funkce `Start`.

```C++
hr = runtimeHost->Start();
```

### <a name="step-5---preparing-appdomain-settings"></a>Krok 5 – Příprava nastavení AppDomain
Po spuštění modulu runtime budeme chtít nastavit doménu AppDomain. K dispozici je několik možností, které je třeba zadat při vytváření domény aplikace .NET, takže je nutné je nejprve připravit.

Příznaky AppDomain určují chování AppDomain související se zabezpečením a interoperabilitou. Starší hostitelé technologie Silverlight používali tato nastavení pro uživatelský kód izolovaného prostoru, ale většina moderních hostitelů .NET Core spouští uživatelský kód jako úplný vztah důvěryhodnosti a povoluje spolupráci.

[!code-cpp[NetCoreHost#5](~/samples/core/hosting/HostWithMscoree/host.cpp#5)]

Až se rozhodnete, které příznaky AppDomain se mají použít, musí být definované vlastnosti AppDomain. Vlastnosti jsou páry klíč/hodnota řetězců. Mnohé z vlastností se týkají způsobu, jakým aplikace AppDomain načte sestavení.

Mezi běžné vlastnosti AppDomain patří:

* `TRUSTED_PLATFORM_ASSEMBLIES` se jedná o seznam cest sestavení (oddělený `;` ve Windows a `:` na Linux/macOS), které by měly mít v doméně přednost při načítání a udělení úplné důvěryhodnosti (i v částečně důvěryhodných doménách). Tento seznam má obsahovat sestavení architektury a jiné důvěryhodné moduly, podobně jako globální mezipaměť sestavení (GAC) v .NET Frameworkch scénářích. Někteří hostitelé vloží do tohoto seznamu všechny knihovny v *CoreCLR. dll* , ostatní mají pevně kódované manifesty, které uvádějí důvěryhodná sestavení pro jejich účely.
* `APP_PATHS` se jedná o seznam cest k testování pro sestavení, pokud se nenalezne v seznamu důvěryhodných platforem sestavení (TPA). Vzhledem k tomu, že hostitel má větší kontrolu nad tím, která sestavení jsou načtena pomocí seznamu TPA, je osvědčeným postupem pro hostitele k určení, která sestavení chtějí načíst a jejich seznam explicitně. Pokud je tato vlastnost potřebná ke zjišťování za běhu, může tento scénář povolit.
* `APP_NI_PATHS` tento seznam je velmi podobný APP_PATHS s tím rozdílem, že se jedná o cesty, které budou zjišťovány pro nativní bitové kopie.
* `NATIVE_DLL_SEARCH_DIRECTORIES` Tato vlastnost je seznam cest, které by měl zavaděč při hledání nativních knihoven DLL volaných prostřednictvím volání nespravovaného testu otestovat.
* `PLATFORM_RESOURCE_ROOTS` tento seznam obsahuje cesty ke sondám pro satelitní sestavení prostředků (v podadresářích závislých na jazykové verzi).

V našem [jednoduchém ukázkovém hostiteli](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithMscoree)se tyto vlastnosti nastavují takto:

[!code-cpp[NetCoreHost#6](~/samples/core/hosting/HostWithMscoree/host.cpp#6)]

### <a name="step-6---create-the-appdomain"></a>Krok 6 – vytvoření domény AppDomain
Po přípravě všech příznaků a vlastností domény aplikace `ICLRRuntimeHost4::CreateAppDomainWithManager` lze použít k nastavení domény AppDomain. Tato funkce volitelně přijímá plně kvalifikovaný název sestavení a název typu, který se použije jako správce domény AppDomain. Správce AppDomain může hostiteli umožnit řídit některé aspekty chování AppDomain a může poskytovat vstupní body pro spuštění spravovaného kódu, pokud hostitel nemá v úmyslu vyvolat kód uživatele přímo.

[!code-cpp[NetCoreHost#7](~/samples/core/hosting/HostWithMscoree/host.cpp#7)]

### <a name="step-7---run-managed-code"></a>Krok 7 – spuštění spravovaného kódu
V případě, že je doména AppDomain spuštěná a spuštěná, může nyní hostitel spouštět spravovaný kód. Nejjednodušší způsob, jak to provést, je použít `ICLRRuntimeHost4::ExecuteAssembly` k vyvolání metody vstupního bodu spravovaného sestavení. Všimněte si, že tato funkce funguje pouze ve scénářích s jednou doménou.

[!code-cpp[NetCoreHost#8](~/samples/core/hosting/HostWithMscoree/host.cpp#8)]

Další možnost, pokud `ExecuteAssembly` nesplňuje potřeby hostitele, je použití `CreateDelegate` k vytvoření ukazatele funkce na statickou spravovanou metodu. To vyžaduje, aby hostitel znal podpis metody, do které volá (aby mohl vytvořit typ ukazatele na funkci), ale umožňuje hostitelům flexibility vyvolat kód jiný než vstupní bod sestavení. Název sestavení zadaný ve druhém parametru je [úplný název spravovaného sestavení](../../standard/assembly/names.md) knihovny, která se má načíst.

```C++
void *pfnDelegate = NULL;
hr = runtimeHost->CreateDelegate(
    domainId,
    L"HW, Version=1.0.0.0, Culture=neutral", // Target managed assembly
    L"ConsoleApplication.Program",           // Target managed type
    L"Main",                                 // Target entry point (static method)
    (INT_PTR*)&pfnDelegate);

((MainMethodFp*)pfnDelegate)(NULL);
```

### <a name="step-8---clean-up"></a>Krok 8 – vyčištění
Nakonec by se měl hostitel vyčistit po samotném uvolněním AppDomains, zastavením modulu runtime a uvolněním `ICLRRuntimeHost4` odkazem.

[!code-cpp[NetCoreHost#9](~/samples/core/hosting/HostWithMscoree/host.cpp#9)]

CoreCLR nepodporuje vykládku. Uvolněte knihovnu CoreCLR.

## <a name="conclusion"></a>Závěr
Po sestavení hostitele je možné ho otestovat spuštěním z příkazového řádku a předávat všechny argumenty, které hostitel očekává (jako je spravovaná aplikace pro spuštění ukázkového hostitele mscoree). Při zadávání aplikace .NET Core pro spuštění hostitele nezapomeňte použít knihovnu DLL, která je vytvořena nástrojem `dotnet build`. Spustitelné soubory (soubory. exe) vytvořené `dotnet publish` pro samostatné aplikace jsou ve skutečnosti výchozím hostitelem .NET Core (aby bylo možné aplikaci spustit přímo z příkazového řádku ve scénářích hlavní); uživatelský kód je zkompilován do knihovny DLL se stejným názvem.

Pokud co nejdříve nefunguje, poklikejte na to, že *CoreCLR. dll* je k dispozici v umístění očekávaném hostitelem, že všechny nezbytné knihovny rozhraní jsou v seznamu TPA a že CoreCLR bitová verze (32-bit nebo 64) odpovídá způsobu sestavení hostitele.

Hostování modulu runtime .NET Core je pokročilý scénář, který nevyžaduje mnoho vývojářů, ale pro uživatele, kteří potřebují spustit spravovaný kód z nativního procesu nebo kteří potřebují větší kontrolu nad chováním modulu runtime .NET Core, může být velmi užitečné.
