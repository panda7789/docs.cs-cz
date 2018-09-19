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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1747d99fbfbc31fb592aee570d10d574b8480b0
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46009796"
---
# <a name="clr-profilers-and-windows-store-apps"></a>Profilery CLR a aplikace pro Windows Store

Toto téma popisuje, co potřebujete zvážit při psaní diagnostické nástroje, které analyzují spravovaný kód běžící uvnitř aplikace Windows Store.  Také poskytuje pokyny k úpravě svoje stávající nástroje pro vývoj, budou nadále fungovat při spuštění před aplikací pro Windows Store.  Chcete-li tyto informace pochopili, je nejlepší, že pokud jste obeznámeni s rozhraním Common Language Runtime profilování API, jste už použili toto rozhraní API v diagnostický nástroj, že běží správně proti aplikací klasické pracovní plochy Windows a teď zajímá. Úprava nástroj Chcete-li spustit správně pro aplikace Windows Store.  
  
## <a name="introduction"></a>Úvod

 Pokud jste provedli za úvodní odstavec, pak už znáte rozhraní API profilování CLR.  Už jste napsali diagnostický nástroj, který funguje dobře na spravované aplikace klasické pracovní plochy.  Teď vás to zajímá, co dělat, tak, aby nástroj funguje se spravovanými aplikacemi pro Windows Store.  Možná jste již zkusili této práci, a zjistili, že není jednoduchý úkol.  Ve skutečnosti existuje několik aspektů, které nemusí být zřejmé všechny nástroje pro vývojáře.  Příklad:  
  
-   Aplikace Windows Store spustit v kontextu se vážně sníženými oprávněními.  
  
-   Soubory metadat Windows mají jedinečné charakteristiky ve srovnání s tradičním spravované moduly.  
  
-   Aplikace Windows Store mají aktualitách sami pozastavení při interaktivitu ocitne mimo provoz.  
  
-   Už nemusí fungovat váš mechanismus meziprocesové komunikace z různých důvodů.  
  
 Toto téma obsahuje seznam věcí, které je potřeba mít na paměti a jak zacházet s nimi správně.  
  
 Pokud jste novými uživateli rozhraní API profilování CLR, přejděte dolů zdrojů na konci tohoto tématu pro vyhledání lépe úvodní informace.  
  
 Poskytuje podrobnosti o konkrétní rozhraní API Windows a jak mají být použity také sahá nad rámec tohoto tématu.  Vezměte v úvahu výchozí bod v tomto tématu a odkazovat na webu MSDN získat další informace o libovolné rozhraní Windows API odkazujete.  
  
## <a name="architecture-and-terminology"></a>Architektura a terminologie

 Diagnostický nástroj obvykle obsahuje architekturu podobný jako na následujícím obrázku. Používá termín "profiler", ale mnoho takových nástrojů přejít i nad rámec typické výkonu nebo profilování paměti do oblastí, například pokrytí kódu, napodobení objektu rozhraní, čas cesty ladění aplikace pro monitorování a tak dále.  Pro jednoduchost Toto téma bude i dál odkazovat na všechny tyto nástroje jako profilovací programy.  
  
 V tomto tématu se používá následující terminologií:  
  
**Aplikace**

Toto je aplikace, která analyzuje profileru.  Obvykle vývojář této aplikace je teď používá profiler pro usnadnění diagnostiky potíží s aplikací.  Tradičně tato aplikace by aplikace klasické pracovní plochy Windows, ale v tomto tématu jsme se podíváte na aplikace Windows Store.  
  
**Profiler DLL**

Toto je komponenta, která načte do procesního prostoru aplikace analyzován.  Tuto součást, označované také jako "agent" profileru implementuje [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)[icorprofilercallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)(2,3, atd.) rozhraní a využívá [ ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)(2,3, atd.) rozhraní ke shromažďování dat o aplikaci, analýze a potenciálně změnit aspekty chování aplikace.  
  
**Profiler uživatelského rozhraní**

Toto je desktopová aplikace, profiler uživatel komunikuje.  Je zodpovědná za zobrazení stavu aplikace pro uživatele a poskytnou tak uživateli způsob, jak řídit chování analyzované aplikace.  Tato součást se vždy spouští ve vlastním procesu prostoru oddělené od procesního prostoru aplikace, které je právě profilována.  Profiler uživatelského rozhraní se mohou chovat i jako "připojit aktivační událost," to je proces, který volá [ICLRProfiling::AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) způsobit analyzované aplikaci načíst knihovnu DLL Profiler v těchto případech, kde je knihovna DLL profileru nebyl – metoda načíst při spuštění.  
  
> [!IMPORTANT]
> Vaše uživatelské rozhraní Profiler by měla zůstat v případě aplikace klasické pracovní plochy Windows i v případě, že se používá k řízení a vytváření sestav v aplikaci Windows Store.  Neočekáváme, že balíček a dodávejte vaše Diagnostika ve Windows Store.  Nástroj se musí provádět operace, které aplikace Windows Store nelze provádět, a řada těchto věcí, které jsou umístěné v Profiler uživatelské rozhraní.  
  
 V tomto dokumentu vzorový kód předpokládá, že:  
  
- Vaše knihovna DLL Profiler je napsaný v jazyce C++, protože musí být nativní knihovnu DLL, podle požadavků rozhraní API profilování CLR.  
  
