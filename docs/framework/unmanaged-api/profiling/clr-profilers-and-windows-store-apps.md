---
title: Profilery CLR a aplikace pro Windows Store
ms.date: 03/30/2017
dev_langs:
- csharp
applies_to:
- Windows 10
- Windows 8
helpviewer_keywords:
- profiling API
- profiling API [.NET Framework]
- profiling managed code
- profiling managed code [Windows Store Apps]
ms.assetid: 1c8eb2e7-f20a-42f9-a795-71503486a0f5
ms.openlocfilehash: 6330a4c2733729da264065d1eec8c3c9eaf9f05c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501024"
---
# <a name="clr-profilers-and-windows-store-apps"></a>Profilery CLR a aplikace pro Windows Store

Toto téma popisuje, co je potřeba vzít v úvahu při psaní diagnostických nástrojů, které analyzují spravovaný kód spuštěný v aplikaci pro Windows Store. Poskytuje také pokyny pro úpravu stávajících nástrojů pro vývoj, aby byly i nadále funkční, když je spustíte v aplikacích pro Windows Store. Aby bylo možné tyto informace pochopit, je nejlepší, pokud jste obeznámeni s rozhraním API profilace modulu CLR (Common Language Runtime), už jste toto rozhraní API používali v diagnostickém nástroji, který správně funguje s aplikacemi pro stolní počítače s Windows, a teď se zajímáte o úpravu nástroje pro správné spouštění proti aplikacím Windows Store.

## <a name="introduction"></a>Úvod

Pokud jste to udělali za úvodním odstavcem, budete obeznámeni s rozhraním API profilace CLR. Už jste napsali diagnostický nástroj, který funguje dobře se spravovanými aplikacemi klasické pracovní plochy. Nyní jste zajímái, co dělat, aby váš nástroj fungoval se spravovanou aplikací pro Windows Store. Možná jste se už pokusili tuto práci provést a zjistili jste, že se nejedná o přímočarý úkol. Ve skutečnosti existuje několik důležitých informací, které nemusí být zřejmé pro všechny vývojáře nástrojů. Příklad:

- Aplikace pro Windows Store běží v kontextu s přísně nižšími oprávněními.

- Soubory metadat systému Windows mají při porovnání s tradičními spravovanými moduly jedinečné charakteristiky.

- Aplikace pro Windows Store mají při výpadku interaktivity možnost je pozastavit.

- Mechanismy vzájemné komunikace mezi procesy možná nebudou fungovat z různých důvodů.

Toto téma obsahuje seznam věcí, o kterých je třeba vědět, a o tom, jak s nimi pracovat správně.

Pokud s rozhraním API profilace CLR začínáte, přeskočte k prostředkům na konci tohoto tématu, kde najdete lepší úvodní informace.

Poskytování podrobných informací o konkrétních rozhraních API systému Windows a jejich použití je také mimo rámec tohoto tématu. Vezměte v úvahu výchozí bod a podívejte se na MSDN, kde najdete další informace o všech rozhraních API pro Windows, na která se odkazuje.

## <a name="architecture-and-terminology"></a>Architektura a terminologie

Diagnostický nástroj obvykle obsahuje architekturu, která je znázorněna na následujícím obrázku. Používá termín "Profiler", ale mnoho takových nástrojů překračuje typický výkon nebo profilaci paměti v oblastech, jako je pokrytí kódu, objektové architektury objektů, doba pro ladění času, monitorování aplikací a tak dále. V zájmu jednoduchosti bude toto téma dál odkazovat na všechny tyto nástroje jako profilery.

V tomto tématu se používá následující terminologie:

**Aplikace**

Toto je aplikace, kterou Profiler analyzuje. Většinou vývojář této aplikace teď používá profiler k diagnostice problémů s aplikací. Tradičně by tato aplikace byla desktopová aplikace pro Windows, ale v tomto tématu se díváte na aplikace pro Windows Store.

**Knihovna DLL profileru**

Toto je komponenta, která se načte do procesního prostoru analyzované aplikace. Tato součást, označovaná také jako Profiler "agent", implementuje rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md)[ICorProfilerCallback](icorprofilercallback-interface.md)(2, 3 atd.) a využívá rozhraní [ICorProfilerInfo](icorprofilerinfo-interface.md)(2, 3 atd.) ke shromažďování dat o analyzované aplikaci a potenciálně upravování aspektů chování aplikace.

**Uživatelské rozhraní profileru**

Jedná se o desktopovou aplikaci, se kterou uživatel profileru komunikuje. Zodpovídá za zobrazení stavu aplikace uživateli a dává uživateli prostředky pro řízení chování analyzované aplikace. Tato součást se vždycky spouští ve vlastním prostoru procesu, a to odděleně od prostoru procesu aplikace, která je profilovaná. Uživatelské rozhraní profileru může fungovat také jako aktivační událost "připojit Trigger", což je proces, který volá metodu [ICLRProfiling:: AttachProfiler –](iclrprofiling-attachprofiler-method.md) , aby mohla analyzovaná aplikace načíst knihovnu DLL profileru v případech, kdy se knihovna DLL profileru při spuštění nenačetla.

> [!IMPORTANT]
> Uživatelské rozhraní profileru by mělo zůstat desktopové aplikace systému Windows, i když je používáno k řízení a sestavování aplikace pro Windows Store. Neočekává se, že nebude možné zabalit a dodávat Nástroj pro diagnostiku ve Windows Storu. Nástroj vyžaduje, aby aplikace pro Windows Store nemohly a mnohé z těchto věcí byly v uživatelském rozhraní profileru.

