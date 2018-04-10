---
title: Hostování rozhraní .NET Core
description: Hostování na .NET Core runtime z nativního kódu
keywords: .NET, .NET Core, Hosting, Hosting .NET Core
author: mjrousos
ms.author: mikerou
ms.date: 2/3/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 13edec8b-614d-47ed-9e95-ed6d3b94ec0c
ms.workload:
- dotnetcore
ms.openlocfilehash: 5ff2e8e4da12b2a9822b595abbb2bdb0f583cf02
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2018
---
# <a name="hosting-net-core"></a>Hostování rozhraní .NET Core

Podobně jako všechny spravovaného kódu jsou aplikace .NET Core provedený hostitele. Hostitel je zodpovědná za spuštění modulu runtime (včetně komponenty, jako jsou JIT a systém uvolňování paměti), vytváření domén a vyvolání spravovat vstupní body.

Hostování na .NET Core runtime je pokročilý scénář a ve většině případů .NET Core vývojáři nemusíte si dělat starosti o hostování, protože sestavení .NET Core procesy zadejte výchozí hostitel ke spouštění aplikací .NET Core. V některých případech specializované ale může být užitečné explicitně hostitele na .NET Core runtime buď jako prostředek k vyvolání spravovaného kódu v procesu nativní nebo aby bylo možné získat lepší kontrolu nad fungování modulu runtime.

Tento článek nabízí přehled kroky nutné ke spuštění z nativního kódu na .NET Core runtime, vytvoření domény aplikace počáteční (<xref:System.AppDomain>) a spusťte spravovaného kódu v ní.

## <a name="prerequisites"></a>Požadavky

Vzhledem k tomu, že mají hostitelé nativních aplikací, v tomto kurzu se bude zabývat vytváření aplikace C++ hostitele .NET Core. Budete potřebovat C++ vývojové prostředí (například poskytnutá [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)).

