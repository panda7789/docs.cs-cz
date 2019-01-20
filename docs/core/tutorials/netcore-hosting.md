---
title: Vytvořit vlastního hostitele modulu runtime .NET Core
description: Zjistěte, jak hostitele modulu runtime .NET Core z nativního kódu, které podporují pokročilé scénáře, které vyžadují řízení, jak modul runtime .NET Core funguje.
author: mjrousos
ms.date: 12/21/2018
ms.custom: seodec18
ms.openlocfilehash: deeda8b166d8a22aac88be313d2555e4b9fa5a1c
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415517"
---
# <a name="write-a-custom-net-core-host-to-control-the-net-runtime-from-your-native-code"></a>Vytvořit vlastního hostitele řídit modul .NET runtime z nativního kódu .NET Core

Stejně jako veškerého spravovaného kódu aplikace .NET Core jsou spouštěny hostitele. Hostitel je zodpovědný za spouštění modulu runtime (včetně komponenty, jako jsou JIT a systému uvolňování paměti) a spravovaný vstupní body volání.

Hostování modulu runtime .NET Core je pokročilý scénář a .NET Core vývojáři nemusíte se starat o hostování, protože procesy sestavení .NET Core ve většině případů poskytují výchozí hostitel pro spouštění aplikací .NET Core. V některých případech specializovaná ale může být užitečné explicitně hostitele modulu runtime .NET Core, buď jako způsob volání spravovaného kódu v nativní proces nebo pokud chcete získat větší kontrolu nad princip modulu runtime.

Tento článek obsahuje přehled kroky potřebné ke spuštění modulu runtime .NET Core z nativního kódu a spuštění spravovaného kódu v ní.

## <a name="prerequisites"></a>Požadavky

Protože jsou hostitelé nativních aplikací, v tomto kurzu se bude vztahovat vytváření aplikace v jazyce C++ pro hostování rozhraní .NET Core. Budete potřebovat vývojové prostředí C++ (například poskytuje [sady Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)).