- Vaše uživatelské rozhraní Profiler je napsána v jazyce C#.  To není nezbytné, ale vzhledem k tomu, že neexistují žádné požadavky na jazyk pro proces Profiler uživatelského rozhraní, případně proč bezpečná není vyberte jazyk, který je stručnějším a jednoduché?  
  
### <a name="windows-rt-devices"></a>Zařízení s Windows RT.

Zařízení s Windows RT se poměrně uzamčen.  Profilovací programy třetích stran jednoduše nelze načíst k takovým zařízením.  Tento dokument se zaměřuje na počítačích s Windows 8.  
  
## <a name="consuming-windows-runtime-apis"></a>Používání rozhraní API Windows Runtime

 Profiler uživatelského rozhraní aplikace klasické pracovní plochy v řadě scénářů, které jsou popsané v následujících částech, musí využívat některé nové rozhraní API Windows Runtime.  Budete chtít najdete v dokumentaci k pochopení, které rozhraní API Windows Runtime lze používat z aplikací klasické pracovní plochy a zda jejich chování se liší při volat z aplikací klasické pracovní plochy a Windows Store apps.  
  
 Pokud Profiler uživatelské rozhraní je zapsána ve spravovaném kódu, bude existovat několik kroků, které je potřeba udělat, aby využívání těchto snadno Windows Runtime pro rozhraní API.  Zobrazit [spravované aplikace klasické pracovní plochy a prostředí Windows Runtime](https://go.microsoft.com/fwlink/?LinkID=271858) najdete další informace.  
  
## <a name="loading-the-profiler-dll"></a>Načítají se Profiler DLL

 Tato část popisuje, jak způsobí, že Profiler uživatelské rozhraní aplikace Windows Store k načtení knihovny DLL Profiler.  Kód popsaných v této části patří v desktopové aplikaci Profiler uživatelského rozhraní a proto je použít rozhraní Windows API, která jsou bezpečná pro aplikace klasické pracovní plochy, ale ne nutně bezpečné pro přístup z aplikace Windows Store.  
  
 Vaše uživatelské rozhraní Profiler může způsobit vaše knihovna DLL Profiler, který se má načíst do procesního prostoru aplikace dvěma způsoby:  
  
-   Při spuštění aplikace, protože řídí proměnné prostředí.  
  
-   Připojením k aplikaci po dokončení spuštění voláním [ICLRProfiling::AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) metody.  
  
 Jeden z prvních problémů, budou se zobrazovat zatížení při spuštění a připojení a načtení knihovny DLL Profiler správně pracovat s aplikacemi pro Windows Store.  Obě formy načítání v běžných sdílení některých zvláštních pokynů, součástem Začneme s nimi.  
  
### <a name="common-considerations-for-startup-and-attach-loads"></a>Častá rozhodnutí při spuštění a připojení zatížení

 **Podepisování váš Profiler knihovny DLL**  
 Když se Windows pokusí se načíst vaše knihovna DLL Profiler, tak ověří, že váš Profiler knihovny DLL je správně podepsaná.  V opačném případě zatížení selže ve výchozím nastavení. Toto lze provést dvěma způsoby:  
  
-   Ujistěte se, že váš Profiler knihovny DLL je podepsané.  
  
-   Informujte uživatele, že musí nainstalovat vývojářskou licenci na Windows 8 počítači před pomocí nástrojů.  To můžete udělat automaticky ze sady Visual Studio, nebo ručně z příkazového řádku.  Další informace najdete v tématu [získat vývojářskou licenci](https://msdn.microsoft.com/library/windows/apps/Hh974578.aspx).  
  
 **Oprávnění systému souborů**  
 Aplikace Windows Store musí mít oprávnění k načtení a provedení váš Profiler knihovny DLL z umístění v systému souborů, ve kterém se nachází.  Ve výchozím nastavení aplikace Windows Store nemá povolení na většině adresáře a jakékoli neúspěšné pokusy o načtení knihovny DLL Profiler vytvoří záznam v protokolu událostí aplikace Windows, která vypadá přibližně takto:  
  
```Output  
NET Runtime version 4.0.30319.17929 - Loading profiler failed during CoCreateInstance.  Profiler CLSID: '{xxxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx}'.  HRESULT: 0x80070005.  Process ID (decimal): 4688.  Message ID: [0x2504].  
```  
  
 Obecně platí Windows Store apps jsou povolené jenom pro přístup k omezené sadě místa na disku.  Každá aplikace Windows Store můžete přístup k vlastní složek s daty aplikací, jakož i několik dalších oblastí v systému souborů, u kterého jsou všechny aplikace Windows Store udělen přístup.  Doporučujeme nainstalovat knihovny DLL Profiler a jeho závislosti někde v rámci Program Files nebo Program Files (x86), protože všechny aplikace Windows Store mají oprávnění číst a spouštět existuje ve výchozím nastavení.  
  
### <a name="startup-load"></a>Po spuštění zatížení

 Obvykle v desktopové aplikaci, váš Profiler uživatelského rozhraní dotaz spuštění načtení knihovny DLL Profiler inicializace blok prostředí, který obsahuje požadované proměnné prostředí rozhraní API profilování CLR (to znamená `COR_PROFILER`, `COR_ENABLE_PROFILING`, a `COR_PROFILER_PATH`), a pak se tento blok prostředí vytvořit nový proces.  To samé platí pro aplikace Windows Store, ale mechanismy se liší.  
  
 **Při spuštění se zvýšenými oprávněními**  
 Pokud proces pokusí spustit aplikaci Windows Store B procesu, proces A měl být spuštěn v střední integrity úrovně, ne na úrovni vysokou integritu (který je, není se zvýšenými oprávněními).  To znamená, že vaše uživatelské rozhraní Profiler by měl být spuštěn na střední úrovni integrity, nebo se musí vytvořit podřízený jiný proces klasické pracovní plochy na střední úrovni integrity pro postará o spuštění aplikace Windows Store.  
  
 **Výběr aplikace Windows Store do profilu**  
 Nejprve budete chtít požádat uživatele, váš profiler která aplikace Windows Store spustit.  Pro aplikace klasické pracovní plochy případně by zobrazil dialogové okno Procházet souboru a uživatel by vyhledejte a vyberte soubor s příponou .exe.  Ale aplikace Windows Store se liší a pomocí dialogového okna procházení nedává smysl.  Místo toho je lepší uživateli zobrazit seznam nainstalovaných pro tohoto uživatele můžete vybírat z aplikací pro Windows Store.  
  
 Můžete použít [PackageManager třídy](https://msdn.microsoft.com/library/windows/apps/windows.management.deployment.packagemanager.aspx) k vygenerování tohoto seznamu.  `PackageManager` je třída Windows Runtime, která je k dispozici pro aplikace klasické pracovní plochy a je ve skutečnosti *pouze* k dispozici pro aplikace klasické pracovní plochy.  
  
 Následující příklad kód z hypotetické uživatelského rozhraní Profiler zapsán jako desktopové aplikace v C# yses `PackageManager` vytvořit seznam aplikací pro Windows:  
  
```csharp  
string currentUserSID = WindowsIdentity.GetCurrent().User.ToString();  
IAppxFactory appxFactory = (IAppxFactory) new AppxFactory();  
PackageManager packageManager = new PackageManager();  
IEnumerable<Package> packages = packageManager.FindPackagesForUser(currentUserSID);  
```  
  
 **Určení blok vlastní prostředí**  
 Nové rozhraní modelu COM, [IPackageDebugSettings](https://msdn.microsoft.com/library/hh438393\(v=vs.85\).aspx), vám umožní přizpůsobit chování při spuštění aplikace pro Windows Store pro usnadnění některé formy diagnostiky.  Jeden z jeho metod [EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=vs.85\).aspx), umožňuje předat blok prostředí do aplikace Windows Store, při jeho spuštění, společně s další užitečné efekty třeba zákaz automatického procesu pozastavení.  Blok prostředí je důležité, protože se jedná, které je potřeba zadat proměnné prostředí (`COR_PROFILER`, `COR_ENABLE_PROFILING`, a `COR_PROFILER_PATH)`) používaná platformou CLR pro načtení knihovny DLL Profiler.  
  
 Vezměte v úvahu následující fragment kódu:  
  
```csharp  
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();  
pkgDebugSettings.EnableDebugging(packgeFullName, debuggerCommandLine,   
                                                                 (IntPtr)fixedEnvironmentPzz);  
```  
  
 Existuje několik položek, které je potřeba získat vpravo:  
  
-   `packageFullName` Během iterace s balíčky a že se dá určit `package.Id.FullName`.  
  
-   `debuggerCommandLine` je o něco zajímavější.  Chcete-li předat blok vlastní prostředí pro aplikace Windows Store, budete muset napsat vlastní, zjednodušenou fiktivní ladicího programu.  Aplikace Windows Store následujícímu Windows tření pozastavení a potom připojí ladicí program spusťte ladicí program pomocí příkazového řádku jako v tomto příkladu:  
  
    ```Output  
    MyDummyDebugger.exe -p 1336 -tid 1424  
    ```  
  
     kde `-p 1336` znamená, že k němu má aplikace Windows Store. 1336 ID procesu, a `-tid 1424` znamená, že 1424 ID vlákna je vlákno, které je pozastaveno.  Fiktivní ladicí program by analyzovat Idvlákna z příkazového řádku a obnovení bylo vlákno a poté ukončete.  
  
     Tady je několik příkladů kódu jazyka C++ k tomu (Nezapomeňte přidat kontrolu chyb!):  
  
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
  
     Budete muset nasadit tuto fiktivní ladicí program jako součást vaší instalace nástroje pro diagnostiku a poté zadejte cestu k tímto ladicím programem v `debuggerCommandLine` parametru.  
  
 **Spuštění aplikace Windows Store**  
 Nakonec dorazila chvíli spustit aplikaci Windows Store. Pokud jste již již zkusili dělat sami, mohli jste si všimnout, který [CreateProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessa) není jak vytvořit proces aplikace Windows Store.  Místo toho budete muset použít [IApplicationActivationManager::ActivateApplication](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-iapplicationactivationmanager-activateapplication) metody.  K tomuto účelu, budete muset získat ID modelu uživatele aplikace, která je spuštěna aplikace Windows Store.  A to znamená, že budete muset udělat pár si prostřednictvím manifest.  
  
 Během iterace s použitím vašich balíčků (naleznete v části "Volba Windows Store do profilu aplikace" v [spuštění zatížení](#Startup) výše v části), je vhodné vzít sadu aplikací, které jsou součástí manifestu aktuální balíček:  
  
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
  
 Ano, jeden balíček může mít více aplikací, a každá aplikace má vlastní ID modelu uživatele aplikace.  Proto budete chtít požádat vašeho uživatele, která aplikace do profilu a získejte ID modelu uživatele aplikace z konkrétní aplikaci:  
  
```csharp  
while (appsEnum.GetHasCurrent() != 0)  
{  
    IAppxManifestApplication app = appsEnum.GetCurrent();  
    string appUserModelId = app.GetAppUserModelId();  
    //...
}
```  
  
 A konečně můžete teď mít co je potřeba spustit aplikaci Windows Store:  
  
```csharp  
IApplicationActivationManager appActivationMgr = new ApplicationActivationManager();  
appActivationMgr.ActivateApplication(appUserModelId, appArgs, ACTIVATEOPTIONS.AO_NONE, out pid);  
```  
  
 **Nezapomeňte volat DisableDebugging**  
 Když jste volali [IPackageDebugSettings::EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=VS.85\).aspx), provedli promise, který by se vyčištění po sobě voláním [IPackageDebugSettings::DisableDebugging](https://msdn.microsoft.com/library/hh438394\(v=vs.85\).aspx) metoda, takže je nutné provést Když je relace profilování.  
  
### <a name="attach-load"></a>Připojit zatížení

 Když Profiler uživatelské rozhraní se chce připojit své DLL Profiler k aplikaci, která byla již spuštěna, používá [ICLRProfiling::AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md).  To samé platí s aplikacemi pro Windows Store.  Ale kromě častá rozhodnutí při výše uvedených Ujistěte se, že není pozastavené cílové aplikace Windows Store.  
  
 **EnableDebugging**  
 Stejně jako u zatížení po spuštění, zavolejte [IPackageDebugSettings::EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=VS.85\).aspx) metody.  Nepotřebujete předávání blok prostředí, ale budete potřebovat jeden z jejích funkcí: Zakázání automatického procesu pozastavení.  Jinak, když vaše uživatelské rozhraní Profiler volá [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md), může být pozastavený cílové aplikace Windows Store.  Ve skutečnosti to je pravděpodobně Pokud uživatel je nyní interakci s Profiler uživatelské rozhraní a aplikací Windows Store není aktivní na všech obrazovkách uživatele.  A pokud se Windows Store je aplikace pozastavená, nebude moct reagovat na všechny signál, že modul CLR odešle k němu připojit Profiler knihovny DLL.  
  
 Proto je vhodné provést vypadat přibližně takto:  
  
```csharp  
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();  
pkgDebugSettings.EnableDebugging(packgeFullName, null /* debuggerCommandLine */,   
                                                                 IntPtr.Zero /* environment */);  
```  
  
 Toto je stejný volání, které by provedete pro případ zatížení po spuštění, s výjimkou nezadáte ladicí program příkazového řádku nebo z bloku prostředí.  
  
 **DisableDebugging**  
 Jako vždy, nezapomeňte volat [IPackageDebugSettings::DisableDebugging](https://msdn.microsoft.com/library/hh438394\(v=vs.85\).aspx) dokončení vaší relace profilování.  
  
<a name="Running"></a>   
## <a name="running-inside-the-windows-store-app"></a>Spuštění v aplikaci Windows Store  
 Aplikace Windows Store tak nakonec načetl váš Profiler knihovny DLL.  Nyní je vaše knihovna DLL Profiler musí být museli pokyny pro hru pomocí různých pravidel vyžadované aplikací Windows Store, včetně, které jsou povolené rozhraní API a jak spouštět s nižší oprávnění.  
  
<a name="APIs"></a>   
### <a name="stick-to-the-windows-store-app-apis"></a>Zůstaňte na rozhraní API pro aplikace Windows Store  
 Při procházení rozhraní Windows API, můžete si všimnout, že každé rozhraní API je popsána jako použitelné pro aplikace klasické pracovní plochy, aplikace Windows Store nebo obojí.  Například **požadavky** část dokumentace pro [InitializeCriticalSectionAndSpinCount](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionandspincount) funkce naznačuje, že funkce používá k pouze aplikace klasické pracovní plochy. Oproti tomu [InitializeCriticalSectionEx](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionex) funkce je k dispozici pro aplikace klasické pracovní plochy a aplikace Windows Store.  
  
 Při vývoji vaší knihovny DLL Profiler, jednejte s ním jako v případě, že je aplikace pro Windows Store a pouze použití rozhraní API, která jsou popsaná jako k dispozici pro aplikace Windows Store.  Analýza závislostí (například můžete spustit `link /dump /imports` proti vaší knihovny DLL Profiler auditování) a potom je prohledejte dokumentace, které závislosti jsou v pořádku a které nejsou.  Ve většině případů lze napravit porušení vašich zásad a nahradí je jednoduše s formuláři novější rozhraní API, které jsou uvedené jako bezpečná (například nahrazení [InitializeCriticalSectionAndSpinCount](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionandspincount) s [ InitializeCriticalSectionEx](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionex)).  
  
 Můžete si všimnout, že vaše knihovna DLL Profiler volá některá rozhraní API, která se vztahují pouze aplikace klasické pracovní plochy a ještě se zdá se, že fungovat i při načtení knihovny DLL Profiler v aplikaci Windows Store.  Mějte na paměti, že se jedná o rizikové použití jakéhokoli rozhraní API není dokumentováno pro použití s aplikacemi pro Windows Store v váš Profiler knihovny DLL při načtení do procesu aplikace Windows Store:  
  
-   Tato rozhraní API zaručené fungování při volání v rámci jedinečný aplikace Windows Store běžet.  
  
-   Tato rozhraní API nemusí fungovat konzistentně při volání z v rámci různých procesů aplikace Windows Store.  
  
-   Tato rozhraní API zdát, že fungovat bez problémů z aplikace Windows Store v aktuální verzi Windows, ale mohou přestat fungovat nebo zakázat v budoucích verzích Windows.  
  
 Nejlepší Rada je opravit všechna narušení a nedošlo k ohrožení.  
  
 Můžete zjistit, že naprosto nejde provést bez dané rozhraní API a nemůžete najít náhradní vhodné pro aplikace Windows Store.  V takovém případě se minimálně:  
  
-   Testování, testování, testování daylights živých z vašeho používání tohoto rozhraní API.  
  
-   Vysvětlení, že rozhraní API může najednou přerušení nebo zmizí, pokud je volána z ve Windows Store apps v budoucích vezích se z Windows.  Nepovažuje se týkají kompatibility společností Microsoft a podporu jeho využití nebudou prioritu.  
  
### <a name="reduced-permissions"></a>Sníženými oprávněními

 Jde nad rámec tohoto tématu, chcete-li vypsat všechny způsoby, kterými oprávnění aplikace Windows Store se liší od aplikací klasické pracovní plochy.  Ale určitě chování se bude lišit při každém váš Profiler knihovny DLL (při načtení do aplikace Windows Store v porovnání s aplikace klasické pracovní plochy) pokusí o přístup ke všem prostředkům.  Systém souborů je Nejběžnějším příkladem.  Existuje ale několik místa na disku, který je povolen přístup k dané aplikaci Windows Store (naleznete v tématu [souborů přístup a oprávnění (aplikace Windows Runtime](https://msdn.microsoft.com/library/windows/apps/hh967755.aspx)), váš Profiler knihovny DLL bude v rámci omezení.  Důkladně otestujte váš kód.  
  
### <a name="inter-process-communication"></a>Komunikace mezi procesy

 Jak je znázorněno na diagramu na začátku tohoto dokumentu, váš Profiler knihovny DLL (načíst do procesního prostoru aplikace Windows Store) bude pravděpodobně nutné pro komunikaci s Profiler uživatelské rozhraní (spuštěné v prostoru procesu samostatné aplikace klasické pracovní plochy) vlastního procesu mezi kanál komunikace (IPC).  Uživatelské rozhraní Profiler odešle signály na Profiler DLL změnit její chování a knihovny DLL Profiler odešle data z analyzovaných aplikace Windows Store zpět na uživatelské rozhraní Profiler pro následné zpracování a zobrazuje uživateli profileru.  
  
 Většina profilery potřeba, abyste tímto způsobem, ale vaše možnosti pro mechanismy IPC jsou omezenější, váš Profiler knihovny DLL při načtení do aplikace Windows Store.  Například pojmenovaných kanálů nejsou součástí Windows Store app SDK, takže nelze je použít.  
  
 Ale samozřejmě soubory jsou stále v byť způsobem omezenější.  Události jsou také k dispozici.  
  
 **Komunikaci přes soubory**  
 Většina dat předá pravděpodobně mezi knihovnou Profiler DLL a Profiler uživatelského rozhraní pomocí souborů.  Klíč je k výběru umístění souborů, které váš Profiler knihovny DLL (v rámci aplikace pro Windows Store) a Profiler uživatelského rozhraní si přečetl(a) a přístup pro zápis.  Například cesta dočasné složky je umístění, které knihovny DLL Profiler a Profiler uživatelského rozhraní, ale žádné jiné balíčky pro aplikace Windows Store můžete přistupovat k (tím ochránit veškeré informace, které se přihlašují z jiných balíčků aplikací Windows Store).  
  
 Profiler uživatelského rozhraní a knihovny DLL Profiler může určit tuto cestu nezávisle na sobě.  Profiler uživatelské rozhraní, když Iteruje přes všechny balíčky nainstalované pro aktuální uživatel (viz dříve ukázkového kódu), získá přístup k `PackageId` třída, ze kterého mohou být odvozeny cesta dočasné složky s kódem, podobně jako tento fragment kódu.  (Jako vždy kontrolu chyb pro zkrácení je vynecháno.)  
  
```csharp  
// C# code for the Profiler UI.  
ApplicationData appData =  
    ApplicationDataManager.CreateForPackageFamily(  
        packageId.FamilyName);  
  
tempDir = appData.TemporaryFolder.Path;  
```  
  
 Mezitím vaše knihovna DLL Profiler může v podstatě to samé udělá, i když může informace snadno vrátíte do [ApplicationData](https://msdn.microsoft.com/library/windows/apps/windows.storage.applicationdata.aspx) pomocí [ApplicationData.Current](https://msdn.microsoft.com/library/windows/apps/windows.storage.applicationdata.current.aspx) vlastnost.  
  
 **Komunikaci prostřednictvím událostí**  
 Pokud chcete, aby jednoduché signalizační sémantice mezi Profiler uživatelského rozhraní a Profiler DLL, můžete použít události uvnitř aplikace Windows Store, jakož i aplikace klasické pracovní plochy.  
  
 Z knihovny DLL Profiler, můžete jednoduše zavoláte [CreateEventEx](/windows/desktop/api/synchapi/nf-synchapi-createeventexa) funkci, která vytvoří na pojmenovanou událost s libovolný název.  Příklad:  
  
```cpp  
// Profiler DLL in Windows Store app (C++).  
CreateEventEx(   
    NULL,  // Not inherited  
    "MyNamedEvent"  
    CREATE_EVENT_MANUAL_RESET, /* explicit ResetEvent() required; leave initial state unsignaled */  
    EVENT_ALL_ACCESS);  
```  
  
 Vaše uživatelské rozhraní Profiler pak musí najít tuto pojmenovaného událost v rámci oboru názvů aplikace Windows Store.  Například lze volat vaše uživatelské rozhraní Profiler [CreateEventEx](/windows/desktop/api/synchapi/nf-synchapi-createeventexa), zadáte jako název události  
  
 `AppContainerNamedObjects\<acSid>\MyNamedEvent`  
  
 `<acSid>` je SID AppContainer aplikace Windows Store.  Předchozí části tohoto tématu vám ukázal, jak k iteraci přes balíčky nainstalované pro aktuálního uživatele.  Z této ukázky kódu můžete získat packageId.  A z packageId, můžete získat `<acSid>` podobně jako následujícím kódem:  
  
```csharp  
IntPtr acPSID;  
DeriveAppContainerSidFromAppContainerName(packageId.FamilyName, out acPSID);  
  
string acSid;  
ConvertSidToStringSid(acPSID, out acSid);  
  
string acDir;  
GetAppContainerFolderPath(acSid, out acDir);  
```  
  
### <a name="no-shutdown-notifications"></a>Žádná oznámení. vypnutí

 Při spuštění v rámci aplikace Windows Store, váš Profiler knihovny DLL, neměli byste tedy spoléhat na buď [icorprofilercallback::Shutdown –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md) nebo dokonce [DllMain](/windows/desktop/Dlls/dllmain) (s `DLL_PROCESS_DETACH`) volaná oznámit váš Profiler knihovny DLL jestli se ukončuje aplikace Windows Store.  Ve skutečnosti měli byste očekávat, že se nebude nikdy volána.  V minulosti mnoho knihoven DLL Profiler použili těchto oznámení jako praktický míst k vyprázdnění mezipaměti na disku, zavírání souborů, odesílat oznámení zpět do uživatelského rozhraní Profiler atd.  Ale teď je potřeba uspořádání trochu jinak, váš Profiler knihovny DLL.  
  
 Vaše knihovna DLL Profiler by měl být informace o protokolování, jak funguje.  Z důvodů výkonu můžete dávkové informace v mezipaměti a vyprázdněte ji na disk s růstem služby batch ve velikosti za některé prahovou hodnotu.  Ale předpokládat, že může dojít ke ztrátě veškeré informace, které ještě nejsou zapsány na disk.  To znamená, že budete chtít vybrat vaše mezní hodnota uvážlivě a, že vaše uživatelské rozhraní Profiler musí být posílené vypořádat s neúplnými informacemi autorem Profiler DLL.  
  
## <a name="windows-runtime-metadata-files"></a>Soubory metadat Windows Runtime

 Je mimo rámec tohoto dokumentu do podrobností na jaké prostředí Windows Runtime metadata (WinMD) jsou soubory.    Tato část je omezený jak rozhraní API profilování CLR reaguje, když jsou soubory WinMD načteny aplikace Windows Store, který analyzuje vaši knihovnu DLL Profiler.  
  
### <a name="managed-and-non-managed-winmds"></a>Soubory Winmd spravované a nespravované

 Pokud vývojář používá Visual Studio vytvořte nový projekt pro součást prostředí Windows Runtime, sestavení projektu vytvoří soubor WinMD, který popisuje metadata (popisy typu třídy, rozhraní, atd.) vytvořené vývojářem.  Pokud tento projekt je projekt spravovaného jazyka napsané v jazyce C# nebo VB, tento stejný soubor WinMD obsahuje také provádění těchto typů (což znamená, že obsahuje všechny IL zkompilovaná ze zdrojového kódu pro vývojáře).  Tyto soubory jsou označovány jako spravované soubory WinMD.  Jsou to zajímavé, neobsahují metadata prostředí Windows Runtime a základní implementací.  
  
 Naopak pokud vývojář vytvoří projekt pro součást prostředí Windows Runtime jazyka C++, sestavení tohoto projektu vytvoří soubor WinMD, který obsahuje pouze metadata a implementaci se zkompiluje do samostatné nativní knihovnu DLL.  Podobně soubory WinMD, které se dodávají v sadě Windows SDK obsahují pouze metadata, s implementací zkompilovány do samostatných nativních knihoven DLL, které se dodávají jako součást Windows.  
  
 Níže uvedené informace platí pro obě spravované soubory Winmd, které obsahují metadat a implementace, a nespravované soubory Winmd, která obsahují pouze metadata.  
  
### <a name="winmd-files-look-like-clr-modules"></a>Soubory WinMD vypadat podobně jako se moduly CLR

 Co se týče CLR, jsou všechny soubory WinMD moduly.  Rozhraní API profilování CLR proto řekne váš Profiler knihovny DLL při načtení soubory WinMD a co jejich identifikátorů Moduleid se stejným způsobem jako u jiných spravované moduly.  
  
 Vaše knihovna DLL Profiler může rozlišit soubory WinMD z jiných modulů voláním [icorprofilerinfo3::getmoduleinfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md) metoda a zkontrolujete `pdwModuleFlags` výstupní parametr pro [COR_PRF_MODULE_WINDOWS_ Modul RUNTIME](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) příznak.  (To je nastavena pokud a pouze v případě, že ModuleID představuje o soubor WinMD.)  
  
### <a name="reading-metadata-from-winmds"></a>Čtení metadat z soubory Winmd

 Soubory WinMD, stejně jako regulární moduly obsahovat metadata, která lze číst prostřednictvím [metadat rozhraní API](../../../../docs/framework/unmanaged-api/metadata/index.md).  Modul CLR však mapuje na typy rozhraní .NET Framework typy Windows Runtime, při čtení tak, aby vývojáři, kteří aplikaci ve spravovaném kódu a využívat soubor WinMD může mít více fyzických programovací prostředí se soubory WinMD.  Některé příklady tato mapování, naleznete v tématu [podpory pro Windows Store aplikací využívajících .NET Framework a prostředí Windows Runtime](../../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md).  
  
 Takže zobrazení, které váš profiler dojde k používá metadat rozhraní API: nezpracované zobrazení modulu Windows Runtime nebo zobrazení mapované rozhraní .NET Framework?  Odpověď: to je na vás.  
  
 Při volání [icorprofilerinfo::getmodulemetadata –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) metodu na soubor WinMD získání metadat rozhraní, jako například [imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), můžete také nastavit [ofNoTransform](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)v `dwOpenFlags` parametr, chcete-li vypnout toto mapování.  V opačném případě výchozí mapování se povolí.  Profiler obvykle, budete mít mapování povolené, tak, aby řetězce, které knihovny DLL Profiler obdrží z metadat WinMD (například názvy typů) bude vypadat známé a přirozené uživateli profileru.  
  
### <a name="modifying-metadata-from-winmds"></a>Úprava metadat z soubory Winmd

 Úprava metadat Winmd se nepodporuje.  Při volání [icorprofilerinfo::getmodulemetadata –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) metodu o soubor WinMD souboru a zadejte [ofWrite](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) v `dwOpenFlags` parametr nebo požádat o zapisovatelné metadat rozhraní, jako [ Imetadataemit –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md), [getmodulemetadata –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) se nezdaří.  To je zvláště důležité k přepisování IL profilovací programy, které je potřeba upravit metadata pro podporu jejich instrumentace (například přidání AssemblyRefs nebo nové metody).  Proto by měla vyhledávat [COR_PRF_MODULE_WINDOWS_RUNTIME](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) nejprve (jak je popsáno v předchozí části) a zdržet s žádostí o rozhraní zapisovatelné metadat na tyto moduly.  
  
### <a name="resolving-assembly-references-with-winmds"></a>Překládají se odkazy na sestavení s soubory Winmd

 Mnoho profilery potřeba vyřešit odkazy v metadatech ručně, aby se vám pomůže s instrumentace nebo typ kontroly.  Takové profilery je potřeba vědět, jak překládá CLR odkazy na sestavení, které odkazují na soubory Winmd, protože tyto odkazy jsou vyřešeny zcela jiným způsobem než standardní odkazy na sestavení.  
  
## <a name="memory-profilers"></a>Profilery paměti

 Systém uvolňování paměti a spravované haldy nejsou fundamentálně odlišný způsob v aplikaci Windows Store a desktopové aplikace.  Existují však některé drobné rozdíly, které je potřeba mít na paměti autoři profileru.  
  
### <a name="forcegc-creates-a-managed-thread"></a>Forcegc – vytvoří spravovaná vlákna

 Při provádění profilace paměti, Profiler knihovny DLL obvykle vytvoří samostatném vlákně, ze kterého se má volat [forcegc – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md) metody.  Toto je není nic nového.  Ale co může být překvapivé, že v rámci provádění uvolnění paměti v aplikaci Windows Store mohou transformovat vaše vlákno na spravované vlákno (například Idvlákna profilování rozhraní API vytvoří se pro toto vlákno).  
  
 Pro pochopení důsledků to, je důležité znát rozdíly mezi synchronní a asynchronní volání podle definice rozhraní API profilování CLR. Všimněte si, že se příliš neliší od konceptu byla zahájena asynchronní volání v aplikacích pro Windows Store.  Najdete v blogovém příspěvku [důvod, proč máme CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](https://blogs.msdn.microsoft.com/davbr/2008/12/23/why-we-have-corprof_e_unsupported_call_sequence/) Další informace.  
  
 Relevantní bod je, že volání vlákna vytvořená modulem profileru jsou vždy považovány za synchronní, i v případě, že tato volání jsou tvořeny mimo implementaci jednoho z vaší knihovny DLL Profiler [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) metody.  Nejméně, který používá v případě.  Teď, když modul CLR vypnul váš profiler vlákna do spravovaného vlákna kvůli volání [forcegc – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md), že vlákno je nelze nadále považovat za váš profiler vláken.  V důsledku toho CLR vynucuje přísnější definicí co splňuje podmínky jako synchronní pro toto vlákno – a to, které musí volání pocházejí z uvnitř některého z vaší knihovny DLL Profiler [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) metody k získání způsobilosti jako synchronní.  
  
 Co to znamená v praxi?  Většina [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) metody jsou bezpečné volat synchronně a okamžitě selžou jinak.  Pokud vaše knihovna DLL Profiler opětovně používá vaše [forcegc – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md) vlákno k provedení jiných volání uskutečněných obvykle na vytvoření profiler vláken (například [requestprofilerdetach –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md), [requestrejit –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md), nebo [requestrevert –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)), budete mít problémy.  I asynchronní typově bezpečné funkce, jako [dostacksnapshot –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) má zvláštní pravidla při volání z spravovaná vlákna. (Naleznete v příspěvku blogu [procházení zásobníku Profiler: základy a dalších fázích můžete využít](https://blogs.msdn.microsoft.com/davbr/2005/10/06/profiler-stack-walking-basics-and-beyond/) Další informace.)  
  
 Proto doporučujeme, aby jakékoli vlákno vytvoří vaše knihovna DLL Profiler volat [forcegc – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md) by měla sloužit *pouze* pro účely aktivace GC a pak odpověď na zpětná volání uvolňování paměti.  Neměli volat do rozhraní API profilování provádět další úkoly, jako je zásobník vzorkování nebo odpojení.  
  
### <a name="conditionalweaktablereferences"></a>ConditionalWeakTableReferences

 Od verze rozhraní .NET Framework 4.5, je nový zpětné volání uvolňování paměti, [conditionalweaktableelementreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md), které umožňuje profileru více úplné informace o *závislé popisovače*. Tyto manipulační body efektivně přidat odkaz ze zdrojového objektu do cílové objektů pro účely správy životního cyklu uvolňování paměti.  Závislé popisovače nejsou žádnou novinkou a vývojáře, kteří programují ve spravovaném kódu byli schopni vytvořit svoje vlastní obslužné rutiny závislé pomocí <xref:System.Runtime.CompilerServices.ConditionalWeakTable%602?displayProperty=nameWithType> třídy i před Windows 8 a rozhraní .NET Framework 4.5.  
  
 Spravované aplikace pro Windows Store XAML, ale provést hojně používají závislé obslužné rutiny.  Konkrétně se používá modul CLR je k vám pomůže se správou cykly odkazů mezi spravované a nespravované objekty modulu Windows Runtime.  To znamená, že se jedná o více důležitější nyní než dřív paměti profilerů, abyste měli informace o těchto závislé popisovačů tak, aby se lze vizualizovat spolu se zbývajícími hrany v grafu haldy.  Vaše knihovna DLL Profiler by měl používat [rootreferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md), [objectreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), a [conditionalweaktableelementreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) dohromady a vytvoří kompletní přehled grafu haldy .  
  
## <a name="conclusion"></a>Závěr

 Je možné použít rozhraní API profilování CLR k analýze spravovaném kódu běžícím uvnitř aplikace Windows Store.  Ve skutečnosti můžete využít existující profileru, který vyvíjíte a provést nějaké konkrétní změny tak, že to cílová aplikace Windows Store.   Uživatelské rozhraní Profiler by měl používat nová rozhraní API pro aktivaci aplikace Windows Store v režimu ladění.  Ujistěte se, že vaše knihovna DLL Profiler využívá jenom těchto rozhraní API pro aplikace Windows Store.  Mechanismus pro komunikaci mezi knihovny DLL Profiler a Profiler uživatelského rozhraní by měly být zapsány pomocí omezení rozhraní API aplikace Windows Store v úvahu a povědomí o omezené oprávnění v místě pro aplikace Windows Store.  Vaše knihovna DLL Profiler by měl být vědět, jak modul CLR zpracovává soubory Winmd, a jak se liší s ohledem na spravovaná vlákna chování systému uvolňování paměti.  
  
## <a name="resources"></a>Prostředky

 **Modul Common Language Runtime**  
 -   [Reference k rozhraní API profilování CLR](../../../../docs/framework/unmanaged-api/profiling/index.md)  
  
-   [Reference k rozhraní API metadat CLR](../../../../docs/framework/unmanaged-api/metadata/index.md)  
  
 **Modul CLR interakce s modulem Windows Runtime**  
 [Podpora pro aplikace pro web Windows Store a prostředí Windows Runtime v rozhraní .NET Framework](../../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)  
  
 **Aplikace Windows Store**  
 -   [Přístup k souborům a oprávnění (aplikace pro Windows Runtime](https://msdn.microsoft.com/library/windows/apps/hh967755.aspx)  
  
-   [Získat vývojářskou licenci](https://msdn.microsoft.com/library/windows/apps/Hh974578.aspx)  
  
-   [IPackageDebugSettings rozhraní](https://msdn.microsoft.com/library/hh438393\(v=vs.85\).aspx)  
  
## <a name="see-also"></a>Viz také

[Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)  
