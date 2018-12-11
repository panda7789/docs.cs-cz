---
title: Vytvořit vlastního hostitele modulu runtime .NET Core
description: Zjistěte, jak hostitele modulu runtime .NET Core z nativního kódu, které podporují pokročilé scénáře, které vyžadují řízení, jak modul runtime .NET Core funguje.
author: mjrousos
ms.date: 02/03/2017
ms.custom: seodec18
ms.openlocfilehash: 861a02d2e409637d11c874f16ecd56a1a0fcd92a
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169635"
---
# <a name="write-a-custom-net-core-host-to-control-the-net-runtime-from-your-native-code"></a>Vytvořit vlastního hostitele řídit modul .NET runtime z nativního kódu .NET Core

Stejně jako veškerého spravovaného kódu aplikace .NET Core jsou spouštěny hostitele. Hostitel je zodpovědný za spouštění modulu runtime (včetně komponenty, jako jsou JIT a systému uvolňování paměti), vytváření objektů třídy AppDomains a vyvolání spravované vstupní body.

Hostování modulu runtime .NET Core je pokročilý scénář a .NET Core vývojáři nemusíte se starat o hostování, protože procesy sestavení .NET Core ve většině případů poskytují výchozí hostitel pro spouštění aplikací .NET Core. V některých případech specializovaná ale může být užitečné explicitně hostitele modulu runtime .NET Core, buď jako způsob volání spravovaného kódu v nativní proces nebo pokud chcete získat větší kontrolu nad princip modulu runtime.

Tento článek obsahuje přehled kroky potřebnými k spuštění modulu runtime .NET Core z nativního kódu, vytvořte doménu počáteční aplikace (<xref:System.AppDomain>) a v ní spustit spravovaný kód.

## <a name="prerequisites"></a>Požadavky

Protože jsou hostitelé nativních aplikací, v tomto kurzu se bude vztahovat vytváření aplikace v jazyce C++ pro hostování rozhraní .NET Core. Budete potřebovat vývojové prostředí C++ (například poskytuje [sady Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)).