Můžete také jednoduchou aplikaci .NET Core testování hostitele, takže byste měli nainstalovat [.NET Core SDK](https://www.microsoft.com/net/core) a [sestavení malou testovací aplikaci .NET Core](../../core/tutorials/with-visual-studio.md) (například aplikace "Hello World"). Vytvoření nové šablony projektu .NET Core console "Zdravím svět" aplikace je dostačující.

## <a name="hosting-apis"></a>Rozhraní API pro hostování
Existují dva různých rozhraní API, které lze použít k hostiteli .NET Core. Tento dokument (spolu s přidruženými [ukázky](https://github.com/dotnet/samples/tree/master/core/hosting)) zahrnují obě možnosti.

* Preferovanou metodu hostování modulu runtime .NET Core je [CoreClrHost.h](https://github.com/dotnet/coreclr/blob/master/src/coreclr/hosts/inc/coreclrhost.h) rozhraní API. Toto rozhraní API poskytuje funkce pro snadné spuštění a zastavení modulu runtime a volání spravovaného kódu (buď spuštěním spravované exe nebo voláním statické metody spravované).
* .NET core je rovněž možné hostovat s `ICLRRuntimeHost2` rozhraní v [mscoree.h](https://github.com/dotnet/coreclr/blob/master/src/pal/prebuilt/inc/mscoree.h). Toto rozhraní API se stále týká delší než CoreClrHost.h, takže jste viděli starší hostitelů pomocí jej. Stále funguje a umožňuje větší kontrolu nad hostitelský proces než CoreClrHost. Pro většinu scénářů ale CoreClrHost.h upřednostňována nyní z důvodu jeho jednodušší rozhraní API.

## <a name="sample-hosts"></a>Ukázka hostitele
[Ukázka hostitele](https://github.com/dotnet/samples/tree/master/core/hosting) demonstrace kroků uvedených v následujících kurzech jsou k dispozici v úložišti dotnet/samples GitHub. Komentáře v ukázkách jasně přidružit očíslovaných kroků v těchto kurzech kde se provádí v ukázce. Pokyny ke stažení najdete v tématu [ukázek a kurzů](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Mějte na paměti, že hostitelé vzorku jsou určené pro výukové účely, proto jsou jasno kontroly chyb a jsou navrženy pro zvýraznění čitelnost přes efektivitu. Další ukázky skutečných hostitele jsou k dispozici v [dotnet/coreclr](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts) úložiště. [CoreRun hostitele](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts/corerun) a [hostitele systému Unix CoreRun](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts/unixcorerun), zejména, jsou vhodné pro obecné účely hostitele studovat po přečtení těchto ukázkách jednodušší.

## <a name="create-a-host-using-coreclrhosth"></a>Vytvoření hostitele pomocí CoreClrHost.h

Následující kroky podrobně popisují použití rozhraní API CoreClrHost.h spustit modul runtime .NET Core v nativní aplikaci a volání do spravovaného statickou metodu. Fragmenty kódu v tomto dokumentu pomocí některá rozhraní API specifické pro Windows, ale [úplnou ukázku hostitele](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithCoreClrHost) ukazuje Windows i Linuxem cesty kódu.

### <a name="step-1---find-and-load-coreclr"></a>Krok 1 – vyhledání a načtení CoreCLR

Modul runtime .NET Core API jsou v *coreclr.dll* (ve Windows), v *libcoreclr.so* (v Linuxu), nebo v *libcoreclr.dylib* (v systému macOS). Prvním krokem k hostování rozhraní .NET Core je načíst knihovnu CoreCLR. Někteří hostitelé sběru dat různých cest nebo najít knihovnu, zatímco ostatní vědět o načtení z určité cestě (vedle hostitele, například nebo z umístění celý počítač) pomocí vstupní parametry.

Jednou najde, se je načíst knihovnu `LoadLibraryEx` (ve Windows) nebo `dlopen` (v systému Linux/Mac).

[!code-cpp[CoreClrHost#1](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#1)]

### <a name="step-2---get-net-core-hosting-functions"></a>Krok 2: získání .NET Core, funkce pro hostování

CoreClrHost má několik důležitých metod užitečné pro hostování rozhraní .NET Core:

* `coreclr_initialize`: Spuštění modulu runtime .NET Core a nastavuje výchozí (a pouze) domény aplikace.
* `coreclr_execute_assembly`: Provede spravovaným sestavením.
* `coreclr_create_delegate`: Vytvoří ukazatel na funkci spravované metodě.
* `coreclr_shutdown`: Ukončení modulu runtime .NET Core.
* `coreclr_shutdown_2`: Stejně jako `coreclr_shutdown`, ale také načte spravovaný kód ukončovací kód.

Po načtení knihovny CoreCLR, dalším krokem je získání odkazů na tyto funkce pomocí `GetProcAddress` (ve Windows) nebo `dlsym` (v systému Linux/Mac).

[!code-cpp[CoreClrHost#2](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#2)]

### <a name="step-3---prepare-runtime-properties"></a>Krok 3 – Příprava vlastnosti modulu runtime

Před zahájením modul runtime, je nezbytné pro přípravu některé vlastnosti k určení chování (zejména zavaděč sestavení). 

Společné vlastnosti patří:

* `TRUSTED_PLATFORM_ASSEMBLIES` Toto je seznam cest sestavení (oddělených pomocí ';' na Windows a ":" v Linuxu) která bude moct resovle ve výchozím nastavení modul runtime. Někteří hostitelé mají pevně zakódované manifest sestavení, které můžete načíst seznam. Ostatní zařadí všechny knihovny v určitých umístěních (vedle *coreclr.dll*, například) v tomto seznamu.
* `APP_PATHS` Toto je seznam cest testovat v sestavení, pokud nebyl nalezen v seznamu důvěryhodných platforma sestavení (TPA). Vzhledem k tomu, že hostitel má větší kontrolu nad tím, které se načítají sestavení pomocí seznamu TPA, je osvědčeným postupem pro hostitele k určení sestavení, očekávané zatížení a jejich seznam explicitně. V případě potřeby testování za běhu, tuto vlastnost můžete povolit tento scénář.
*  `APP_NI_PATHS` Tento seznam je podobný APP_PATHS s tím rozdílem, že má sloužit cesty, které bude zkoumat nativních bitových kopií.
*  `NATIVE_DLL_SEARCH_DIRECTORIES` Tato vlastnost je seznam cest, které by měl zavaděč testu při hledání nativních knihoven volání prostřednictvím p/invoke.
*  `PLATFORM_RESOURCE_ROOTS` Tento seznam obsahuje cesty ke sběru dat v pro satelitní sestavení prostředků (v podadresářích specifické pro jazykovou verzi).

Tato ukázka hostiteli je vytvářený seznamu TPA jednoduše výpis všech knihoven v aktuálním adresáři:

[!code-cpp[CoreClrHost#7](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#7)]

Ukázka je jednoduché, potřebuje pouze `TRUSTED_PLATFORM_ASSEMBLIES` vlastnost:

[!code-cpp[CoreClrHost#3](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#3)]

### <a name="step-4---start-the-runtime"></a>Krok 4: spuštění modulu runtime

Na rozdíl od mscoree.h hostujícího rozhraní API (popsaných níže), rozhraní API CoreCLRHost.h spustit modul runtime a vytvořit výchozí domény aplikace vše v jednom volání. `coreclr_initialize` Funkce přijímá základní cesta, název a vlastnosti popsané výše a vrátí zpět do hostitele prostřednictvím popisovač `hostHandle` parametru.

[!code-cpp[CoreClrHost#4](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#4)]

### <a name="step-5---run-managed-code"></a>Krok 5: spuštění spravovaného kódu.

S modulem runtime spuštěna hostitel může volat spravovaný kód. To můžete udělat několika různými způsoby. Vzorový kód propojené na tento kurz používá `coreclr_create_delegate` funkce k vytvoření delegáta na statickou metodu spravované. Toto rozhraní API trvá [název sestavení](../../framework/app-domains/assembly-names.md), název typu kvalifikovaného oboru názvů a název metody, stejně jako vstupy a vrací delegáta, který lze použít k vyvolání metody.

[!code-cpp[CoreClrHost#5](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#5)]

V této ukázce, můžete nyní volat hostitele `managedDelegate` ke spuštění `ManagedWorker.DoWork` metody.

Další možností `coreclr_execute_assembly` funkce můžete použít ke spuštění spravované spustitelný soubor. Toto rozhraní API přijímá jako vstupní parametry cesta k sestavení a služby pole argumentů. Načte sestavení v této cestě a jeho hlavní metoda vyvolá. 

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

Nakonec po dokončení spuštění spravovaného kódu hostitele modulu runtime .NET Core je vypnutý pomocí `coreclr_shutdown` nebo `coreclr_shutdown_2`.

[!code-cpp[CoreClrHost#6](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#6)]

Mějte na paměti pomocí knihovny CoreCLR uvolnit `FreeLibrary` (ve Windows) nebo `dlclose` (v systému Linux/Mac).

## <a name="creating-a-host-using-mscoreeh"></a>Vytvoření hostitele pomocí Mscoree.h

Jak už bylo zmíněno dříve, CoreClrHost.h je teď preferovanou metodu hostování modulu runtime .NET Core. `ICLRRuntimeHost2` Rozhraní je stále možné, ale pokud CoreClrHost.h rozhraní nejsou dostatečná (podle potřeby nestandardní spuštění příznaky jsou například nebo potřeby AppDomainManager pro výchozí doménu). Tyto pokyny vás provedou s .NET Core pomocí mscoree.h hostování.

### <a name="a-note-about-mscoreeh"></a>Poznámka k mscoree.h
`ICLRRuntimeHost2` Hostitelského rozhraní je definováno v .NET Core [MSCOREE. IDL](https://github.com/dotnet/coreclr/blob/master/src/inc/MSCOREE.IDL). Hlavička verze tohoto souboru (mscoree.h), které hostitele bude muset odkazovat, je vytvořen prostřednictvím MIDL při [.NET Core runtime](https://github.com/dotnet/coreclr/) je vytvořená. Pokud nechcete sestavení modulu runtime .NET Core, mscoree.h je také k dispozici [předem sestavených záhlaví](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc) v úložišti dotnet/coreclr. [Pokyny týkající se sestavení modulu runtime .NET Core](https://github.com/dotnet/coreclr#building-the-repository) najdete ve svém úložišti Githubu. 

### <a name="step-1---identify-the-managed-entry-point"></a>Krok 1 – identifikace spravovaný vstupní bod
Po odkazující na potřebné hlavičky ([mscoree.h](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc/mscoree.h) a stdio.h, například), jedním z prvních věcí, které musíte udělat hostitele .NET Core je najít spravovaný vstupní bod budou používat. V naší ukázkové hostitele, je to provedením pouze první argument příkazového řádku na naše hostitele jako cestu pro spravované binární jehož `main` metody se spustí.

[!code-cpp[NetCoreHost#1](~/samples/core/hosting/HostWithMscoree/host.cpp#1)]

### <a name="step-2---find-and-load-coreclr"></a>Krok 2 – vyhledání a načtení CoreCLR
Modul runtime .NET Core API jsou v *CoreCLR.dll* (ve Windows). K získání našeho hostitelských rozhraní (`ICLRRuntimeHost2`), je potřeba najít a načíst *CoreCLR.dll*. Je hostitel k definování zásad pro jak bude vyhledávat *CoreCLR.dll*. Někteří hostitelé očekávat soubor, který má být k dispozici v dobře známé celý počítač umístění (například *%programfiles%\dotnet\shared\Microsoft.NETCore.App\2.1.6*). Ostatní očekávat, že *CoreCLR.dll* se načtou z umístění vedle zvolenému hostiteli samotné nebo aplikaci zajistit také jejich hostování. Ostatní může stále najdete proměnnou prostředí k nalezení knihovny.

V systému Linux nebo Mac, je základní modul runtime knihovny *libcoreclr.so* nebo *libcoreclr.dylib*v uvedeném pořadí.

Naše ukázka hostitele sondy několik běžných umístění *CoreCLR.dll*. Jednou najde, musí být načten prostřednictvím `LoadLibrary` (nebo `dlopen` v systému Linux/Mac).

[!code-cpp[NetCoreHost#2](~/samples/core/hosting/HostWithMscoree/host.cpp#2)]

### <a name="step-3---get-an-iclrruntimehost2-instance"></a>Krok 3 – získání ICLRRuntimeHost2 Instance
`ICLRRuntimeHost2` Hostování rozhraní je načten voláním `GetProcAddress` (nebo `dlsym` v systému Linux/Mac) na `GetCLRRuntimeHost`a potom volání této funkce. 

[!code-cpp[NetCoreHost#3](~/samples/core/hosting/HostWithMscoree/host.cpp#3)]

### <a name="step-4---setting-startup-flags-and-starting-the-runtime"></a>Krok 4 – nastavení příznaků spuštění a spouští se modul runtime
Pomocí `ICLRRuntimeHost2` spolupráce, jsme teď můžete zadat při spuštění modulu runtime celou příznaky a spustit modul runtime. Po spuštění příznaky určit, které systému uvolňování paměti (GC) použijte (souběžné nebo serveru), pokud budeme používat jedinou doménu AppDomain nebo více objektů třídy AppDomains a jaké zásady optimalizace zavaděče (pro načtení doménově neutrální sestavení).

[!code-cpp[NetCoreHost#4](~/samples/core/hosting/HostWithMscoree/host.cpp#4)]

Modul runtime se spustí s volání `Start` funkce.

```C++
hr = runtimeHost->Start();
```

### <a name="step-5---preparing-appdomain-settings"></a>Krok 5: Příprava domény aplikace nastavení
Po zahájení modul runtime se chcete nastavit doméně AppDomain. Existuje mnoho možností, které se musí zadat při vytváření .NET AppDomain, ale tak, aby byl nezbytné pro přípravu nejprve.

Doména AppDomain příznaky zadejte chování AppDomain souvisejících se zabezpečením a zprostředkovatele komunikace s objekty. Starší technologie Silverlight hostitele použít tato nastavení do izolovaného prostoru uživatelský kód, ale většina moderních hostitelů .NET Core spouští uživatelský kód při úplném vztahu důvěryhodnosti a povolit zprostředkovatele komunikace s objekty.

[!code-cpp[NetCoreHost#5](~/samples/core/hosting/HostWithMscoree/host.cpp#5)]

Jakmile se rozhodnete, které doména AppDomain příznaky pro použití, musí být definovány vlastnosti domény aplikace. Vlastnosti jsou páry klíč/hodnota z řetězce. Mnoho vlastností se týkají způsob načtení sestavení domény aplikace.

Společná nastavení domény aplikace patří:

* `TRUSTED_PLATFORM_ASSEMBLIES` Toto je seznam cest sestavení (oddělené `;` na Windows a `:` v systému Linux/Mac) který AppDomain by měl upřednostňovat načítání a poskytují úplný vztah důvěryhodnosti (i v částečně důvěryhodné domény). Tento seznam slouží k obsahovat sestavení "Rozhraní" a další důvěryhodné moduly, podobně jako v GAC ve scénářích rozhraní .NET Framework. Někteří hostitelé zařadí všechny knihovny vedle *coreclr.dll* v tomto seznamu další ho mají pevně zakódované manifesty seznamem důvěryhodných sestavení pro svoje účely.
* `APP_PATHS` Toto je seznam cest testovat v sestavení, pokud nebyl nalezen v seznamu důvěryhodných platforma sestavení (TPA). Vzhledem k tomu, že hostitel má větší kontrolu nad tím, které se načítají sestavení pomocí seznamu TPA, je osvědčeným postupem pro hostitele k určení sestavení, očekávané zatížení a jejich seznam explicitně. V případě potřeby testování za běhu, tuto vlastnost můžete povolit tento scénář.
*  `APP_NI_PATHS` Tento seznam je velmi podobný APP_PATHS s tím rozdílem, že má sloužit cesty, které bude zkoumat nativních bitových kopií.
*  `NATIVE_DLL_SEARCH_DIRECTORIES` Tato vlastnost je seznam cesty, které by měl zavaděč testu při hledání nativních knihoven DLL volání prostřednictvím p/invoke.
*  `PLATFORM_RESOURCE_ROOTS` Tento seznam obsahuje cesty ke sběru dat v pro satelitní sestavení prostředků (v podadresářích specifické pro jazykovou verzi).

V našem [jednoduchého ukázkového hostitele](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithMscoree), tyto vlastnosti jsou wmm nastavit takto:

[!code-cpp[NetCoreHost#6](~/samples/core/hosting/HostWithMscoree/host.cpp#6)]

### <a name="step-6---create-the-appdomain"></a>Krok 6: vytvoření domény aplikace
Jakmile jsou připraveny všechny příznaky domény aplikace a vlastnosti, `ICLRRuntimeHost2::CreateAppDomainWithManager` slouží k nastavení domény aplikace. Tato funkce přebírá volitelně plně kvalifikovaný název sestavení a název typu, který se použije jako správce domény AppDomain. Správce domény aplikace můžete povolit pro hostitele a ovládat některé aspekty chování AppDomain a může poskytnout vstupní body pro spuštění spravovaného kódu, pokud hostitel není v úmyslu vyvolat uživatelský kód přímo.   

[!code-cpp[NetCoreHost#7](~/samples/core/hosting/HostWithMscoree/host.cpp#7)]

### <a name="step-7---run-managed-code"></a>Krok 7: spuštění spravovaného kódu.
S doméně AppDomain pracovat, hostitel teď můžete začít spouští spravovaný kód. Nejjednodušší způsob je použít `ICLRRuntimeHost2::ExecuteAssembly` vyvolat metodu vstupního bodu spravovaného sestavení. Všimněte si, že tato funkce funguje pouze v jedné doméně scénáře.

[!code-cpp[NetCoreHost#8](~/samples/core/hosting/HostWithMscoree/host.cpp#8)]

Další možnost, pokud `ExecuteAssembly` nevyhovuje potřebám vašeho hostitele, je použití `CreateDelegate` vytvoření ukazatele na funkci na statickou spravované metody. To vyžaduje, aby hostitel znát podpis metody je volání do (Chcete-li vytvořit typ ukazatele na funkci) ale umožňuje hostitelům flexibilitu při vyvolání kódu než sestavení vstupního bodu. Název sestavení, pokud je druhý parametr [název spravovaného sestavení úplné](../../framework/app-domains/assembly-names.md) knihovny určené k načtení.

```C++
void *pfnDelegate = NULL;
hr = runtimeHost->CreateDelegate(
  domainId,
  L"HW, Version=1.0.0.0, Culture=neutral",  // Target managed assembly
  L"ConsoleApplication.Program",            // Target managed type
  L"Main",                                  // Target entry point (static method)
  (INT_PTR*)&pfnDelegate);

((MainMethodFp*)pfnDelegate)(NULL);
```

### <a name="step-8---clean-up"></a>Krok 8 – čištění
Nakonec se hostitele by měl vyčištění po samotné uvolňování objektů třídy AppDomains, zastavení modulu runtime a uvolněním `ICLRRuntimeHost2` odkaz.

[!code-cpp[NetCoreHost#9](~/samples/core/hosting/HostWithMscoree/host.cpp#9)]

## <a name="conclusion"></a>Závěr
Jakmile hostitele je sestavená, ho můžete otestovat spuštěním z příkazového řádku a předávání argumentů hostitele očekává, že (jako je spuštění pro hostitele příklad mscoree spravované aplikace). Při zadávání aplikaci .NET Core pro hostitele ke spuštění, nezapomeňte použít soubor .dll, který je vytvořen `dotnet build`. Spustitelné soubory (soubory .exe) vytvářených `dotnet publish` pro samostatné aplikace jsou ve skutečnosti výchozí hostitel .NET Core (tak, aby aplikaci můžete spustit přímo z příkazového řádku v hlavní linii scénáře); uživatelský kód je zkompilován do knihovny dll se stejným názvem. 

Pokud věci zpočátku nefunguje, zkontrolujte *coreclr.dll* je k dispozici v umístění očekává hostitele, jsou v seznamu TPA všechny potřebné knihovny rozhraní Framework, který odpovídá této CoreCLR bitové verze (32 - a 64-bit) jak byla vytvořena hostitele.

Hostování modulu runtime .NET Core je pokročilý scénář celá řada vývojářů nebude vyžadovat, že pro ty, kteří potřebují ke spuštění spravovaného kódu z nativní proces nebo který potřebujete větší kontrolu nad chování modulu runtime .NET Core, může být velmi užitečné. Protože je možné spouštět vedle sebe .NET Core se sebou samým, je dokonce možné vytvořit hostitele, kteří inicializaci a spuštění více verzí modulu runtime .NET Core a spouštění aplikací na všechny z nich ve stejném procesu. 
