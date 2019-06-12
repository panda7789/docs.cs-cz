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
ms.openlocfilehash: fd1773b184b9ea39b83b91c139acb09658beae11
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2019
ms.locfileid: "66832824"
---
# <a name="ngenexe-native-image-generator"></a>Ngen.exe (generátor nativních obrázků)

Generátor nativních bitových kopií (Ngen.exe) je nástroj zvyšující výkon spravovaných aplikací. Nástroj Ngen.exe vytváří nativní bitové kopie, což jsou soubory obsahující zkompilovaný strojový kód specifický pro procesor, a instaluje je do mezipaměti nativních bitových kopií v místním počítači. Modul runtime může ke kompilaci původního sestavení použít nativní bitové kopie z mezipaměti namísto kompilátoru JIT (just-in-time).

Změny Ngen.exe v rozhraní .NET Framework 4:

- Nástroj Ngen.exe nyní kompiluje sestavení s úplnou důvěryhodností, přičemž zabezpečení přístupu kódu (CAS) již není vyhodnocováno.

- Nativní bitové kopie generované nástrojem Ngen.exe již nemohou být načteny do aplikací spuštěných s částečnou důvěryhodností.

Změny nástroje Ngen.exe v rozhraní .NET Framework verze 2.0:

- Instalace sestavení nainstaluje také jeho závislosti, což zjednodušuje syntaxi nástroje Ngen.exe.

- Nativní bitové kopie mohou být nyní sdíleny napříč doménami aplikací.

- Nová akce `update`, znovu vytvoří bitové kopie, které byly zneplatněny.

- Pro generování a instalaci bitových kopií může být spuštění akcí odloženo službou využívající dobu nečinnosti.

- Některé příčiny zneplatnění bitové kopie byly odstraněny.

