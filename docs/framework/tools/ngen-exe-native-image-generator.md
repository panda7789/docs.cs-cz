---
title: Ngen.exe (generátor nativních obrázků)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Native Image Generator
- images [.NET Framework], native
- side-by-side execution, native images
- assemblies [.NET Framework], native image
- Ngen.exe
- native image generation
- native image cache
- publisher policy applied for native images
- invalid images
- BypassNGenAttribute
- System.Runtime.BypassNGenAttribute
ms.assetid: 44bf97aa-a9a4-4eba-9a0d-cfaa6fc53a66
ms.openlocfilehash: 297bc3f9182e76523eda4d4be3112f4d1d7e3fee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75741788"
---
# <a name="ngenexe-native-image-generator"></a>Ngen.exe (generátor nativních obrázků)

Generátor nativních bitových kopií (Ngen.exe) je nástroj zvyšující výkon spravovaných aplikací. Nástroj Ngen.exe vytváří nativní bitové kopie, což jsou soubory obsahující zkompilovaný strojový kód specifický pro procesor, a instaluje je do mezipaměti nativních bitových kopií v místním počítači. Modul runtime může ke kompilaci původního sestavení použít nativní bitové kopie z mezipaměti namísto kompilátoru JIT (just-in-time).

> [!NOTE]
> Ngen.exe zkompiluje nativní bitové kopie pro sestavení, která cílí pouze na rozhraní .NET Framework. Ekvivalentní generátor nativního obrazu pro .NET Core je [CrossGen](https://github.com/dotnet/runtime/blob/master/docs/workflow/building/coreclr/crossgen.md).

Změny programu Ngen.exe v rozhraní .NET Framework 4:

- Nástroj Ngen.exe nyní kompiluje sestavení s úplnou důvěryhodností, přičemž zabezpečení přístupu kódu (CAS) již není vyhodnocováno.

- Nativní bitové kopie generované nástrojem Ngen.exe již nemohou být načteny do aplikací spuštěných s částečnou důvěryhodností.

Změny nástroje Ngen.exe v rozhraní .NET Framework verze 2.0:

- Instalace sestavení nainstaluje také jeho závislosti, což zjednodušuje syntaxi nástroje Ngen.exe.

- Nativní bitové kopie mohou být nyní sdíleny napříč doménami aplikací.

- Nová akce `update`, znovu vytvoří obrazy, které byly zrušeny.

- Pro generování a instalaci bitových kopií může být spuštění akcí odloženo službou využívající dobu nečinnosti.

- Některé příčiny zneplatnění bitové kopie byly odstraněny.

Ve Windows 8 najdete v [tématu Nativní úloha bitové kopie](#native-image-task).

Další informace o použití souboru Ngen.exe a nativní služby bitové kopie naleznete v [tématu Native Image Service](#native-image-service).

> [!NOTE]
> Syntaxi ngen.exe pro verze 1.0 a 1.1 rozhraní .NET Framework naleznete v [části Nativní generátor obrázků (Ngen.exe) Starší syntaxe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms165073(v=vs.100)).

Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li nástroj spustit, použijte příkazový řádek pro vývojáře pro sadu Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace naleznete v [příkazových koncích](developer-command-prompt-for-vs.md).

V příkazovém řádku zadejte následující:

## <a name="syntax"></a>Syntaxe

```console
ngen action [options]
```

```console
ngen /? | /help
```

## <a name="actions"></a>Akce

V následující tabulce je `action`uvedena syntaxe každého z nich . Popis jednotlivých `action`částí tabulky , [argumenty](#ArgumentTable), úrovně [priority](#PriorityTable), [scénáře](#ScenarioTable)a [konfigurace.](#ConfigTable) Tabulka [Možnosti](#OptionTable) popisuje `options` přepínače nápovědy a.

|Akce|Popis|
|------------|-----------------|
|`install`[`assemblyName` `assemblyPath`&#124; [`scenarios`]`config`[`/queue``:`[`1` `2` { `3`&#124;&#124;}]]|Vygeneruje nativní bitové kopie sestavení a jeho závislosti a nainstaluje bitové kopie do mezipaměti nativních bitových kopií.<br /><br /> Pokud `/queue` je zadán, akce je zařazena do fronty pro nativní image služby. Výchozí hodnota priority je 3. Viz tabulka [Úrovně priority.](#PriorityTable)|
|`uninstall`[`assemblyName` `assemblyPath`&#124; [`scenarios`] [`config`]|Odstraní nativní bitové kopie sestavení a jeho závislosti z mezipaměti nativních bitových kopií.<br /><br /> Chcete-li odinstalovat pouze jednu bitovou kopii a její závislosti, použijte stejné argumenty příkazového řádku, které byly použity při instalaci kopie. **Poznámka:**  Počínaje rozhraním .NET Framework `uninstall` 4 již není akce * podporována.|
|`update` [`/queue`]|Aktualizuje nativní bitové kopie, které se staly neplatnými.<br /><br /> Pokud `/queue` je zadán, aktualizace jsou zařazeny do fronty pro nativní image služby. Aktualizace jsou vždy naplánovány s prioritou 3, jsou tedy spouštěny při nečinnosti počítače.|
|`display`[`assemblyName` `assemblyPath`&#124;|Zobrazí stav nativních bitových kopií pro sestavení a jeho závislosti.<br /><br /> Není-li zadán žádný argument, je zobrazen celý obsah mezipaměti nativních bitových kopií.|
|`executeQueuedItems` [<code>1&#124;2&#124;3</code>]<br /><br /> -nebo-<br /><br /> `eqi`[1&#124;2&#124;3]|Spustí úlohy kompilace ve frontě.<br /><br /> Je-li zadána priorita, jsou spuštěny úlohy kompilace s větší nebo shodnou prioritou. Není-li priorita zadána, jsou spuštěny všechny úlohy kompilace.|
|`queue`{`pause` `continue` &#124; `status`&#124; }|Pozastaví službu nativních bitových kopií, umožní pozastavené službě pokračovat nebo se dotáže na stav služby.|

<a name="ArgumentTable"></a>

## <a name="arguments"></a>Argumenty

|Argument|Popis|
|--------------|-----------------|
|`assemblyName`|Plný zobrazovaný název sestavení. Například, `"myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5"`. **Poznámka:**  Můžete zadat částečný název sestavy, `myAssembly`například `display` `uninstall` , pro akce a. <br /><br /> V jednom příkazovém řádku nástroje Ngen.exe lze zadat pouze jedno sestavení.|
|`assemblyPath`|Explicitní cesta k sestavení. Lze zadat úplnou nebo relativní cestu.<br /><br /> Zadáte-li název souboru bez cesty, musí se sestavení nacházet v aktuálním adresáři.<br /><br /> V jednom příkazovém řádku nástroje Ngen.exe lze zadat pouze jedno sestavení.|

<a name="PriorityTable"></a>

## <a name="priority-levels"></a>Úrovně priority

|Priorita|Popis|
|--------------|-----------------|
|`1`|Nativní bitové kopie jsou generovány a nainstalovány okamžitě, nečeká se na nečinnost počítače.|
|`2`|Nativní bitové kopie jsou generovány a instalovány bez čekání na nečinnost počítače, ale až po dokončení všech akcí s prioritou 1 (a jejich závislostí).|
|`3`|Nativní bitové kopie jsou nainstalovány ve chvíli, kdy služba nativních bitových kopií zjistí, že je počítač nečinný. Viz [Nativní služba image .](#native-image-service)|

<a name="ScenarioTable"></a>

## <a name="scenarios"></a>Scénáře

|Scénář|Popis|
|--------------|-----------------|
|`/Debug`|Vygeneruje nativní bitové kopie, které lze použít v ladicím programu.|
|`/Profile`|Vygeneruje nativní bitové kopie, které lze použít v profileru.|
|`/NoDependencies`|Vygeneruje minimální počet nativních bitových kopií požadovaný zadanými možnostmi scénáře.|

<a name="ConfigTable"></a>

## <a name="config"></a>Config

|Konfigurace|Popis|
|-------------------|-----------------|
|`/ExeConfig:` `exePath`|Použije konfiguraci zadaného spustitelného sestavení.<br /><br /> Při vytváření vazeb na závislosti musí nástroj Ngen.exe učinit stejná rozhodnutí jako zavaděč. Při načtení sdílené součásti za <xref:System.Reflection.Assembly.Load%2A> běhu pomocí metody určuje konfigurační soubor aplikace závislosti, které jsou načteny pro sdílenou komponentu, například verzi načtení závislosti. Přepínač `/ExeConfig` poskytuje Ngen.exe pokyny, na které závislosti by být načteny v době běhu.|
|`/AppBase:` `directoryPath`|Při hledání závislostí aplikace použije jako základ cesty zadaný adresář.|

<a name="OptionTable"></a>

## <a name="options"></a>Možnosti

|Možnost|Popis|
|------------|-----------------|
|`/nologo`|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|
|`/silent`|Potlačí zobrazování zpráv o úspěchu.|
|`/verbose`|Zobrazí podrobné informace o ladění. **Poznámka:**  Z důvodu omezení operačního systému tato možnost nezobrazuje tolik dalších informací v systémech Windows 98 a Windows Millennium Edition.|
|`/help`, `/?`|Zobrazí syntaxi příkazu a možnosti aktuální verze.|

## <a name="remarks"></a>Poznámky

Chcete-li spustit nástroj Ngen.exe, je zapotřebí mít oprávnění správce.

> [!CAUTION]
> Nástroj Ngen.exe nespouštějte pro sestavení, která nemají plnou důvěryhodnost. Počínaje rozhraním .NET Framework 4 ngen.exe zkompiluje sestavení s úplným vztahem důvěryhodnosti a zásada zabezpečení přístupu kódu (CAS) již není vyhodnocována.

Počínaje rozhraním .NET Framework 4 již nelze nativní bitové kopie, které jsou generovány pomocí programu Ngen.exe, načíst do aplikací, které jsou spuštěny v částečném vztahu důvěryhodnosti. Namísto toho je vyvolán kompilátor za běhu (JIT).

Ngen.exe generuje nativní bitové kopie `assemblyname` pro `install` sestavení určené argumentem akce a všechny jeho závislosti. Závislosti se stanoví z odkazů v manifestu sestavení. Jediný scénář, ve kterém je třeba nainstalovat závislost samostatně je při aplikace načte <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> pomocí reflexe, například voláním metody.

> [!IMPORTANT]
> Nepoužívejte metodu s nativními <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> obrázky. Bitovou kopii zavedenou touto metodou nelze v kontextu spuštění používat jinými sestaveními.

Nástroj Ngen.exe udržuje počet odkazů na závislosti. Předpokládejme například, `MyAssembly.exe` `YourAssembly.exe` a jsou nainstalovány v mezipaměti nativní bitové kopie a oba mají odkazy na `OurDependency.dll`. Pokud `MyAssembly.exe` je odinstalován, `OurDependency.dll` není odinstalován. Je odebrán pouze `YourAssembly.exe` při odinstalaci.

Pokud generujete nativní bitovou kopii pro sestavení v globální mezipaměti sestavení (GAC), zadejte její zobrazovaný název. Viz třída <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>.

Nativní bitové kopie, které generuje Ngen.exe, mohou být sdíleny napříč doménami aplikace. To znamená, že nástroj Ngen.exe lze použít ve scénářích aplikací, které vyžadují, aby byla sestavení sdílena napříč doménami aplikace. Určení neutrality domény:

- Použijte <xref:System.LoaderOptimizationAttribute> atribut pro vaši aplikaci.

- Nastavte <xref:System.AppDomainSetup.LoaderOptimization%2A?displayProperty=nameWithType> vlastnost při vytváření informací o instalaci pro novou doménu aplikace.

Vždy je třeba použít doménově neutrální kód, pokud je dané sestavení načítáno do více domén aplikace. Pokud je nativní bitová kopie načtena do nesdílené domény aplikace poté, co byla načtena do sdílené domény, nelze ji použít.

> [!NOTE]
> Doménově neutrální kód nemůže být uvolněn a výkon může být mírně snížen, zvláště při přistupování ke statickým členům.

V této sekci Poznámky:

- [Generování bitových kopií pro různé scénáře](#Scenarios)

- [Určení, kdy použít nativní obrázky](#WhenToUse)

  - [Lepší využití paměti](#Memory)

  - [Rychlejší spuštění aplikace](#Startup)

  - [Shrnutí aspektů použití](#UsageSummary)

- [Důležitost adres základny sestavení](#BaseAddresses)

- [Tvrdá vazba](#HardBinding)

  - [Určení nápovědy vazby pro závislost](#DependencyHint)

  - [Určení výchozí nápovědy vazby pro sestavení](#AssemblyHint)

- [Odložené zpracování](#Deferred)

- [Nativní obrázky a kompilace JIT](#JITCompilation)

  - [Neplatné obrázky](#InvalidImages)

- [Řešení potíží](#Troubleshooting)

  - [vazba sestavení – prohlížeč protokolu](#Fusion)

  - [Asistent ladění spravovaných JITCompilationStart](#MDA)

  - [Odhlášení z nativní generace obrázků](#OptOut)

<a name="Scenarios"></a>

## <a name="generating-images-for-----different-scenarios"></a>Generování bitových kopií pro různé scénáře

Po vygenerování nativní bitové kopie pro sestavení se čas runtime automaticky pokusí vyhledat a použít tento nativní bitovou kopii při každém spuštění sestavení. V závislosti na scénáři lze generovat více bitových kopií.

Například pokud spustíte sestavení ve scénáři ladění nebo profilování, runtime hledá nativní bitovou `/Debug` `/Profile` kopii, která byla generována s možnostmi nebo. Pokud nemůže najít odpovídající nativní bitovou kopii, vrátí se modul runtime ke standardní JIT kompilaci. Jediný způsob, jak ladit nativní obrazy, je `/Debug` vytvořit nativní obraz s volbou.

Akce `uninstall` také rozpoznat scénáře, takže můžete odinstalovat všechny scénáře nebo pouze vybrané scénáře.

<a name="WhenToUse"></a>

## <a name="determining-when-to-use-native-images"></a>Určení, kdy použít nativní obrázky

Nativní bitové kopie mohou poskytnout zvýšení výkonu ve dvou oblastech: lepší využití paměti a rychlejší spouštění.

> [!NOTE]
> Výkon nativních bitových kopií závisí na několika faktorech, které analýzu výkonu znesnadňují, například přístupové vzory kódu a dat, počet volání napříč hranicemi modulu či počet závislostí již načtených jinými aplikacemi. Jediným způsobem, jak určit, zda nativní bitové kopie prospívají aplikaci, je pečlivé měření výkonu v klíčových scénářích nasazení.

<a name="Memory"></a>

### <a name="improved-memory-use"></a>Lepší využití paměti

Nativní bitové kopie mohou významně zlepšit využití paměti, je-li kód sdílen mezi procesy. Nativní bitové kopie jsou soubory Windows PE, tudíž jedna kopie souboru .dll může být sdílena několika procesy. Naproti tomu nativní kód vytvořený kompilátorem JIT je uložen v soukromé paměti a nelze jej sdílet.

Aplikace spuštěné v rámci terminálových služeb také využívají výhod sdílených znakových stránek.

Kromě toho skutečnost, že není načítán kompilátor JIT, ušetří pevně dané množství paměti pro každou instanci aplikace.

<a name="Startup"></a>

### <a name="faster-application-startup"></a>Rychlejší spuštění aplikace

Předkompilování sestavení programem Ngen.exe může zvýšit rychlost spuštění některých aplikací. Obecně lze zvýšení výkonu dosáhnout tam, kde aplikace sdílejí sestavení komponent, protože po prvním spuštění aplikace jsou komponenty sdílené s jinými aplikacemi již načteny. Úplné spuštění, při němž musí být všechna sestavení aplikace načtena z pevného disku, nevyužívají výhod nativních bitových kopií v takové míře, protože má převahu přístupová doba pevného disku.

Pevné vazby mohou ovlivnit rychlost spuštění, protože všechny bitové kopie pevně svázané s hlavním sestavením aplikace musí být načteny najednou.

> [!NOTE]
> Před rozhraní .NET Framework 3.5 Service Pack 1 byste měli do globální mezipaměti sestavení umístit sdílené součásti se silným názvem, protože zavaděč provádí další ověření u sestavení se silným názvem, která nejsou v globální mezipaměti sestavení, což účinně eliminuje jakékoli zlepšení doby spuštění získané pomocí nativních obrázků. Optimalizace, které byly zavedeny v rozhraní .NET Framework 3.5 SP1 odebrány další ověření.

<a name="UsageSummary"></a>

### <a name="summary-of-usage-considerations"></a>Shrnutí aspektů použití

Následující obecné a aplikační informace vám mohou pomoci rozhodnout, zda může být vyhodnocení nativních bitových kopií pro aplikaci přínosem:

- Nativní bitové kopie se načítají rychleji než jazyk MSIL, protože odstraňují potřebu mnoha aktivit při spouštění, například kompilaci JIT a ověření bezpečnosti typů.

- Nativní bitové kopie vyžadují menší počáteční pracovní sadu, protože není zapotřebí použít kompilátor JIT.

- Nativní bitové kopie umožňují sdílení kódu mezi procesy.

- Nativní bitové kopie vyžadují více místa na disku než sestavení MSIL a jejich generování může trvat značně dlouho.

- Nativní bitové kopie musí být udržovány.

  - Je-li upraveno původní sestavení nebo jedna z jeho závislostí, je zapotřebí bitové kopie znovu vygenerovat.

  - Jediné sestavení může vyžadovat několik nativních bitových kopií pro použití v různých aplikacích a scénářích. Například informace o konfiguraci dvou aplikací může vyústit v různá rozhodnutí o vazbách stejného závislého sestavení.

  - Nativní bitové kopie musí být generovány správcem; tj. z účtu systému Windows ve skupině Administrators.

Spolu s těmito obecnými informacemi je zapotřebí při určování, zda mohou nativní bitové kopie poskytnout zvýšení výkonu, zvážit i povahu aplikace:

- Je-li aplikace spouštěna v prostředí, které využívá mnoho sdílených komponent, nativní bitové kopie umožňují sdílení komponent mezi mnoha procesy.

- Používá-li aplikace více domén aplikace, nativní bitové kopie umožňují sdílení znakových stránek mezi doménami.

    > [!NOTE]
    > V rozhraních .NET Framework verze 1.0 a 1.1 nemohou být nativní bitové kopie sdíleny napříč doménami aplikace. Verze 2.0 a novější již toto omezení nemají.

- Bude-li aplikace spuštěna v rámci Terminálového serveru, nativní bitové kopie umožní sdílení znakových stránek.

- Rozsáhlé aplikace obecně těží z výhod kompilace do nativních bitových kopií. Malým aplikacím nativní bitové kopie obvykle výhody nepřinášejí.

- Pro dlouho běžící aplikace vykazuje kompilace JIT za běhu mírně vyšší výkon než nativní bitové kopie. (Pevné vazby mohou tento rozdíl ve výkonu do určité míry zmenšit.)

<a name="BaseAddresses"></a>

## <a name="importance-of-assembly-base-addresses"></a>Důležitost adres základny sestavení

Jelikož nativní bitové kopie jsou soubory Windows PE, týkají se jich stejné problémy související se změnou základní cesty jako u ostatních spustitelných souborů. Snížení výkonu vinou přemístění je ještě větší, jsou-li použity pevné vazby.

Chcete-li nastavit základní adresu pro nativní bitovou kopii, použijte příslušnou možnost kompilátoru pro nastavení základní adresy sestavení. Tuto základní adresu používá nástroj Ngen.exe pro nativní bitové kopie.

> [!NOTE]
> Nativní bitové kopie jsou větší než spravovaná sestavení, z nichž byly vytvořeny. Základní adresy musí být vypočteny tak, aby tyto větší velikosti umožňovaly.

Chcete-li zobrazit preferovanou základní adresu nativní bitové kopie, můžete použít například nástroj dumpbin.exe.

<a name="HardBinding"></a>

## <a name="hard-binding"></a>Tvrdá vazba

Pevné vazby zvyšují propustnost a snižují velikost pracovní sady pro nativní bitové kopie. Nevýhodou pevné vazby je, že všechny bitové kopie, které jsou pevně vázány na sestavení, musí být načteny při načtení sestavení. To u velkých aplikací může výrazně prodloužit spouštění.

Pevná vazba je vhodná pro závislosti, které jsou načteny ve všech scénářích aplikace, u kterých velmi záleží na výkonu. Stejně jako u jakéhokoli jiného aspektu použití nativní bitové kopie je měření výkonu jediným způsobem, jak určit, zda pevná vazba zlepšuje výkon vaší aplikace.

<xref:System.Runtime.CompilerServices.DependencyAttribute> Atributy <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> a umožňují poskytnout rady pro tvrdou vazbu pro ngen.exe.

> [!NOTE]
> Tyto atributy jsou informace pro Ngen.exe, nikoli příkazy. Jejich použití nezaručuje pevné vazby. V budoucích verzích se může změnit význam těchto atributů.

<a name="DependencyHint"></a>

### <a name="specifying-a-binding-hint-for-a-dependency"></a>Určení nápovědy vazby pro závislost

Použijte <xref:System.Runtime.CompilerServices.DependencyAttribute> sestavení k označení pravděpodobnosti, že zadaná závislost bude načtena. <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType>označuje, že pevné <xref:System.Runtime.CompilerServices.LoadHint.Default> vazby je vhodné, označuje, že <xref:System.Runtime.CompilerServices.LoadHint.Sometimes> výchozí pro závislost by měla být použita a označuje, že pevné vazby není vhodné.

Následující kód zobrazuje atributy pro sestavení, které má dvě závislosti. První závislost (Assembly1) je vhodným kandidátem pro pevnou vazbu, druhá závislost (Assembly2) nikoliv.

```vb
Imports System.Runtime.CompilerServices
<Assembly:DependencyAttribute("Assembly1", LoadHint.Always)>
<Assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)>
```

```csharp
using System.Runtime.CompilerServices;
[assembly:DependencyAttribute("Assembly1", LoadHint.Always)]
[assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)]
```

```cpp
using namespace System::Runtime::CompilerServices;
[assembly:DependencyAttribute("Assembly1", LoadHint.Always)];
[assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)];
```

Název sestavení neobsahuje příponu názvu souboru. Lze použít zobrazené názvy.

<a name="AssemblyHint"></a>

### <a name="specifying-a-default-binding-hint-for-an-assembly"></a>Určení výchozí nápovědy vazby pro sestavení

Výchozí pokyny pro vazby jsou zapotřebí pouze pro sestavení, která budou použita okamžitě a často aplikací, která na nich závisí. Použijte <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> s <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> na takové sestavy určit, že pevné vazby by měly být použity.

> [!NOTE]
> Neexistuje žádný důvod <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> použít na sestavení .dll, které nespadají do této kategorie, protože <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> použití atributu s jinou hodnotou než má stejný účinek jako nepoužití atributu vůbec.

Společnost Microsoft <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> používá k určení, že pevné vazby je výchozí pro velmi malý počet sestavení v rozhraní .NET Framework, jako je například mscorlib.dll.

<a name="Deferred"></a>

## <a name="deferred-processing"></a>Odložené zpracování

Generování nativních bitových kopií pro velmi velké aplikace může být časově náročné. Obdobně změny sdílené komponenty nebo změny nastavení počítače mohou vyžadovat aktualizaci mnoha nativních bitových kopií. Akce `install` `update` a mají `/queue` možnost, která zařadí operaci do fronty pro odložené spuštění službou nativní bitové kopie. Kromě toho Ngen.exe `queue` `executeQueuedItems` má a akce, které poskytují určitou kontrolu nad službou. Další informace naleznete [v tématu Native Image Service](#native-image-service).

<a name="JITCompilation"></a>

## <a name="native-images-and-jit-compilation"></a>Nativní obrázky a kompilace JIT

Pokud Ngen.exe v sestavení zaznamená jakékoli metody, které neumí generovat, vyloučí je z nativní bitové kopie. Jakmile modul runtime spustí toto sestavení, vrátí se k JIT kompilaci pro ty metody, které nejsou zahrnuty v nativní bitové kopii.

Kromě toho nejsou nativní bitové kopie použity v případě, že bylo sestavení inovováno, nebo pokud byla bitová kopie z jakéhokoliv důvodu zneplatněna.

<a name="InvalidImages"></a>

### <a name="invalid-images"></a>Neplatné obrázky

Při použití nástroje Ngen.exe pro vytvoření nativní bitové kopie sestavení závisí výstup na zadaných možnostech příkazového řádku a určitých nastaveních počítače. Mezi tato nastavení patří následující:

- Verze rozhraní .NET Framework.

- Verze operačního systému, pokud je změna z řady Windows 9x na systém řady Windows NT.

- Přesná identita sestavení (rekompilace identitu mění).

- Přesná identita všech sestavení, na které sestavení odkazuje (rekompilace identitu mění).

- Bezpečnostní faktory.

Nástroj Ngen.exe zaznamenává tyto informace při generování nativní bitové kopie. Po spuštění sestavení modul runtime hledá nativní bitovou kopii vytvořenou s možnostmi a nastavením, které odpovídají aktuálnímu prostředí počítače. Modul runtime se vrátí k JIT kompilaci sestavení, pokud nemůže najít odpovídající nativní bitovou kopii. Následující změny nastavení a prostředí počítače způsobí zneplatnění nativních bitových kopií:

- Verze rozhraní .NET Framework.

     Pokud použijete aktualizaci rozhraní .NET Framework, všechny nativní bitové kopie, které jste vytvořili pomocí Ngen.exe, se zneplatní. Z tohoto důvodu všechny aktualizace rozhraní .NET Framework provést `Ngen Update` příkaz, aby zajistily, že všechny nativní bitové kopie jsou obnoveny. Rozhraní .NET Framework automaticky vytvoří nové nativní bitové kopie pro knihovny rozhraní .NET Framework, které nainstaluje.

- Verze operačního systému, pokud je změna z řady Windows 9x na systém řady Windows NT.

     Pokud se například verze operačního systému spuštěná v počítači změní ze systému Windows 98 na systém Windows XP, všechny nativní bitové kopie uložené v nativní mezipaměti bitové kopie se stanou neplatnými. Pokud se však operační systém změní ze systému Windows 2000 na systém Windows XP, nebudou bitové kopie zrušeny.

- Přesná identita sestavení.

     Pokud je provedena rekompilace sestavení, odpovídající nativní bitové kopie se stanou neplatnými.

- Přesná identita všech sestavení, na která sestavení odkazuje.

     Pokud aktualizujete spravované sestavení, všechny nativní bitové kopie, které přímo nebo nepřímo závisí na tomto sestavení, se zneplatní a musí být znovu vygenerovány. To zahrnuje jak běžné odkazy, tak pevně vázané závislosti. Při každém použití aktualizace softwaru by měl `Ngen Update` instalační program provést příkaz, který zajistí, že budou znovu vygenerovány všechny závislé nativní bitové kopie.

- Bezpečnostní faktory.

     Změna zásad zabezpečení počítače směřující k omezení dříve udělených oprávnění sestavení může způsobit, že se dříve zkompilované nativní bitové kopie sestavení stanou neplatnými.

     Podrobné informace o tom, jak běžný jazyk runtime spravuje zabezpečení přístupu kódu a jak používat oprávnění, naleznete v [tématu Zabezpečení přístupu kódu](../misc/code-access-security.md).

<a name="Troubleshooting"></a>

## <a name="troubleshooting"></a>Řešení potíží

Následující témata řešení potíží umožňují zjistit, které nativní bitové kopie jsou používány a které aplikace nemůže použít, k určení, kdy kompilátor JIT začne kompilovat metodu, a ukazuje, jak se odhlásit z kompilace nativních bitových kopií zadaného Metody.

<a name="Fusion"></a>

### <a name="assembly-binding-log-viewer"></a>vazba sestavení – prohlížeč protokolu

Chcete-li ověřit, že nativní obrázky jsou používány vaší aplikací, můžete použít [Fuslogvw.exe (Assembly Binding Log Viewer)](fuslogvw-exe-assembly-binding-log-viewer.md). Select **Native Images** in the **Log Categories** box on the binding log viewer window. Fuslogvw.exe poskytuje informace o důvodu, proč byla nativní bitová kopie odmítnuta.

<a name="MDA"></a>

### <a name="the-jitcompilationstart-managed-debugging-assistant"></a>Asistent ladění spravovaných JITCompilationStart

Pomocí pomocníka pro ladění spravovaného [jitCompilationStart](../debug-trace-profile/jitcompilationstart-mda.md) (MDA) můžete určit, kdy kompilátor JIT začne kompilovat funkci.

<a name="OptOut"></a>

### <a name="opting-out-of-native-image-generation"></a>Odhlášení z nativní generace obrázků

V některých případech NGen.exe může mít potíže s generováním nativníbitá bitová kopie pro určitou metodu, nebo můžete dát přednost tomu, aby byla metoda zkompilován JIT, a nikoli zkompilován do nativního obrazu. V takovém případě můžete `System.Runtime.BypassNGenAttribute` pomocí atributu zabránit programu NGen.exe ve generování nativního obrazu pro určitou metodu. Atribut musí být použit jednotlivě pro každou metodu, jejíž kód nechcete zahrnout do nativního obrázku. NGen.exe rozpozná atribut a negeneruje kód v nativním obrázku pro odpovídající metodu.

Všimněte si `BypassNGenAttribute` však, že není definován jako typ v knihovně tříd rozhraní .NET Framework. Chcete-li spotřebovat atribut v kódu, musíte jej nejprve definovat takto:

[!code-csharp[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#1)]
[!code-vb[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#1)]

Atribut pak můžete použít na základě metody. Následující příklad instruuje generátor nativních bitových obrázků, že by neměl generovat nativní bitovou kopii pro metodu. `ExampleClass.ToJITCompile`

[!code-csharp[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#2)]
[!code-vb[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#2)]

## <a name="examples"></a>Příklady

Následující příkaz vygeneruje nativní bitovou kopii pro `ClientApp.exe`aplikaci umístěnou v aktuálním adresáři a nainstaluje ji do nativní mezipaměti bitové kopie. Pokud pro sestavení existuje soubor nastavení, Ngen.exe jej použije. Kromě toho jsou nativní obrázky generovány `ClientApp.exe` pro všechny soubory DLL, na které odkazují.

```console
ngen install ClientApp.exe
```

Bitová kopie nainstalovaná pomocí Ngen.exe se také nazývá kořen. Kořen může být aplikace nebo sdílená komponenta.

Následující příkaz generuje nativní `MyAssembly.exe` obraz se zadanou cestou.

```console
ngen install c:\myfiles\MyAssembly.exe
```

Při hledání sestavení a jejich závislosti používá Ngen.exe stejnou logiku při zjišťování, jaká je použita u Common Language Runtime (CLR). Ve výchozím nastavení se `ClientApp.exe` adresář, který obsahuje, používá jako základní adresář aplikace a veškeré zjišťování sestavení začíná v tomto adresáři. Toto chování můžete přepsat `/AppBase` pomocí této možnosti.

> [!NOTE]
> Jde o změnu oproti chování nástroje Ngen.exe v rozhraních .NET Framework verze 1.0 a 1.1, kde základ cesty aplikace je nastaven na aktuální adresář.

Sestavení může mít závislost bez odkazu, například pokud načte soubor DLL pomocí <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody. Pro takový soubor DLL můžete vytvořit nativní bitovou kopii pomocí `/ExeConfig` informací o konfiguraci pro sestavení aplikace s možností. Následující příkaz generuje nativní `MyLib.dll,` bitovou kopii `MyApp.exe`pro použití informací o konfiguraci z aplikace .

```console
ngen install c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe
```

Při odebrání aplikace nebudou odebrána sestavení nainstalovaná tímto způsobem.

Chcete-li odinstalovat závislost, použijte stejné možnosti příkazového řádku, které byly použity k její instalaci. Následující příkaz odinstaluje `MyLib.dll` z předchozího příkladu.

```console
ngen uninstall c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe
```

Chcete-li vytvořit nativní bitovou kopii pro sestavení v globální mezipaměti sestavení (GAC), použijte zobrazovaný název sestavení. Například:

```console
ngen install "ClientApp, Version=1.0.0.0, Culture=neutral,
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"
```

NGen.exe vytváří samostatnou sadu bitových kopií pro každý scénář, který instalujete. Například následující příkazy nainstalují kompletní sadu nativních bitových kopií pro normální provoz, jinou kompletní sadu pro ladění a třetí pro profilování:

```console
ngen install MyApp.exe
ngen install MyApp.exe /debug
ngen install MyApp.exe /profile
```

### <a name="displaying-the-native-image-cache"></a>Zobrazení mezipaměti nativních bitových kopií

Jakmile jsou nativní bitové kopie nainstalovány v mezipaměti, lze je zobrazit pomocí nástroje Ngen.exe. Následující příkaz zobrazí všechny nativní bitové kopie v mezipaměti nativních bitových kopií.

```console
ngen display
```

Akce `display` obsahuje seznam všech kořenových sestavení jako první, následovaný seznamem všech nativních bitových kopií v počítači.

Chcete-li zobrazit pouze informace o sestavení, použijte jeho jednoduchý název. Následující příkaz zobrazí všechny nativní bitové kopie v `MyAssembly`mezipaměti nativních obrázků, které odpovídají `MyAssembly`částečnému názvu , jejich závislostem a všem kořenům, které jsou závislé na :

```console
ngen display MyAssembly
```

Znalost kořenů závisí na sestavě sdílené součásti je `update` užitečná při měření dopadu akce po upgradu sdílené součásti.

Zadáte-li příponu souboru sestavení, musí být buď zadána cesta, nebo spuštěn nástroj Ngen.exe z adresáře obsahujícího sestavení:

```console
ngen display c:\myApps\MyAssembly.exe
```

Následující příkaz zobrazí všechny nativní obrazy v `MyAssembly` mezipaměti nativních obrázků s názvem a verzí 1.0.0.0.

```console
ngen display "myAssembly, version=1.0.0.0"
```

### <a name="updating-images"></a>Aktualizace bitových kopií

Bitové kopie jsou obvykle aktualizovány po upgradu sdílené komponenty. Chcete-li aktualizovat všechny nativní bitové kopie, které `update` se změnily nebo jejichž závislosti se změnily, použijte akci bez argumentů.

```console
ngen update
```

Aktualizace všech bitových kopií může být časově náročný proces. Pomocí `/queue` možnosti můžete zařadit aktualizace do fronty pro spuštění službou nativní bitové kopie. Další informace o `/queue` možnosti a prioritách instalace naleznete v [tématu Native Image Service](#native-image-service).

```console
ngen update /queue
```

### <a name="uninstalling-images"></a>Odinstalování bitových kopií

Nástroj Ngen.exe udržuje seznam závislostí, takže sdílené komponenty jsou odstraněny pouze v případě, že byla odebrána všechna sestavení, která na nich závisí. Kromě toho, pokud byla sdílená komponenta nainstalována jako kořen, nebude odstraněna.

Následující příkaz odinstaluje všechny `ClientApp.exe`scénáře pro kořenový adresář :

```console
ngen uninstall ClientApp
```

Akci `uninstall` lze použít k odebrání konkrétních scénářů. Následující příkaz odinstaluje všechny `ClientApp.exe`scénáře ladění pro :

```console
ngen uninstall ClientApp /debug
```

> [!NOTE]
> Odinstalování `/debug` scénářů neodinstaluje scénář, který zahrnuje jak `/profile``/debug.`

Následující příkaz odinstaluje všechny scénáře `ClientApp.exe`pro konkrétní verzi aplikace :

```console
ngen uninstall "ClientApp, Version=1.0.0.0"
```

Následující příkazy odinstalují všechny scénáře pro `"ClientApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL",` nebo pouze scénář ladění pro toto sestavení:

```console
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL" /debug
```

Stejně `install` jako u akce, poskytování rozšíření vyžaduje buď provádění Ngen.exe z adresáře obsahujícího sestavení nebo zadání úplné cesty.

Příklady týkající se nativní služby image naleznete v [tématu Nativní služba image Service](#native-image-service).

## <a name="native-image-task"></a>Úloha pro nativní bitové kopie

Nativní úloha bitové kopie je úloha systému Windows, která generuje a udržuje nativní bitové kopie. Nativní úloha bitové kopie generuje a uvolňuje nativní bitové kopie automaticky pro podporované scénáře. Umožňuje také instalačním programům používat [ngen.exe (Native Image Generator)](ngen-exe-native-image-generator.md) k vytváření a aktualizaci nativních bitových kopií v odloženém čase.

Nativní úloha bitové kopie je registrována jednou pro každou architekturu procesoru podporovanou v počítači, aby byla povolena kompilace pro aplikace, které cílí na každou architekturu:

|Název úlohy|32bitový počítač|64bitový počítač|
|---------------|----------------------|----------------------|
|NET Framework NGEN v4.0.30319|Ano|Ano|
|NET Framework NGEN v4.0.30319 64|Ne|Ano|

Nativní úloha bitové kopie je k dispozici v rozhraní .NET Framework 4.5 a novějších verzích při spuštění v systému Windows 8 nebo novějším. V dřívějších verzích systému Windows používá rozhraní .NET Framework [nativní službu image Service](#native-image-service).

### <a name="task-lifetime"></a>Doba trvání úlohy

Plánovač úloh systému Windows obecně spustí nativní úlohu bitové kopie každou noc, když je počítač nečinný. Úkol kontroluje všechny odložené práce, která je zařazena do fronty instalačními programy aplikace, všechny požadavky na odložené nativní aktualizace bitové kopie a jakékoli automatické vytváření bitových obrázků. Úkol dokončí nevyřízené pracovní položky a potom se vypne. Pokud počítač přestane být nečinný, když je úloha spuštěna, úloha se zastaví.

Nativní úlohu bitové kopie můžete také spustit ručně prostřednictvím ui plánovače úloh nebo prostřednictvím ručních volání ngen.exe. Pokud je úloha spuštěna pomocí jedné z těchto metod, bude pokračovat v běhu, když počítač již není nečinný. Obrázky vytvořené ručně pomocí programu NGen.exe jsou upřednostňovány tak, aby umožňovaly předvídatelné chování instalačních programů aplikací.

## <a name="native-image-service"></a>Nativní bitová kopie služby

Nativní služba bitové kopie je služba systému Windows, která generuje a udržuje nativní bitové kopie. Nativní služba bitové kopie umožňuje vývojáři odložit instalaci a aktualizaci nativních bitových kopií na období, kdy je počítač nečinný.

Nativní obrazová služba je obvykle iniciována instalačním programem (instalačním programem) pro aplikaci nebo aktualizaci. Pro akce s prioritou 3 se služba provede během doby nečinnosti v počítači. Služba uloží svůj stav a je schopna pokračovat prostřednictvím více restartování v případě potřeby. Více kompilací obrázků může být zařazeno do fronty.

Služba také spolupracuje s ručním příkazem Ngen.exe. Ruční příkazy mají přednost před aktivitou na pozadí.

> [!NOTE]
> V systému Windows Vista je název zobrazený pro nativní bitovou kopiovou službu "Microsoft.NET Framework NGEN v2.0.50727_X86" nebo "Microsoft.NET Framework NGEN v2.0.50727_X64". Ve všech předchozích verzích systému Microsoft Windows je název ".NET Runtime Optimization Service v2.0.50727_X86" nebo ".NET Runtime Optimization Service v2.0.50727_X64".

### <a name="launching-deferred-operations"></a>Spuštění odložené operace

Před zahájením instalace nebo upgradu se doporučuje pozastavovat službu. Tím je zajištěno, že služba nebude spuštěna, zatímco instalační program kopíruje soubory nebo umisňuje sestavení do globální mezipaměti sestavení. Následující příkazový řádek Ngen.exe pozastaví službu:

```console
ngen queue pause
```

Po zařazení všech odložených operací do fronty umožňuje následující příkaz službě pokračovat:

```console
ngen queue continue
```

Chcete-li odložit generování nativní bitové kopie při instalaci `/queue` nové `install` aplikace `update` nebo při aktualizaci sdílené součásti, použijte tuto možnost s akcemi nebo. Následující příkazové řádky Ngen.exe nainstalují nativní bitovou kopii pro sdílenou součást a provedou aktualizaci všech kořenových adresářů, které mohly být ovlivněny:

```console
ngen install MyComponent /queue
ngen update /queue
```

Akce `update` regeneruje všechny nativní obrázky, které byly zrušeny, nejen ty, které používají `MyComponent`.

Pokud se aplikace skládá z mnoha kořenových adresářů, můžete řídit prioritu odložených akcí. Následující příkazy zařadí instalaci tří kořenových adresářů do fronty. `Assembly1`je nainstalován jako první, bez čekání na dobu nečinnosti. `Assembly2`je také nainstalován bez čekání na dobu nečinnosti, ale po dokončení všech akcí priority 1. `Assembly3`je nainstalován, když služba zjistí, že počítač je nečinný.

```console
ngen install Assembly1 /queue:1
ngen install Assembly2 /queue:2
ngen install Assembly3 /queue:3
```

Pomocí `executeQueuedItems` akce můžete vynutit synchronní akce zařazené do fronty. Pokud zadáte volitelnou prioritu, tato akce ovlivní pouze akce ve frontě, které mají stejnou nebo nižší prioritu. Výchozí priorita je 3, takže následující příkaz Ngen.exe zpracuje všechny akce ve frontě okamžitě a nevrátí se, dokud nebudou dokončeny:

```console
ngen executeQueuedItems
```

Synchronní příkazy jsou spouštěny ngen.exe a nepoužívají nativní image služby. Můžete provádět akce pomocí Ngen.exe, zatímco nativní image služby je spuštěna.

### <a name="service-shutdown"></a>Vypnutí služby

Po zahájení spuštění příkazu Ngen.exe, který `/queue` obsahuje možnost, služba běží na pozadí, dokud nebudou dokončeny všechny akce. Služba uloží svůj stav, takže může pokračovat prostřednictvím více restartování v případě potřeby. Když služba zjistí, že nejsou žádné další akce ve frontě, obnoví svůj stav tak, aby se nerestartuje při příštím spuštění počítače a potom se sám vypne.

### <a name="service-interaction-with-clients"></a>Interakce služeb s klienty

V rozhraní .NET Framework verze 2.0 je jediná interakce se službou nativníbitá image prostřednictvím nástroje příkazového řádku Ngen.exe. Pomocí nástroje příkazového řádku v instalačních skriptech můžete zařadit akce do fronty pro nativní službu bitové kopie a pracovat se službou.

## <a name="see-also"></a>Viz také

- [Nástroje](index.md)
- [Proces spravovaného spouštění](../../standard/managed-execution-process.md)
- [Jak běhové prostředí vyhledává sestavení](../deployment/how-the-runtime-locates-assemblies.md)
- [Příkazové řádky](developer-command-prompt-for-vs.md)
