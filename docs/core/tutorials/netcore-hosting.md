---
title: Napsat vlastního hostitele runtime jádra .NET
description: Naučte se hostovat runtime jádra .NET z nativního kódu pro podporu pokročilých scénářů, které vyžadují řízení fungování runtime .NET Core.
author: mjrousos
ms.date: 12/21/2018
ms.openlocfilehash: 46c7873a1865db04cf1c2b1bb2ded2b5dacbcc8d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78239895"
---
# <a name="write-a-custom-net-core-host-to-control-the-net-runtime-from-your-native-code"></a>Napište vlastní hostiteli jádra .NET pro řízení běhu .NET z nativního kódu

Stejně jako všechny spravované kódy, .NET Core aplikace jsou spouštěny hostitelem. Hostitel je zodpovědný za spuštění runtime (včetně součástí, jako je JIT a uvolňování paměti) a vyvolání spravovaných vstupních bodů.

Hostování runtime .NET Core je pokročilý scénář a ve většině případů vývojáři .NET Core se nemusí starat o hostování, protože procesy sestavení .NET Core poskytují výchozího hostitele pro spuštění aplikací .NET Core. V některých specializovaných okolností však může být užitečné explicitně hostovat zaběhu .NET Core, buď jako prostředek vyvolání spravovaného kódu v nativním procesu, nebo za účelem získání větší kontroly nad tím, jak runtime funguje.

Tento článek poskytuje přehled kroků nezbytných ke spuštění runtime .NET Core z nativního kódu a spuštění spravovaného kódu v něm.

## <a name="prerequisites"></a>Požadavky