V systému Windows 8 naleznete v tématu [Native Image Task](#native-image-task).

Další informace o použití Ngen.exe a službu nativních bitových kopií naleznete v tématu [Native Image Service](#native-image-service).

> [!NOTE]
> Syntaxe Ngen.exe pro verze 1.0 a 1.1 rozhraní .NET Framework lze nalézt v [Native Image Generator (Ngen.exe) Legacy Syntax](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms165073(v=vs.100)).

Tento nástroj je automaticky nainstalován se sadou Visual Studio. Ke spuštění nástroje, použijte příkazový řádek pro vývojáře pro Visual Studio (nebo příkazový řádek Visual Studio ve Windows 7). Další informace najdete v tématu [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md).

V příkazovém řádku zadejte následující:

## <a name="syntax"></a>Syntaxe

```
ngen action [options]
```

```
ngen /? | /help
```

## <a name="actions"></a>Akce

Následující tabulka ukazuje syntaxi každé `action`. Popisy jednotlivých částí `action`, najdete v článku [argumenty](#ArgumentTable), [úrovně Priority](#PriorityTable), [scénáře](#ScenarioTable), a [Config](#ConfigTable)tabulky. [Možnosti](#OptionTable) tabulka popisuje `options` a přepínače nápovědy.

|Akce|Popis|
|------------|-----------------|
|`install` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`] [`/queue`[`:`{`1`&#124;`2`&#124;`3`}]]|Vygeneruje nativní bitové kopie sestavení a jeho závislosti a nainstaluje bitové kopie do mezipaměti nativních bitových kopií.<br /><br /> Pokud `/queue` není zadána, akce je zařazena do fronty pro službu nativních bitových kopií. Výchozí hodnota priority je 3. Zobrazit [úrovně Priority](#PriorityTable) tabulky.|
|`uninstall` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`]|Odstraní nativní bitové kopie sestavení a jeho závislosti z mezipaměti nativních bitových kopií.<br /><br /> Chcete-li odinstalovat pouze jednu bitovou kopii a její závislosti, použijte stejné argumenty příkazového řádku, které byly použity při instalaci kopie. **Poznámka:**  Od verze rozhraní .NET Framework 4, akce `uninstall` * se už nepodporuje.|
|`update` [`/queue`]|Aktualizuje nativní bitové kopie, které se staly neplatnými.<br /><br /> Pokud `/queue` není zadána, aktualizace jsou zařazeny do fronty pro službu nativních bitových kopií. Aktualizace jsou vždy naplánovány s prioritou 3, jsou tedy spouštěny při nečinnosti počítače.|
|`display` [`assemblyName` &#124; `assemblyPath`]|Zobrazí stav nativních bitových kopií pro sestavení a jeho závislosti.<br /><br /> Není-li zadán žádný argument, je zobrazen celý obsah mezipaměti nativních bitových kopií.|
|`executeQueuedItems` [<code>1&#124;2&#124;3</code>]<br /><br /> -nebo-<br /><br /> `eqi` [1&#124;2&#124;3]|Spustí úlohy kompilace ve frontě.<br /><br /> Je-li zadána priorita, jsou spuštěny úlohy kompilace s větší nebo shodnou prioritou. Není-li priorita zadána, jsou spuštěny všechny úlohy kompilace.|
|`queue` {`pause` &#124; `continue` &#124; `status`}|Pozastaví službu nativních bitových kopií, umožní pozastavené službě pokračovat nebo se dotáže na stav služby.|

<a name="ArgumentTable"></a>

## <a name="arguments"></a>Arguments

|Argument|Popis|
|--------------|-----------------|
|`assemblyName`|Plný zobrazovaný název sestavení. Například, `"myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5"`. **Poznámka:**  Lze zadat částečný název sestavení, například `myAssembly`, pro `display` a `uninstall` akce. <br /><br /> V jednom příkazovém řádku nástroje Ngen.exe lze zadat pouze jedno sestavení.|
|`assemblyPath`|Explicitní cesta k sestavení. Lze zadat úplnou nebo relativní cestu.<br /><br /> Zadáte-li název souboru bez cesty, musí se sestavení nacházet v aktuálním adresáři.<br /><br /> V jednom příkazovém řádku nástroje Ngen.exe lze zadat pouze jedno sestavení.|

<a name="PriorityTable"></a>

## <a name="priority-levels"></a>Úrovně priority

|Priorita|Popis|
|--------------|-----------------|
|`1`|Nativní bitové kopie jsou generovány a nainstalovány okamžitě, nečeká se na nečinnost počítače.|
|`2`|Nativní bitové kopie jsou generovány a instalovány bez čekání na nečinnost počítače, ale až po dokončení všech akcí s prioritou 1 (a jejich závislostí).|
|`3`|Nativní bitové kopie jsou nainstalovány ve chvíli, kdy služba nativních bitových kopií zjistí, že je počítač nečinný. Zobrazit [službu nativních bitových kopií](#native-image-service).|

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
|`/ExeConfig:``exePath`|Použije konfiguraci zadaného spustitelného sestavení.<br /><br /> Při vytváření vazeb na závislosti musí nástroj Ngen.exe učinit stejná rozhodnutí jako zavaděč. Pokud sdílená komponenta načtena za běhu, pomocí <xref:System.Reflection.Assembly.Load%2A> metoda, konfigurační soubor aplikace určí závislosti, která jsou načtena pro sdílenou komponentu – například verzi načtené závislosti. `/ExeConfig` Přepínač poskytuje Ngen.exe pokyny, na které závislosti budou načteny za běhu.|
|`/AppBase:``directoryPath`|Při hledání závislostí aplikace použije jako základ cesty zadaný adresář.|

<a name="OptionTable"></a>

## <a name="options"></a>Možnosti

|Možnost|Popis|
|------------|-----------------|
|`/nologo`|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|
|`/silent`|Potlačí zobrazování zpráv o úspěchu.|
|`/verbose`|Zobrazí podrobné informace o ladění. **Poznámka:**  Vzhledem k omezením operačního systému tato možnost nezobrazí dodatečných informací o Windows 98 a Windows Millennium Edition.|
|`/help`, `/?`|Zobrazí syntaxi příkazu a možnosti aktuální verze.|

## <a name="remarks"></a>Poznámky

Chcete-li spustit nástroj Ngen.exe, je zapotřebí mít oprávnění správce.

> [!CAUTION]
> Nástroj Ngen.exe nespouštějte pro sestavení, která nemají plnou důvěryhodnost. Od verze rozhraní .NET Framework 4, Ngen.exe kompiluje sestavení s úplným vztahem důvěryhodnosti a zásady (CAS) zabezpečení přístupu kódu už nevyhodnocuje.

Od verze rozhraní .NET Framework 4, nativní bitové kopie generované nástrojem Ngen.exe již být načteny do aplikací, na kterých běží v částečném vztahu důvěryhodnosti. Namísto toho je vyvolán kompilátor za běhu (JIT).

Ngen.exe vytváří nativní bitové kopie pro sestavení určené parametrem `assemblyname` argument `install` akce a všechny jeho závislosti. Závislosti se stanoví z odkazů v manifestu sestavení. Jediný scénář, ve které je potřeba nainstalovat závislost odděleně se při načtení aplikace, například pomocí reflexe, voláním <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody.

> [!IMPORTANT]
> Nepoužívejte <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metodu s nativní bitové kopie. Bitovou kopii zavedenou touto metodou nelze v kontextu spuštění používat jinými sestaveními.

Nástroj Ngen.exe udržuje počet odkazů na závislosti. Předpokládejme například, že `MyAssembly.exe` a `YourAssembly.exe` současně nainstalovány v mezipaměti nativních bitových kopií a obě mají odkazy na `OurDependency.dll`. Pokud `MyAssembly.exe` odinstalaci `OurDependency.dll` nebude odinstalován. Je jenom odebrány při `YourAssembly.exe` je odinstalována také.

Pokud generujete nativní bitovou kopii pro sestavení v globální mezipaměti sestavení (GAC), zadejte její zobrazovaný název. Viz <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>.

Nativní bitové kopie, které generuje Ngen.exe, mohou být sdíleny napříč doménami aplikace. To znamená, že nástroj Ngen.exe lze použít ve scénářích aplikací, které vyžadují, aby byla sestavení sdílena napříč doménami aplikace. Určení neutrality domény:

- Použít <xref:System.LoaderOptimizationAttribute> své aplikace atribut.

- Nastavte <xref:System.AppDomainSetup.LoaderOptimization%2A?displayProperty=nameWithType> vlastnost při vytváření nastavení informace pro novou doménu aplikace.

Vždy je třeba použít doménově neutrální kód, pokud je dané sestavení načítáno do více domén aplikace. Pokud je nativní bitová kopie načtena do nesdílené domény aplikace poté, co byla načtena do sdílené domény, nelze ji použít.

> [!NOTE]
> Doménově neutrální kód nemůže být uvolněn a výkon může být mírně snížen, zvláště při přistupování ke statickým členům.

V této části Poznámky:

- [Generování bitových kopií pro různé scénáře](#Scenarios)

- [Určení, kdy použít nativní bitové kopie](#WhenToUse)

  - [Lepší využití paměti](#Memory)

  - [Rychlejší spuštění aplikace](#Startup)

  - [Souhrnné informace o použití](#UsageSummary)

- [Důležitost základních adres sestavení](#BaseAddresses)

- [Pevné vazby](#HardBinding)

  - [Určení pokynu vazby pro závislost](#DependencyHint)

  - [Určení pokynu výchozí vazby pro sestavení](#AssemblyHint)

- [Odložené zpracování](#Deferred)

- [Nativní bitové kopie a JIT kompilace](#JITCompilation)

  - [Neplatné bitové kopie](#InvalidImages)

- [Odstraňování potíží](#Troubleshooting)

  - [Assembly Binding Log Viewer](#Fusion)

  - [JITCompilationStart Pomocník spravovaného ladění](#MDA)

  - [Výslovné odhlášení z generování nativních bitových kopií](#OptOut)

<a name="Scenarios"></a>

## <a name="generating-images-for-----different-scenarios"></a>Generování bitových kopií pro různé scénáře

Po vygenerování nativní bitové kopie pro sestavení, modul runtime automaticky pokusí vyhledat a použít tuto nativní bitovou kopii při každém spuštění sestavení. V závislosti na scénáři lze generovat více bitových kopií.

Například při spuštění sestavení ve scénáři ladění nebo profilování, modul runtime vyhledá nativní bitovou kopii, která byla vygenerována s `/Debug` nebo `/Profile` možnosti. Pokud nemůže najít odpovídající nativní bitovou kopii, vrátí se modul runtime ke standardní JIT kompilaci. Vytvoření nativní bitové kopie s je jediný způsob, jak ladit nativní bitové kopie `/Debug` možnost.

`uninstall` Akce také rozpoznává scénáře, takže můžete odinstalovat všechny scénáře nebo pouze vybrané scénáře.

<a name="WhenToUse"></a>

## <a name="determining-when-to-use-native-images"></a>Určení, kdy použít nativní bitové kopie

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
> Před rozhraní .NET Framework 3.5 Service Pack 1 byste měli umístit sdílené se silným názvem součásti v globální mezipaměti sestavení, protože zavaděč sestavení se silným názvem, které nejsou v globální mezipaměti sestavení, čímž provádí ověřování navíc všechna zlepšení času spuštění získaná použitím nativních bitových kopií. Optimalizace představené v rozhraní .NET Framework 3.5 SP1 odebrat tato ověřování.

<a name="UsageSummary"></a>

### <a name="summary-of-usage-considerations"></a>Souhrnné informace o použití

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

## <a name="hard-binding"></a>Pevné vazby

Pevné vazby zvyšují propustnost a snižují velikost pracovní sady pro nativní bitové kopie. Nevýhodou pevné vazby je, že všechny bitové kopie, které jsou pevně vázány na sestavení, musí být načteny při načtení sestavení. To u velkých aplikací může výrazně prodloužit spouštění.

Pevná vazba je vhodná pro závislosti, které jsou načteny ve všech scénářích aplikace, u kterých velmi záleží na výkonu. Stejně jako u jakéhokoli jiného aspektu použití nativní bitové kopie je měření výkonu jediným způsobem, jak určit, zda pevná vazba zlepšuje výkon vaší aplikace.

<xref:System.Runtime.CompilerServices.DependencyAttribute> a <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> atributy umožňují poskytovat Ngen.exe pevné vazby.

> [!NOTE]
> Tyto atributy jsou informace pro Ngen.exe, nikoli příkazy. Jejich použití nezaručuje pevné vazby. V budoucích verzích se může změnit význam těchto atributů.

<a name="DependencyHint"></a>

### <a name="specifying-a-binding-hint-for-a-dependency"></a>Určení pokynu vazby pro závislost

Použít <xref:System.Runtime.CompilerServices.DependencyAttribute> sestavení k označení pravděpodobnost, že určená závislost bude načtena. <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> Označuje, že pevná vazba je vhodná, <xref:System.Runtime.CompilerServices.LoadHint.Default> označuje, že má být použita výchozí hodnota pro závislost, a <xref:System.Runtime.CompilerServices.LoadHint.Sometimes> označuje, že pevná vazba není vhodná.

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

### <a name="specifying-a-default-binding-hint-for-an-assembly"></a>Určení pokynu výchozí vazby pro sestavení

Výchozí pokyny pro vazby jsou zapotřebí pouze pro sestavení, která budou použita okamžitě a často aplikací, která na nich závisí. Použít <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> s <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> na taková sestavení k určení, že má být použit pevné vazby.

> [!NOTE]
> Neexistuje žádný důvod použít <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> na .dll sestavení, které nespadají do této kategorie, protože použití atributu s jinou hodnotou než <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> má stejný účinek jako vynechání atributu vůbec.

Společnost Microsoft používá <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> k určení, že pevná vazba je výchozí nastavení pro velmi malý počet sestavení v rozhraní .NET Framework, jako například mscorlib.dll.

<a name="Deferred"></a>

## <a name="deferred-processing"></a>Odložené zpracování

Generování nativních bitových kopií pro velmi velké aplikace může být časově náročné. Obdobně změny sdílené komponenty nebo změny nastavení počítače mohou vyžadovat aktualizaci mnoha nativních bitových kopií. `install` a `update` mají akce `/queue` možnost, která se zařadí do fronty operace k odloženému spuštění službou nativních bitových kopií. Kromě toho má Ngen.exe `queue` a `executeQueuedItems` akce, které poskytuje určitou kontrolu nad službu. Další informace najdete v tématu [Native Image Service](#native-image-service).

<a name="JITCompilation"></a>

## <a name="native-images-and-jit-compilation"></a>Nativní bitové kopie a JIT kompilace

Pokud Ngen.exe v sestavení zaznamená jakékoli metody, které neumí generovat, vyloučí je z nativní bitové kopie. Jakmile modul runtime spustí toto sestavení, vrátí se k JIT kompilaci pro ty metody, které nejsou zahrnuty v nativní bitové kopii.

Kromě toho nejsou nativní bitové kopie použity v případě, že bylo sestavení inovováno, nebo pokud byla bitová kopie z jakéhokoliv důvodu zneplatněna.

<a name="InvalidImages"></a>

### <a name="invalid-images"></a>Neplatné bitové kopie

Při použití nástroje Ngen.exe pro vytvoření nativní bitové kopie sestavení závisí výstup na zadaných možnostech příkazového řádku a určitých nastaveních počítače. Mezi tato nastavení patří následující:

- Verze rozhraní .NET Framework.

- Verze operačního systému, pokud je změna z řady Windows 9 x na řadu Windows NT.

- Přesná identita sestavení (rekompilace identitu mění).

- Přesná identita všech sestavení, na které sestavení odkazuje (rekompilace identitu mění).

- Bezpečnostní faktory.

Nástroj Ngen.exe zaznamenává tyto informace při generování nativní bitové kopie. Po spuštění sestavení modul runtime hledá nativní bitovou kopii vytvořenou s možnostmi a nastavením, které odpovídají aktuálnímu prostředí počítače. Modul runtime se vrátí k JIT kompilaci sestavení, pokud nemůže najít odpovídající nativní bitovou kopii. Následující změny nastavení a prostředí počítače způsobí zneplatnění nativních bitových kopií:

- Verze rozhraní .NET Framework.

     Pokud použijete aktualizaci rozhraní .NET Framework, všechny nativní bitové kopie, které jste vytvořili pomocí Ngen.exe, se zneplatní. Z tohoto důvodu všechny aktualizace rozhraní .NET Framework spustit `Ngen Update` příkazu, ujistěte se, že všechny nativní bitové kopie budou znovu vygenerovány. Rozhraní .NET Framework automaticky vytvoří nové nativní bitové kopie pro knihovny rozhraní .NET Framework, které nainstaluje.

- Verze operačního systému, pokud je změna z řady Windows 9 x na řadu Windows NT.

     Například pokud verze operačního systému spuštěného na počítači změní z Windows 98 na Windows XP, všechny nativní bitové kopie, které jsou uložené v mezipaměti nativní bitové kopie se zneplatní. Nicméně pokud operační systém změní z Windows 2000 na Windows XP, bitové kopie nejsou zneplatněny.

- Přesná identita sestavení.

     Pokud je provedena rekompilace sestavení, odpovídající nativní bitové kopie se stanou neplatnými.

- Přesná identita všech sestavení, na která sestavení odkazuje.

     Pokud aktualizujete spravované sestavení, všechny nativní bitové kopie, které přímo nebo nepřímo závisí na tomto sestavení, se zneplatní a musí být znovu vygenerovány. To zahrnuje jak běžné odkazy, tak pevně vázané závislosti. Pokaždé, když je aplikována aktualizace softwaru, by se měl spustit instalační program `Ngen Update` příkaz, kterým zajistíte, že všechny závislé nativní bitové kopie budou znovu vygenerovány.

- Bezpečnostní faktory.

     Změna zásad zabezpečení počítače směřující k omezení dříve udělených oprávnění sestavení může způsobit, že se dříve zkompilované nativní bitové kopie sestavení stanou neplatnými.

     Podrobné informace o tom, jak modul CLR spravuje bezpečnost přístupu kódu a jak použít oprávnění najdete v tématu [zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security.md).

<a name="Troubleshooting"></a>

## <a name="troubleshooting"></a>Poradce při potížích

Následující témata odstraňování problémů umožňují zobrazit, které nativní bitové kopie se používají a které nelze použít v aplikaci, můžete určit, kdy začne ke kompilaci metody kompilátor JIT a ukazuje, jak se odhlásit ze sestavování nativních bitových kopií zadaný metody.

<a name="Fusion"></a>

### <a name="assembly-binding-log-viewer"></a>vazba sestavení – prohlížeč protokolu

Potvrďte, že se nativní bitové kopie slouží v aplikaci, můžete použít [Fuslogvw.exe (Assembly Binding Log Viewer)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md). Vyberte **nativní bitové kopie** v **kategorie protokolu** pole v okně prohlížeče protokolu vazeb. Fuslogvw.exe poskytuje informace o důvodu, proč byla nativní bitová kopie odmítnuta.

<a name="MDA"></a>

### <a name="the-jitcompilationstart-managed-debugging-assistant"></a>JITCompilationStart Pomocník spravovaného ladění

Můžete použít [jitCompilationStart](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md) pomocníka spravovaného ladění (MDA) k určení, kdy začne kompilátor JIT kompilovat funkci.

<a name="OptOut"></a>

### <a name="opting-out-of-native-image-generation"></a>Výslovné odhlášení z generování nativních bitových kopií

NGen.exe v některých případech může mít potíže při generování, které nativních bitových kopií pro konkrétní metody, ale možná dáte přednost, že metoda být kompilována JIT místo toho potom zkompiluje nativních bitových kopií. V takovém případě můžete použít `System.Runtime.BypassNGenAttribute` atribut zabránit NGen.exe generuje nativní bitové kopie pro konkrétní metody. Atribut musí být použit jednotlivě pro každou metodu, jejíž kód nechcete zahrnout do nativních bitových kopií. NGen.exe rozpozná atribut a nevygeneruje žádný kód v nativních bitových kopií pro odpovídající metody.

Upozorňujeme, že `BypassNGenAttribute` není definován jako typ v knihovně tříd rozhraní .NET Framework. Aby bylo možné využívat atribut ve vašem kódu, je nutné definovat ho následujícím způsobem:

[!code-csharp[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#1)]
[!code-vb[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#1)]

Atribut lze následně použít na základě-method. Následující příklad nastaví Native Image Generator, že by neměla generovat nativních bitových kopií pro `ExampleClass.ToJITCompile` metody.

[!code-csharp[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#2)]
[!code-vb[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#2)]

## <a name="examples"></a>Příklady

Následující příkaz vytvoří nativní bitovou kopii pro `ClientApp.exe`nachází v aktuálním adresáři a nainstaluje bitovou kopii v mezipaměti nativních bitových kopií. Pokud pro sestavení existuje soubor nastavení, Ngen.exe jej použije. Kromě toho nativní bitové kopie jsou generovány pro všechny soubory .dll, který `ClientApp.exe` odkazy.

```
ngen install ClientApp.exe
```

Bitová kopie nainstalovaná pomocí Ngen.exe se také nazývá kořen. Kořen může být aplikace nebo sdílená komponenta.

Následující příkaz vytvoří nativní bitovou kopii pro `MyAssembly.exe` se zadanou cestou.

```
ngen install c:\myfiles\MyAssembly.exe
```

Při hledání sestavení a jejich závislosti používá Ngen.exe stejnou logiku při zjišťování, jaká je použita u Common Language Runtime (CLR). Ve výchozím adresáři, který obsahuje `ClientApp.exe` slouží jako základní adresář aplikace a veškeré zjišťování sestavení začíná v tomto adresáři. Toto chování můžete přepsat pomocí `/AppBase` možnost.

> [!NOTE]
> Jde o změnu oproti chování nástroje Ngen.exe v rozhraních .NET Framework verze 1.0 a 1.1, kde základ cesty aplikace je nastaven na aktuální adresář.

Sestavení může mít závislost bez odkazu, například pokud načte soubor .dll pomocí <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody. Můžete vytvořit nativní bitovou kopii pro takový soubor .dll pomocí konfigurační informace pro sestavení aplikace s `/ExeConfig` možnost. Následující příkaz vytvoří nativní bitovou kopii pro `MyLib.dll,` pomocí konfiguračních informací z `MyApp.exe`.

```
ngen install c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe
```

Při odebrání aplikace nebudou odebrána sestavení nainstalovaná tímto způsobem.

Chcete-li odinstalovat závislost, použijte stejné možnosti příkazového řádku, které byly použity k její instalaci. Následující příkaz odinstaluje `MyLib.dll` z předchozího příkladu.

```
ngen uninstall c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe
```

Chcete-li vytvořit nativní bitovou kopii pro sestavení v globální mezipaměti sestavení (GAC), použijte zobrazovaný název sestavení. Příklad:

```
ngen install "ClientApp, Version=1.0.0.0, Culture=neutral,
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"
```

NGen.exe vytváří samostatnou sadu bitových kopií pro každý scénář, který instalujete. Například následující příkazy nainstalují kompletní sadu nativních bitových kopií pro normální provoz, jinou kompletní sadu pro ladění a třetí pro profilování:

```
ngen install MyApp.exe
ngen install MyApp.exe /debug
ngen install MyApp.exe /profile
```

### <a name="displaying-the-native-image-cache"></a>Zobrazení mezipaměti nativních bitových kopií

Jakmile jsou nativní bitové kopie nainstalovány v mezipaměti, lze je zobrazit pomocí nástroje Ngen.exe. Následující příkaz zobrazí všechny nativní bitové kopie v mezipaměti nativních bitových kopií.

```
ngen display
```

`display` Seznamy akcí všechna kořenová sestavení nejprve následovaný seznamem všech nativních bitových kopií v počítači.

Chcete-li zobrazit pouze informace o sestavení, použijte jeho jednoduchý název. Následující příkaz zobrazí všechny nativní bitové kopie v mezipaměti nativních bitových kopií, které se shodují v částečném názvu `MyAssembly`, jejich závislostech a všech kořenech majících závislost na `MyAssembly`:

```
ngen display MyAssembly
```

Znalost, které kořeny závisí na sdíleném sestavení komponenty je užitečná při měření dopadu `update` akce po upgradu sdílené komponenty.

Zadáte-li příponu souboru sestavení, musí být buď zadána cesta, nebo spuštěn nástroj Ngen.exe z adresáře obsahujícího sestavení:

```
ngen display c:\myApps\MyAssembly.exe
```

Následující příkaz zobrazí všechny nativní bitové kopie v mezipaměti nativních bitových kopií s názvem `MyAssembly` a verzi 1.0.0.0.

```
ngen display "myAssembly, version=1.0.0.0"
```

### <a name="updating-images"></a>Aktualizace bitových kopií

Bitové kopie jsou obvykle aktualizovány po upgradu sdílené komponenty. Chcete-li aktualizovat všechny nativní bitové kopie, které se změnily, nebo se změnily jejich závislosti, použijte `update` akce bez argumentů.

```
ngen update
```

Aktualizace všech bitových kopií může být časově náročný proces. Aktualizace pro spuštění službou nativních bitových kopií může fronty pomocí `/queue` možnost. Další informace o `/queue` možnost a instalačních prioritách naleznete v tématu [Native Image Service](#native-image-service).

```
ngen update /queue
```

### <a name="uninstalling-images"></a>Odinstalování bitových kopií

Nástroj Ngen.exe udržuje seznam závislostí, takže sdílené komponenty jsou odstraněny pouze v případě, že byla odebrána všechna sestavení, která na nich závisí. Kromě toho, pokud byla sdílená komponenta nainstalována jako kořen, nebude odstraněna.

Následující příkaz odinstaluje všechny scénáře kořenu `ClientApp.exe`:

```
ngen uninstall ClientApp
```

`uninstall` Akce slouží k odebrání konkrétních scénářů. Následující příkaz odinstaluje všechny ladicí scénáře pro `ClientApp.exe`:

```
ngen uninstall ClientApp /debug
```

> [!NOTE]
> Odinstalace `/debug` scénáře neodinstaluje scénáře zahrnující současně obě `/profile` a `/debug.`

Následující příkaz odinstaluje všechny scénáře pro konkrétní verzi `ClientApp.exe`:

```
ngen uninstall "ClientApp, Version=1.0.0.0"
```

Následující příkaz odinstaluje všechny scénáře pro `"ClientApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL",` nebo pouze jeho ladicí scénář pro toto sestavení:

```
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL" /debug
```

Stejně jako u `install` akce zadání přípony zapotřebí buď spuštění Ngen.exe z adresáře obsahujícího sestavení, nebo zadání úplné cesty.

Příklady pro službu nativních bitových kopií naleznete v tématu [Native Image Service](#native-image-service).

## <a name="native-image-task"></a>Úloha pro nativní bitové kopie

Úloha pro nativní bitové kopie je Windows úlohu, která vytváří a udržuje nativní bitové kopie. Úloha pro nativní bitové kopie vygeneruje a uvolní nativních bitových kopií automaticky pro podporované scénáře. Umožňuje také instalační programy používat [Ngen.exe (Generátor nativních obrázků)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) vytvářet a aktualizovat nativní bitové kopie odložené najednou.

Úloha pro nativní bitové kopie je zaregistrovaný jednou pro každý procesor architektury podporována v počítači, aby kompilace pro aplikace, které se zaměřují každou architekturu:

|Název úlohy|32bitový počítač|64bitový počítač|
|---------------|----------------------|----------------------|
|NET Framework NGEN v4.0.30319|Ano|Ano|
|NET Framework NGEN v4.0.30319 64|Ne|Ano|

Úloha pro nativní bitové kopie je k dispozici v rozhraní .NET Framework 4.5 a novější verze, při spouštění v systému Windows 8 nebo novější. Ve starších verzích Windows rozhraní .NET Framework používá [Native Image Service](#native-image-service).

### <a name="task-lifetime"></a>Doba života úkolu

Obecně platí Plánovač úloh Windows spustí úloha pro nativní bitové kopie každou noc, pokud je počítač nečinný. Úloha zkontroluje odložená práce, zařazených do fronty tak, že instalační programy aplikací, všechny žádosti o aktualizaci odložené nativních bitových kopií a vytvoření jakékoli automatické bitové kopie. Úloha dokončení nevyřízených pracovních položek a potom vypne. Pokud počítač přestane nečinnosti, zatímco úloha běží, zastaví úlohu.

Můžete spustit také úkol nativní bitové kopie ručně prostřednictvím uživatelského rozhraní plánovače úloh nebo ruční volání NGen.exe. Pokud úloha je spuštěna pomocí některé z těchto metod, budou spuštěny při nečinnosti počítače už. Bitové kopie ručně vytvořené pomocí NGen.exe budou mít vyšší prioritu, abyste umožnili předvídatelný chování pro instalační programy aplikací.

## <a name="native-image-service"></a>Nativní bitová kopie služby

Službu nativních bitových kopií je služba Windows, která vytváří a udržuje nativní bitové kopie. Službu nativních bitových kopií umožňuje vývojářům odložení instalace a aktualizace nativní bitové kopie do období při nečinnosti počítače.

Za normálních okolností instalačního programu (Instalační program) pro aplikace nebo aktualizace Inicializuje službu nativních bitových kopií. Pro akce prioritou 3 služba prováděla během doby nečinnosti počítače. Služba ukládá svůj stav a je schopný pokračováním prostřednictvím více restartování v případě potřeby. Více kompilace image můžete zařadit do fronty.

Služba také pracuje s ruční příkaz Ngen.exe. Ruční příkazy mají přednost před aktivitu na pozadí.

> [!NOTE]
> V systému Windows Vista je název zobrazený pro službu nativních bitových kopií "v2.0.50727_X86 NGEN Microsoft.NET Framework" nebo "Microsoft.NET Framework NGEN v2.0.50727_X64". Všechny starší verze systému Microsoft Windows název je "Služby .NET Runtime optimalizace v2.0.50727_X86" nebo "Služby .NET Runtime optimalizace v2.0.50727_X64".

### <a name="launching-deferred-operations"></a>Spouští se operace odložené

Před zahájením instalace nebo upgradu, se doporučuje pozastavení služby. Tím se zajistí, že služba nespustí při kopírování souborů instalačního programu nebo vložení sestavení do globální mezipaměti sestavení. Následující příkazový řádek Ngen.exe pozastaví službu:

```
ngen queue pause
```

Pokud všechny operace odložené byl zařazen do fronty, umožňuje následující příkaz na obnovení služby:

```
ngen queue continue
```

Chcete-li odložit generování nativních bitových kopií při instalaci nové aplikace nebo při aktualizaci sdílené komponenty, použijte `/queue` spolu s možností `install` nebo `update` akce. Následujících příkazových řádků Ngen.exe instalaci nativních bitových kopií pro sdílené komponenty a proveďte aktualizaci všechny kořenové adresáře, které může mít dopad:

```
ngen install MyComponent /queue
ngen update /queue
```

`update` Akce obnoví všechny nativní bitové kopie, které byly zneplatněny, nejen ty, které používají `MyComponent`.

Pokud vaše aplikace se skládá z mnoha kořeny, můžete určit prioritu odložené akce. Následující příkazy fronty instalace tři kořenové adresáře. `Assembly1` je nainstalována jako první, bez čekání na nečinnost. `Assembly2` je také nainstalovat bez čekací dobu nečinnosti, ale po dokončení všech akcí s prioritou 1. `Assembly3` je nainstalována, když služba zjistí, že je počítač nečinný.

```
ngen install Assembly1 /queue:1
ngen install Assembly2 /queue:2
ngen install Assembly3 /queue:3
```

Můžete vynutit zařazených do fronty akce neproběhne synchronně pomocí `executeQueuedItems` akce. Pokud zadáte volitelné prioritu, tato akce ovlivní pouze zařazených do fronty akce, které mají stejné nebo nižší prioritu. Výchozí hodnota priority je 3, tak příkaz Ngen.exe okamžitě zpracovává všechny akce ve frontě a nevrací až skončí:

```
ngen executeQueuedItems
```

Synchronní příkazy jsou spouštěny příkazem Ngen.exe a nepoužívejte službu nativních bitových kopií. Můžete provést akce pomocí Ngen.exe, zatímco se službou nativních bitových kopií.

### <a name="service-shutdown"></a>Vypnutí služby

Po iniciováno prováděním příkazu Ngen.exe, která zahrnuje `/queue` možnost, služba běží na pozadí dokud nejsou dokončeny všechny akce. Služba ukládá svůj stav tak, že můžete pokračovat až do více restartování v případě potřeby. Když služba zjistí, že neexistují žádné další akce ve frontě, obnoví svůj stav tak, aby nerestartuje při příštím spuštění počítače a pak ji vypne samotný.

### <a name="service-interaction-with-clients"></a>Služba interakci s klienty

V rozhraní .NET Framework verze 2.0 je pouze interakci se službou nativních bitových kopií pomocí příkazového řádku nástroje Ngen.exe. Pomocí nástroje příkazového řádku ve skriptů instalace pro akce fronty pro službu nativních bitových kopií a k interakci se službou.

## <a name="see-also"></a>Viz také:

- [Nástroje](../../../docs/framework/tools/index.md)
- [Proces spravovaného spuštění](../../../docs/standard/managed-execution-process.md)
- [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