V tomto dokumentu ukázkový kód předpokládá, že:

- Vaše knihovna DLL profileru je zapsána v jazyce C++, protože musí být nativní knihovny DLL, podle požadavků rozhraní API profilování CLR.

- Vaše uživatelské rozhraní profileru je napsané v jazyce C#. To není nutné, ale vzhledem k tomu, že neexistují žádné požadavky na jazyk pro proces uživatelského rozhraní profileru, proč nemusíte vybírat jazyk, který je výstižný a jednoduchý?

### <a name="windows-rt-devices"></a>Zařízení s Windows RT

Zařízení se systémem Windows RT jsou poměrně uzamčena. Profilery třetích stran jednoduše nejde na taková zařízení načíst. Tento dokument se zaměřuje na počítače se systémem Windows 8.

## <a name="consuming-windows-runtime-apis"></a>Využívání rozhraní API pro prostředí Windows Runtime

V několika scénářích popsaných v následujících částech musí vaše aplikace pracovní plochy uživatelského rozhraní profileru spotřebovat některá nová rozhraní prostředí Windows Runtime API. V dokumentaci budete chtít zjistit, které prostředí Windows Runtime rozhraní API se dají použít z desktopových aplikací, a jestli se jejich chování liší od aplikací klasické pracovní plochy a aplikací pro Windows Store.

