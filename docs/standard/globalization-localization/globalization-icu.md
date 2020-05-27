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
# <a name="net-globalization-and-icu"></a>Rozhraní .NET globalizace a ICU

Rozhraní API globalizace .NET v minulosti používaly různé základní knihovny na různých platformách. V systému UNIX rozhraní API používala [mezinárodní komponenty pro Unicode (ICU)](http://site.icu-project.org/home)a ve Windows používaly [národní podporu národního oddělení (NLS)](/windows/win32/intl/national-language-support). To vedlo k nějakým rozdílům v chování v několik rozhraní API globalizace při spouštění aplikací na různých platformách. Rozdíly v chování byly patrné z těchto oblastí:

- Jazykové verze a data jazykové verze
- Velikost řetězce
- Řazení a hledání řetězců
- Klíče řazení
- Normalizace řetězců
- Podpora mezinárodních názvů domén (IDN)
- Zobrazované jméno časového pásma na platformě Linux

Od .NET 5,0 mají vývojáři větší kontrolu nad tím, která základní knihovna se používá, a umožňuje aplikacím vyhnout se rozdílům na různých platformách.

## <a name="icu-on-windows"></a>ICU ve Windows

Windows 10 Květen 2019 Update a novější verze obsahují [ICU. dll](/windows/win32/intl/international-components-for-unicode--icu-) jako součást operačního systému a .NET 5,0 a novější verze standardně používají ICU. Při spuštění v systému Windows se .NET 5,0 a novější verze pokusí načíst `icu.dll` , a pokud jsou k dispozici, používá je pro implementaci globalizace.  Pokud tuto knihovnu nemůžete najít nebo načíst, například při spuštění ve starších verzích Windows, .NET 5,0 a novější verze se vrátí k implementaci založené na NLS.

> [!NOTE]
> I při použití ICU, `CurrentCulture` , `CurrentUICulture` a používají i `CurrentRegion` Členové rozhraní API operačního systému Windows k respektování uživatelských nastavení.

### <a name="using-nls-instead-of-icu"></a>Použití NLS místo ICU

Použití ICU místo NLS může mít za následek rozdíly v chování s některými operacemi souvisejícími s globalizací. Pokud se chcete vrátit zpět k používání NLS, vývojář může odhlásit ICU implementaci. Aplikace mohou povolit režim NLS některým z následujících způsobů:

- V souboru projektu:

```xml
<ItemGroup>
  <RuntimeHostConfigurationOption Include="System.Globalization.UseNls" Value="true" />
</ItemGroup>
```

- V souboru `runtimeconfig.json`:

```json
{
  "runtimeOptions": {
     "configProperties": {
       "System.Globalization.UseNls": true
      }
  }
}
```

- Nastavením proměnné prostředí `DOTNET_SYSTEM_GLOBALIZATION_USENLS` na hodnotu `true` nebo `1` .

> [!NOTE]
> Hodnota nastavená v projektu nebo v `runtimeconfig.json` souboru má přednost před proměnnou prostředí.

Další informace najdete v tématu [nastavení konfigurace běhu](../../core/run-time-config/globalization.md#nls).

## <a name="app-local-icu"></a>ICU místní aplikace

Každé vydání ICU může přinést opravy chyb IT a také aktualizovaná data úložiště Common locale data (CLDR), která popisují jazyky světa. Přesun mezi verzemi ICU může mít slabší dopad na chování aplikace, když se dostane k operacím souvisejícím s globalizací.  Aby mohli vývojáři aplikací zajistit konzistenci napříč všemi nasazeními, rozhraní .NET 5,0 a novější verze umožňují aplikacím v systémech Windows i UNIX přenášet a používat vlastní kopii ICU.

Aplikace se můžou do režimu implementace ICU v rámci aplikace přihlásit některým z následujících způsobů:

- V souboru projektu:

```xml
<ItemGroup>
  <RuntimeHostConfigurationOption Include="System.Globalization.AppLocalIcu" Value="<suffix>:<version> or <version>" />
</ItemGroup>
```

- V souboru `runtimeconfig.json`:

```json
{
  "runtimeOptions": {
     "configProperties": {
       "System.Globalization.AppLocalIcu": "<suffix>:<version> or <version>"
      }
  }
}
```

- Nastavením proměnné prostředí `DOTNET_SYSTEM_GLOBALIZATION_APPLOCALICU` na hodnotu `<suffix>:<version>` nebo `<version>` .

`<suffix>`: V rámci veřejných ICUch konvencí pro vytváření balíčků je volitelná přípona o délce méně než 36 znaků. Při sestavování vlastního ICU ho můžete přizpůsobit, aby se vytvořily názvy lib a exportované symboly, které obsahují příponu, například `libicuucmyapp` , kde `myapp` je přípona.

`<version>`: Platná verze ICU, například 67,1. Tato verze se používá k načtení binárních souborů a k získání exportovaných symbolů.

Pokud chcete načíst ICU v případě, že je nastaven místní přepínač aplikace, .NET používá <xref:System.Runtime.InteropServices.NativeLibrary.TryLoad%2A?displayProperty=nameWithType> metodu, která sonduje více cest. Metoda se nejprve pokusí najít knihovnu ve `NATIVE_DLL_SEARCH_DIRECTORIES` vlastnosti, která je vytvořena hostitelem dotnet na základě `deps.json` souboru pro aplikaci. Další informace najdete v tématu [výchozí zjišťování](../../core/dependency-loading/default-probing.md).

V případě aplikací, které jsou samostatně obsaženy, nevyžaduje uživatel žádnou zvláštní akci, kromě toho, že je ICU v adresáři aplikace (pro samoobslužné aplikace, ve výchozím nastavení se jedná o pracovní adresář `NATIVE_DLL_SEARCH_DIRECTORIES` ).

Pokud pracujete ICU prostřednictvím balíčku NuGet, funguje to v aplikacích závislých na rozhraní. NuGet vyřeší nativní prostředky a zahrne je do `deps.json` souboru a do výstupního adresáře aplikace v `runtimes` adresáři. Rozhraní .NET ho načte odtud.

U aplikací závislých na rozhraní (mimo sebe), kde je ICU spotřebované z místního sestavení, je nutné provést další kroky. Sada .NET SDK zatím neobsahuje funkci pro začlenění "volných" nativních binárních souborů, do kterých se mají zahrnout `deps.json` (podívejte se na [Tento problém sady SDK](https://github.com/dotnet/sdk/issues/11373)). Místo toho jej můžete povolit přidáním dalších informací do souboru projektu aplikace. Například:

```xml
<ItemGroup>
  <IcuAssemblies Include="icu\*.so*" />
  <RuntimeTargetsCopyLocalItems Include="@(IcuAssemblies)" AssetType="native" CopyLocal="true" DestinationSubDirectory="runtimes/linux-x64/native/" DestinationSubPath="%(FileName)%(Extension)" RuntimeIdentifier="linux-x64" NuGetPackageId="System.Private.Runtime.UnicodeData" />
</ItemGroup>
```

To je nutné provést pro všechny binární soubory ICU pro podporované moduly runtime. `NuGetPackageId`Metadata ve `RuntimeTargetsCopyLocalItems` skupině položek musí také odpovídat balíčku NuGet, který projekt ve skutečnosti odkazuje.

### <a name="macos-behavior"></a>chování macOS

`macOS`má jiné chování pro řešení závislých dynamických knihoven z příkazů load zadaných v souboru, `match-o` než je zavaděč Linux. V zavaděči Linux může .NET vyzkoušet `libicudata` , `libicuuc` a `libicui18n` (v tomto pořadí) pro splnění ICU grafu závislostí. V macOS ale to nefunguje. Při sestavování ICU v macOS můžete ve výchozím nastavení získat dynamickou knihovnu pomocí těchto příkazů load v `libicuuc` . Například:

```sh
~/ % otool -L /Users/santifdezm/repos/icu-build/icu/install/lib/libicuuc.67.1.dylib
/Users/santifdezm/repos/icu-build/icu/install/lib/libicuuc.67.1.dylib:
 libicuuc.67.dylib (compatibility version 67.0.0, current version 67.1.0)
 libicudata.67.dylib (compatibility version 67.0.0, current version 67.1.0)
 /usr/lib/libSystem.B.dylib (compatibility version 1.0.0, current version 1281.100.1)
 /usr/lib/libc++.1.dylib (compatibility version 1.0.0, current version 902.1.0)
```

Tyto příkazy odkazují jenom na název závislých knihoven pro ostatní komponenty ICU. Zavaděč provede hledání podle `dlopen` konvencí, které zahrnují tyto knihovny v systémových adresářích nebo nastavení `LD_LIBRARY_PATH` proměnných ENV nebo ICU v adresáři na úrovni aplikace. Pokud nemůžete nastavit `LD_LIBRARY_PATH` nebo zajistit, aby byly binární soubory ICU v adresáři na úrovni aplikace, budete muset udělat další práci.

Existují některé direktivy pro zavaděč, jako `@loader_path` je například, který říká zavaděči, aby vyhledal tuto závislost ve stejném adresáři jako binární soubor s tímto příkazem Load. Toho můžete dosáhnout dvěma způsoby:

- `install_name_tool -change`

  Spusťte následující příkazy:

```bash
install_name_tool -change "libicudata.67.dylib" "@loader_path/libicudata.67.dylib" /path/to/libicuuc.67.1.dylib
install_name_tool -change "libicudata.67.dylib" "@loader_path/libicudata.67.dylib" /path/to/libicui18n.67.1.dylib
install_name_tool -change "libicuuc.67.dylib" "@loader_path/libicuuc.67.dylib" /path/to/libicui18n.67.1.dylib
```

- Opravte ICU, aby se vytvořily názvy pro instalaci.`@loader_path`

  Před spuštěním AUTOCONF ( `./runConfigureICU` ) změňte [tyto řádky](https://github.com/unicode-org/icu/blob/ef91cc3673d69a5e00407cda94f39fcda3131451/icu4c/source/config/mh-darwin#L32-L37) na:

```
LD_SONAME = -Wl,-compatibility_version -Wl,$(SO_TARGET_VERSION_MAJOR) -Wl,-current_version -Wl,$(SO_TARGET_VERSION) -install_name @loader_path/$(notdir $(MIDDLE_SO_TARGET))
```
