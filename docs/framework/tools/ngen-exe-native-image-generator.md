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
ms.openlocfilehash: f0811e32a9483238d1cd15084c19951075c8a36a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399539"
---
# <a name="ngenexe-native-image-generator"></a>Ngen.exe (generátor nativních obrázků)
Generátor nativních bitových kopií (Ngen.exe) je nástroj zvyšující výkon spravovaných aplikací. Nástroj Ngen.exe vytváří nativní bitové kopie, což jsou soubory obsahující zkompilovaný strojový kód specifický pro procesor, a instaluje je do mezipaměti nativních bitových kopií v místním počítači. Modul runtime může ke kompilaci původního sestavení použít nativní bitové kopie z mezipaměti namísto kompilátoru JIT (just-in-time).  
  
 Změny Ngen.exe v [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]:  
  
-   Nástroj Ngen.exe nyní kompiluje sestavení s úplnou důvěryhodností, přičemž zabezpečení přístupu kódu (CAS) již není vyhodnocováno.  
  
-   Nativní bitové kopie generované nástrojem Ngen.exe již nemohou být načteny do aplikací spuštěných s částečnou důvěryhodností.  
  
 Změny nástroje Ngen.exe v rozhraní .NET Framework verze 2.0:  
  
-   Instalace sestavení nainstaluje také jeho závislosti, což zjednodušuje syntaxi nástroje Ngen.exe.  
  
-   Nativní bitové kopie mohou být nyní sdíleny napříč doménami aplikací.  
  
-   Nová akce `update`, znovu vytvoří bitové kopie, které se zrušila platnost.  
  
-   Pro generování a instalaci bitových kopií může být spuštění akcí odloženo službou využívající dobu nečinnosti.  
  