Vzhledem k tomu, že hostitelé jsou nativní aplikace, tento kurz zahrnuje konstrukci aplikace Jazyka C++ pro hostování .NET Core. Budete potřebovat vývojové prostředí jazyka C++ (například prostředí poskytované [aplikací Visual Studio).](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

Budete také chtít jednoduchou aplikaci .NET Core pro testování hostitele, takže byste měli nainstalovat [.NET Core SDK](https://dotnet.microsoft.com/download) a [vytvořit malou testovací aplikaci .NET Core](with-visual-studio.md) (například aplikaci Hello World). Aplikace Hello World vytvořená novou šablonou konzoly .NET Core je dostatečná.

## <a name="hosting-apis"></a>Hostování apis
Existují tři různá rozhraní API, která lze použít k hostování .NET Core. Tento článek (a jeho přidružené [ukázky)](https://github.com/dotnet/samples/tree/master/core/hosting)pokrývá všechny možnosti.

* Upřednostňovanou metodou hostování runtime jádra .NET v rozhraní .NET `nethost` Core `hostfxr` 3.0 a vyšší je rozhraní API a knihovny. Tyto vstupní body zpracovávají složitost hledání a nastavení runtime pro inicializaci a umožňují spuštění spravované aplikace a volání do statické spravované metody.
* Upřednostňovanou metodou hostování runtime .NET Core před rozhraním .NET Core 3.0 je [rozhraní CoreClrHost.h](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/hosts/inc/coreclrhost.h) API. Toto rozhraní API zveřejňuje funkce pro snadné spuštění a zastavení runtime a vyvolání spravovaného kódu (buď spuštěním spravovaného exe nebo voláním statických spravovaných metod).
* .NET Core lze také hostovat s rozhraním `ICLRRuntimeHost4` v [mscoree.h](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/pal/prebuilt/inc/mscoree.h). Toto rozhraní API bylo delší než CoreClrHost.h, takže jste možná viděli starší hostitele, kteří ho používají. Stále funguje a umožňuje trochu větší kontrolu nad procesem hostování než CoreClrHost. Pro většinu scénářů je však CoreClrHost.h nyní upřednostňován z důvodu jeho jednodušších api.

## <a name="sample-hosts"></a>Ukázkové hostitele

[Ukázkoví hostitelé](https://github.com/dotnet/samples/tree/master/core/hosting) demonstrující kroky popsané v níže uvedených kurzech jsou k dispozici v úložišti GitHub dotnet/samples. Komentáře ve vzorcích jasně přidružit číslované kroky z těchto kurzů s kde jsou prováděny v ukázce. Pokyny ke stažení naleznete v [tématu Ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Mějte na paměti, že ukázkové hostitele jsou určeny pro účely učení, takže jsou lehké na kontrolu chyb a jsou navrženy tak, aby zdůraznily čitelnost oproti efektivitě.

## <a name="create-a-host-using-nethosth-and-hostfxrh"></a>Vytvoření hostitele pomocí NetHost.h a HostFxr.h

Následující kroky podrobně popisují, `nethost` `hostfxr` jak pomocí knihoven a spustit runtime .NET Core v nativní aplikaci a volat do spravované statické metody. [Ukázka](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithHostFxr) používá `nethost` záhlaví a knihovnu nainstalovanou sadou .NET SDK a kopie souborů [`coreclr_delegates.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/coreclr_delegates.h) a [`hostfxr.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/hostfxr.h) z úložiště [dotnet/core-setup.](https://github.com/dotnet/core-setup)

### <a name="step-1---load-hostfxr-and-get-exported-hosting-functions"></a>Krok 1 - Načíst HostFxr a získat exportované hostitelské funkce

Knihovna `nethost` poskytuje `get_hostfxr_path` funkci pro vyhledání knihovny. `hostfxr` Knihovna `hostfxr` zveřejňuje funkce pro hostování za běhu jádra .NET. Úplný seznam funkcí lze nalézt [`hostfxr.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/hostfxr.h) v a [nativní hosting návrhdokumentu](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/native-hosting.md). Ukázka a tento kurz používají následující:

* `hostfxr_initialize_for_runtime_config`: Inicializuje kontext hostitele a připraví se na inicializaci zaběhu .NET Core pomocí zadané konfigurace runtime.
* `hostfxr_get_runtime_delegate`: Získá delegáta pro funkce za běhu.
* `hostfxr_close`: Zavře kontext hostitele.

Knihovna se `hostfxr` `get_hostfxr_path`nachází pomocí . Potom je načten a jeho exporty jsou načteny.

[!code-cpp[HostFxrHost#LoadHostFxr](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#LoadHostFxr)]

### <a name="step-2---initialize-and-start-the-net-core-runtime"></a>Krok 2 – Inicializovat a spustit zaběhu jádra .NET

Funkce `hostfxr_initialize_for_runtime_config` `hostfxr_get_runtime_delegate` a inicializují a spouštějí zaběhu .NET Core pomocí konfigurace runtime pro spravovanou součást, která bude načtena. Funkce `hostfxr_get_runtime_delegate` se používá k získání delegáta za běhu, který umožňuje načtení spravovaného sestavení a získání ukazatele funkce na statickou metodu v tomto sestavení.

[!code-cpp[HostFxrHost#Initialize](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#Initialize)]

### <a name="step-3---load-managed-assembly-and-get-function-pointer-to-a-managed-method"></a>Krok 3 – Načtení spravovaného sestavení a získání ukazatele funkce na spravovanou metodu

Delegát za běhu je volán k načtení spravovaného sestavení a získání ukazatele funkce na spravovanou metodu. Delegát vyžaduje cestu sestavení, název typu a název metody jako vstupy a vrátí ukazatel funkce, který lze použít k vyvolání spravované metody.

[!code-cpp[HostFxrHost#LoadAndGet](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#LoadAndGet)]

Předáním `nullptr` jako název typu delegáta při volání delegáta runtime ukázka používá výchozí podpis pro spravovanou metodu:

```csharp
public delegate int ComponentEntryPoint(IntPtr args, int sizeBytes);
```

Jiný podpis lze použít zadáním názvu typu delegáta při volání zástupce runtime.

### <a name="step-4---run-managed-code"></a>Krok 4 – Spusťte spravovaný kód!

Nativní hostitel nyní může volat spravovanou metodu a předat jí požadované parametry.

[!code-cpp[HostFxrHost#CallManaged](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#CallManaged)]

## <a name="create-a-host-using-coreclrhosth"></a>Vytvoření hostitele pomocí CoreClrHost.h

Následující kroky podrobně popisují, jak pomocí rozhraní CoreClrHost.h API spustit runtime .NET Core v nativní aplikaci a volat do spravované statické metody. Fragmenty kódu v tomto dokumentu používají některá api specifická pro systém Windows, ale [úplný ukázkový hostitel](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithCoreClrHost) zobrazuje cesty kódu systému Windows i Linux.

Unix [CoreRun host](https://github.com/dotnet/runtime/tree/master/src/coreclr/src/hosts/unixcorerun) ukazuje složitější, real-svět příklad hostingu pomocí coreclrhost.h.

### <a name="step-1---find-and-load-coreclr"></a>Krok 1 – Nalezení a načtení coreclru

Rozhraní .NET Core runtime API jsou v *coreclr.dll* (v systému Windows), v *libcoreclr.so* (na Linuxu) nebo v *libcoreclr.dylib* (na macOS). Prvním krokem k hostování .NET Core je načtení knihovny CoreCLR. Někteří hostitelé sondují různé cesty nebo používají vstupní parametry k nalezení knihovny, zatímco jiní vědí, že ji mají načíst z určité cesty (například vedle hostitele nebo z umístění v celém počítači).

Po nalezení je knihovna `LoadLibraryEx` načtena (ve Windows) nebo `dlopen` (na Linuxu /macOS).

[!code-cpp[CoreClrHost#1](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#1)]

### <a name="step-2---get-net-core-hosting-functions"></a>Krok 2 – Získání funkcí hostingu .NET Core

CoreClrHost má několik důležitých metod užitečných pro hostování .NET Core:

* `coreclr_initialize`: Spustí runtime jádra .NET a nastaví výchozí (a pouze) AppDomain.
* `coreclr_execute_assembly`: Provede spravované sestavení.
* `coreclr_create_delegate`: Vytvoří ukazatel funkce na spravovanou metodu.
* `coreclr_shutdown`: Vypne zaběhu .NET Core.
* `coreclr_shutdown_2`: `coreclr_shutdown`To se mi líbí , ale také načte ukončovací kód spravovaného kódu.

Po načtení knihovny CoreCLR je dalším krokem získání `GetProcAddress` odkazů na tyto `dlsym` funkce pomocí (ve Windows) nebo (v Linuxu/macOS).

[!code-cpp[CoreClrHost#2](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#2)]

### <a name="step-3---prepare-runtime-properties"></a>Krok 3 – Příprava vlastností runtime

Před spuštěním runtime je nutné připravit některé vlastnosti pro určení chování (zejména pokud jde o montážní zavaděč).

Mezi běžné vlastnosti patří:

* `TRUSTED_PLATFORM_ASSEMBLIES`Toto je seznam cest sestavení (oddělených ';' v systému Windows a ':' v systému Linux), které bude runtime schopen vyřešit ve výchozím nastavení. Někteří hostitelé mají pevně zakódované manifesty se seznamem sestavení, která mohou načíst. Ostatní budou umístit všechny knihovny v určitých umístěních (vedle *coreclr.dll*, například) v tomto seznamu.
* `APP_PATHS`Toto je seznam cest pro sondy v sestavení, pokud nelze nalézt v seznamu sestavení důvěryhodných platforem (TPA). Vzhledem k tomu, že hostitel má větší kontrolu nad sestaveními, která jsou načtena pomocí seznamu TPA, je osvědčeným postupem pro hostitele určit, která sestavení očekávají, že načtou a výslovně je vydají. Pokud je potřeba zjišťování za běhu, ale tato vlastnost můžete povolit tento scénář.
* `APP_NI_PATHS`Tento seznam je podobný APP_PATHS kromě toho, že je určen k cestám, které budou sondovány pro nativní obrázky.
* `NATIVE_DLL_SEARCH_DIRECTORIES`Tato vlastnost je seznam cest zavaděč by měl sondy při hledání nativní knihovny volána prostřednictvím p/invoke.
* `PLATFORM_RESOURCE_ROOTS`Tento seznam obsahuje cesty ke sondě v pro satelitní sestavení prostředků (v podadresářích specifických pro jazykovou verzi).

V tomto ukázkovém hostiteli je seznam TPA vytvořen jednoduše výpisem všech knihoven v aktuálním adresáři:

[!code-cpp[CoreClrHost#7](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#7)]

Vzhledem k tomu, že `TRUSTED_PLATFORM_ASSEMBLIES` ukázka je jednoduchá, potřebuje pouze vlastnost:

[!code-cpp[CoreClrHost#3](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#3)]

### <a name="step-4---start-the-runtime"></a>Krok 4 – spuštění běhu

Na rozdíl od hostitelského rozhraní API mscoree.h (popsané níže) rozhraní API CoreCLRHost.h spustí runtime a vytvoří výchozí doménu AppDomain s jediným voláním. Funkce `coreclr_initialize` trvá základní cestu, název a vlastnosti popsané výše a vrátí zpět `hostHandle` popisovač hostitele prostřednictvím parametru.

[!code-cpp[CoreClrHost#4](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#4)]

### <a name="step-5---run-managed-code"></a>Krok 5 – Spusťte spravovaný kód!

Se spuštěním runtime může hostitel volat spravovaný kód. To lze provést několika různými způsoby. Ukázkový kód propojený s `coreclr_create_delegate` tímto kurzem používá funkci k vytvoření delegáta statické spravované metody. Toto rozhraní API přebírá [název sestavení](../../standard/assembly/names.md), název typu s kvalifikovanou kvalifikací oboru názvů a název metody jako vstupy a vrátí delegáta, který lze použít k vyvolání metody.

[!code-cpp[CoreClrHost#5](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#5)]

V této ukázce `managedDelegate` může hostitel `ManagedWorker.DoWork` nyní volat ke spuštění metody.

Alternativně `coreclr_execute_assembly` lze funkci použít ke spuštění spravovaného spustitelného souboru. Toto rozhraní API přebírá cestu sestavení a pole argumentů jako vstupní parametry. Načte sestavení na této cestě a vyvolá jeho hlavní metodu.

```C++
int hr = executeAssembly(
        hostHandle,
        domainId,
        argumentCount,
        arguments,
        "HelloWorld.exe",
        (unsigned int*)&exitCode);
```

### <a name="step-6---shutdown-and-clean-up"></a>Krok 6 – Vypnutí a vyčištění

Nakonec po dokončení spuštění spravovaného kódu hostitele je runtime jádra .NET vypnuto pomocí `coreclr_shutdown` nebo `coreclr_shutdown_2`.

[!code-cpp[CoreClrHost#6](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#6)]

CoreCLR nepodporuje reinicializaci nebo uvolnění. Nevolejte `coreclr_initialize` znovu nebo uvolnit knihovnu CoreCLR.

## <a name="create-a-host-using-mscoreeh"></a>Vytvoření hostitele pomocí mscoree.h

Jak již bylo zmíněno dříve, CoreClrHost.h je nyní upřednostňovanou metodou hostování runtime .NET Core. Rozhraní `ICLRRuntimeHost4` lze stále použít, i když pokud rozhraní CoreClrHost.h nejsou dostatečné (pokud jsou potřeba nestandardní spouštěcí příznaky, například, nebo pokud AppDomainManager je potřeba na výchozí doméně). Tyto pokyny vás provedou hostováním .NET Core pomocí souboru mscoree.h.

[CoreRun host](https://github.com/dotnet/runtime/tree/master/src/coreclr/src/hosts/corerun) ukazuje složitější, real-svět příklad hostování pomocí mscoree.h.

### <a name="a-note-about-mscoreeh"></a>Poznámka o mscoree.h
Hostitelské `ICLRRuntimeHost4` rozhraní .NET Core je definováno v [MSCOREE. IDL](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/inc/MSCOREE.IDL). Hlavičková verze tohoto souboru (mscoree.h), na kterou bude váš hostitel muset odkazovat, je vytvořena prostřednictvím protokolu MIDL při vytvoření [runtime .NET Core.](https://github.com/dotnet/runtime/) Pokud nechcete vytvářet runtime .NET Core, mscoree.h je také k dispozici jako [předem sestavené záhlaví](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/pal/prebuilt/inc/) v úložišti dotnet/runtime.

### <a name="step-1---identify-the-managed-entry-point"></a>Krok 1 – Identifikace spravovaného vstupního bodu
Po odkazování na nezbytné hlavičky[(například mscoree.h](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/pal/prebuilt/inc/mscoree.h) a stdio.h) je jednou z prvních věcí, kterou musí hostitel .NET Core udělat, najít spravovaný vstupní bod, který bude používat. V našem ukázkovém hostiteli se to provádí pouze tím, že první argument `main` příkazového řádku našeho hostitele jako cestu ke spravovanébinární, jehož metoda bude spuštěna.

[!code-cpp[NetCoreHost#1](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#1)]

### <a name="step-2---find-and-load-coreclr"></a>Krok 2 – Nalezení a načtení coreclr
Rozhraní API prostředí .NET Core runtime jsou v *souboru CoreCLR.dll* (v systému Windows). Chcete-li získat`ICLRRuntimeHost4`naše hostingové rozhraní ( ), je nutné najít a načíst *CoreCLR.dll*. Je na hostiteli, aby definoval konvenci, jak bude vyhledávat *soubor CoreCLR.dll*. Někteří hostitelé očekávají, že soubor bude přítomen ve známém umístění pro celý počítač (například *%programfiles%\dotnet\shared\Microsoft.NETCore.App\2.1.6*). Jiní očekávají, že *CoreCLR.dll* bude načten z umístění vedle samotného hostitele nebo aplikace, která má být hostována. Ještě jiní mohou konzultovat proměnné prostředí najít knihovnu.

V Linuxu nebo macOS je základní runtime knihovna *libcoreclr.so* nebo *libcoreclr.dylib*.

Naše ukázkové hostitelské sondy několik běžných umístění pro *CoreCLR.dll*. Jakmile je nalezen, musí `LoadLibrary` být `dlopen` načten přes (nebo na Linuxu / macOS).

[!code-cpp[NetCoreHost#2](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#2)]

### <a name="step-3---get-an-iclrruntimehost4-instance"></a>Krok 3 – získání instance ICLRRuntimeHost4
Hostitelské `ICLRRuntimeHost4` rozhraní je načteno `GetProcAddress` voláním (nebo `dlsym` na Linuxu/macOS) na `GetCLRRuntimeHost`a následným vyvoláním této funkce.

[!code-cpp[NetCoreHost#3](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#3)]

### <a name="step-4---set-startup-flags-and-start-the-runtime"></a>Krok 4 – Nastavení příznaků spuštění a spuštění běhu
S `ICLRRuntimeHost4` in-hand, nyní můžeme zadat runtime-wide spouštěcí příznaky a spustit. Příznaky spuštění určují, který systém uvolňování paměti (GC) se má použít (souběžně nebo server), zda použijeme jednu doménu AppDomain nebo více domén AppDomain a jaké zásady optimalizace zavaděče použít (pro neutrální načítání sestavení domény).

[!code-cpp[NetCoreHost#4](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#4)]

Runtime je spuštěn s voláním `Start` funkce.

```C++
hr = runtimeHost->Start();
```

### <a name="step-5---preparing-appdomain-settings"></a>Krok 5 – Příprava nastavení domény aplikace
Po spuštění runtime budeme chtít nastavit AppDomain. Existuje několik možností, které musí být zadány při vytváření .NET AppDomain, ale proto je nutné připravit ty první.

Příznaky AppDomain určují chování Domény AppDomain související se zabezpečením a interop. Starší hostitelé Silverlight používali tato nastavení k izolovanému prostoru uživatelského kódu, ale většina moderních hostitelů .NET Core spouštěla uživatelský kód jako úplný vztah důvěryhodnosti a povoluje interop.

[!code-cpp[NetCoreHost#5](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#5)]

Po rozhodnutí, které příznaky AppDomain použít, AppDomain vlastnosti musí být definovány. Vlastnosti jsou dvojice řetězce klíč/hodnota. Mnoho vlastností se vztahuje k tomu, jak AppDomain načte sestavení.

Mezi běžné vlastnosti AppDomain patří:

* `TRUSTED_PLATFORM_ASSEMBLIES`Toto je seznam cest sestavení (oddělený chod `;` na Windows a `:` na Linuxu/macOS), které AppDomain by měl yutování načítání a dát plnou důvěru (i v částečně důvěryhodných doménách). Tento seznam má obsahovat sestavení rozhraní Framework a další důvěryhodné moduly, podobně jako gac ve scénářích rozhraní .NET Framework. Někteří hostitelé budou mít všechny knihovny vedle *coreclr.dll* na tomto seznamu, jiní mají pevně zakódované manifesty výpis důvěryhodných sestavení pro jejich účely.
* `APP_PATHS`Toto je seznam cest pro sondy v sestavení, pokud nelze nalézt v seznamu sestavení důvěryhodných platforem (TPA). Vzhledem k tomu, že hostitel má větší kontrolu nad sestaveními, která jsou načtena pomocí seznamu TPA, je osvědčeným postupem pro hostitele určit, která sestavení očekávají, že načtou a výslovně je vydají. Pokud je potřeba zjišťování za běhu, ale tato vlastnost můžete povolit tento scénář.
* `APP_NI_PATHS`Tento seznam je velmi podobný APP_PATHS kromě toho, že to má být cesty, které budou sondoval pro nativní obrázky.
* `NATIVE_DLL_SEARCH_DIRECTORIES`Tato vlastnost je seznam cest zavaděč by měl sondy při hledání nativní knihovny DLL volány prostřednictvím p/invoke.
* `PLATFORM_RESOURCE_ROOTS`Tento seznam obsahuje cesty ke sondě v pro satelitní sestavení prostředků (v podadresářích specifických pro jazykovou verzi).

V našem [jednoduchém ukázkovém hostiteli](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithMscoree)jsou tyto vlastnosti nastaveny takto:

[!code-cpp[NetCoreHost#6](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#6)]

### <a name="step-6---create-the-appdomain"></a>Krok 6 – Vytvoření domény aplikace
Po přípravě všech příznaků a `ICLRRuntimeHost4::CreateAppDomainWithManager` vlastností AppDomain lze nastavit AppDomain. Tato funkce volitelně přebírá plně kvalifikovaný název sestavení a název typu, který chcete použít jako správce domény AppDomain. Správce AppDomain může umožnit hostiteli řídit některé aspekty chování AppDomain a může poskytnout vstupní body pro spuštění spravovaného kódu, pokud hostitel nemá v úmyslu vyvolat uživatelský kód přímo.

[!code-cpp[NetCoreHost#7](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#7)]

### <a name="step-7---run-managed-code"></a>Krok 7 – Spusťte spravovaný kód!
S AppDomain v provozu, hostitel nyní můžete spustit provádění spravovaného kódu. Nejjednodušší způsob, jak to provést, je použít `ICLRRuntimeHost4::ExecuteAssembly` k vyvolání metody vstupního bodu spravovaného sestavení. Všimněte si, že tato funkce funguje pouze ve scénářích s jednou doménou.

[!code-cpp[NetCoreHost#8](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#8)]

Další možností, `ExecuteAssembly` pokud nevyhovuje potřebám hostitele, je `CreateDelegate` použít k vytvoření ukazatele funkce na statickou spravovanou metodu. To vyžaduje, aby hostitel znát podpis metody, kterou volá do (chcete-li vytvořit typ ukazatele funkce), ale umožňuje hostitelům flexibilitu vyvolat kód jiný než vstupní bod sestavení. Název sestavení zadaný v druhém parametru je [úplný název spravovaného sestavení](../../standard/assembly/names.md) knihovny, který má být načíst.

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

### <a name="step-8---clean-up"></a>Krok 8 – Vyčištění
Nakonec by měl hostitel vyčistit po sobě uvolněním AppDomains, zastavením `ICLRRuntimeHost4` runtime a uvolněním odkazu.

[!code-cpp[NetCoreHost#9](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#9)]

CoreCLR nepodporuje uvolnění. Neuvolnovat knihovnu CoreCLR.

## <a name="conclusion"></a>Závěr
Jakmile je hostitel sestaven, může být testován spuštěním z příkazového řádku a předáním všech argumentů, které hostitel očekává (jako je spravovaná aplikace, která má být spuštěna pro hostitele příkladu mscoree). Při zadávání aplikace .NET Core pro spuštění hostitele nezapomeňte použít soubor DLL, `dotnet build`který je vytvářen aplikací . Spustitelné soubory (.exe soubory) vytvořené `dotnet publish` pro samostatné aplikace jsou ve skutečnosti výchozí hostitel .NET Core (takže aplikace může být spuštěna přímo z příkazového řádku v mainline scénáře); uživatelský kód je zkompilován do dll se stejným názvem.

Pokud věci nefungují zpočátku, zkontrolujte, zda *coreclr.dll* je k dispozici v umístění očekává hostitele, že všechny potřebné framework knihovny jsou v seznamu TPA a že Bitness CoreCLR (32bitový nebo 64bitový) odpovídá způsobu, jakým byl vytvořen hostitel.

Hostování runtime .NET Core je pokročilý scénář, který mnoho vývojářů nebude vyžadovat, ale pro ty, kteří potřebují spustit spravovaný kód z nativního procesu nebo kteří potřebují větší kontrolu nad chováním runtime .NET Core, může být velmi užitečné.