Můžete také jednoduchou aplikaci .NET Core k testování hostitele, takže byste měli nainstalovat [.NET Core SDK](https://www.microsoft.com/net/core) a [sestavení malé testování aplikace .NET Core](../../core/tutorials/with-visual-studio.md) (například "Zdravím svět" aplikace). Vytvořit novou šablonou projektu konzoly .NET Core "Zdravím svět" aplikace je dostačující.

Tento kurz a jeho přidružené ukázkové sestavení hostitele Windows; v části poznámky na konci tohoto článku o hostování v systému Unix.

## <a name="creating-the-host"></a>Vytváření hostitele

A [Ukázkový hostitel](https://github.com/dotnet/samples/tree/master/core/hosting) demonstraci podle kroků uvedených v tomto článku je k dispozici v úložišti GitHub dotnet nebo ukázky. Komentáře v ukázce je *host.cpp* souboru jasně přidružení číslem kroků tohoto kurzu, pomocí které se provádí v ukázce. Pokyny ke stažení najdete v tématu [ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Mějte na paměti, že Ukázkový hostitel je určen pro použití pro učení účely, takže je indikátor na Kontrola chyb a slouží k zdůraznil čitelnost přes efektivitu. Další ukázky reálného hostitele jsou k dispozici v [dotnet/coreclr](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts) úložiště. [CoreRun hostitele](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts/corerun), zejména, je dobré pro obecné účely hostitele studovat po přečtení prostřednictvím jednodušší ukázka.

### <a name="a-note-about-mscoreeh"></a>Poznámka o mscoree.h
Primární .NET Core, který je hostitelem rozhraní (`ICLRRuntimeHost2`) je definován v [MSCOREE. IDL](https://github.com/dotnet/coreclr/blob/master/src/inc/MSCOREE.IDL). Záhlaví verze tohoto souboru (mscoree.h), který chcete-li potřebovat váš hostitel, vytváří prostřednictvím MIDL při [.NET Core runtime](https://github.com/dotnet/coreclr/) je sestaven. Pokud nechcete vytvořit na .NET Core runtime, mscoree.h je také k dispozici jako [předdefinovaných záhlaví](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc) v úložišti dotnet/coreclr. [Pokyny pro vytváření na .NET Core runtime](https://github.com/dotnet/coreclr#building-the-repository) lze nalézt v jeho úložiště GitHub. 

### <a name="step-1---identify-the-managed-entry-point"></a>Krok 1 – identifikace spravované vstupního bodu
Po odkazující na potřebné hlavičky ([mscoree.h](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc/mscoree.h) a stdio.h, např.), jedním z nejdůležitějších věcí, musíte udělat na .NET Core hostitele je najít spravované vstupní bod budou používat. V hostiteli naše ukázka k tomu je potřeba jenom trvá první argument příkazového řádku na našem hostitele jako cesta k spravované binární jejichž `main` metoda bude proveden.

[!code-cpp[NetCoreHost#1](../../../samples/core/hosting/host.cpp#1)]

### <a name="step-2---find-and-load-coreclrdll"></a>Krok 2 – vyhledání a načtení CoreCLR.dll
Na .NET Core runtime rozhraní API jsou v *CoreCLR.dll* (v systému Windows). Chcete-li získat naše hostování rozhraní (`ICLRRuntimeHost2`), je nutné k vyhledání a načtení *CoreCLR.dll*. Je hostitel k definování konvence pro jak bude najít *CoreCLR.dll*. Některé hostitele očekávají, že byl soubor přítomen v dobře známé umístění celého systému (například % programfiles%\dotnet\shared\Microsoft.NETCore.App\1.1.0). Ostatní očekávat, který *CoreCLR.dll* budou načteny z umístění vedle buď hostitele sám sebe nebo aplikace pro hostování. Ostatní může stále poraďte se proměnná prostředí k nalezení knihovny.

Mac nebo Linux, je základní modul runtime knihovny *libcoreclr.so* nebo *libcoreclr.dylib*, v uvedeném pořadí.

Naše ukázka hostitele sondy několik společné umístění pro *CoreCLR.dll*. Jednou najde, musí být načteny prostřednictvím `LoadLibrary` (nebo `dlopen` v systému Linux nebo Mac).

[!code-cpp[NetCoreHost#2](../../../samples/core/hosting/host.cpp#2)]

### <a name="step-3---get-an-iclrruntimehost2-instance"></a>Krok 3 – získat instanci ICLRRuntimeHost2
`ICLRRuntimeHost2` Hostování rozhraní se načítají pomocí volání `GetProcAddress` (nebo `dlsym` v systému Linux nebo Mac) na `GetCLRRuntimeHost`a pak volání této funkce. 

[!code-cpp[NetCoreHost#3](../../../samples/core/hosting/host.cpp#3)]

### <a name="step-4---setting-startup-flags-and-starting-the-runtime"></a>Krok 4 – nastavení příznaky spuštění a spuštění modulu runtime
S `ICLRRuntimeHost2` na skladě, jsme teď můžete zadat příznaky runtime celou spuštění a spuštění modulu runtime. Příznaky spuštění určí, které systém uvolňování paměti (GC) použít (souběžných nebo serveru), jestli budeme používat jeden AppDomain nebo více domén a jaké zásady optimalizace zavaděče (pro domény jazykově neutrální načítání sestavení).

[!code-cpp[NetCoreHost#4](../../../samples/core/hosting/host.cpp#4)]

Modul runtime je spuštěn s volání `Start` funkce.

```C++
hr = runtimeHost->Start();
```

### <a name="step-5---preparing-appdomain-settings"></a>Krok 5 – nastavení Příprava domény aplikace
Jakmile začne modul runtime, jsme budou chtít nastavit možnost objektu AppDomain. Existuje několik možností, které se musí zadat při vytváření .NET AppDomain, ale je nezbytné pro přípravu tyto první.

Doména AppDomain příznaky zadejte AppDomain chování souvisejících se zabezpečením a zprostředkovatel komunikace s objekty. Starší hostitelů Silverlight použít tato nastavení do izolovaného prostoru uživatelského kódu, ale většina moderních hostitele .NET Core spuštění uživatelského kódu jako úplný vztah důvěryhodnosti a povolit zprostředkovatele komunikace s objekty.

[!code-cpp[NetCoreHost#5](../../../samples/core/hosting/host.cpp#5)]

Jakmile se rozhodnete, které AppDomain flags používat, musí být definovány vlastnosti domény aplikace. Vlastnosti jsou páry klíč – hodnota řetězce. Mnoho z těchto vlastností se týkají způsob načtení sestavení domény aplikace.

Běžné vlastnosti objektu třídy AppDomain:

* `TRUSTED_PLATFORM_ASSEMBLIES` Toto je seznam sestavení cesty (oddělený podle ';' v systému Windows a ':' v systému Unix) které domény aplikace by měl upřednostňovat načítání a udělte úplný vztah důvěryhodnosti (i v částečně důvěryhodné domény). Tento seznam slouží k obsahovat sestavení 'architektury a další důvěryhodné moduly, podobně jako do mezipaměti GAC ve scénářích rozhraní .NET Framework. Někteří hostitelé budou vedle put žádnou knihovnu *coreclr.dll* v tomto seznamu, ostatní uživatelé mají pevně manifesty seznam důvěryhodných sestavení pro svoje účely.
* `APP_PATHS` Toto je seznam cest k testu v sestavení, pokud nebyl nalezen v seznamu důvěryhodných platformy sestavení (TPA). Tyto cesty jsou určeny jako umístění, kde můžete najít sestavení uživatelů. V doméně AppDomain v izolovaném prostoru sestavení, které jsou načteny z těchto cest bude poskytnuta pouze částečnou důvěryhodností. Běžné cesty APP_PATH obsahovat cestu, kterou aplikace target byla načtena z nebo jiných umístění, kde jsou známé prostředky uživatele za provozu.
*  `APP_NI_PATHS` Tento seznam je velmi podobné APP_PATHS s tím rozdílem, že má měl představovat cesty, které bude zjištěný pro nativní bitové kopie.
*  `NATIVE_DLL_SEARCH_DIRECTORIES` Tato vlastnost je seznam cesty, které by měl zavaděč testu při hledání nativních knihoven DLL volání prostřednictvím p/invoke.
*  `PLATFORM_RESOURCE_ROOTS` Tento seznam obsahuje cest k testu v pro prostředek satelitní sestavení (v podadresářích specifické pro jazykovou verzi).
*  `AppDomainCompatSwitch` Tento řetězec Určuje, které adaptivní kompatibility se mají použít pro sestavení bez explicitního Přezdívka Framework cíl (úrovni sestavení atribut, která určuje, které Framework sestavení je určen ke spouštění). Obvykle to musí být nastavena na `"UseLatestBehaviorWhenTFMNotSpecified"` , ale některé hostitele nastavit tak, aby starší Silverlight nebo Windows Phone adaptivní kompatibility, místo toho získat.

V našem [jednoduchého ukázkového hostitele](https://github.com/dotnet/samples/tree/master/core/hosting), tyto vlastnosti jsou nastavíte takto:

[!code-cpp[NetCoreHost#6](../../../samples/core/hosting/host.cpp#6)]

### <a name="step-6---create-the-appdomain"></a>Krok 6 – Vytvoření domény aplikace
Jakmile jsou připravené všechny AppDomain příznaky a vlastnosti, `ICLRRuntimeHost2::CreateAppDomainWithManager` slouží k nastavení domény aplikace. Tato funkce přebírá volitelně plně kvalifikovaný název sestavení a název typu, který bude použit jako správce domény AppDomain. Správce domény aplikace můžete povolit hostitele k řízení některých aspektů AppDomain chování a může poskytnout vstupní body pro spuštění spravovaného kódu, pokud hostitel není v úmyslu přímo vyvolat uživatelského kódu.   

[!code-cpp[NetCoreHost#7](../../../samples/core/hosting/host.cpp#7)]

### <a name="step-7---run-managed-code"></a>Krok 7: spravovaný kód a spusťte!
Pomocí objektu AppDomain spuštěná, hostitele nyní můžete spustit provádění spravovaného kódu. Nejjednodušším způsobem je použití `ICLRRuntimeHost2::ExecuteAssembly` k vyvolání metody vstupní bod spravované sestavení. Všimněte si, že tato funkce funguje jen v jedné doméně scénáře.

[!code-cpp[NetCoreHost#8](../../../samples/core/hosting/host.cpp#8)]

Další možnost, pokud `ExecuteAssembly` nevyhovuje potřebám vaší hostitele, je použití `CreateDelegate` vytvoření ukazatel funkce na statického spravovanou metoda. To vyžaduje hostitele vědět podpis metody je volání do (Chcete-li vytvořit typ ukazatele funkce), ale umožňuje hostitelům flexibilitu při vyvolání kódu než sestavení vstupní bod.

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

### <a name="step-8---clean-up"></a>Krok 8 – vyčistit.
Nakonec se hostitele by měl vyčištění po samotné uvolnění domén, zastavení modulu runtime a uvolněním `ICLRRuntimeHost2` odkaz.

[!code-cpp[NetCoreHost#9](../../../samples/core/hosting/host.cpp#9)]

## <a name="about-hosting-net-core-on-unix"></a>O hostování rozhraní .NET Core v systému Unix
.NET core je produkt napříč platformami, běžící na operačních systémech Windows, Linuxu a Macu. Jako nativních aplikací ale hostitele pro různé platformy bude mít některé rozdíly mezi nimi. Proces popsaný výše použití `ICLRRuntimeHost2` spustit modul runtime, vytvoření objektu AppDomain a spouštět spravovaného kódu, by měly fungovat pro všechny podporované operační systémy. Rozhraní definované v mscoree.h však může být náročná pracovat na platformách systému Unix, vzhledem k tomu, že mscoree díky mnoha Win32 předpoklady.

Chcete-li hostování na platformě Unix jednodušší, jsou k dispozici v sadu další rozhraní API obálky hostování platformy jazykově neutrální [coreclrhost.h](https://github.com/dotnet/coreclr/blob/master/src/coreclr/hosts/inc/coreclrhost.h).

Příklad použití coreclrhost.h (namísto přímo mscoree.h) si můžete prohlédnout ve [UnixCoreRun hostitele](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts). Kroky při použití rozhraní API z coreclrhost.h jako hostitele modulu runtime jsou podobné kroky při použití mscoree.h:

1. Identifikovat spravovaného kódu k provedení (z příkazového řádku parametrů, třeba). 
2. Načtení knihovny CoreCLR.
    1. `dlopen("./libcoreclr.so", RTLD_NOW | RTLD_LOCAL);` 
3. Získání ukazatele na funkce do CoreCLR na `coreclr_initialize`, `coreclr_create_delegate`, `coreclr_execute_assembly`, a `coreclr_shutdown` funkcí pomocí `dlsym`
    1. `coreclr_initialize_ptr coreclr_initialize = (coreclr_initialize_ptr)dlsym(coreclrLib, "coreclr_initialize");`
4. Nastavte vlastnosti domény aplikace (např. seznam TPA). Toto je stejný jako krok 5 z mscoree pracovní postup, výše.
5. Použití `coreclr_initialize` spuštění modulu runtime a vytvoření objektu AppDomain. Tím se vytvoří `hostHandle` ukazatele, který se použije v budoucnosti hostování volání.
    1. Pamatujte, že tato funkce role oba kroky 4 a 6 z předchozí pracovního postupu. 
6. Použijte buď `coreclr_execute_assembly` nebo `coreclr_create_delegate` provést spravovaného kódu. Tyto funkce jsou obdobou na mscoree `ExecuteAssembly` a `CreateDelegate` funkce z kroku 7 předchozí pracovního postupu.
7. Použití `coreclr_shutdown` pro uvolnění domény aplikace a vypnutí modulu runtime. 

## <a name="conclusion"></a>Závěr
Po vašem hostiteli, lze je testovat pomocí spuštění z příkazového řádku a předání argumentů (jako spravovanou aplikaci spustit) očekává hostitele. Při zadávání aplikace .NET Core pro hostitele ke spuštění, je nutné používat .dll, který je produkovaný `dotnet build`. Spustitelné soubory vyprodukované `dotnet publish` pro samostatné aplikace jsou ve skutečnosti výchozí hostitel .NET Core (tak, aby aplikace může být spuštěn přímo z příkazového řádku v nejdůležitějších scénáře); kompilace kódu uživatele do knihovny dll se stejným názvem. 

Pokud původně nefungují věcí, zkontrolujte *coreclr.dll* je k dispozici v umístění očekávání pro hostitele, který všechny nezbytné Framework knihovny jsou v seznamu TPA a že CoreCLR počtu bitů (32 - nebo 64 bitů) odpovídá jak bylo vytvořeno hostitele.

Hostování na .NET Core runtime je pokročilý scénář, že nebude vyžadovat celá řada vývojářů, ale pro ty, kteří potřebují spustit spravovaného kódu z nativní proces, nebo kteří potřebují větší kontrolu nad na .NET Core runtime chování, může být velmi užitečné. Protože je možné spouštět souběžně sdílená .NET Core s samostatně, je i možné vytvořit hostitelů inicializaci a spustit několik verzí .NET Core runtime a spuštění aplikace na všech těchto v rámci jednoho procesu. 