Pokud je vaše uživatelské rozhraní profileru napsané ve spravovaném kódu, bude potřeba provést několik kroků, abyste tyto prostředí Windows Runtime rozhraní API mohli snadno spotřebovat. Další informace najdete v článku [spravované aplikace klasické pracovní plochy a prostředí Windows Runtime](https://docs.microsoft.com/previous-versions/windows/apps/jj856306(v=win.10)) .

## <a name="loading-the-profiler-dll"></a>Načtení knihovny DLL profileru

Tato část popisuje, jak vaše uživatelské rozhraní profileru způsobí, že aplikace pro Windows Store načte knihovnu DLL profileru. Kód, který je popsaný v této části, patří do vaší aplikace vašeho uživatelského rozhraní profileru a proto zahrnuje použití rozhraní API systému Windows, která jsou bezpečná pro desktopové aplikace, ale ne nutně bezpečná pro aplikace pro Windows Store.

Vaše uživatelské rozhraní profileru může způsobit, že se vaše knihovna DLL profileru načte do procesního prostoru aplikace dvěma způsoby:

- Při spuštění aplikace, jak je řízeno proměnnými prostředí.

- Připojením k aplikaci po dokončení spuštění voláním metody [ICLRProfiling:: AttachProfiler –](iclrprofiling-attachprofiler-method.md) .

Jedna z vašich prvních překážek bude získávat spouštěcí načtení a připojení k načtení knihovny DLL profileru pro správnou práci s aplikacemi pro Windows Store. Obě formy načítání sdílejí některé zvláštní důležité požadavky, takže je začneme s nimi.

### <a name="common-considerations-for-startup-and-attach-loads"></a>Běžné požadavky pro spuštění a připojení zatížení

**Podepisování knihovny DLL profileru**

Když se systém Windows pokusí načíst knihovnu DLL profileru, ověří, že je vaše knihovna DLL profileru správně podepsaná. V takovém případě se zatížení ve výchozím nastavení nepovede. Toto lze provést dvěma způsoby:

- Ujistěte se, že je vaše knihovna DLL profileru podepsaná.

- Před použitím tohoto nástroje sdělte uživateli, že musí na svém počítači s Windows 8 nainstalovat vývojářskou licenci. To lze provést automaticky ze sady Visual Studio nebo ručně z příkazového řádku. Další informace najdete v tématu [získání vývojářské licence](https://docs.microsoft.com/previous-versions/windows/apps/hh974578(v=win.10)).

**Oprávnění systému souborů**

Aplikace pro Windows Store musí mít oprávnění načíst a spustit knihovnu DLL profileru z umístění v systému souborů, ve kterém je residesBy výchozí, aplikace pro Windows Store nemá takové oprávnění ve většině adresářů a všechny neúspěšné pokus o načtení knihovny DLL profileru vytvoří záznam v protokolu událostí aplikace systému Windows, který vypadá nějak takto. :

```output
NET Runtime version 4.0.30319.17929 - Loading profiler failed during CoCreateInstance.  Profiler CLSID: '{xxxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx}'.  HRESULT: 0x80070005.  Process ID (decimal): 4688.  Message ID: [0x2504].
```

Obecně platí, že aplikace pro Windows Store mají povolený přístup jenom k omezené sadě míst na disku. Každá aplikace pro Windows Store má přístup k vlastním složkám aplikačních dat a také k několika dalším oblastem v systému souborů, pro které mají všechny aplikace pro Windows Store udělený přístup. Doporučuje se nainstalovat knihovnu DLL profileru a její závislosti někam do složky programové soubory nebo Program Files (x86), protože všechny aplikace pro Windows Store mají ve výchozím nastavení oprávnění ke čtení a spouštění.

### <a name="startup-load"></a>Spouštěcí zatížení

V desktopové aplikaci se obvykle uživatelské rozhraní profileru zeptá na spouštěcí načtení knihovny DLL profileru inicializací bloku prostředí, který obsahuje požadované proměnné prostředí API profilace modulu CLR (tj., `COR_PROFILER` , `COR_ENABLE_PROFILING` a `COR_PROFILER_PATH` ), a pak vytvoří nový proces s tímto blokem prostředí. Totéž platí pro aplikace pro Windows Store, ale mechanismy se liší.

**Nespouštět se zvýšenými oprávněními**

Pokud se pokusíte zpracovat proces aplikace pro Windows Store B, proces A by měl běžet na střední úrovni integrity, nikoli na úrovni vysoké integrity (tj. ne zvýšené). To znamená, že vaše uživatelské rozhraní profileru by mělo být spuštěné na střední úrovni integrity nebo musí vytvořit jiný pracovní proces na střední úrovni integrity, aby se postaral o spuštění aplikace pro Windows Store.

**Volba aplikace pro Windows Store, která se má profilovat**

Nejdřív budete chtít požádat uživatele profileru, kterou aplikaci pro Windows Store spustit. U desktopových aplikací možná budete chtít zobrazit dialog procházení souborů a uživatel najde a vybere soubor. exe. Aplikace pro Windows Store se ale liší a použití dialogového okna pro procházení neposkytuje smysl. Místo toho je lepší zobrazit uživatele seznam aplikací pro Windows Store nainstalovaných pro daného uživatele, ze kterého chcete vybrat.

<xref:Windows.Management.Deployment.PackageManager>K vygenerování tohoto seznamu můžete použít třídu. `PackageManager`je prostředí Windows Runtime třída, která je dostupná pro desktopové aplikace, a ve skutečnosti je dostupná *jenom* pro desktopové aplikace.

Následující příklad kódu z hypotetického uživatelského rozhraní profileru zapsaného jako desktopová aplikace v jazyce C# používá `PackageManager` ke generování seznamu aplikací pro Windows:

```csharp
string currentUserSID = WindowsIdentity.GetCurrent().User.ToString();
IAppxFactory appxFactory = (IAppxFactory) new AppxFactory();
PackageManager packageManager = new PackageManager();
IEnumerable<Package> packages = packageManager.FindPackagesForUser(currentUserSID);
```

**Určení vlastního bloku prostředí**

Nové rozhraní modelu COM, [IPackageDebugSettings](/windows/desktop/api/shobjidl_core/nn-shobjidl_core-ipackagedebugsettings), umožňuje přizpůsobit chování při spouštění aplikace pro Windows Store a usnadnit tak určité formy diagnostiky. Jedna z jejích metod, [EnableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-enabledebugging), umožňuje předat bloku prostředí do aplikace pro Windows Store, když se spustí, spolu s dalšími užitečnými účinky, jako je zakázání automatického pozastavení procesu. Blok prostředí je důležitý, protože je nutné zadat proměnné prostředí ( `COR_PROFILER` , `COR_ENABLE_PROFILING` , a `COR_PROFILER_PATH)` ) používané modulem CLR k načtení knihovny DLL profileru.

Vezměte v úvahu následující fragment kódu:

```csharp
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();
pkgDebugSettings.EnableDebugging(packageFullName, debuggerCommandLine,
                                                                 (IntPtr)fixedEnvironmentPzz);
```

K dispozici je několik položek, které je potřeba získat hned:

- `packageFullName`dá se určit při iteracích balíčků a převzetí `package.Id.FullName` .

- `debuggerCommandLine`je trochu zajímavější. Aby bylo možné předat vlastní blok prostředí do aplikace pro Windows Store, musíte napsat vlastní zjednodušený fiktivní ladicí program. Windows vytvoří pozastavenou aplikaci pro Windows Store a pak připojí ladicí program spuštěním ladicího programu s příkazovým řádkem, jako v tomto příkladu:

    ```console
    MyDummyDebugger.exe -p 1336 -tid 1424
    ```

     kde `-p 1336` to znamená, že aplikace pro Windows Store má ID procesu 1336, a `-tid 1424` znamená, že vlákno s ID 1424 je pozastavené. Váš fiktivní ladicí program by analyzoval IDvlákna z příkazového řádku, pokračuje v tomto vláknu a potom ukončí.

     Zde je příklad kódu jazyka C++ k tomu, aby to bylo možné (nezapomeňte přidat kontrolu chyb!):

    ```cpp
    int wmain(int argc, wchar_t* argv[])
    {
        // …
        // Parse command line here
        // …

        HANDLE hThread = OpenThread(THREAD_SUSPEND_RESUME,
                                                                  FALSE /* bInheritHandle */, nThreadID);
        ResumeThread(hThread);
        CloseHandle(hThread);
        return 0;
    }
    ```

     Tento fiktivní ladicí program bude nutné nasadit jako součást instalace nástroje pro diagnostiku a poté zadat cestu k tomuto ladicímu programu v `debuggerCommandLine` parametru.

**Spouští se aplikace pro Windows Store.**

Okamžik pro spuštění aplikace pro Windows Store byl nakonec doručen. Pokud jste to již zkusili sami, možná jste si všimli, že funkce [CreateProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessa) nezpůsobuje vytvoření procesu aplikace pro Windows Store. Místo toho budete muset použít metodu [IApplicationActivationManager:: ActivateApplication](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-iapplicationactivationmanager-activateapplication) . Abyste to mohli udělat, musíte získat ID uživatelského modelu aplikace aplikace pro Windows Store, který spouštíte. To znamená, že budete muset provést trochu prozkoumá prostřednictvím manifestu.

Při iteraci na balíčcích (v předchozím oddílu [spouštěcího načtení](#startup-load) v části Výběr aplikace pro Windows Store do profilu) budete chtít převzít sadu aplikací obsažených v manifestu aktuálního balíčku:

```csharp
string manifestPath = package.InstalledLocation.Path + "\\AppxManifest.xml";

AppxPackaging.IStream manifestStream;
SHCreateStreamOnFileEx(
                    manifestPath,
                    0x00000040,     // STGM_READ | STGM_SHARE_DENY_NONE
                    0,              // file creation attributes
                    false,          // fCreate
                    null,           // reserved
                    out manifestStream);

IAppxManifestReader manifestReader = appxFactory.CreateManifestReader(manifestStream);

IAppxManifestApplicationsEnumerator appsEnum = manifestReader.GetApplications();
```

Ano, jeden balíček může mít více aplikací a každá aplikace má vlastní ID modelu uživatele aplikace. Proto budete chtít požádat uživatele, aby aplikaci profiloval, a učinit ID modelu uživatele aplikace z této konkrétní aplikace:

```csharp
while (appsEnum.GetHasCurrent() != 0)
{
    IAppxManifestApplication app = appsEnum.GetCurrent();
    string appUserModelId = app.GetAppUserModelId();
    //...
}
```

Nakonec teď máte k dispozici, co potřebujete k otevření aplikace pro Windows Store:

```csharp
IApplicationActivationManager appActivationMgr = new ApplicationActivationManager();
appActivationMgr.ActivateApplication(appUserModelId, appArgs, ACTIVATEOPTIONS.AO_NONE, out pid);
```

**Nezapomeňte zavolat DisableDebugging**

Když jste volali [IPackageDebugSettings:: EnableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-enabledebugging), provedli jste příslib, který byste měli vyčistit po sobě voláním metody [IPackageDebugSettings::D isabledebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-disabledebugging) , takže nezapomeňte to udělat, když je relace profilování.

### <a name="attach-load"></a>Připojit zatížení

Když vaše uživatelské rozhraní profileru chce připojit svoji knihovnu DLL profileru k aplikaci, která už je spuštěná, používá [ICLRProfiling:: AttachProfiler –](iclrprofiling-attachprofiler-method.md). Totéž platí pro aplikace pro Windows Store. Ale kromě běžných otázek uvedených výše se ujistěte, že cílová aplikace pro Windows Store není pozastavená.

**EnableDebugging**

Stejně jako u spouštěcího zatížení volejte metodu [IPackageDebugSettings:: EnableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-enabledebugging) . Nepotřebujete ho pro předání bloku prostředí, ale budete potřebovat jednu z dalších funkcí: Zakázání automatického pozastavení procesu. V opačném případě, když vaše uživatelské rozhraní profileru volá [AttachProfiler –](iclrprofiling-attachprofiler-method.md), může být cílová aplikace pro Windows Store pozastavena. Ve skutečnosti je to nejspíš v případě, že uživatel teď pracuje s vaším uživatelským ROZHRANÍm profileru a aplikace pro Windows Store není aktivní na žádném z obrazovek uživatele. A pokud je aplikace pro Windows Store pozastavená, nebude moct reagovat na žádný signál, který ho CLR pošle, aby se připojila vaše knihovna DLL profileru.

Takže budete chtít udělat něco podobného:

```csharp
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();
pkgDebugSettings.EnableDebugging(packageFullName, null /* debuggerCommandLine */,
                                                                 IntPtr.Zero /* environment */);
```

Jedná se o stejné volání, které jste provedli pro případ spuštění při načítání, s výjimkou, že neurčíte příkazový řádek ladicího programu nebo blok prostředí.

**DisableDebugging**

Jako vždy nezapomeňte při dokončení relace profilování volat [IPackageDebugSettings::D isabledebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-disabledebugging) .

## <a name="running-inside-the-windows-store-app"></a>Spuštění v aplikaci pro Windows Store

Takže aplikace pro Windows Store nakonec načetla knihovnu DLL profileru. Vaše knihovna DLL profileru se teď musí považovat za výuku různých pravidel vyžadovaných aplikacemi pro Windows Store, včetně toho, jaká rozhraní API jsou povolená a jak se dají spouštět s omezenými oprávněními.

### <a name="stick-to-the-windows-store-app-apis"></a>Přilepit na rozhraní API aplikací pro Windows Store

Když procházíte rozhraní API systému Windows, všimnete si, že všechna rozhraní API jsou zdokumentována jako platná pro aplikace klasické pracovní plochy, aplikace pro Windows Store nebo obojí. Například část **požadavky** v dokumentaci pro funkci [InitializeCriticalSectionAndSpinCount](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionandspincount) označuje, že se funkce vztahuje pouze na desktopové aplikace. Naproti tomu funkce [InitializeCriticalSectionEx](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionex) je k dispozici pro aplikace klasické pracovní plochy i pro aplikace pro Windows Store.

Při vývoji knihovny DLL profileru ji považujte za, jako by byla aplikace pro Windows Store, a používejte pouze rozhraní API, která jsou zdokumentována jako dostupná pro aplikace pro Windows Store. Analyzujte závislosti (například můžete spustit `link /dump /imports` s knihovnou DLL profileru pro audit) a potom hledat v dokumentaci, abyste viděli, které z vašich závislostí jsou OK a které nejsou. Ve většině případů je možné opravit porušení pouhým nahrazením novějším formulářem rozhraní API, které je dokumentováno jako bezpečné (například nahrazením [InitializeCriticalSectionAndSpinCount](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionandspincount) pomocí [InitializeCriticalSectionEx](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionex)).

Můžete si všimnout, že vaše knihovna DLL profileru volá některá rozhraní API, která se vztahují jenom na desktopové aplikace, a přesto se zdají fungovat i v případě, že je vaše knihovna DLL profileru načtená v aplikaci pro Windows Store Počítejte s tím, že při načítání do procesu aplikace pro Windows Store je riskantní používat rozhraní API, které není dokumentováno pro použití s aplikacemi pro Windows Store v knihovně DLL profileru:

- Tato rozhraní API nejsou zaručena funkčnost při volání v jedinečném kontextu, ve kterém jsou spuštěny aplikace pro Windows Store.

- Taková rozhraní API nemusí při volání v rámci různých procesů aplikací pro Windows Store fungovat konzistentně.

- Taková rozhraní API se můžou zdát pracovat bez problémů s aplikacemi pro Windows Store v aktuální verzi Windows, ale v budoucích verzích Windows se ale můžou rušit nebo zakázat.

Nejlepším doporučením je opravit všechna porušení a vyhnout se rizikům.

Může se stát, že naprosto nemůžete bez konkrétního rozhraní API dělat a nemůžete najít náhradu vhodnou pro aplikace pro Windows Store. V takovém případě přinejmenším:

- Test, testování, testování živých letních zařízení z vašeho využití tohoto rozhraní API.

- Pochopení, že rozhraní API může být náhle přerušeno nebo zmizí, pokud je voláno z aplikací pro Windows Store v budoucích verzích systému Windows. Tato akce se nepovažuje za problém týkající se kompatibility společnosti Microsoft a podpora jejich použití nebude mít prioritu.

### <a name="reduced-permissions"></a>Omezená oprávnění

Je mimo rámec tohoto tématu, kde jsou uvedeny všechny způsoby, kterými se oprávnění aplikace pro Windows Store liší od aplikací klasické pracovní plochy. Ale určitě se chování bude lišit pokaždé, když se vaše knihovna DLL profileru (když se načte do aplikace pro Windows Store ve srovnání s desktopovou aplikací) pokusí o přístup k žádným prostředkům. Nejběžnějším příkladem je systém souborů. Na disku je ale několik míst, na které má aplikace pro Windows Store přístup povolená (viz [přístup k souborům a oprávnění (prostředí Windows Runtime aplikace](https://docs.microsoft.com/previous-versions/windows/apps/hh967755(v=win.10))) a vaše knihovna DLL profileru se bude shodovat s omezeními. Důkladně otestujte kód.

### <a name="inter-process-communication"></a>Komunikace mezi procesy

Jak je znázorněno v diagramu na začátku tohoto dokumentu, vaše knihovna DLL profileru (načtená do prostoru procesu aplikace pro Windows Store) bude pravděpodobně potřebovat komunikovat s vaším uživatelským rozhraním profileru (spuštěným v samostatném prostoru procesu aplikace klasické pracovní plochy) prostřednictvím vlastního kanálu IPC (Inter-Process Communication). Uživatelské rozhraní profileru odesílá signály do knihovny DLL profileru pro úpravu jejího chování a knihovna DLL profileru odesílá data z analyzované aplikace pro Windows Store zpátky do uživatelského rozhraní profileru pro následné zpracování a zobrazení uživateli profileru.

Většina profilovacích modulů potřebuje tento způsob pracovat, ale pokud je vaše knihovna DLL profileru načtená do aplikace pro Windows Store, jsou možnosti pro mechanismy IPC omezené. Například pojmenované kanály nejsou součástí sady Windows Store app SDK, takže je nemůžete použít.

Ale samozřejmě jsou soubory stále v, i když jsou omezené. K dispozici jsou také události.

**Komunikace prostřednictvím souborů**

Většina vašich dat bude pravděpodobně předána mezi knihovnou DLL profileru a uživatelským rozhraním profileru prostřednictvím souborů. Klíčem je vybrat umístění souboru, ke kterému má vaše knihovna DLL profileru (v kontextu aplikace pro Windows Store) a uživatelského rozhraní profileru přístup pro čtení a zápis. Například cesta k dočasné složce je umístění, ke kterému má přístup vaše knihovna DLL profileru i uživatelské rozhraní profileru, ale přístup k němu nemá žádný jiný balíček aplikace pro Windows Store (proto se chrání všechny informace, které protokolují z jiných balíčků aplikací pro Windows Store).

Tuto cestu můžete určit nezávisle na uživatelském rozhraní profileru i v knihovně DLL profileru. Vaše uživatelské rozhraní profileru při iteraci všemi balíčky nainstalovanými pro aktuálního uživatele (viz ukázkový kód dříve), získá přístup ke `PackageId` třídě, ze které může být cesta k dočasné složce odvozena podobným kódem jako tento fragment. (Jako vždy je kontrola chyb pro zkrácení vynechána.)

```csharp
// C# code for the Profiler UI.
ApplicationData appData =
    ApplicationDataManager.CreateForPackageFamily(
        packageId.FamilyName);

tempDir = appData.TemporaryFolder.Path;
```

Mezitím může vaše knihovna DLL profileru provádět stejné věci, i když ji lze snadno získat <xref:Windows.Storage.ApplicationData> pomocí vlastnosti [ApplicationData. Current](xref:Windows.Storage.ApplicationData.Current%2A) .

**Komunikace prostřednictvím událostí**

Pokud chcete, aby byla sémantika jednoduchého signalizace mezi uživatelským rozhraním profileru a knihovnou DLL profileru, můžete použít události v aplikacích pro Windows Store i v desktopových aplikacích.

Z vaší knihovny DLL profileru můžete jednoduše zavolat funkci [CreateEventEx](/windows/desktop/api/synchapi/nf-synchapi-createeventexa) a vytvořit pojmenovanou událost s libovolným názvem, který chcete. Příklad:

```cpp
// Profiler DLL in Windows Store app (C++).
CreateEventEx(
    NULL,  // Not inherited
    "MyNamedEvent"
    CREATE_EVENT_MANUAL_RESET, /* explicit ResetEvent() required; leave initial state unsignaled */
    EVENT_ALL_ACCESS);
```

Vaše uživatelské rozhraní profileru pak musí najít tuto pojmenovanou událost pod oborem názvů aplikace pro Windows Store. Například vaše uživatelské rozhraní profileru může volat [CreateEventEx](/windows/desktop/api/synchapi/nf-synchapi-createeventexa)a zadat název události jako

`AppContainerNamedObjects\<acSid>\MyNamedEvent`

`<acSid>`je kontejneru AppContainer SID aplikace pro Windows Store. Předchozí část tohoto tématu ukázala, jak iterovat balíčky nainstalované pro aktuálního uživatele. Z tohoto ukázkového kódu můžete získat packageId. A z packageId můžete získat `<acSid>` kód podobný následujícímu:

```csharp
IntPtr acPSID;
DeriveAppContainerSidFromAppContainerName(packageId.FamilyName, out acPSID);

string acSid;
ConvertSidToStringSid(acPSID, out acSid);

string acDir;
GetAppContainerFolderPath(acSid, out acDir);
```

### <a name="no-shutdown-notifications"></a>Žádná oznámení o vypnutí

Při spuštění v aplikaci pro Windows Store by vaše knihovna DLL profileru neměla spoléhat buď na [ICorProfilerCallback:: Shutdown](icorprofilercallback-shutdown-method.md) , nebo dokonce na [DllMain](/windows/desktop/Dlls/dllmain) (with), která `DLL_PROCESS_DETACH` oznamuje vaší knihovně DLL profileru, že se aplikace pro Windows Store ukončuje. Ve skutečnosti byste měli očekávat, že nebudou nikdy volány. Historicky mnoho knihoven DLL profileru používalo tato oznámení jako vhodná místa pro vyprázdnění mezipamětí na disk, zavírání souborů, odesílání oznámení zpět do uživatelského rozhraní profileru atd. Teď ale vaše knihovna DLL profileru musí být uspořádaná trochu odlišně.

Vaše knihovna DLL profileru by měla zaprotokolovat informace v průběhu jejího přechodu. Z důvodů výkonu můžete chtít dávkovat informace v paměti a vyprázdnit je na disk, protože dávka roste velikost po určité prahové hodnotě. Ale předpokládejte, že všechny informace, které ještě nejsou vyčištěné na disk, se můžou ztratit. To znamená, že budete chtít, aby se prahová hodnota vybrala i v případě, že vaše uživatelské rozhraní profileru musí být posílené, aby se zapsaly neúplné informace napsané knihovnou DLL profileru

## <a name="windows-runtime-metadata-files"></a>prostředí Windows Runtime soubory metadat

Je mimo rozsah tohoto dokumentu, aby se mohl detailně přejít na to, co jsou soubory prostředí Windows Runtimech metadat (WinMD). Tato část je omezená na to, jak rozhraní API profilace CLR reaguje, když jsou soubory WinMD načteny aplikací pro Windows Store, které vaše Profilerová knihovna DLL analyzuje.

### <a name="managed-and-non-managed-winmds"></a>Spravované a nespravované soubory WinMD

Pokud vývojář používá sadu Visual Studio k vytvoření nového projektu komponenty prostředí Windows Runtime, sestavení tohoto projektu vytvoří soubor WinMD, který popisuje metadata (popisy typů tříd, rozhraní atd.) vytvořené vývojářem. Pokud je tento projekt projekt spravovaného jazyka napsaný v jazyce C# nebo Visual Basic, stejný soubor WinMD také obsahuje implementaci těchto typů (to znamená, že obsahuje všechny IL zkompilované ze zdrojového kódu vývojáře). Takové soubory se nazývají spravované soubory WinMD. Jsou zajímavé v tom, že obsahují jak metadata prostředí Windows Runtime, tak i základní implementaci.

Naopak pokud vývojář vytvoří projekt komponenty prostředí Windows Runtime pro jazyk C++, sestavení tohoto projektu vytvoří soubor WinMD, který obsahuje pouze metadata a implementace je zkompilována do samostatné nativní knihovny DLL. Podobně soubory WinMD dodávané v Windows SDK obsahují pouze metadata a implementace je zkompilována do samostatných nativních knihoven DLL, které jsou dodávány jako součást systému Windows.

Níže uvedené informace se vztahují na spravované soubory WinMD, které obsahují metadata a implementace, a na nespravované soubory WinMD, které obsahují jenom metadata.

### <a name="winmd-files-look-like-clr-modules"></a>Soubory WinMD vypadají jako moduly CLR

V případě, že je dotyčný modul CLR, jsou všechny soubory WinMD moduly. Rozhraní API profilování CLR proto říká vaší knihovně DLL profileru, když soubory WinMD načtou a co jejich ModuleIDs jsou, stejně jako pro jiné spravované moduly.

Vaše knihovna DLL profileru může odlišit soubory WinMD z jiných modulů voláním metody [ICorProfilerInfo3:: GetModuleInfo2 –](icorprofilerinfo3-getmoduleinfo2-method.md) a kontrolou `pdwModuleFlags` výstupního parametru pro příznak [COR_PRF_MODULE_WINDOWS_RUNTIME](cor-prf-module-flags-enumeration.md) . (To je nastaveno pouze v případě, že ModuleID představuje WinMD.)

### <a name="reading-metadata-from-winmds"></a>Čtení metadat z soubory WinMD

Soubory WinMD, jako jsou běžné moduly, obsahují metadata, která lze číst prostřednictvím [rozhraní API metadat](../metadata/index.md). Modul CLR však mapuje prostředí Windows Runtime typy pro .NET Framework typů při čtení souborů WinMD, takže vývojáři, kteří programují spravovaný kód a využívají soubor WinMD, mohou mít přirozenější programovací prostředí. Některé příklady těchto mapování najdete v tématu [.NET Framework podpoře aplikací pro Windows Store a prostředí Windows Runtime](../../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md).

Takže zobrazení, které váš Profiler získá, když používá rozhraní API metadat: zobrazení nezpracovaná prostředí Windows Runtime nebo namapované .NET Framework zobrazení?  Odpověď: je to na vás.

Při volání metody [ICorProfilerInfo:: GetModuleMetaData –](icorprofilerinfo-getmodulemetadata-method.md) na winmd pro získání rozhraní metadat, jako je například [IMetaDataImport](../metadata/imetadataimport-interface.md), se můžete rozhodnout pro nastavení [ofNoTransform](../metadata/coropenflags-enumeration.md) v `dwOpenFlags` parametru pro vypnutí tohoto mapování. V opačném případě se ve výchozím nastavení povolí mapování. Profiler obvykle zachová povolené mapování, aby řetězce, které knihovna DLL profileru získá z metadat WinMD (například názvy typů), vypadaly i pro uživatele profileru jako známé a přirozené.

### <a name="modifying-metadata-from-winmds"></a>Úprava metadat z soubory WinMD

Úprava metadat v soubory WinMD se nepodporuje. Pokud zavoláte metodu [ICorProfilerInfo:: GetModuleMetaData –](icorprofilerinfo-getmodulemetadata-method.md) pro soubor winmd a v parametru [ofWrite](../metadata/coropenflags-enumeration.md) určíte ofWrite `dwOpenFlags` nebo požádáte o rozhraní zapisovatelného metadat, jako je například [IMetaDataEmit](../metadata/imetadataemit-interface.md), [GetModuleMetaData –](icorprofilerinfo-getmodulemetadata-method.md) se nezdaří. To je obzvláště důležité pro přepisování profilerů, které potřebují měnit metadata pro podporu jejich instrumentace (například pro přidání AssemblyRefs nebo nových metod). Proto byste měli nejdříve vyhledat [COR_PRF_MODULE_WINDOWS_RUNTIME](cor-prf-module-flags-enumeration.md) (jak je popsáno v předchozí části) a upustit od vyžádání rozhraní metadat s možností zápisu v těchto modulech.

### <a name="resolving-assembly-references-with-winmds"></a>Překládání odkazů na sestavení pomocí soubory WinMD

Mnoho profilerů potřebuje ručně vyřešit odkazy na metadata, aby bylo možné pomoci s instrumentací nebo kontrolou typu. Tyto profilery potřebují vědět, jak CLR překládá odkazy na sestavení, které odkazují na soubory WinMD, protože tyto odkazy jsou vyřešeny úplně jiným způsobem než standardní odkazy na sestavení.

## <a name="memory-profilers"></a>Profily paměti

Systém uvolňování paměti a spravovaná halda se v aplikaci pro Windows Store a desktopové aplikaci neliší. Existuje však několik drobných rozdílů, o kterých autoři profilerů potřebují vědět.

### <a name="forcegc-creates-a-managed-thread"></a>ForceGC – vytvoří spravované vlákno.

Při provádění profilování paměti vaše knihovna DLL profileru obvykle vytvoří samostatné vlákno, ze kterého se má volat metoda [ForceGC – metody](icorprofilerinfo-forcegc-method.md) . Nejedná se o nic nového. Ale to, co může být překvapivé, je, že úkony uvolňování paměti uvnitř aplikace pro Windows Store mohou transformovat vlákno do spravovaného vlákna (například pro toto vlákno bude vytvořeno IDvlákna rozhraní API pro profilování).

Pro pochopení důsledků tohoto je důležité porozumět rozdílům mezi synchronním a asynchronním voláním, jak je definováno rozhraním API profilace CLR. Všimněte si, že se velmi liší od konceptu asynchronních volání v aplikacích pro Windows Store. Další informace najdete v blogovém příspěvku o tom, [Proč máme CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](https://docs.microsoft.com/archive/blogs/davbr/why-we-have-corprof_e_unsupported_call_sequence) .

Relevantním bodem je, že volání prováděná na vláknech vytvořených vaším profilerem jsou vždy považována za synchronní, i když jsou tato volání vytvořena mimo implementaci jedné z metod [ICORPROFILERCALLBACK](icorprofilercallback-interface.md) knihovny profileru. Aspoň, který se používá pro případ. Nyní, když modul CLR přepnul vlákno profileru do spravovaného vlákna kvůli volání [metody ForceGC –](icorprofilerinfo-forcegc-method.md), toto vlákno již není považováno za vlákno profileru. V takovém případě CLR vynutil přísnější definici toho, co je pro vlákno považováno za synchronní – konkrétně to, že volání musí pocházet z jedné z metod [ICorProfilerCallback](icorprofilercallback-interface.md) vašich knihoven DLL profileru, které mají být kvalifikovány jako synchronní.

Co to znamená v praxi? Většinu metod [ICorProfilerInfo](icorprofilerinfo-interface.md) je bezpečné volat pouze synchronně a v opačném případě dojde k chybě okamžitě. Takže pokud vaše knihovna DLL profileru znovu používá vlákno [metody ForceGC –](icorprofilerinfo-forcegc-method.md) pro jiná volání obvykle vytvořená na vláknech vytvořených profilerem (například na [RequestProfilerDetach](icorprofilerinfo3-requestprofilerdetach-method.md), [RequestReJIT –](icorprofilerinfo4-requestrejit-method.md)nebo [RequestRevert –](icorprofilerinfo4-requestrevert-method.md)), budete mít potíže. I funkce asynchronního zabezpečení, jako je [DoStackSnapshot –](icorprofilerinfo2-dostacksnapshot-method.md) , má při volání ze spravovaných vláken zvláštní pravidla. (Další informace najdete v blogovém příspěvku [zásobníku profileru: základy a](https://docs.microsoft.com/archive/blogs/davbr/profiler-stack-walking-basics-and-beyond) více.)

Proto doporučujeme, aby v každém vlákně, které vaše knihovna DLL profileru vytvoří volání [metody ForceGC –](icorprofilerinfo-forcegc-method.md) , měla být použita *pouze* pro účely aktivace GC a přestala reagovat na zpětná volání GC. Neměl by volat rozhraní API profilování, aby prováděl jiné úkoly, jako vzorkování zásobníku nebo odpojení.

### <a name="conditionalweaktablereferences"></a>ConditionalWeakTableReferences

Počínaje .NET Framework 4,5 se nachází nové zpětné volání GC [ConditionalWeakTableElementReferences –](icorprofilercallback5-conditionalweaktableelementreferences-method.md), které poskytuje profileru úplnější informace o *závislých popisovačích*. Tyto popisovače efektivně přidávají odkaz ze zdrojového objektu do cílového objektu pro účely správy životnosti GC. Závislé obslužné rutiny nejsou žádné nové a vývojáři, kteří program ve spravovaném kódu, mohou vytvořit vlastní závislé obslužné rutiny pomocí <xref:System.Runtime.CompilerServices.ConditionalWeakTable%602?displayProperty=nameWithType> třídy, a to i před Windows 8 a .NET Framework 4,5.

Spravované aplikace pro Windows Store v jazyce XAML teď ale výrazně využívají závislé obslužné rutiny. Konkrétně je modul CLR používá pro pomoc se správou referenčních cyklů mezi spravovanými objekty a nespravovanými prostředí Windows Runtime objekty. To znamená, že je nyní důležitější než dřív, aby byly profily paměti informované o těchto závislých popisovačích, aby je bylo možné vizuálně rozlišit s ostatními okraji v grafu haldy. Vaše knihovna DLL profileru by měla používat [RootReferences2 –](icorprofilercallback2-rootreferences2-method.md), [objectReferences –](icorprofilercallback-objectreferences-method.md)a [ConditionalWeakTableElementReferences –](icorprofilercallback5-conditionalweaktableelementreferences-method.md) společně pro vytvoření kompletního zobrazení grafu haldy.

## <a name="conclusion"></a>Závěr

Je možné použít rozhraní API profilování CLR k analýze spravovaného kódu spuštěného v aplikacích pro Windows Store. Ve skutečnosti můžete převzít existující Profiler, který vyvíjíte, a udělat určité konkrétní změny, aby bylo možné cílit na aplikace pro Windows Store. Vaše uživatelské rozhraní profileru by mělo používat nová rozhraní API pro aktivaci aplikace pro Windows Store v režimu ladění. Ujistěte se, že vaše knihovna DLL profileru spotřebovává jenom rozhraní API platná pro aplikace pro Windows Store. Mechanismus komunikace mezi knihovnou DLL profileru a uživatelským rozhraním profileru by se měl zapsat pomocí omezení rozhraní API pro aplikace pro Windows Store a s vědomím omezených oprávnění, která jsou na místě pro aplikace pro Windows Store. Vaše knihovna DLL profileru by měla vědět, jak CLR zpracovává soubory WinMD a jak se chování systému uvolňování paměti liší v závislosti na spravovaných vláknech.

## <a name="resources"></a>Zdroje a prostředky

**Modul CLR (Common Language Runtime)**

- [Profilace (odkaz na nespravované rozhraní API)](index.md)

- [Metadata (nespravované reference rozhraní API)](../metadata/index.md)

**Interakce CLR s prostředí Windows Runtime**

- [Podpora pro aplikace pro web Windows Store a prostředí Windows Runtime v rozhraní .NET Framework](../../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)

**Aplikace pro Windows Store**

- [Přístup k souborům a oprávnění (prostředí Windows Runtime aplikace](https://docs.microsoft.com/previous-versions/windows/apps/hh967755%28v=win.10%29)

- [Získat vývojářskou licenci](https://docs.microsoft.com/previous-versions/windows/apps/hh974578%28v=win.10%29)

- [Rozhraní IPackageDebugSettings](/windows/desktop/api/shobjidl_core/nn-shobjidl_core-ipackagedebugsettings)