-   Některé příčiny zneplatnění bitové kopie byly odstraněny.  
  
 V systému Windows 8, najdete v části [nativní bitové kopie úloh](http://msdn.microsoft.com/library/9b1f7590-4e0d-4737-90ef-eaf696932afb).  
  
 Další informace o používání Ngen.exe a služba nativních bitových kopií naleznete v části [nativní bitové kopie služby][Native Image Service].  
  
> [!NOTE]
>  Ngen.exe syntaxi pro verze 1.0 a 1.1 rozhraní .NET Framework naleznete v [generátor (Ngen.exe) zastaralé syntaxe](http://msdn.microsoft.com/library/5a69fc7a-103f-4afc-8ab4-606adcb46324).  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7). Další informace najdete v tématu [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ngen action [options]  
```  
  
```  
ngen /? | /help  
```  
  
## <a name="actions"></a>Akce  
 Následující tabulka ukazuje syntaxi jednotlivých `action`. Popis jednotlivých částí `action`, najdete v článku [argumenty](#ArgumentTable), [úroveň Priority](#PriorityTable), [scénáře](#ScenarioTable), a [konfigurace](#ConfigTable)tabulky. [Možnosti](#OptionTable) tabulce jsou popsány `options` a přepínače nápovědy.  
  
|Akce|Popis|  
|------------|-----------------|  
|`install` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`] [`/queue`[`:`{`1`&#124;`2`&#124;`3`}]]|Vygeneruje nativní bitové kopie sestavení a jeho závislosti a nainstaluje bitové kopie do mezipaměti nativních bitových kopií.<br /><br /> Pokud `/queue` je zadána akce ve frontě pro službu nativních bitových kopií. Výchozí hodnota priority je 3. Najdete v článku [úroveň Priority](#PriorityTable) tabulky.|  
|`uninstall` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`]|Odstraní nativní bitové kopie sestavení a jeho závislosti z mezipaměti nativních bitových kopií.<br /><br /> Chcete-li odinstalovat pouze jednu bitovou kopii a její závislosti, použijte stejné argumenty příkazového řádku, které byly použity při instalaci kopie. **Poznámka:** začínající [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], akce `uninstall` * již není podporována.|  
|`update` [`/queue`]|Aktualizuje nativní bitové kopie, které se staly neplatnými.<br /><br /> Pokud `/queue` není zadaný, aktualizace jsou zařazeny do fronty pro službu nativních bitových kopií. Aktualizace jsou vždy naplánovány s prioritou 3, jsou tedy spouštěny při nečinnosti počítače.|  
|`display` [`assemblyName` &#124; `assemblyPath`]|Zobrazí stav nativních bitových kopií pro sestavení a jeho závislosti.<br /><br /> Není-li zadán žádný argument, je zobrazen celý obsah mezipaměti nativních bitových kopií.|  
|`executeQueuedItems` [<code>1&#124;2&#124;3</code>]<br /><br /> -nebo-<br /><br /> `eqi` [1&#124;2&#124;3]|Spustí úlohy kompilace ve frontě.<br /><br /> Je-li zadána priorita, jsou spuštěny úlohy kompilace s větší nebo shodnou prioritou. Není-li priorita zadána, jsou spuštěny všechny úlohy kompilace.|  
|`queue` {`pause` &#124; `continue` &#124; `status`}|Pozastaví službu nativních bitových kopií, umožní pozastavené službě pokračovat nebo se dotáže na stav služby.|  
  
<a name="ArgumentTable"></a>   
## <a name="arguments"></a>Arguments  
  
|Argument|Popis|  
|--------------|-----------------|  
|`assemblyName`|Plný zobrazovaný název sestavení. Například `"myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5"`. **Poznámka:** můžete například zadat název částečného sestavení, `myAssembly`, pro `display` a `uninstall` akce. <br /><br /> V jednom příkazovém řádku nástroje Ngen.exe lze zadat pouze jedno sestavení.|  
|`assemblyPath`|Explicitní cesta k sestavení. Lze zadat úplnou nebo relativní cestu.<br /><br /> Zadáte-li název souboru bez cesty, musí se sestavení nacházet v aktuálním adresáři.<br /><br /> V jednom příkazovém řádku nástroje Ngen.exe lze zadat pouze jedno sestavení.|  
  
<a name="PriorityTable"></a>   
## <a name="priority-levels"></a>Úrovně priority  
  
|Priorita|Popis|  
|--------------|-----------------|  
|`1`|Nativní bitové kopie jsou generovány a nainstalovány okamžitě, nečeká se na nečinnost počítače.|  
|`2`|Nativní bitové kopie jsou generovány a instalovány bez čekání na nečinnost počítače, ale až po dokončení všech akcí s prioritou 1 (a jejich závislostí).|  
|`3`|Nativní bitové kopie jsou nainstalovány ve chvíli, kdy služba nativních bitových kopií zjistí, že je počítač nečinný. V tématu [nativních bitových kopií služby][Native Image Service].|  
  
<a name="ScenarioTable"></a>   
## <a name="scenarios"></a>Scénáře  
  
|Scénář|Popis|  
|--------------|-----------------|  
|`/Debug`|Vygeneruje nativní bitové kopie, které lze použít v ladicím programu.|  
|`/Profile`|Vygeneruje nativní bitové kopie, které lze použít v profileru.|  
|`/NoDependencies`|Vygeneruje minimální počet nativních bitových kopií požadovaný zadanými možnostmi scénáře.|  
  
<a name="ConfigTable"></a>   
## <a name="config"></a>Konfigurace  
  
|Konfigurace|Popis|  
|-------------------|-----------------|  
|`/ExeConfig:``exePath`|Použije konfiguraci zadaného spustitelného sestavení.<br /><br /> Při vytváření vazeb na závislosti musí nástroj Ngen.exe učinit stejná rozhodnutí jako zavaděč. Po načtení sdílená součást v době běhu pomocí <xref:System.Reflection.Assembly.Load%2A> metoda, konfigurační soubor aplikace určuje závislosti, které jsou načteny sdílená součást – například verzi závislostí, který je načten. `/ExeConfig` Přepínač poskytuje pokyny Ngen.exe, na kterém by závislosti načíst za běhu.|  
|`/AppBase:``directoryPath`|Při hledání závislostí aplikace použije jako základ cesty zadaný adresář.|  
  
<a name="OptionTable"></a>   
## <a name="options"></a>Možnosti  
  
|Možnost|Popis|  
|------------|-----------------|  
|`/nologo`|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|  
|`/silent`|Potlačí zobrazování zpráv o úspěchu.|  
|`/verbose`|Zobrazí podrobné informace o ladění. **Poznámka:** z důvodu omezení operačního systému, tato možnost nezobrazí tolik Další informace v systému Windows 98 a Windows Millennium Edition.|  
|`/help`, `/?`|Zobrazí syntaxi příkazu a možnosti aktuální verze.|  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li spustit nástroj Ngen.exe, je zapotřebí mít oprávnění správce.  
  
> [!CAUTION]
>  Nástroj Ngen.exe nespouštějte pro sestavení, která nemají plnou důvěryhodnost. Od verze [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]Ngen.exe zkompiluje sestavení s úplným vztahem důvěryhodnosti a zásady (CAS) zabezpečení přístupu kódu už nevyhodnocuje.  
  
 Od verze [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], nativní bitové kopie, které se generují s Ngen.exe již nebude možné načíst do aplikace, které jsou spuštěny v částečné důvěryhodnosti. Namísto toho je vyvolán kompilátor za běhu (JIT).  
  
 Ngen.exe generuje nativní bitové kopie pro sestavení určeného `assemblyname` argument `install` akce a všechny jeho závislé součásti. Závislosti se stanoví z odkazů v manifestu sestavení. Jediný scénář, ve kterém je potřeba instalovat samostatně závislost je při načtení aplikace pomocí reflexe, například voláním <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metoda.  
  
> [!IMPORTANT]
>  Nepoužívejte <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metoda s nativní bitové kopie. Bitovou kopii zavedenou touto metodou nelze v kontextu spuštění používat jinými sestaveními.  
  
 Nástroj Ngen.exe udržuje počet odkazů na závislosti. Předpokládejme například, `MyAssembly.exe` a `YourAssembly.exe` jsou nainstalovány v mezipaměť nativních bitových kopií a mohou mít odkazy na `OurDependency.dll`. Pokud `MyAssembly.exe` odinstalaci `OurDependency.dll` není odinstalována. Je jenom odebrány při `YourAssembly.exe` je také odinstalovat.  
  
 Pokud generujete nativní bitovou kopii pro sestavení v globální mezipaměti sestavení (GAC), zadejte její zobrazovaný název. V tématu <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>.  
  
 Nativní bitové kopie, které generuje Ngen.exe, mohou být sdíleny napříč doménami aplikace. To znamená, že nástroj Ngen.exe lze použít ve scénářích aplikací, které vyžadují, aby byla sestavení sdílena napříč doménami aplikace. Určení neutrality domény:  
  
-   Použít <xref:System.LoaderOptimizationAttribute> atributu do vaší aplikace.  
  
-   Nastavte <xref:System.AppDomainSetup.LoaderOptimization%2A?displayProperty=nameWithType> vlastnost při vytváření informace o instalaci pro novou doménu aplikace.  
  
 Vždy je třeba použít doménově neutrální kód, pokud je dané sestavení načítáno do více domén aplikace. Pokud je nativní bitová kopie načtena do nesdílené domény aplikace poté, co byla načtena do sdílené domény, nelze ji použít.  
  
> [!NOTE]
>  Doménově neutrální kód nemůže být uvolněn a výkon může být mírně snížen, zvláště při přistupování ke statickým členům.  
  
 V této části Poznámky:  
  
-   [Generování bitových kopií pro různé scénáře](#Scenarios)  
  
-   [Určení, kdy použít nativní bitové kopie](#WhenToUse)  
  
    -   [Vylepšené využití paměti](#Memory)  
  
    -   [Rychlejší spuštění aplikace](#Startup)  
  
    -   [Souhrn využití aspekty](#UsageSummary)  
  
-   [Důležitost základní adresy sestavení](#BaseAddresses)  
  
-   [Pevné vazby](#HardBinding)  
  
    -   [Určení vazby nápovědu pro závislosti](#DependencyHint)  
  
    -   [Určení výchozí vazby nápovědu pro sestavení](#AssemblyHint)  
  
-   [Odložené zpracování](#Deferred)  
  
-   [Nativní bitové kopie a JIT – kompilace](#JITCompilation)  
  
    -   [Neplatné obrázky](#InvalidImages)  
  
-   [Odstraňování potíží](#Troubleshooting)  
  
    -   [Vazba sestavení – Prohlížeč protokolu](#Fusion)  
  
    -   [JITCompilationStart spravované ladění pomocníka](#MDA)  
  
    -   [Zrušení generování nativních bitových kopií](#OptOut)  
  
<a name="Scenarios"></a>   
## <a name="generating-images-for-----different-scenarios"></a>Generování bitových kopií pro různé scénáře  
 Po vygenerování nativních bitových kopií pro sestavení modulu runtime automaticky pokusí vyhledat a použít tento nativních bitových kopií pokaždé, když ji spustí sestavení. V závislosti na scénáři lze generovat více bitových kopií.  
  
 Například pokud spustíte sestavení ladění nebo profilace scénář, modul runtime hledá nativních bitových kopií, který se vygeneroval s `/Debug` nebo `/Profile` možnosti. Pokud nemůže najít odpovídající nativní bitovou kopii, vrátí se modul runtime ke standardní JIT kompilaci. Jediný způsob, jak ladit nativní bitové kopie je vytvoření nativní bitové kopie s `/Debug` možnost.  
  
 `uninstall` Akce také rozpoznat scénáře, takže můžete odinstalovat všechny scénáře nebo pouze vybraného scénáře.  
  
<a name="WhenToUse"></a>   
## <a name="determining-when-to-use-native-images"></a>Určení, kdy použít nativní bitové kopie  
 Nativní bitové kopie mohou poskytnout zvýšení výkonu ve dvou oblastech: lepší využití paměti a rychlejší spouštění.  
  
> [!NOTE]
>  Výkon nativních bitových kopií závisí na několika faktorech, které analýzu výkonu znesnadňují, například přístupové vzory kódu a dat, počet volání napříč hranicemi modulu či počet závislostí již načtených jinými aplikacemi. Jediným způsobem, jak určit, zda nativní bitové kopie prospívají aplikaci, je pečlivé měření výkonu v klíčových scénářích nasazení.  
  
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
>  Před [!INCLUDE[net_v35SP1_long](../../../includes/net-v35sp1-long-md.md)], byste měli umístit sdílené, silným názvem součásti v globální mezipaměti sestavení, protože zavaděč provádí sestavení se silným názvem, které nejsou v globální mezipaměti sestavení, což eliminuje efektivně zlepšení doplňující ověření v čase spuštění získaných pomocí nativní bitové kopie. Optimalizace, které byly zavedeny v [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] odebrat doplňující ověření.  
  
<a name="UsageSummary"></a>   
### <a name="summary-of-usage-considerations"></a>Souhrn využití aspekty  
 Následující obecné a aplikační informace vám mohou pomoci rozhodnout, zda může být vyhodnocení nativních bitových kopií pro aplikaci přínosem:  
  
-   Nativní bitové kopie se načítají rychleji než jazyk MSIL, protože odstraňují potřebu mnoha aktivit při spouštění, například kompilaci JIT a ověření bezpečnosti typů.  
  
-   Nativní bitové kopie vyžadují menší počáteční pracovní sadu, protože není zapotřebí použít kompilátor JIT.  
  
-   Nativní bitové kopie umožňují sdílení kódu mezi procesy.  
  
-   Nativní bitové kopie vyžadují více místa na disku než sestavení MSIL a jejich generování může trvat značně dlouho.  
  
-   Nativní bitové kopie musí být udržovány.  
  
    -   Je-li upraveno původní sestavení nebo jedna z jeho závislostí, je zapotřebí bitové kopie znovu vygenerovat.  
  
    -   Jediné sestavení může vyžadovat několik nativních bitových kopií pro použití v různých aplikacích a scénářích. Například informace o konfiguraci dvou aplikací může vyústit v různá rozhodnutí o vazbách stejného závislého sestavení.  
  
    -   Nativní bitové kopie musí být generovány správcem; tj. z účtu systému Windows ve skupině Administrators.  
  
 Spolu s těmito obecnými informacemi je zapotřebí při určování, zda mohou nativní bitové kopie poskytnout zvýšení výkonu, zvážit i povahu aplikace:  
  
-   Je-li aplikace spouštěna v prostředí, které využívá mnoho sdílených komponent, nativní bitové kopie umožňují sdílení komponent mezi mnoha procesy.  
  
-   Používá-li aplikace více domén aplikace, nativní bitové kopie umožňují sdílení znakových stránek mezi doménami.  
  
    > [!NOTE]
    >  V rozhraních .NET Framework verze 1.0 a 1.1 nemohou být nativní bitové kopie sdíleny napříč doménami aplikace. Verze 2.0 a novější již toto omezení nemají.  
  
-   Bude-li aplikace spuštěna v rámci Terminálového serveru, nativní bitové kopie umožní sdílení znakových stránek.  
  
-   Rozsáhlé aplikace obecně těží z výhod kompilace do nativních bitových kopií. Malým aplikacím nativní bitové kopie obvykle výhody nepřinášejí.  
  
-   Pro dlouho běžící aplikace vykazuje kompilace JIT za běhu mírně vyšší výkon než nativní bitové kopie. (Pevné vazby mohou tento rozdíl ve výkonu do určité míry zmenšit.)  
  
<a name="BaseAddresses"></a>   
## <a name="importance-of-assembly-base-addresses"></a>Důležitost základní adresy sestavení  
 Jelikož nativní bitové kopie jsou soubory Windows PE, týkají se jich stejné problémy související se změnou základní cesty jako u ostatních spustitelných souborů. Snížení výkonu vinou přemístění je ještě větší, jsou-li použity pevné vazby.  
  
 Chcete-li nastavit základní adresu pro nativní bitovou kopii, použijte příslušnou možnost kompilátoru pro nastavení základní adresy sestavení. Tuto základní adresu používá nástroj Ngen.exe pro nativní bitové kopie.  
  
> [!NOTE]
>  Nativní bitové kopie jsou větší než spravovaná sestavení, z nichž byly vytvořeny. Základní adresy musí být vypočteny tak, aby tyto větší velikosti umožňovaly.  
  
 Chcete-li zobrazit preferovanou základní adresu nativní bitové kopie, můžete použít například nástroj dumpbin.exe.  
  
<a name="HardBinding"></a>   
## <a name="hard-binding"></a>Pevné vazby  
 Pevné vazby zvyšují propustnost a snižují velikost pracovní sady pro nativní bitové kopie. Nevýhodou pevné vazby je, že všechny bitové kopie, které jsou pevně vázány na sestavení, musí být načteny při načtení sestavení. To u velkých aplikací může výrazně prodloužit spouštění.  
  
 Pevná vazba je vhodná pro závislosti, které jsou načteny ve všech scénářích aplikace, u kterých velmi záleží na výkonu. Stejně jako u jakéhokoli jiného aspektu použití nativní bitové kopie je měření výkonu jediným způsobem, jak určit, zda pevná vazba zlepšuje výkon vaší aplikace.  
  
 <xref:System.Runtime.CompilerServices.DependencyAttribute> a <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> atributů umožňují poskytovat pevný vazby k Ngen.exe.  
  
> [!NOTE]
>  Tyto atributy jsou informace pro Ngen.exe, nikoli příkazy. Jejich použití nezaručuje pevné vazby. V budoucích verzích se může změnit význam těchto atributů.  
  
<a name="DependencyHint"></a>   
### <a name="specifying-a-binding-hint-for-a-dependency"></a>Určení vazby nápovědu pro závislosti  
 Použít <xref:System.Runtime.CompilerServices.DependencyAttribute> k sestavení udávajících pravděpodobnost, že zadaná závislost budou načteny. <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> Označuje, že je vhodné, pevné vazby <xref:System.Runtime.CompilerServices.LoadHint.Default> označuje, že má být použita výchozí hodnota pro závislost, a <xref:System.Runtime.CompilerServices.LoadHint.Sometimes> označuje, že pevné vazba není vhodná.  
  
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
### <a name="specifying-a-default-binding-hint-for-an-assembly"></a>Určení výchozí vazby nápovědu pro sestavení  
 Výchozí pokyny pro vazby jsou zapotřebí pouze pro sestavení, která budou použita okamžitě a často aplikací, která na nich závisí. Použít <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> s <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> na takové sestavení k určení, že má být použita pevný vazby.  
  
> [!NOTE]
>  Neexistuje žádný důvod pro použití <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> na sestavení .dll, které nepatří do této kategorie patří, protože jiné než použití atributu s hodnotou <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> má stejný účinek jako nejsou vůbec použití atributu.  
  
 Společnost Microsoft používá <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> pevný vazba je výchozí nastavení pro velmi malý počet sestavení v rozhraní .NET Framework, jako je například mscorlib.dll.  
  
<a name="Deferred"></a>   
## <a name="deferred-processing"></a>Odložené zpracování  
 Generování nativních bitových kopií pro velmi velké aplikace může být časově náročné. Obdobně změny sdílené komponenty nebo změny nastavení počítače mohou vyžadovat aktualizaci mnoha nativních bitových kopií. `install` a `update` mají akce `/queue` možnost, která fronty operaci pro odložené provedení službou nativních bitových kopií. Kromě toho má Ngen.exe `queue` a `executeQueuedItems` akce, které poskytuje určitou kontrolu nad službu. Další informace najdete v tématu [nativní bitové kopie služby][Native Image Service].  
  
<a name="JITCompilation"></a>   
## <a name="native-images-and-jit-compilation"></a>Nativní bitové kopie a JIT – kompilace  
 Pokud Ngen.exe v sestavení zaznamená jakékoli metody, které neumí generovat, vyloučí je z nativní bitové kopie. Jakmile modul runtime spustí toto sestavení, vrátí se k JIT kompilaci pro ty metody, které nejsou zahrnuty v nativní bitové kopii.  
  
 Kromě toho nejsou nativní bitové kopie použity v případě, že bylo sestavení inovováno, nebo pokud byla bitová kopie z jakéhokoliv důvodu zneplatněna.  
  
<a name="InvalidImages"></a>   
### <a name="invalid-images"></a>Neplatné obrázky  
 Při použití nástroje Ngen.exe pro vytvoření nativní bitové kopie sestavení závisí výstup na zadaných možnostech příkazového řádku a určitých nastaveních počítače. Mezi tato nastavení patří následující:  
  
-   Verze rozhraní .NET Framework.  
  
-   Verze operačního systému, pokud se změna týká ze systémů řady Windows 9 x řady systému Windows NT.  
  
-   Přesná identita sestavení (rekompilace identitu mění).  
  
-   Přesná identita všech sestavení, na které sestavení odkazuje (rekompilace identitu mění).  
  
-   Bezpečnostní faktory.  
  
 Nástroj Ngen.exe zaznamenává tyto informace při generování nativní bitové kopie. Po spuštění sestavení modul runtime hledá nativní bitovou kopii vytvořenou s možnostmi a nastavením, které odpovídají aktuálnímu prostředí počítače. Modul runtime se vrátí k JIT kompilaci sestavení, pokud nemůže najít odpovídající nativní bitovou kopii. Následující změny nastavení a prostředí počítače způsobí zneplatnění nativních bitových kopií:  
  
-   Verze rozhraní .NET Framework.  
  
     Pokud použijete aktualizaci rozhraní .NET Framework, všechny nativní bitové kopie, které jste vytvořili pomocí Ngen.exe, se zneplatní. Z tohoto důvodu všechny aktualizace rozhraní .NET Framework provést `Ngen Update` příkazu, ujistěte se, že se znova vygeneroval všechny nativní bitové kopie. Rozhraní .NET Framework automaticky vytvoří nové nativní bitové kopie pro knihovny rozhraní .NET Framework, které nainstaluje.  
  
-   Verze operačního systému, pokud se změna týká ze systémů řady Windows 9 x řady systému Windows NT.  
  
     Například, pokud verze operačního systému na počítač se změní ze systému Windows 98 do systému Windows XP, budou všechny nativní bitové kopie, které jsou uložené v mezipaměti nativních bitových kopií neplatné. Pokud se operační systém se změní ze systému Windows 2000 na systém Windows XP, nejsou zrušena bitové kopie.  
  
-   Přesná identita sestavení.  
  
     Pokud je provedena rekompilace sestavení, odpovídající nativní bitové kopie se stanou neplatnými.  
  
-   Přesná identita všech sestavení, na která sestavení odkazuje.  
  
     Pokud aktualizujete spravované sestavení, všechny nativní bitové kopie, které přímo nebo nepřímo závisí na tomto sestavení, se zneplatní a musí být znovu vygenerovány. To zahrnuje jak běžné odkazy, tak pevně vázané závislosti. Vždy, když se použije aktualizace softwaru, by měla spustit instalační program `Ngen Update` zajistěte, aby všechny závislé nativní bitové kopie jsou obnovovaly.  
  
-   Bezpečnostní faktory.  
  
     Změna zásad zabezpečení počítače směřující k omezení dříve udělených oprávnění sestavení může způsobit, že se dříve zkompilované nativní bitové kopie sestavení stanou neplatnými.  
  
     Podrobné informace o tom, jak modul common language runtime spravuje zabezpečení přístupu kódu a jak používat oprávnění najdete v tématu [zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security.md).  
  
<a name="Troubleshooting"></a>   
## <a name="troubleshooting"></a>Poradce při potížích  
 V následujících tématech řešení potíží umožňují zobrazit které nativní bitové kopie se používají a které nelze použít v aplikaci, pro určení, kdy JIT kompilátoru spustí zkompilovat metodu a ukazuje, jak pro vyjádření výslovného nesouhlasu kompilaci nativních bitových kopií zadat metody.  
  
<a name="Fusion"></a>   
### <a name="assembly-binding-log-viewer"></a>vazba sestavení – prohlížeč protokolu  
 Pokud chcete potvrdit, že nativní bitové kopie jsou používány aplikací, můžete použít [Fuslogvw.exe (sestavení vazby Log Viewer)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md). Vyberte **nativní bitové kopie** v **kategorií protokolu** pole v okně Prohlížeč protokolu vazby. Fuslogvw.exe poskytuje informace o důvodu, proč byla nativní bitová kopie odmítnuta.  
  
<a name="MDA"></a>   
### <a name="the-jitcompilationstart-managed-debugging-assistant"></a>JITCompilationStart spravované ladění pomocníka  
 Můžete použít [jitCompilationStart](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md) pomocníka spravovaného ladění (MDA) k určení, kdy začne JIT kompilátoru zkompilovat funkce.  
  
<a name="OptOut"></a>   
### <a name="opting-out-of-native-image-generation"></a>Zrušení generování nativních bitových kopií  
 V některých případech může mít NGen.exe generování potíže, které nativních bitových kopií pro konkrétní metody, nebo můžete můžou upřednostňovat, že metoda být JIT zkompilovat místo poté zkompilovány do nativní bitové kopie. V takovém případě můžete použít `System.Runtime.BypassNGenAttribute` atribut zabránit NGen.exe generování nativních bitových kopií pro konkrétní metody. Atribut se musí použít jednotlivě u jednotlivých metod, jejichž kód není chcete zahrnout do nativních bitových kopií. NGen.exe rozpozná atribut a nevygeneruje žádný kód v nativních bitových kopií pro odpovídající metodu.  
  
 Upozorňujeme však, který `BypassNGenAttribute` není definován jako typ v knihovně tříd rozhraní .NET Framework. Aby bylo možné využívat atribut ve vašem kódu, je nutné nejprve definovat ho následujícím způsobem:  
  
 [!code-csharp[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#1)]
 [!code-vb[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#1)]  
  
 Atribut lze následně použít na základě-method. Následující příklad dá pokyn, generátor, to by nemělo generovat nativních bitových kopií pro `ExampleClass.ToJITCompile` metoda.  
  
 [!code-csharp[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#2)]
 [!code-vb[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#2)]  
  
## <a name="examples"></a>Příklady  
 Následující příkaz vytvoří nativních bitových kopií pro `ClientApp.exe`, umístěný v aktuálním adresáři a nainstaluje bitovou kopii do mezipaměti nativních bitových kopií. Pokud pro sestavení existuje soubor nastavení, Ngen.exe jej použije. Kromě toho jsou generována nativní bitové kopie, pro žádné DLL, soubory, které `ClientApp.exe` odkazy.  
  
```  
ngen install ClientApp.exe  
```  
  
 Bitová kopie nainstalovaná pomocí Ngen.exe se také nazývá kořen. Kořen může být aplikace nebo sdílená komponenta.  
  
 Následující příkaz vytvoří nativních bitových kopií pro `MyAssembly.exe` se zadanou cestou.  
  
```  
ngen install c:\myfiles\MyAssembly.exe  
```  
  
 Při hledání sestavení a jejich závislosti používá Ngen.exe stejnou logiku při zjišťování, jaká je použita u Common Language Runtime (CLR). Ve výchozím adresáři, který obsahuje `ClientApp.exe` slouží jako základní adresář aplikace a začne zjišťování všechna sestavení v tomto adresáři. Toto chování můžete přepsat pomocí `/AppBase` možnost.  
  
> [!NOTE]
>  Jde o změnu oproti chování nástroje Ngen.exe v rozhraních .NET Framework verze 1.0 a 1.1, kde základ cesty aplikace je nastaven na aktuální adresář.  
  
 Sestavení mohou mít závislosti bez odkazu, například pokud načte soubor s příponou DLL pomocí <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metoda. Nativních bitových kopií pro soubor .dll můžete vytvořit pomocí konfigurační informace pro sestavení aplikace pomocí `/ExeConfig` možnost. Následující příkaz vytvoří nativních bitových kopií pro `MyLib.dll,` pomocí konfiguračních informací z `MyApp.exe`.  
  
```  
ngen install c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe  
```  
  
 Při odebrání aplikace nebudou odebrána sestavení nainstalovaná tímto způsobem.  
  
 Chcete-li odinstalovat závislost, použijte stejné možnosti příkazového řádku, které byly použity k její instalaci. Příkaz odinstaluje `MyLib.dll` z předchozího příkladu.  
  
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
  
 `display` Akce jsou uvedeny všechny kořenové sestavení nejprve následuje seznam nativní bitové kopie na počítače.  
  
 Chcete-li zobrazit pouze informace o sestavení, použijte jeho jednoduchý název. Následující příkaz zobrazí všechny nativní bitové kopie v mezipaměti nativních bitových kopií, které odpovídají částečný název `MyAssembly`, jejich závislosti a všechny kořenové adresáře, které jsou závislé na `MyAssembly`:  
  
```  
ngen display MyAssembly  
```  
  
 Zároveň budete vědět, jaké kořeny závisí na sestavení sdílená součást je užitečný při měření dopad `update` akce po upgradu sdílená součást.  
  
 Zadáte-li příponu souboru sestavení, musí být buď zadána cesta, nebo spuštěn nástroj Ngen.exe z adresáře obsahujícího sestavení:  
  
```  
ngen display c:\myApps\MyAssembly.exe  
```  
  
 Následující příkaz zobrazí všechny nativní bitové kopie v mezipaměti nativní bitové kopie s názvem `MyAssembly` a verzi 1.0.0.0.  
  
```  
ngen display "myAssembly, version=1.0.0.0"  
```  
  
### <a name="updating-images"></a>Aktualizace bitových kopií  
 Bitové kopie jsou obvykle aktualizovány po upgradu sdílené komponenty. Chcete-li aktualizovat všechny nativní bitové kopie, které změnily, nebo se změnily jehož závislosti, použijte `update` akce bez argumentů.  
  
```  
ngen update  
```  
  
 Aktualizace všech bitových kopií může být časově náročný proces. Aktualizace pro spuštění pomocí služby nativních bitových kopií můžete fronty pomocí `/queue` možnost. Další informace o `/queue` možnost a instalace priority, najdete v části [nativní bitové kopie služby][Native Image Service].  
  
```  
ngen update /queue  
```  
  
### <a name="uninstalling-images"></a>Odinstalování bitových kopií  
 Nástroj Ngen.exe udržuje seznam závislostí, takže sdílené komponenty jsou odstraněny pouze v případě, že byla odebrána všechna sestavení, která na nich závisí. Kromě toho, pokud byla sdílená komponenta nainstalována jako kořen, nebude odstraněna.  
  
 Příkaz odinstaluje všechny scénáře pro kořenovou `ClientApp.exe`:  
  
```  
ngen uninstall ClientApp  
```  
  
 `uninstall` Akci lze použít k odebrání konkrétních scénářů. Příkaz odinstaluje všechny scénáře ladění pro `ClientApp.exe`:  
  
```  
ngen uninstall ClientApp /debug  
```  
  
> [!NOTE]
>  Odinstalace `/debug` scénáře neodinstaluje scénáře, který zahrnuje obě `/profile` a `/debug.`  
  
 Příkaz odinstaluje všechny scénáře pro určitou verzi `ClientApp.exe`:  
  
```  
ngen uninstall "ClientApp, Version=1.0.0.0"  
```  
  
 Následující příkazy odinstalovat všechny scénáře pro `"ClientApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL",` nebo právě tento scénář ladění pro toto sestavení:  
  
```  
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,   
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"  
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,   
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL" /debug  
```  
  
 Stejně jako u `install` akce, poskytuje rozšíření vyžaduje buď provádění Ngen.exe z adresáře, který obsahuje sestavení nebo zadat úplnou cestu.  
  
 Příklady týkající se služby nativních bitových kopií naleznete v tématu [nativní bitové kopie služby][Native Image Service].  
  
## <a name="native-image-task"></a>Úloha pro nativní bitové kopie  
 Úloha nativních bitových kopií je úloh systému Windows, která vytváří a udržuje nativní bitové kopie. Úloha nativních bitových kopií generuje a získá nativní bitové kopie automaticky pro podporované scénáře. (Viz [vytváření nativní bitové kopie](http://msdn.microsoft.com/library/2bc8b678-dd8d-4742-ad82-319e9bf52418).) Umožňuje také instalační programy používat [Ngen.exe (Generátor nativních obrázků)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) k vytváření a aktualizaci nativní bitové kopie odložené najednou.  
  
 Jakmile pro každý procesor architektura podporovaný na počítači, aby kompilace pro aplikace, že cíl každou architekturu registraci nativních bitových kopií úlohy:  
  
|Název úlohy|32bitový počítač|64bitový počítač|  
|---------------|----------------------|----------------------|  
|NET Framework NGEN v4.0.30319|Ano|Ano|  
|NET Framework NGEN v4.0.30319 64|Ne|Ano|  
  
 Tato úloha nativních bitových kopií je je k dispozici v rozhraní .NET Framework 4.5 a novějších verzích, při spuštění v systému Windows 8 nebo novější. V dřívějších verzích systému Windows, používá rozhraní .NET Framework [nativní bitové kopie služby][Native Image Service].  
  
### <a name="task-lifetime"></a>Doba platnosti úloh  
 Obecně platí plánovače úloh systému Windows spustí úlohu nativních bitových kopií každou noc, když je počítač v nečinnosti. Úloha zkontroluje všechny odložené práci, kterou je zařazena ve frontě instalační programy aplikací, všechny žádosti o aktualizaci odložené nativních bitových kopií a vytvoření všechny automatické bitové kopie. Úloha dokončení zbývajících pracovní položky a pak se ukončí. Pokud se počítač zastaví nečinnosti, když je spuštěn úkol, zastaví úlohu.  
  
 Můžete také spustit úlohu nativních bitových kopií ručně prostřednictvím uživatelského rozhraní plánovače úloh nebo ruční volání NGen.exe. Pokud úloha se spustí pomocí jedné z těchto metod, bude spuštěn, když se počítač již není nečinný. Bitové kopie ručně vytvořené pomocí NGen.exe budou mít vyšší prioritu, chcete-li povolit předvídatelné chování pro instalační programy aplikací.  
  
## <a name="native-image-service"></a>Nativní bitová kopie služby  
 Služba nativních bitových kopií je služba systému Windows, která vytváří a udržuje nativní bitové kopie. Službu nativních bitových kopií umožňuje vývojáři odložení instalace a aktualizace nativních bitových kopií do doby, kdy počítač nečinný.  
  
 Za normálních okolností službu nativních bitových kopií inicializuje instalačního programu (Instalační program) pro aplikace nebo aktualizace. Pro akce s prioritou 3 služba provede během doby nečinnosti v počítači. Služba uloží stav a se může nadále prostřednictvím více restartování v případě potřeby. Více kompilace bitové kopie můžete zařadit do fronty.  
  
 Službu taky komunikuje s ruční Ngen.exe příkaz. Ruční příkazy mají přednost před aktivita na pozadí.  
  
> [!NOTE]
>  V systému Windows Vista je název zobrazený pro službu nativních bitových kopií "Microsoft.NET Framework NGEN v2.0.50727_X86" nebo "Microsoft.NET Framework NGEN v2.0.50727_X64". Na všechny starší verze systému Microsoft Windows je název "Služba optimalizace modulu Runtime .NET v2.0.50727_X86" nebo "Služba optimalizace modulu Runtime .NET v2.0.50727_X64".  
  
### <a name="launching-deferred-operations"></a>Spuštění operace odložené  
 Před zahájením instalace nebo upgradu, se doporučuje pozastavení služby. Tím se zajistí, že služba nespustí při kopírování souborů nebo uvedení sestavení v globální mezipaměti sestavení Instalační služby. Následující příkazový řádek Ngen.exe pozastaví službu:  
  
```  
ngen queue pause  
```  
  
 Pokud všechny odložené operace byla zařazena do fronty, následující příkaz umožňuje službu, kterou chcete obnovit:  
  
```  
ngen queue continue  
```  
  
 Chcete-li při instalaci nové aplikace, nebo při aktualizaci sdílené součásti, odložení generování nativních bitových kopií, použijte `/queue` možnost s `install` nebo `update` akce. Na příkazovém řádku následující Ngen.exe instalace nativních bitových kopií pro sdílené součást a proveďte aktualizaci všechny kořenové adresáře, které byly:  
  
```  
ngen install MyComponent /queue  
ngen update /queue  
```  
  
 `update` Akce regeneruje všechny nativní bitové kopie, které se zrušila platnost, nikoli pouze ty, které používají `MyComponent`.  
  
 Pokud vaše aplikace obsahuje mnoho kořeny, můžete řídit prioritu odložené akce. Následující příkazy ve frontě pro instalaci tři kořenových certifikačních autorit. `Assembly1` je nainstalována jako první, bez čekání na čas nečinnosti. `Assembly2` je také nainstalován bez čekání na dobu nečinnosti, ale po dokončení všech akcí priority 1. `Assembly3` nainstaluje se při službu zjistí, že je počítač v nečinnosti.  
  
```  
ngen install Assembly1 /queue:1  
ngen install Assembly2 /queue:2  
ngen install Assembly3 /queue:3  
```  
  
 Můžete vynutit akce ve frontě proběhnout synchronně pomocí `executeQueuedItems` akce. Pokud zadáte volitelné prioritu, tato akce ovlivní pouze zařazených do fronty akce, které mají stejné nebo nižší prioritu. Výchozí priorita je 3, takže příkaz Ngen.exe okamžitě zpracovává všechny akce ve frontě a nevrací až skončí:  
  
```  
ngen executeQueuedItems  
```  
  
 Synchronní příkazy jsou provedený Ngen.exe a nepoužívejte službu nativních bitových kopií. Můžete provést akce s použitím Ngen.exe během spuštěné služby nativních bitových kopií.  
  
### <a name="service-shutdown"></a>Vypnutí služby  
 Po se iniciovat provádění příkaz Ngen.exe, která zahrnuje `/queue` možnost, služba bude spuštěna na pozadí dokud všechny akce byly dokončeny. Služba uloží stav, aby mohl pokračovat prostřednictvím více restartování v případě potřeby. Když službu zjistí, že neexistují žádné další akce ve frontě, obnoví stav tak, že ji nebude restartování při příštím spuštění počítače a pak se ukončí sám.  
  
### <a name="service-interaction-with-clients"></a>Služba interakci s klienty  
 V rozhraní .NET Framework verze 2.0 je jediná interakce s nativních bitových kopií služby pomocí nástroje příkazového řádku Ngen.exe. Pomocí nástroje příkazového řádku ve skriptech instalace do fronty akce pro službu nativních bitových kopií a komunikovat se službou.  
  
## <a name="see-also"></a>Viz také  
 [Nástroje](../../../docs/framework/tools/index.md)  
 [Proces spravovaného spuštění](../../../docs/standard/managed-execution-process.md)  
 [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

[Native Image Service]: #native-image-service
