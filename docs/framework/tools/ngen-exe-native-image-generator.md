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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20e5f166aad8bc2504ed27b93ec6730bcd26387d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911587"
---
# <a name="ngenexe-native-image-generator"></a>Ngen.exe (generátor nativních obrázků)

Generátor nativních bitových kopií (Ngen.exe) je nástroj zvyšující výkon spravovaných aplikací. Nástroj Ngen.exe vytváří nativní bitové kopie, což jsou soubory obsahující zkompilovaný strojový kód specifický pro procesor, a instaluje je do mezipaměti nativních bitových kopií v místním počítači. Modul runtime může ke kompilaci původního sestavení použít nativní bitové kopie z mezipaměti namísto kompilátoru JIT (just-in-time).

> [!NOTE]
> Ngen. exe zkompiluje nativní bitové kopie pro sestavení, která cílí pouze na .NET Framework. Ekvivalentní generátor nativních bitových kopií pro .NET Core je [CrossGen](https://github.com/dotnet/coreclr/blob/master/Documentation/building/crossgen.md). 

Změny nástroje Ngen. exe v .NET Framework 4:

- Nástroj Ngen.exe nyní kompiluje sestavení s úplnou důvěryhodností, přičemž zabezpečení přístupu kódu (CAS) již není vyhodnocováno.

- Nativní bitové kopie generované nástrojem Ngen.exe již nemohou být načteny do aplikací spuštěných s částečnou důvěryhodností.

Změny nástroje Ngen.exe v rozhraní .NET Framework verze 2.0:

- Instalace sestavení nainstaluje také jeho závislosti, což zjednodušuje syntaxi nástroje Ngen.exe.

- Nativní bitové kopie mohou být nyní sdíleny napříč doménami aplikací.

- Nová akce `update`způsobí, že znovu vytvoří image, jejichž platnost byla zrušena.

- Pro generování a instalaci bitových kopií může být spuštění akcí odloženo službou využívající dobu nečinnosti.

- Některé příčiny zneplatnění bitové kopie byly odstraněny.

V systému Windows 8, viz [úloha nativní bitové kopie](#native-image-task).

Další informace o použití nástroje Ngen. exe a služby nativních bitových kopií naleznete v tématu [nativní Image Service](#native-image-service).

> [!NOTE]
> Syntaxe Ngen. exe pro verze 1,0 a 1,1 .NET Framework se dá najít v [syntaxi starší verze generátoru nativních imagí (Ngen. exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms165073(v=vs.100)).

Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace najdete v tématu [výzvy k zadání příkazu](../../../docs/framework/tools/developer-command-prompt-for-vs.md).

V příkazovém řádku zadejte následující:

## <a name="syntax"></a>Syntaxe

```console
ngen action [options]
```

```console
ngen /? | /help
```

## <a name="actions"></a>Akce

V následující tabulce je uvedena syntaxe každého z `action`nich. Popisy `action`jednotlivých částí sady najdete v tabulkách [argumenty](#ArgumentTable), [úrovně priority](#PriorityTable), [scénáře](#ScenarioTable)a [Konfigurace](#ConfigTable) . V tabulce [Options](#OptionTable) jsou popsány `options` přepínače Help a.

|Akce|Popis|
|------------|-----------------|
|`install` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`] [`/queue`[`:`{`1`&#124;`2`&#124;`3`}]]|Vygeneruje nativní bitové kopie sestavení a jeho závislosti a nainstaluje bitové kopie do mezipaměti nativních bitových kopií.<br /><br /> Je `/queue` -li parametr zadán, je akce zařazena do fronty pro službu nativních bitových kopií. Výchozí hodnota priority je 3. Podívejte se na tabulku [úrovně priority](#PriorityTable) .|
|`uninstall` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`]|Odstraní nativní bitové kopie sestavení a jeho závislosti z mezipaměti nativních bitových kopií.<br /><br /> Chcete-li odinstalovat pouze jednu bitovou kopii a její závislosti, použijte stejné argumenty příkazového řádku, které byly použity při instalaci kopie. **Poznámka:**  Počínaje .NET Framework 4 není akce `uninstall` * nadále podporována.|
|`update` [`/queue`]|Aktualizuje nativní bitové kopie, které se staly neplatnými.<br /><br /> Pokud `/queue` je zadaný, aktualizace se zařadí do fronty pro nativní Image Service. Aktualizace jsou vždy naplánovány s prioritou 3, jsou tedy spouštěny při nečinnosti počítače.|
|`display` [`assemblyName` &#124; `assemblyPath`]|Zobrazí stav nativních bitových kopií pro sestavení a jeho závislosti.<br /><br /> Není-li zadán žádný argument, je zobrazen celý obsah mezipaměti nativních bitových kopií.|
|`executeQueuedItems` [<code>1&#124;2&#124;3</code>]<br /><br /> -nebo-<br /><br /> `eqi` [1&#124;2&#124;3]|Spustí úlohy kompilace ve frontě.<br /><br /> Je-li zadána priorita, jsou spuštěny úlohy kompilace s větší nebo shodnou prioritou. Není-li priorita zadána, jsou spuštěny všechny úlohy kompilace.|
|`queue` {`pause` &#124; `continue` &#124; `status`}|Pozastaví službu nativních bitových kopií, umožní pozastavené službě pokračovat nebo se dotáže na stav služby.|

<a name="ArgumentTable"></a>

## <a name="arguments"></a>Arguments

|Argument|Popis|
|--------------|-----------------|
|`assemblyName`|Plný zobrazovaný název sestavení. Například, `"myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5"`. **Poznámka:**  Pro akce `myAssembly` a`uninstall`můžete uvést částečný název sestavení, například. `display` <br /><br /> V jednom příkazovém řádku nástroje Ngen.exe lze zadat pouze jedno sestavení.|
|`assemblyPath`|Explicitní cesta k sestavení. Lze zadat úplnou nebo relativní cestu.<br /><br /> Zadáte-li název souboru bez cesty, musí se sestavení nacházet v aktuálním adresáři.<br /><br /> V jednom příkazovém řádku nástroje Ngen.exe lze zadat pouze jedno sestavení.|

<a name="PriorityTable"></a>

## <a name="priority-levels"></a>Úrovně priority

|Priority|Popis|
|--------------|-----------------|
|`1`|Nativní bitové kopie jsou generovány a nainstalovány okamžitě, nečeká se na nečinnost počítače.|
|`2`|Nativní bitové kopie jsou generovány a instalovány bez čekání na nečinnost počítače, ale až po dokončení všech akcí s prioritou 1 (a jejich závislostí).|
|`3`|Nativní bitové kopie jsou nainstalovány ve chvíli, kdy služba nativních bitových kopií zjistí, že je počítač nečinný. Viz [nativní Image Service](#native-image-service).|

<a name="ScenarioTable"></a>

## <a name="scenarios"></a>Scénáře

|Scénář|Popis|
|--------------|-----------------|
|`/Debug`|Vygeneruje nativní bitové kopie, které lze použít v ladicím programu.|
|`/Profile`|Vygeneruje nativní bitové kopie, které lze použít v profileru.|
|`/NoDependencies`|Vygeneruje minimální počet nativních bitových kopií požadovaný zadanými možnostmi scénáře.|

<a name="ConfigTable"></a>

## <a name="config"></a>Konfigurace

|Konfiguraci|Popis|
|-------------------|-----------------|
|`/ExeConfig:``exePath`|Použije konfiguraci zadaného spustitelného sestavení.<br /><br /> Při vytváření vazeb na závislosti musí nástroj Ngen.exe učinit stejná rozhodnutí jako zavaděč. Při načtení sdílené komponenty za běhu pomocí <xref:System.Reflection.Assembly.Load%2A> metody určuje konfigurační soubor aplikace závislosti, které jsou načteny pro sdílenou součást, například verzi načtené závislosti. `/ExeConfig` Přepínač poskytuje pokyny Ngen. exe, na kterých by se měly načíst závislosti za běhu.|
|`/AppBase:``directoryPath`|Při hledání závislostí aplikace použije jako základ cesty zadaný adresář.|

<a name="OptionTable"></a>

## <a name="options"></a>Možnosti

|Možnost|Popis|
|------------|-----------------|
|`/nologo`|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|
|`/silent`|Potlačí zobrazování zpráv o úspěchu.|
|`/verbose`|Zobrazí podrobné informace o ladění. **Poznámka:**  V důsledku omezení operačního systému Tato možnost nezobrazuje ve Windows 98 a Windows Millennium Edition tolik dalších informací.|
|`/help`, `/?`|Zobrazí syntaxi příkazu a možnosti aktuální verze.|

## <a name="remarks"></a>Poznámky

Chcete-li spustit nástroj Ngen.exe, je zapotřebí mít oprávnění správce.

> [!CAUTION]
> Nástroj Ngen.exe nespouštějte pro sestavení, která nemají plnou důvěryhodnost. Počínaje .NET Framework 4, Ngen. exe zkompiluje sestavení s úplným vztahem důvěryhodnosti a zásady zabezpečení přístupu kódu (CAS) se už nevyhodnotí.

Počínaje .NET Framework 4 již nelze načíst nativní bitové kopie, které jsou generovány pomocí nástroje Ngen. exe, do aplikací, které běží v částečném vztahu důvěryhodnosti. Namísto toho je vyvolán kompilátor za běhu (JIT).

Ngen. exe generuje nativní bitové kopie pro sestavení určené `assemblyname` argumentem `install` pro akci a všechny její závislosti. Závislosti se stanoví z odkazů v manifestu sestavení. Jediným scénářem, kdy je nutné nainstalovat závislost samostatně, je, když ji aplikace načte pomocí reflexe, například voláním <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody.

> [!IMPORTANT]
> Nepoužívejte <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metodu s nativními bitovými kopiemi. Bitovou kopii zavedenou touto metodou nelze v kontextu spuštění používat jinými sestaveními.

Nástroj Ngen.exe udržuje počet odkazů na závislosti. Předpokládejme například, že `MyAssembly.exe` a `YourAssembly.exe` jsou nainstalovány v mezipaměti nativní bitové kopie a oba mají odkazy na `OurDependency.dll`. Pokud `MyAssembly.exe` je odinstalován, `OurDependency.dll` nedojde k odinstalaci. Odstraní se jenom v případě `YourAssembly.exe` , že se taky odinstaluje.

Pokud generujete nativní bitovou kopii pro sestavení v globální mezipaměti sestavení (GAC), zadejte její zobrazovaný název. Viz <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>.

Nativní bitové kopie, které generuje Ngen.exe, mohou být sdíleny napříč doménami aplikace. To znamená, že nástroj Ngen.exe lze použít ve scénářích aplikací, které vyžadují, aby byla sestavení sdílena napříč doménami aplikace. Určení neutrality domény:

- <xref:System.LoaderOptimizationAttribute> Použijte atribut pro aplikaci.

- <xref:System.AppDomainSetup.LoaderOptimization%2A?displayProperty=nameWithType> Nastavte vlastnost při vytváření informací o instalaci pro novou doménu aplikace.

Vždy je třeba použít doménově neutrální kód, pokud je dané sestavení načítáno do více domén aplikace. Pokud je nativní bitová kopie načtena do nesdílené domény aplikace poté, co byla načtena do sdílené domény, nelze ji použít.

> [!NOTE]
> Doménově neutrální kód nemůže být uvolněn a výkon může být mírně snížen, zvláště při přistupování ke statickým členům.

V tomto oddílu Poznámky:

- [Generování imagí pro různé scénáře](#Scenarios)

- [Určení, kdy použít nativní bitové kopie](#WhenToUse)

  - [Vylepšené využití paměti](#Memory)

  - [Rychlejší spuštění aplikace](#Startup)

  - [Souhrn důležitých informací o použití](#UsageSummary)

- [Důležitost základních adres sestavení](#BaseAddresses)

- [Pevná vazba](#HardBinding)

  - [Zadání pomocného parametru vazby pro závislost](#DependencyHint)

  - [Určení výchozího parametru vazby pro sestavení](#AssemblyHint)

- [Odložené zpracování](#Deferred)

- [Nativní bitové kopie a kompilace JIT](#JITCompilation)

  - [Neplatné obrázky](#InvalidImages)

- [Odstraňování potíží](#Troubleshooting)

  - [Prohlížeč protokolu vazby sestavení](#Fusion)

  - [Pomocníka spravovaného ladění jitCompilationStart –](#MDA)

  - [Vypnutí generování nativních imagí](#OptOut)

<a name="Scenarios"></a>

## <a name="generating-images-for-----different-scenarios"></a>Generování imagí pro různé scénáře

Po vygenerování nativní bitové kopie pro sestavení se modul runtime automaticky pokusí vyhledat a použít tuto nativní bitovou kopii při každém spuštění sestavení. V závislosti na scénáři lze generovat více bitových kopií.

Například pokud spustíte sestavení ve scénáři ladění nebo profilace, modul runtime vyhledá nativní bitovou kopii, která byla vygenerována s `/Debug` možnostmi nebo. `/Profile` Pokud nemůže najít odpovídající nativní bitovou kopii, vrátí se modul runtime ke standardní JIT kompilaci. Jediným způsobem, jak ladit nativní bitové kopie, je vytvořit nativní bitovou kopii `/Debug` s možností.

Tato `uninstall` akce také rozpoznává scénáře, takže můžete odinstalovat všechny scénáře nebo pouze vybrané scénáře.

<a name="WhenToUse"></a>

## <a name="determining-when-to-use-native-images"></a>Určení, kdy použít nativní bitové kopie

Nativní bitové kopie mohou poskytnout zvýšení výkonu ve dvou oblastech: lepší využití paměti a rychlejší spouštění.

> [!NOTE]
> Výkon nativních bitových kopií závisí na několika faktorech, které analýzu výkonu znesnadňují, například přístupové vzory kódu a dat, počet volání napříč hranicemi modulu či počet závislostí již načtených jinými aplikacemi. Jediným způsobem, jak určit, zda nativní bitové kopie prospívají aplikaci, je pečlivé měření výkonu v klíčových scénářích nasazení.

<a name="Memory"></a>

### <a name="improved-memory-use"></a>Vylepšené využití paměti

Nativní bitové kopie mohou významně zlepšit využití paměti, je-li kód sdílen mezi procesy. Nativní bitové kopie jsou soubory Windows PE, tudíž jedna kopie souboru .dll může být sdílena několika procesy. Naproti tomu nativní kód vytvořený kompilátorem JIT je uložen v soukromé paměti a nelze jej sdílet.

Aplikace spuštěné v rámci terminálových služeb také využívají výhod sdílených znakových stránek.

Kromě toho skutečnost, že není načítán kompilátor JIT, ušetří pevně dané množství paměti pro každou instanci aplikace.

<a name="Startup"></a>

### <a name="faster-application-startup"></a>Rychlejší spuštění aplikace

Předkompilování sestavení programem Ngen.exe může zvýšit rychlost spuštění některých aplikací. Obecně lze zvýšení výkonu dosáhnout tam, kde aplikace sdílejí sestavení komponent, protože po prvním spuštění aplikace jsou komponenty sdílené s jinými aplikacemi již načteny. Úplné spuštění, při němž musí být všechna sestavení aplikace načtena z pevného disku, nevyužívají výhod nativních bitových kopií v takové míře, protože má převahu přístupová doba pevného disku.

Pevné vazby mohou ovlivnit rychlost spuštění, protože všechny bitové kopie pevně svázané s hlavním sestavením aplikace musí být načteny najednou.

> [!NOTE]
> Před .NET Framework 3,5 aktualizace Service Pack 1 byste měli umístit sdílené a silně pojmenované komponenty do globální mezipaměti sestavení (GAC), protože zavaděč provádí dodatečné ověřování pro sestavení se silným názvem, která nejsou v globální mezipaměti sestavení (GAC), efektivně se eliminují. jakékoli zlepšení času spuštění získaného pomocí nativních imagí. Optimalizace, které byly představeny v .NET Framework 3,5 SP1, odebraly dodatečné ověření.

<a name="UsageSummary"></a>

### <a name="summary-of-usage-considerations"></a>Souhrn důležitých informací o použití

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

## <a name="importance-of-assembly-base-addresses"></a>Důležitost základních adres sestavení

Jelikož nativní bitové kopie jsou soubory Windows PE, týkají se jich stejné problémy související se změnou základní cesty jako u ostatních spustitelných souborů. Snížení výkonu vinou přemístění je ještě větší, jsou-li použity pevné vazby.

Chcete-li nastavit základní adresu pro nativní bitovou kopii, použijte příslušnou možnost kompilátoru pro nastavení základní adresy sestavení. Tuto základní adresu používá nástroj Ngen.exe pro nativní bitové kopie.

> [!NOTE]
> Nativní bitové kopie jsou větší než spravovaná sestavení, z nichž byly vytvořeny. Základní adresy musí být vypočteny tak, aby tyto větší velikosti umožňovaly.

Chcete-li zobrazit preferovanou základní adresu nativní bitové kopie, můžete použít například nástroj dumpbin.exe.

<a name="HardBinding"></a>

## <a name="hard-binding"></a>Pevná vazba

Pevné vazby zvyšují propustnost a snižují velikost pracovní sady pro nativní bitové kopie. Nevýhodou pevné vazby je, že všechny bitové kopie, které jsou pevně vázány na sestavení, musí být načteny při načtení sestavení. To u velkých aplikací může výrazně prodloužit spouštění.

Pevná vazba je vhodná pro závislosti, které jsou načteny ve všech scénářích aplikace, u kterých velmi záleží na výkonu. Stejně jako u jakéhokoli jiného aspektu použití nativní bitové kopie je měření výkonu jediným způsobem, jak určit, zda pevná vazba zlepšuje výkon vaší aplikace.

Atributy <xref:System.Runtime.CompilerServices.DependencyAttribute> a<xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> umožňují zadat pomocný parametr pro pevné vazby do nástroje Ngen. exe.

> [!NOTE]
> Tyto atributy jsou informace pro Ngen.exe, nikoli příkazy. Jejich použití nezaručuje pevné vazby. V budoucích verzích se může změnit význam těchto atributů.

<a name="DependencyHint"></a>

### <a name="specifying-a-binding-hint-for-a-dependency"></a>Zadání pomocného parametru vazby pro závislost

<xref:System.Runtime.CompilerServices.DependencyAttribute> Použijte pro sestavení k označení pravděpodobnosti, že se načte zadaná závislost. <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType>označuje, že pevná vazba je vhodná <xref:System.Runtime.CompilerServices.LoadHint.Default> , indikuje, že by měla být použita výchozí hodnota závislosti, <xref:System.Runtime.CompilerServices.LoadHint.Sometimes> a označuje, že pevná vazba není vhodná.

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

### <a name="specifying-a-default-binding-hint-for-an-assembly"></a>Určení výchozího parametru vazby pro sestavení

Výchozí pokyny pro vazby jsou zapotřebí pouze pro sestavení, která budou použita okamžitě a často aplikací, která na nich závisí. <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> Použijte s <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> u těchto sestavení k určení, že se má použít pevná vazba.

> [!NOTE]
> Neexistuje žádný důvod, jak použít <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> na sestavení knihovny DLL, která nespadají do této kategorie, protože použití atributu s jinou hodnotou než <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> má stejný efekt jako nepoužití atributu vůbec.

Společnost Microsoft používá <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> k určení této pevné vazby výchozí hodnotu pro velmi malý počet sestavení v .NET Framework, jako je například mscorlib. dll.

<a name="Deferred"></a>

## <a name="deferred-processing"></a>Odložené zpracování

Generování nativních bitových kopií pro velmi velké aplikace může být časově náročné. Obdobně změny sdílené komponenty nebo změny nastavení počítače mohou vyžadovat aktualizaci mnoha nativních bitových kopií. Akce `install` a `update` mají`/queue` možnost, která zařadí do fronty operaci pro odložené spouštění pomocí nativní bitové kopie služby. Kromě toho nástroj Ngen. exe obsahuje `queue` akce `executeQueuedItems` a, které poskytují určitou kontrolu nad službou. Další informace najdete v tématu [nativní Image Service](#native-image-service).

<a name="JITCompilation"></a>

## <a name="native-images-and-jit-compilation"></a>Nativní bitové kopie a kompilace JIT

Pokud Ngen.exe v sestavení zaznamená jakékoli metody, které neumí generovat, vyloučí je z nativní bitové kopie. Jakmile modul runtime spustí toto sestavení, vrátí se k JIT kompilaci pro ty metody, které nejsou zahrnuty v nativní bitové kopii.

Kromě toho nejsou nativní bitové kopie použity v případě, že bylo sestavení inovováno, nebo pokud byla bitová kopie z jakéhokoliv důvodu zneplatněna.

<a name="InvalidImages"></a>

### <a name="invalid-images"></a>Neplatné obrázky

Při použití nástroje Ngen.exe pro vytvoření nativní bitové kopie sestavení závisí výstup na zadaných možnostech příkazového řádku a určitých nastaveních počítače. Mezi tato nastavení patří následující:

- Verze rozhraní .NET Framework.

- Verze operačního systému, pokud je změna z řady Windows 9x na řadu Windows NT.

- Přesná identita sestavení (rekompilace identitu mění).

- Přesná identita všech sestavení, na které sestavení odkazuje (rekompilace identitu mění).

- Bezpečnostní faktory.

Nástroj Ngen.exe zaznamenává tyto informace při generování nativní bitové kopie. Po spuštění sestavení modul runtime hledá nativní bitovou kopii vytvořenou s možnostmi a nastavením, které odpovídají aktuálnímu prostředí počítače. Modul runtime se vrátí k JIT kompilaci sestavení, pokud nemůže najít odpovídající nativní bitovou kopii. Následující změny nastavení a prostředí počítače způsobí zneplatnění nativních bitových kopií:

- Verze rozhraní .NET Framework.

     Pokud použijete aktualizaci rozhraní .NET Framework, všechny nativní bitové kopie, které jste vytvořili pomocí Ngen.exe, se zneplatní. Z tohoto důvodu všechny aktualizace .NET Framework spustí `Ngen Update` příkaz, aby se zajistilo opětovné vygenerování všech nativních imagí. Rozhraní .NET Framework automaticky vytvoří nové nativní bitové kopie pro knihovny rozhraní .NET Framework, které nainstaluje.

- Verze operačního systému, pokud je změna z řady Windows 9x na řadu Windows NT.

     Například pokud se verze operačního systému běžícího na počítači změní z Windows 98 na Windows XP, všechny nativní bitové kopie uložené v mezipaměti nativních imagí se stanou neplatnými. Pokud se ale operační systém změní z Windows 2000 na Windows XP, bitové kopie se neověřují.

- Přesná identita sestavení.

     Pokud je provedena rekompilace sestavení, odpovídající nativní bitové kopie se stanou neplatnými.

- Přesná identita všech sestavení, na která sestavení odkazuje.

     Pokud aktualizujete spravované sestavení, všechny nativní bitové kopie, které přímo nebo nepřímo závisí na tomto sestavení, se zneplatní a musí být znovu vygenerovány. To zahrnuje jak běžné odkazy, tak pevně vázané závislosti. Pokaždé, když se použije aktualizace softwaru, instalační program by měl `Ngen Update` spustit příkaz, aby se zajistilo, že se znovu vygenerují všechny závislé nativní bitové kopie.

- Bezpečnostní faktory.

     Změna zásad zabezpečení počítače směřující k omezení dříve udělených oprávnění sestavení může způsobit, že se dříve zkompilované nativní bitové kopie sestavení stanou neplatnými.

     Podrobné informace o tom, jak modul CLR (Common Language Runtime) spravuje zabezpečení přístupu kódu a používání oprávnění, najdete v tématu [zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security.md).

<a name="Troubleshooting"></a>

## <a name="troubleshooting"></a>Poradce při potížích

Následující témata Poradce při potížích umožňují zjistit, které nativní bitové kopie jsou používány a které nemohou být použity vaší aplikací, k určení, kdy kompilátor JIT začne kompilovat metodu a ukazuje, jak se odhlásit ze zadaného nativního kompilování bitové kopie. způsobů.

<a name="Fusion"></a>

### <a name="assembly-binding-log-viewer"></a>vazba sestavení – prohlížeč protokolu

Chcete-li potvrdit, že aplikace používá nativní bitové kopie, můžete použít [Fuslogvw. exe (Prohlížeč protokolu vazby sestavení)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md). V okně prohlížeče protokolu vazby v poli **Kategorie protokolů** vyberte **nativní bitové kopie** . Fuslogvw.exe poskytuje informace o důvodu, proč byla nativní bitová kopie odmítnuta.

<a name="MDA"></a>

### <a name="the-jitcompilationstart-managed-debugging-assistant"></a>Pomocníka spravovaného ladění jitCompilationStart –

K určení, kdy kompilátor JIT začne kompilovat funkci, můžete použít pomocníka spravovaného ladění (MDA) [jitCompilationStart –](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md) .

<a name="OptOut"></a>

### <a name="opting-out-of-native-image-generation"></a>Vypnutí generování nativních imagí

V některých případech může NGen. exe mít potíže při generování nativní bitové kopie pro konkrétní metodu, nebo může být vhodnější, aby byla metoda JIT zkompilována, spíše zkompilována do nativní bitové kopie. V takovém případě můžete použít `System.Runtime.BypassNGenAttribute` atribut k zabránění generování nativní bitové kopie pro určitou metodu pomocí atributu Ngen. exe. Atribut musí být použit samostatně pro každou metodu, jejíž kód nechcete zahrnout do nativní bitové kopie. NGen. exe rozpoznává atribut a negeneruje kód v nativní imagi pro odpovídající metodu.

Všimněte si však, že `BypassNGenAttribute` není definován jako typ v knihovně tříd .NET Framework. Aby bylo možné používat atribut v kódu, je nutné nejprve definovat následující:

[!code-csharp[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#1)]
[!code-vb[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#1)]

Pak můžete použít atribut na základě jednotlivých metod. Následující příklad instruuje generátor nativních bitových kopií, který by neměl generovat nativní bitovou kopii `ExampleClass.ToJITCompile` pro metodu.

[!code-csharp[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#2)]
[!code-vb[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#2)]

## <a name="examples"></a>Příklady

Následující příkaz vytvoří nativní bitovou kopii pro `ClientApp.exe`objekt umístěný v aktuálním adresáři a nainstaluje bitovou kopii do mezipaměti nativní bitové kopie. Pokud pro sestavení existuje soubor nastavení, Ngen.exe jej použije. Kromě toho jsou vygenerovány nativní bitové kopie pro všechny soubory DLL `ClientApp.exe` , které odkazují na.

```console
ngen install ClientApp.exe
```

Bitová kopie nainstalovaná pomocí Ngen.exe se také nazývá kořen. Kořen může být aplikace nebo sdílená komponenta.

Následující příkaz vytvoří nativní bitovou kopii pro `MyAssembly.exe` zadanou cestu.

```console
ngen install c:\myfiles\MyAssembly.exe
```

Při hledání sestavení a jejich závislosti používá Ngen.exe stejnou logiku při zjišťování, jaká je použita u Common Language Runtime (CLR). Ve výchozím nastavení se adresář, který `ClientApp.exe` obsahuje, používá jako základní adresář aplikace a veškeré zjišťování sestavení začíná v tomto adresáři. Toto chování můžete přepsat pomocí `/AppBase` možnosti.

> [!NOTE]
> Jde o změnu oproti chování nástroje Ngen.exe v rozhraních .NET Framework verze 1.0 a 1.1, kde základ cesty aplikace je nastaven na aktuální adresář.

Sestavení může mít závislost bez odkazu, například pokud načte soubor DLL pomocí <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody. Můžete vytvořit nativní bitovou kopii pro takový soubor. dll pomocí informací o konfiguraci pro sestavení aplikace s `/ExeConfig` možností. Následující příkaz vytvoří nativní bitovou kopii pro `MyLib.dll,` použití informací o konfiguraci z `MyApp.exe`.

```console
ngen install c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe
```

Při odebrání aplikace nebudou odebrána sestavení nainstalovaná tímto způsobem.

Chcete-li odinstalovat závislost, použijte stejné možnosti příkazového řádku, které byly použity k její instalaci. Následující příkaz odinstaluje `MyLib.dll` z předchozího příkladu.

```console
ngen uninstall c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe
```

Chcete-li vytvořit nativní bitovou kopii pro sestavení v globální mezipaměti sestavení (GAC), použijte zobrazovaný název sestavení. Příklad:

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

`display` Akce nejprve Vypíše všechna kořenová sestavení a potom seznam všech nativních bitových kopií v počítači.

Chcete-li zobrazit pouze informace o sestavení, použijte jeho jednoduchý název. Následující příkaz zobrazí všechny nativní bitové kopie v mezipaměti nativních imagí, které odpovídají částečnému `MyAssembly`názvu, jejich závislostem a všem kořenům, na `MyAssembly`kterých závisí:

```console
ngen display MyAssembly
```

Znalost toho, které kořeny závisí na sestavení sdílené komponenty, je užitečné v měření dopad `update` akce po upgradu sdílené komponenty.

Zadáte-li příponu souboru sestavení, musí být buď zadána cesta, nebo spuštěn nástroj Ngen.exe z adresáře obsahujícího sestavení:

```console
ngen display c:\myApps\MyAssembly.exe
```

Následující příkaz zobrazí všechny nativní bitové kopie v mezipaměti nativních imagí s názvem `MyAssembly` a verzí 1.0.0.0.

```console
ngen display "myAssembly, version=1.0.0.0"
```

### <a name="updating-images"></a>Aktualizace bitových kopií

Bitové kopie jsou obvykle aktualizovány po upgradu sdílené komponenty. Chcete-li aktualizovat všechny nativní bitové kopie, které se změnily nebo jejichž závislosti se `update` změnily, použijte akci bez argumentů.

```console
ngen update
```

Aktualizace všech bitových kopií může být časově náročný proces. Aktualizace můžete zařadit do fronty pro spouštění pomocí služby nativních imagí pomocí `/queue` možnosti. Další informace o `/queue` možnosti a prioritách instalace najdete v tématu [nativní Image Service](#native-image-service).

```console
ngen update /queue
```

### <a name="uninstalling-images"></a>Odinstalování bitových kopií

Nástroj Ngen.exe udržuje seznam závislostí, takže sdílené komponenty jsou odstraněny pouze v případě, že byla odebrána všechna sestavení, která na nich závisí. Kromě toho, pokud byla sdílená komponenta nainstalována jako kořen, nebude odstraněna.

Následující příkaz odinstaluje všechny scénáře pro kořen `ClientApp.exe`:

```console
ngen uninstall ClientApp
```

`uninstall` Akci lze použít k odebrání konkrétních scénářů. Následující příkaz odinstaluje všechny scénáře ladění pro `ClientApp.exe`:

```console
ngen uninstall ClientApp /debug
```

> [!NOTE]
> Při `/debug` odinstalaci scénářů nedojde k odinstalování `/profile` scénáře, který zahrnuje i`/debug.`

Následující příkaz odinstaluje všechny scénáře pro konkrétní verzi `ClientApp.exe`nástroje:

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

Stejně jako u `install` akce vyžaduje poskytnutí rozšíření buď spuštění nástroje Ngen. exe z adresáře obsahujícího sestavení, nebo zadání úplné cesty.

Příklady týkající se služby nativních bitových kopií naleznete v tématu [Native Image Service](#native-image-service).

## <a name="native-image-task"></a>Úloha pro nativní bitové kopie

Úloha nativní bitové kopie je úloha systému Windows, která generuje a udržuje nativní bitové kopie. Úloha nativní bitové kopie generuje a obnoví nativní bitové kopie automaticky pro podporované scénáře. Umožňuje také instalačním nástrojům použít [Ngen. exe (generátor nativních bitových kopií)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) k vytváření a aktualizaci nativních imagí v odloženém čase.

Úloha nativní bitové kopie je zaregistrovaná jednou pro každou architekturu procesoru podporovanou v počítači, aby se povolila kompilace pro aplikace cílené na jednotlivé architektury:

|Název úlohy|32 – bitový počítač|64 – bitový počítač|
|---------------|----------------------|----------------------|
|Rozhraní .NET Framework NGEN v 4.0.30319|Ano|Ano|
|Rozhraní .NET Framework NGEN v 4.0.30319 64|Ne|Ano|

Úloha nativní bitové kopie je k dispozici v .NET Framework 4,5 a novějších verzích při použití v systému Windows 8 nebo novějším. V dřívějších verzích Windows používá .NET Framework [službu nativních bitových kopií](#native-image-service).

### <a name="task-lifetime"></a>Doba života úlohy

Obecně platí, že Windows Plánovač úloh spustí úlohu nativní bitové kopie každou noc, když je počítač nečinný. Úkol vyhledá všechny odložené práce, které jsou zařazené do fronty instalačními programy aplikací, všechny odložené požadavky na aktualizaci nativních imagí a jakékoli automatické vytváření imagí. Úkol dokončí nedokončené pracovní položky a pak se ukončí. Pokud se počítač zastaví v nečinnosti, zatímco je úloha spuštěná, úloha se zastaví.

Můžete také spustit úlohu nativní bitové kopie ručně prostřednictvím uživatelského rozhraní Plánovač úloh nebo ručním voláním nástroje NGen. exe. Pokud je úloha spuštěná kteroukoli z těchto metod, bude pokračovat v provozu, i když počítač přestane být nečinný. Image vytvořené ručně pomocí nástroje NGen. exe jsou upřednostňovány, aby umožňovaly předvídatelné chování pro instalační programy aplikací.

## <a name="native-image-service"></a>Nativní bitová kopie služby

Nativní Image Service je služba systému Windows, která generuje a udržuje nativní bitové kopie. Nativní Image Service umožňuje vývojářům odložit instalaci a aktualizaci nativních imagí na období, kdy je počítač nečinný.

Za normálních okolností je nativní Image Service inicializovaná instalačním programem (instalační program) pro aplikaci nebo aktualizaci. U akcí s prioritou 3 se služba spouští během nečinnosti počítače. Služba ukládá svůj stav a v případě potřeby může pokračovat v několika restartováních. Více kompilací obrázků lze zařadit do fronty.

Služba také komunikuje s ručním příkazem Ngen. exe. Ruční příkazy mají přednost před aktivitou na pozadí.

> [!NOTE]
> V systému Windows Vista je název zobrazený pro nativní Image Service "Microsoft.NET Framework NGEN v 2.0.50727 _X86" nebo "Microsoft.NET Framework NGEN v 2.0.50727 _X64". Ve všech starších verzích Microsoft Windows se jedná o název ".NET runtime Optimization Service v 2.0.50727 _X86" nebo ".NET runtime Optimization Service v 2.0.50727 _X64".

### <a name="launching-deferred-operations"></a>Spouštění odložených operací

Než začnete s instalací nebo upgradem, doporučujeme pozastavit službu. Tím se zajistí, že se služba nespustí, zatímco instalační program kopíruje soubory nebo umísťují sestavení do globální mezipaměti sestavení (GAC). Následující příkazový řádek nástroje Ngen. exe pozastaví službu:

```console
ngen queue pause
```

Když jsou všechny odložené operace zařazené do fronty, následující příkaz umožní službě obnovit:

```console
ngen queue continue
```

Chcete-li při instalaci nové aplikace nebo při aktualizaci sdílené součásti odložit generování nativních imagí, `/queue` použijte možnost `install` s akcemi nebo `update` . Následující příkazové řádky nástroje Ngen. exe nainstalují nativní bitovou kopii pro sdílenou součást a provedou aktualizaci všech kořenových složek, které mohly být ovlivněny:

```console
ngen install MyComponent /queue
ngen update /queue
```

Akce znovu vygeneruje všechny neověřené nativní bitové kopie, nikoli jenom ty, které používají `MyComponent`. `update`

Pokud se vaše aplikace skládá z mnoha kořenů, můžete řídit prioritu odložených akcí. Následující příkazy zařadí do fronty instalaci tří kořenů. `Assembly1`je nainstalovaná jako první, bez čekání na dobu nečinnosti. `Assembly2`je nainstalována i bez čekání na čas nečinnosti, ale po dokončení všech akcí s prioritou 1. `Assembly3`se nainstaluje, když služba zjistí, že je počítač nečinný.

```console
ngen install Assembly1 /queue:1
ngen install Assembly2 /queue:2
ngen install Assembly3 /queue:3
```

Můžete vynutit, aby se akce zařazené do fronty probíhaly `executeQueuedItems` synchronně pomocí akce. Pokud zadáte volitelnou prioritu, tato akce ovlivní pouze akce zařazené do fronty, které mají stejnou nebo nižší prioritu. Výchozí priorita je 3, takže následující příkaz Ngen. exe zpracuje všechny akce zařazené do fronty hned a nevrátí, dokud nebudou dokončeny:

```console
ngen executeQueuedItems
```

Synchronní příkazy jsou spouštěny pomocí nástroje Ngen. exe a nepoužívají službu nativních bitových kopií. Můžete provést akce pomocí nástroje Ngen. exe, když je spuštěná nativní Image Service.

### <a name="service-shutdown"></a>Vypnutí služby

Po spuštění příkazu Ngen. exe, který obsahuje `/queue` možnost, je služba spuštěna na pozadí, dokud nebudou dokončeny všechny akce. Služba ukládá svůj stav, takže v případě potřeby může pokračovat v několika restartováních. Pokud služba zjistí, že žádné další akce nejsou zařazeny do fronty, obnoví její stav tak, aby se při příštím spuštění počítače nerestartoval a pak se sám ukončí.

### <a name="service-interaction-with-clients"></a>Interakce služby s klienty

V .NET Framework verze 2,0 je jediná interakce s nativní imagí pomocí nástroje příkazového řádku Ngen. exe. Použijte nástroj příkazového řádku v instalačních skriptech k zařazení akcí do fronty pro službu nativních bitových kopií a pro interakci se službou.

## <a name="see-also"></a>Viz také:

- [Nástroje](../../../docs/framework/tools/index.md)
- [Proces spravovaného spuštění](../../standard/managed-execution-process.md)
- [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