Můžete také jednoduchou aplikaci .NET Core testování hostitele, takže byste měli nainstalovat [.NET Core SDK](https://www.microsoft.com/net/core) a [sestavení malou testovací aplikaci .NET Core](../../core/tutorials/with-visual-studio.md) (například aplikace "Hello World"). Vytvoření nové šablony projektu .NET Core console "Zdravím svět" aplikace je dostačující.

V tomto kurzu a její přidružené ukázkové sestavení hostitele Windows; viz poznámky na konci tohoto článku o hostování v systému Unix.

## <a name="creating-the-host"></a>Vytvoření hostitele

A [Ukázkový hostitel](https://github.com/dotnet/samples/tree/master/core/hosting) demonstrace kroků uvedených v tomto článku je k dispozici v úložišti dotnet/samples GitHub. Komentáře ve vzorku *host.cpp* souboru jasně přidružit očíslovaných kroků v tomto kurzu, pomocí které se provádějí v ukázce. Pokyny ke stažení najdete v tématu [ukázek a kurzů](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Mějte na paměti, že Ukázkový hostitel je určená pro výukové účely, proto je indikátor na kontrolu chyb a slouží k zvýraznit čitelnost přes efektivitu. Další ukázky skutečných hostitele jsou k dispozici v [dotnet/coreclr](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts) úložiště. [CoreRun hostitele](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts/corerun), zejména je dobrá pro obecné účely hostitel studovat po přečtení jednodušší vzorku.

### <a name="a-note-about-mscoreeh"></a>Poznámka k mscoree.h
Primární .NET Core, který je hostitelem rozhraní (`ICLRRuntimeHost2`) je definován v [MSCOREE. IDL](https://github.com/dotnet/coreclr/blob/master/src/inc/MSCOREE.IDL). Hlavička verze tohoto souboru (mscoree.h), které hostitele bude muset odkazovat, je vytvořen prostřednictvím MIDL při [.NET Core runtime](https://github.com/dotnet/coreclr/) je vytvořená. Pokud nechcete sestavení modulu runtime .NET Core, mscoree.h je také k dispozici [předem sestavených záhlaví](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc) v úložišti dotnet/coreclr. [Pokyny týkající se sestavení modulu runtime .NET Core](https://github.com/dotnet/coreclr#building-the-repository) najdete ve svém úložišti Githubu. 

### <a name="step-1---identify-the-managed-entry-point"></a>Krok 1 – identifikace spravovaný vstupní bod
Po odkazující na potřebné hlavičky ([mscoree.h](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc/mscoree.h) a stdio.h, například), jedním z prvních věcí, které musíte udělat hostitele .NET Core je najít spravovaný vstupní bod budou používat. V naší ukázkové hostitele, je to provedením pouze první argument příkazového řádku na naše hostitele jako cestu pro spravované binární jehož `main` metody se spustí.

[!code-cpp[NetCoreHost#1](../../../samples/core/hosting/host.cpp#1)]

### <a name="step-2---find-and-load-coreclrdll"></a>Krok 2 – vyhledání a načtení CoreCLR.dll
Modul runtime .NET Core API jsou v *CoreCLR.dll* (ve Windows). K získání našeho hostitelských rozhraní (`ICLRRuntimeHost2`), je potřeba najít a načíst *CoreCLR.dll*. Je hostitel k definování zásad pro jak bude vyhledávat *CoreCLR.dll*. Někteří hostitelé očekávat, že soubor, který má být k dispozici v dobře známé celý počítač umístění (například % programfiles%\dotnet\shared\Microsoft.NETCore.App\1.1.0). Ostatní očekávat, že *CoreCLR.dll* se načtou z umístění vedle zvolenému hostiteli samotné nebo aplikaci zajistit také jejich hostování. Ostatní může stále najdete proměnnou prostředí k nalezení knihovny.

V systému Linux nebo Mac, je základní modul runtime knihovny *libcoreclr.so* nebo *libcoreclr.dylib*v uvedeném pořadí.

Naše ukázka hostitele sondy několik běžných umístění *CoreCLR.dll*. Jednou najde, musí být načten prostřednictvím `LoadLibrary` (nebo `dlopen` v systému Linux/Mac).

[!code-cpp[NetCoreHost#2](../../../samples/core/hosting/host.cpp#2)]

### <a name="step-3---get-an-iclrruntimehost2-instance"></a>Krok 3 – získání ICLRRuntimeHost2 Instance
`ICLRRuntimeHost2` Hostování rozhraní je načten voláním `GetProcAddress` (nebo `dlsym` v systému Linux/Mac) na `GetCLRRuntimeHost`a potom volání této funkce. 

[!code-cpp[NetCoreHost#3](../../../samples/core/hosting/host.cpp#3)]

### <a name="step-4---setting-startup-flags-and-starting-the-runtime"></a>Krok 4 – nastavení příznaků spuštění a spouští se modul runtime
Pomocí `ICLRRuntimeHost2` spolupráce, jsme teď můžete zadat při spuštění modulu runtime celou příznaky a spustit modul runtime. Po spuštění příznaky určí, které systému uvolňování paměti (GC) použijte (souběžné nebo serveru), pokud budeme používat jedinou doménu AppDomain nebo více objektů třídy AppDomains a jaké zásady optimalizace zavaděče (pro načtení doménově neutrální sestavení).

[!code-cpp[NetCoreHost#4](../../../samples/core/hosting/host.cpp#4)]

Modul runtime se spustí s volání `Start` funkce.

```C++
hr = runtimeHost->Start();
```

### <a name="step-5---preparing-appdomain-settings"></a>Krok 5: Příprava domény aplikace nastavení
Po zahájení modul runtime se chcete nastavit doméně AppDomain. Existuje mnoho možností, které se musí zadat při vytváření .NET AppDomain, ale tak, aby byl nezbytné pro přípravu nejprve.

Doména AppDomain příznaky zadejte chování AppDomain souvisejících se zabezpečením a zprostředkovatele komunikace s objekty. Starší technologie Silverlight hostitele použít tato nastavení do izolovaného prostoru uživatelský kód, ale většina moderních hostitelů .NET Core spouští uživatelský kód při úplném vztahu důvěryhodnosti a povolit zprostředkovatele komunikace s objekty.

[!code-cpp[NetCoreHost#5](../../../samples/core/hosting/host.cpp#5)]

Jakmile se rozhodnete, které doména AppDomain příznaky pro použití, musí být definovány vlastnosti domény aplikace. Vlastnosti jsou páry klíč/hodnota z řetězce. Mnoho vlastností se týkají způsob načtení sestavení domény aplikace.

Společná nastavení domény aplikace patří:

* `TRUSTED_PLATFORM_ASSEMBLIES` Toto je seznam cest sestavení (oddělených pomocí ';' na Windows a ":" v Unixu) který AppDomain by měl upřednostňovat načítání a poskytují úplný vztah důvěryhodnosti (i v částečně důvěryhodné domény). Tento seznam slouží k obsahovat sestavení "Rozhraní" a další důvěryhodné moduly, podobně jako v GAC ve scénářích rozhraní .NET Framework. Někteří hostitelé zařadí všechny knihovny vedle *coreclr.dll* v tomto seznamu další ho mají pevně zakódované manifesty seznamem důvěryhodných sestavení pro svoje účely.
* `APP_PATHS` Toto je seznam cest testovat v sestavení, pokud nebyl nalezen v seznamu důvěryhodných platforma sestavení (TPA). Tyto cesty jsou určené jako umístění, kde lze nalézt sestavení uživatelů. V doméně AppDomain v izolovaném prostoru sestavení načtené z těchto cest bude udělen jenom v částečném vztahu důvěryhodnosti. Běžné APP_PATH programy zahrnují cestu, která cílovou aplikaci byl načten z nebo jiné umístění, ve kterém se ví live prostředky uživatele.
*  `APP_NI_PATHS` Tento seznam je velmi podobný APP_PATHS s tím rozdílem, že má sloužit cesty, které bude zkoumat nativních bitových kopií.
*  `NATIVE_DLL_SEARCH_DIRECTORIES` Tato vlastnost je seznam cesty, které by měl zavaděč testu při hledání nativních knihoven DLL volání prostřednictvím p/invoke.
*  `PLATFORM_RESOURCE_ROOTS` Tento seznam obsahuje cesty ke sběru dat v pro satelitní sestavení prostředků (v podadresářích specifické pro jazykovou verzi).

V našem [jednoduchého ukázkového hostitele](https://github.com/dotnet/samples/tree/master/core/hosting), tyto vlastnosti jsou wmm nastavit takto:

[!code-cpp[NetCoreHost#6](../../../samples/core/hosting/host.cpp#6)]

### <a name="step-6---create-the-appdomain"></a>Krok 6: vytvoření domény aplikace
Jakmile jsou připraveny všechny příznaky domény aplikace a vlastnosti, `ICLRRuntimeHost2::CreateAppDomainWithManager` slouží k nastavení domény aplikace. Tato funkce přebírá volitelně plně kvalifikovaný název sestavení a název typu, který se použije jako správce domény AppDomain. Správce domény aplikace můžete povolit pro hostitele a ovládat některé aspekty chování AppDomain a může poskytnout vstupní body pro spuštění spravovaného kódu, pokud hostitel není v úmyslu vyvolat uživatelský kód přímo.   

[!code-cpp[NetCoreHost#7](../../../samples/core/hosting/host.cpp#7)]

### <a name="step-7---run-managed-code"></a>Krok 7: spuštění spravovaného kódu.
S doméně AppDomain pracovat, hostitel teď můžete začít spouští spravovaný kód. Nejjednodušší způsob je použít `ICLRRuntimeHost2::ExecuteAssembly` vyvolat metodu vstupního bodu spravovaného sestavení. Všimněte si, že tato funkce funguje pouze v jedné doméně scénáře.

[!code-cpp[NetCoreHost#8](../../../samples/core/hosting/host.cpp#8)]

Další možnost, pokud `ExecuteAssembly` nevyhovuje potřebám vašeho hostitele, je použití `CreateDelegate` vytvoření ukazatele na funkci na statickou spravované metody. To vyžaduje, aby hostitel znát podpis metody je volání do (Chcete-li vytvořit typ ukazatele na funkci) ale umožňuje hostitelům flexibilitu při vyvolání kódu než sestavení vstupního bodu.

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

[!code-cpp[NetCoreHost#9](../../../samples/core/hosting/host.cpp#9)]

## <a name="about-hosting-net-core-on-unix"></a>Informace o hostování rozhraní .NET Core v systému Unix
.NET core je multiplatformní produkt, běží v systémech Windows, Linux a Mac. Jako nativní aplikace ale hostitele pro různé platformy bude mít některé rozdíly mezi nimi. Proces popsaný výše použití `ICLRRuntimeHost2` spustit modul runtime, doméně AppDomain vytvoření a spuštění spravovaného kódu by měla fungovat pro všechny podporované operační systémy. Rozhraní definované v mscoree.h však může být náročná fungovat s na platformách systému Unix, protože knihovna mscoree díky mnoho předpokladů Win32.

Chcete-li hostování na platformě Unix jednodušší, jsou k dispozici v sadu další rozhraní API obálky hostitelské platformy neutrální [coreclrhost.h](https://github.com/dotnet/coreclr/blob/master/src/coreclr/hosts/inc/coreclrhost.h).

Příklad použití coreclrhost.h (namísto přímo mscoree.h) si můžete prohlédnout ve [UnixCoreRun hostitele](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts). Postup používání rozhraní API z coreclrhost.h jako hostitele modulu runtime jsou podobné kroky při použití mscoree.h:

1. Najděte v něm spravovaný kód ke spuštění (z příkazového řádku parametrů, třeba). 
2. Načtěte knihovnu CoreCLR.
    1. `dlopen("./libcoreclr.so", RTLD_NOW | RTLD_LOCAL);` 
3. Získání ukazatele na funkce CoreCLR pro `coreclr_initialize`, `coreclr_create_delegate`, `coreclr_execute_assembly`, a `coreclr_shutdown` funkce používající `dlsym`
    1. `coreclr_initialize_ptr coreclr_initialize = (coreclr_initialize_ptr)dlsym(coreclrLib, "coreclr_initialize");`
4. Nastavte vlastnosti domény aplikace (např. seznam TPA). To je stejný jako krok 5 z postupu mscoree výše.
5. Použití `coreclr_initialize` spusťte modul runtime a vytvořte doméně AppDomain. Tím se vytvoří `hostHandle` ukazatel, který se použije v budoucnu hostování volání.
    1. Všimněte si, že tato funkce provede role oba kroky 4 až 6 z předchozí pracovního postupu. 
6. Použijte buď `coreclr_execute_assembly` nebo `coreclr_create_delegate` pro spuštění spravovaného kódu. Tyto funkce jsou podobná společnosti mscoree `ExecuteAssembly` a `CreateDelegate` funkce z kroku 7 předchozí pracovního postupu.
7. Použití `coreclr_shutdown` uvolnění domény AppDomain a ukončení modulu runtime. 

## <a name="conclusion"></a>Závěr
Jakmile hostitele je sestavená, můžete otestovat spuštěním z příkazového řádku a předáním argumentů (jako je spuštění spravované aplikace) očekává hostitele. Při zadávání aplikaci .NET Core pro hostitele ke spuštění, nezapomeňte použít soubor .dll, který je vytvořen `dotnet build`. Spustitelné soubory vytvářené `dotnet publish` pro samostatné aplikace jsou ve skutečnosti výchozí hostitel .NET Core (tak, aby aplikaci můžete spustit přímo z příkazového řádku v hlavní linii scénáře); uživatelský kód je zkompilován do knihovny dll se stejným názvem. 

Pokud věci zpočátku nefunguje, zkontrolujte *coreclr.dll* je k dispozici v umístění očekává hostitele, jsou v seznamu TPA všechny potřebné knihovny rozhraní Framework, který odpovídá této CoreCLR bitové verze (32 - a 64-bit) jak byla vytvořena hostitele.

Hostování modulu runtime .NET Core je pokročilý scénář celá řada vývojářů nebude vyžadovat, že pro ty, kteří potřebují ke spuštění spravovaného kódu z nativní proces nebo který potřebujete větší kontrolu nad chování modulu runtime .NET Core, může být velmi užitečné. Protože je možné spouštět vedle sebe .NET Core se sebou samým, je dokonce možné vytvořit hostitele, kteří inicializaci a spuštění více verzí modulu runtime .NET Core a spouštění aplikací na všechny z nich ve stejném procesu. 
