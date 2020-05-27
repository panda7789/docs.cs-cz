---
title: Globalizace a ICU
ms.date: 05/21/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- globalization [.NET Framework], about globalization
- global applications, globalization
- international applications [.NET Framework], globalization
- world-ready applications, globalization
- application development [.NET Framework], globalization
- culture, globalization
- icu, icu on windows, ms-icu
ms.openlocfilehash: 6ea848d4a60069e6702b9d60fd90a55f572fb043
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842525"
---
# <a name="net-globalization-and-icu"></a><span data-ttu-id="f85b6-102">Rozhraní .NET globalizace a ICU</span><span class="sxs-lookup"><span data-stu-id="f85b6-102">.NET globalization and ICU</span></span>

<span data-ttu-id="f85b6-103">Rozhraní API globalizace .NET v minulosti používaly různé základní knihovny na různých platformách.</span><span class="sxs-lookup"><span data-stu-id="f85b6-103">In the past, the .NET globalization APIs used different underlying libraries on different platforms.</span></span> <span data-ttu-id="f85b6-104">V systému UNIX rozhraní API používala [mezinárodní komponenty pro Unicode (ICU)](http://site.icu-project.org/home)a ve Windows používaly [národní podporu národního oddělení (NLS)](/windows/win32/intl/national-language-support).</span><span class="sxs-lookup"><span data-stu-id="f85b6-104">On Unix, the APIs used [International Components for Unicode (ICU)](http://site.icu-project.org/home), and on Windows, they used [National Language Support (NLS)](/windows/win32/intl/national-language-support).</span></span> <span data-ttu-id="f85b6-105">To vedlo k nějakým rozdílům v chování v několik rozhraní API globalizace při spouštění aplikací na různých platformách.</span><span class="sxs-lookup"><span data-stu-id="f85b6-105">This resulted in some behavioral differences in a handful of globalization APIs when running applications on different platforms.</span></span> <span data-ttu-id="f85b6-106">Rozdíly v chování byly patrné z těchto oblastí:</span><span class="sxs-lookup"><span data-stu-id="f85b6-106">Behavior differences were evident in these areas:</span></span>

- <span data-ttu-id="f85b6-107">Jazykové verze a data jazykové verze</span><span class="sxs-lookup"><span data-stu-id="f85b6-107">Cultures and culture data</span></span>
- <span data-ttu-id="f85b6-108">Velikost řetězce</span><span class="sxs-lookup"><span data-stu-id="f85b6-108">String casing</span></span>
- <span data-ttu-id="f85b6-109">Řazení a hledání řetězců</span><span class="sxs-lookup"><span data-stu-id="f85b6-109">String sorting and searching</span></span>
- <span data-ttu-id="f85b6-110">Klíče řazení</span><span class="sxs-lookup"><span data-stu-id="f85b6-110">Sort keys</span></span>
- <span data-ttu-id="f85b6-111">Normalizace řetězců</span><span class="sxs-lookup"><span data-stu-id="f85b6-111">String normalization</span></span>
- <span data-ttu-id="f85b6-112">Podpora mezinárodních názvů domén (IDN)</span><span class="sxs-lookup"><span data-stu-id="f85b6-112">Internationalized Domain Names (IDN) support</span></span>
- <span data-ttu-id="f85b6-113">Zobrazované jméno časového pásma na platformě Linux</span><span class="sxs-lookup"><span data-stu-id="f85b6-113">Time zone display name on Linux</span></span>

<span data-ttu-id="f85b6-114">Od .NET 5,0 mají vývojáři větší kontrolu nad tím, která základní knihovna se používá, a umožňuje aplikacím vyhnout se rozdílům na různých platformách.</span><span class="sxs-lookup"><span data-stu-id="f85b6-114">Starting with .NET 5.0, developers have more control over which underlying library is used, enabling applications to avoid differences across platforms.</span></span>

## <a name="icu-on-windows"></a><span data-ttu-id="f85b6-115">ICU ve Windows</span><span class="sxs-lookup"><span data-stu-id="f85b6-115">ICU on Windows</span></span>

<span data-ttu-id="f85b6-116">Windows 10 Květen 2019 Update a novější verze obsahují [ICU. dll](/windows/win32/intl/international-components-for-unicode--icu-) jako součást operačního systému a .NET 5,0 a novější verze standardně používají ICU.</span><span class="sxs-lookup"><span data-stu-id="f85b6-116">Windows 10 May 2019 Update and later versions include [icu.dll](/windows/win32/intl/international-components-for-unicode--icu-) as part of the OS, and .NET 5.0 and later versions use ICU by default.</span></span> <span data-ttu-id="f85b6-117">Při spuštění v systému Windows se .NET 5,0 a novější verze pokusí načíst `icu.dll` , a pokud jsou k dispozici, používá je pro implementaci globalizace.</span><span class="sxs-lookup"><span data-stu-id="f85b6-117">When running on Windows, .NET 5.0 and later versions try to load `icu.dll` and if it's available, uses it for the globalization implementation.</span></span>  <span data-ttu-id="f85b6-118">Pokud tuto knihovnu nemůžete najít nebo načíst, například při spuštění ve starších verzích Windows, .NET 5,0 a novější verze se vrátí k implementaci založené na NLS.</span><span class="sxs-lookup"><span data-stu-id="f85b6-118">If that library can't be found or loaded, such as when running on older versions of Windows, .NET 5.0 and later versions fall back to the NLS-based implementation.</span></span>

> [!NOTE]
> <span data-ttu-id="f85b6-119">I při použití ICU, `CurrentCulture` , `CurrentUICulture` a používají i `CurrentRegion` Členové rozhraní API operačního systému Windows k respektování uživatelských nastavení.</span><span class="sxs-lookup"><span data-stu-id="f85b6-119">Even when using ICU, the `CurrentCulture`, `CurrentUICulture`, and `CurrentRegion` members still use Windows operating system APIs to honor user settings.</span></span>

### <a name="using-nls-instead-of-icu"></a><span data-ttu-id="f85b6-120">Použití NLS místo ICU</span><span class="sxs-lookup"><span data-stu-id="f85b6-120">Using NLS instead of ICU</span></span>

<span data-ttu-id="f85b6-121">Použití ICU místo NLS může mít za následek rozdíly v chování s některými operacemi souvisejícími s globalizací.</span><span class="sxs-lookup"><span data-stu-id="f85b6-121">Using ICU instead of NLS may result in behavioral differences with some globalization-related operations.</span></span> <span data-ttu-id="f85b6-122">Pokud se chcete vrátit zpět k používání NLS, vývojář může odhlásit ICU implementaci.</span><span class="sxs-lookup"><span data-stu-id="f85b6-122">To revert back to using NLS, a developer can opt out of the ICU implementation.</span></span> <span data-ttu-id="f85b6-123">Aplikace mohou povolit režim NLS některým z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="f85b6-123">Applications can enable NLS mode in any of the following ways:</span></span>

- <span data-ttu-id="f85b6-124">V souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="f85b6-124">In the project file:</span></span>

```xml
<ItemGroup>
  <RuntimeHostConfigurationOption Include="System.Globalization.UseNls" Value="true" />
</ItemGroup>
```

- <span data-ttu-id="f85b6-125">V souboru `runtimeconfig.json`:</span><span class="sxs-lookup"><span data-stu-id="f85b6-125">In the `runtimeconfig.json` file:</span></span>

```json
{
  "runtimeOptions": {
     "configProperties": {
       "System.Globalization.UseNls": true
      }
  }
}
```

- <span data-ttu-id="f85b6-126">Nastavením proměnné prostředí `DOTNET_SYSTEM_GLOBALIZATION_USENLS` na hodnotu `true` nebo `1` .</span><span class="sxs-lookup"><span data-stu-id="f85b6-126">By setting the environment variable `DOTNET_SYSTEM_GLOBALIZATION_USENLS` to the value `true` or `1`.</span></span>

> [!NOTE]
> <span data-ttu-id="f85b6-127">Hodnota nastavená v projektu nebo v `runtimeconfig.json` souboru má přednost před proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="f85b6-127">A value set in the project or in the `runtimeconfig.json` file takes precedence over the environment variable.</span></span>

<span data-ttu-id="f85b6-128">Další informace najdete v tématu [nastavení konfigurace běhu](../../core/run-time-config/globalization.md#nls).</span><span class="sxs-lookup"><span data-stu-id="f85b6-128">For more information, see [Run-time config settings](../../core/run-time-config/globalization.md#nls).</span></span>

## <a name="app-local-icu"></a><span data-ttu-id="f85b6-129">ICU místní aplikace</span><span class="sxs-lookup"><span data-stu-id="f85b6-129">App-local ICU</span></span>

<span data-ttu-id="f85b6-130">Každé vydání ICU může přinést opravy chyb IT a také aktualizovaná data úložiště Common locale data (CLDR), která popisují jazyky světa.</span><span class="sxs-lookup"><span data-stu-id="f85b6-130">Each release of ICU may bring with it bug fixes as well as updated Common Locale Data Repository (CLDR) data that describes the world's languages.</span></span> <span data-ttu-id="f85b6-131">Přesun mezi verzemi ICU může mít slabší dopad na chování aplikace, když se dostane k operacím souvisejícím s globalizací.</span><span class="sxs-lookup"><span data-stu-id="f85b6-131">Moving between versions of ICU can subtly impact app behavior when it comes to globalization-related operations.</span></span>  <span data-ttu-id="f85b6-132">Aby mohli vývojáři aplikací zajistit konzistenci napříč všemi nasazeními, rozhraní .NET 5,0 a novější verze umožňují aplikacím v systémech Windows i UNIX přenášet a používat vlastní kopii ICU.</span><span class="sxs-lookup"><span data-stu-id="f85b6-132">To help application developers ensure consistency across all deployments, .NET 5.0 and later versions enable apps on both Windows and Unix to carry and use their own copy of ICU.</span></span>

<span data-ttu-id="f85b6-133">Aplikace se můžou do režimu implementace ICU v rámci aplikace přihlásit některým z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="f85b6-133">Applications can opt in to an app-local ICU implementation mode in any of the following ways:</span></span>

- <span data-ttu-id="f85b6-134">V souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="f85b6-134">In  the project file:</span></span>

```xml
<ItemGroup>
  <RuntimeHostConfigurationOption Include="System.Globalization.AppLocalIcu" Value="<suffix>:<version> or <version>" />
</ItemGroup>
```

- <span data-ttu-id="f85b6-135">V souboru `runtimeconfig.json`:</span><span class="sxs-lookup"><span data-stu-id="f85b6-135">In the `runtimeconfig.json` file:</span></span>

```json
{
  "runtimeOptions": {
     "configProperties": {
       "System.Globalization.AppLocalIcu": "<suffix>:<version> or <version>"
      }
  }
}
```

- <span data-ttu-id="f85b6-136">Nastavením proměnné prostředí `DOTNET_SYSTEM_GLOBALIZATION_APPLOCALICU` na hodnotu `<suffix>:<version>` nebo `<version>` .</span><span class="sxs-lookup"><span data-stu-id="f85b6-136">By setting the environment variable `DOTNET_SYSTEM_GLOBALIZATION_APPLOCALICU` to the value `<suffix>:<version>` or `<version>`.</span></span>

<span data-ttu-id="f85b6-137">`<suffix>`: V rámci veřejných ICUch konvencí pro vytváření balíčků je volitelná přípona o délce méně než 36 znaků.</span><span class="sxs-lookup"><span data-stu-id="f85b6-137">`<suffix>`: Optional suffix of less than 36 characters in length, following the public ICU packaging conventions.</span></span> <span data-ttu-id="f85b6-138">Při sestavování vlastního ICU ho můžete přizpůsobit, aby se vytvořily názvy lib a exportované symboly, které obsahují příponu, například `libicuucmyapp` , kde `myapp` je přípona.</span><span class="sxs-lookup"><span data-stu-id="f85b6-138">When building a custom ICU, you can customize it to produce the lib names and exported symbol names to contain a suffix, for example, `libicuucmyapp`, where `myapp` is the suffix.</span></span>

<span data-ttu-id="f85b6-139">`<version>`: Platná verze ICU, například 67,1.</span><span class="sxs-lookup"><span data-stu-id="f85b6-139">`<version>`: A valid ICU version, for example, 67.1.</span></span> <span data-ttu-id="f85b6-140">Tato verze se používá k načtení binárních souborů a k získání exportovaných symbolů.</span><span class="sxs-lookup"><span data-stu-id="f85b6-140">This version is used to load the binaries and to get the exported symbols.</span></span>

<span data-ttu-id="f85b6-141">Pokud chcete načíst ICU v případě, že je nastaven místní přepínač aplikace, .NET používá <xref:System.Runtime.InteropServices.NativeLibrary.TryLoad%2A?displayProperty=nameWithType> metodu, která sonduje více cest.</span><span class="sxs-lookup"><span data-stu-id="f85b6-141">To load ICU when the app-local switch is set, .NET uses the <xref:System.Runtime.InteropServices.NativeLibrary.TryLoad%2A?displayProperty=nameWithType> method, which probes multiple paths.</span></span> <span data-ttu-id="f85b6-142">Metoda se nejprve pokusí najít knihovnu ve `NATIVE_DLL_SEARCH_DIRECTORIES` vlastnosti, která je vytvořena hostitelem dotnet na základě `deps.json` souboru pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f85b6-142">The method first tries to find the library in the `NATIVE_DLL_SEARCH_DIRECTORIES` property, which is created by the dotnet host based on the `deps.json` file for the app.</span></span> <span data-ttu-id="f85b6-143">Další informace najdete v tématu [výchozí zjišťování](../../core/dependency-loading/default-probing.md).</span><span class="sxs-lookup"><span data-stu-id="f85b6-143">For more information, see [Default probing](../../core/dependency-loading/default-probing.md).</span></span>

<span data-ttu-id="f85b6-144">V případě aplikací, které jsou samostatně obsaženy, nevyžaduje uživatel žádnou zvláštní akci, kromě toho, že je ICU v adresáři aplikace (pro samoobslužné aplikace, ve výchozím nastavení se jedná o pracovní adresář `NATIVE_DLL_SEARCH_DIRECTORIES` ).</span><span class="sxs-lookup"><span data-stu-id="f85b6-144">For self-contained apps, no special action is required by the user, other than making sure ICU is in the app directory (for self-contained apps, the working directory defaults to `NATIVE_DLL_SEARCH_DIRECTORIES`).</span></span>

<span data-ttu-id="f85b6-145">Pokud pracujete ICU prostřednictvím balíčku NuGet, funguje to v aplikacích závislých na rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f85b6-145">If you're consuming ICU via a NuGet package, this works in framework-dependent applications.</span></span> <span data-ttu-id="f85b6-146">NuGet vyřeší nativní prostředky a zahrne je do `deps.json` souboru a do výstupního adresáře aplikace v `runtimes` adresáři.</span><span class="sxs-lookup"><span data-stu-id="f85b6-146">NuGet resolves the native assets and includes them in the `deps.json` file and in the output directory for the application under the `runtimes` directory.</span></span> <span data-ttu-id="f85b6-147">Rozhraní .NET ho načte odtud.</span><span class="sxs-lookup"><span data-stu-id="f85b6-147">.NET loads it from there.</span></span>

<span data-ttu-id="f85b6-148">U aplikací závislých na rozhraní (mimo sebe), kde je ICU spotřebované z místního sestavení, je nutné provést další kroky.</span><span class="sxs-lookup"><span data-stu-id="f85b6-148">For framework-dependent apps (not self contained) where ICU is consumed from a local build, you must take additional steps.</span></span> <span data-ttu-id="f85b6-149">Sada .NET SDK zatím neobsahuje funkci pro začlenění "volných" nativních binárních souborů, do kterých se mají zahrnout `deps.json` (podívejte se na [Tento problém sady SDK](https://github.com/dotnet/sdk/issues/11373)).</span><span class="sxs-lookup"><span data-stu-id="f85b6-149">The .NET SDK doesn't yet have a feature for "loose" native binaries to be incorporated into `deps.json` (see [this SDK issue](https://github.com/dotnet/sdk/issues/11373)).</span></span> <span data-ttu-id="f85b6-150">Místo toho jej můžete povolit přidáním dalších informací do souboru projektu aplikace.</span><span class="sxs-lookup"><span data-stu-id="f85b6-150">Instead, you can enable this by adding additional information into the application's project file.</span></span> <span data-ttu-id="f85b6-151">Například:</span><span class="sxs-lookup"><span data-stu-id="f85b6-151">For example:</span></span>

```xml
<ItemGroup>
  <IcuAssemblies Include="icu\*.so*" />
  <RuntimeTargetsCopyLocalItems Include="@(IcuAssemblies)" AssetType="native" CopyLocal="true" DestinationSubDirectory="runtimes/linux-x64/native/" DestinationSubPath="%(FileName)%(Extension)" RuntimeIdentifier="linux-x64" NuGetPackageId="System.Private.Runtime.UnicodeData" />
</ItemGroup>
```

<span data-ttu-id="f85b6-152">To je nutné provést pro všechny binární soubory ICU pro podporované moduly runtime.</span><span class="sxs-lookup"><span data-stu-id="f85b6-152">This must be done for all the ICU binaries for the supported runtimes.</span></span> <span data-ttu-id="f85b6-153">`NuGetPackageId`Metadata ve `RuntimeTargetsCopyLocalItems` skupině položek musí také odpovídat balíčku NuGet, který projekt ve skutečnosti odkazuje.</span><span class="sxs-lookup"><span data-stu-id="f85b6-153">Also, the `NuGetPackageId` metadata in the `RuntimeTargetsCopyLocalItems` item group needs to match a NuGet package that the project actually references.</span></span>

### <a name="macos-behavior"></a><span data-ttu-id="f85b6-154">chování macOS</span><span class="sxs-lookup"><span data-stu-id="f85b6-154">macOS behavior</span></span>

<span data-ttu-id="f85b6-155">`macOS`má jiné chování pro řešení závislých dynamických knihoven z příkazů load zadaných v souboru, `match-o` než je zavaděč Linux.</span><span class="sxs-lookup"><span data-stu-id="f85b6-155">`macOS` has a different behavior for resolving dependent dynamic libraries from the load commands specified in the `match-o` file than the Linux loader.</span></span> <span data-ttu-id="f85b6-156">V zavaděči Linux může .NET vyzkoušet `libicudata` , `libicuuc` a `libicui18n` (v tomto pořadí) pro splnění ICU grafu závislostí.</span><span class="sxs-lookup"><span data-stu-id="f85b6-156">In the Linux loader, .NET can try `libicudata`, `libicuuc`, and `libicui18n` (in that order) to satisfy ICU dependency graph.</span></span> <span data-ttu-id="f85b6-157">V macOS ale to nefunguje.</span><span class="sxs-lookup"><span data-stu-id="f85b6-157">However, on macOS, this doesn't work.</span></span> <span data-ttu-id="f85b6-158">Při sestavování ICU v macOS můžete ve výchozím nastavení získat dynamickou knihovnu pomocí těchto příkazů load v `libicuuc` .</span><span class="sxs-lookup"><span data-stu-id="f85b6-158">When building ICU on macOS, you, by default, get a dynamic library with these load commands in `libicuuc`.</span></span> <span data-ttu-id="f85b6-159">Například:</span><span class="sxs-lookup"><span data-stu-id="f85b6-159">For example.:</span></span>

```sh
~/ % otool -L /Users/santifdezm/repos/icu-build/icu/install/lib/libicuuc.67.1.dylib
/Users/santifdezm/repos/icu-build/icu/install/lib/libicuuc.67.1.dylib:
 libicuuc.67.dylib (compatibility version 67.0.0, current version 67.1.0)
 libicudata.67.dylib (compatibility version 67.0.0, current version 67.1.0)
 /usr/lib/libSystem.B.dylib (compatibility version 1.0.0, current version 1281.100.1)
 /usr/lib/libc++.1.dylib (compatibility version 1.0.0, current version 902.1.0)
```

<span data-ttu-id="f85b6-160">Tyto příkazy odkazují jenom na název závislých knihoven pro ostatní komponenty ICU.</span><span class="sxs-lookup"><span data-stu-id="f85b6-160">These commands just reference the name of the dependent libraries for the other components of ICU.</span></span> <span data-ttu-id="f85b6-161">Zavaděč provede hledání podle `dlopen` konvencí, které zahrnují tyto knihovny v systémových adresářích nebo nastavení `LD_LIBRARY_PATH` proměnných ENV nebo ICU v adresáři na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="f85b6-161">The loader performs the search following the `dlopen` conventions, which involves having these libraries in the system directories or setting the `LD_LIBRARY_PATH` env vars, or having ICU at the app-level directory.</span></span> <span data-ttu-id="f85b6-162">Pokud nemůžete nastavit `LD_LIBRARY_PATH` nebo zajistit, aby byly binární soubory ICU v adresáři na úrovni aplikace, budete muset udělat další práci.</span><span class="sxs-lookup"><span data-stu-id="f85b6-162">If you can't set `LD_LIBRARY_PATH` or ensure that ICU binaries are at the app-level directory, you will need to do some extra work.</span></span>

<span data-ttu-id="f85b6-163">Existují některé direktivy pro zavaděč, jako `@loader_path` je například, který říká zavaděči, aby vyhledal tuto závislost ve stejném adresáři jako binární soubor s tímto příkazem Load.</span><span class="sxs-lookup"><span data-stu-id="f85b6-163">There are some directives for the loader, like `@loader_path`, which tell the loader to search for that dependency in the same directory as the binary with that load command.</span></span> <span data-ttu-id="f85b6-164">Toho můžete dosáhnout dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="f85b6-164">There are two ways to achieve this:</span></span>

- `install_name_tool -change`

  <span data-ttu-id="f85b6-165">Spusťte následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="f85b6-165">Run the following commands:</span></span>

```bash
install_name_tool -change "libicudata.67.dylib" "@loader_path/libicudata.67.dylib" /path/to/libicuuc.67.1.dylib
install_name_tool -change "libicudata.67.dylib" "@loader_path/libicudata.67.dylib" /path/to/libicui18n.67.1.dylib
install_name_tool -change "libicuuc.67.dylib" "@loader_path/libicuuc.67.dylib" /path/to/libicui18n.67.1.dylib
```

- <span data-ttu-id="f85b6-166">Opravte ICU, aby se vytvořily názvy pro instalaci.`@loader_path`</span><span class="sxs-lookup"><span data-stu-id="f85b6-166">Patch ICU to produce the install names with `@loader_path`</span></span>

  <span data-ttu-id="f85b6-167">Před spuštěním AUTOCONF ( `./runConfigureICU` ) změňte [tyto řádky](https://github.com/unicode-org/icu/blob/ef91cc3673d69a5e00407cda94f39fcda3131451/icu4c/source/config/mh-darwin#L32-L37) na:</span><span class="sxs-lookup"><span data-stu-id="f85b6-167">Before running autoconf (`./runConfigureICU`), change [these lines](https://github.com/unicode-org/icu/blob/ef91cc3673d69a5e00407cda94f39fcda3131451/icu4c/source/config/mh-darwin#L32-L37) to:</span></span>

```
LD_SONAME = -Wl,-compatibility_version -Wl,$(SO_TARGET_VERSION_MAJOR) -Wl,-current_version -Wl,$(SO_TARGET_VERSION) -install_name @loader_path/$(notdir $(MIDDLE_SO_TARGET))
```
