---
title: Profilery CLR a aplikace pro Windows Store
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: csharp
applies_to:
- Windows 10
- Windows 8
helpviewer_keywords:
- profiling API
- profiling API [.NET Framework]
- profiling managed code
- profiling managed code [Windows Store Apps]
ms.assetid: 1c8eb2e7-f20a-42f9-a795-71503486a0f5
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: db1152e82edde34dc8dbaba09f20b9f769dffbca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="clr-profilers-and-windows-store-apps"></a>Profilery CLR a aplikace pro Windows Store
Toto téma popisuje, co je potřeba myslet při psaní diagnostické nástroje, které analýza spravovaného kódu běžících v rámci aplikace pro Windows Store.  Obsahuje také pokyny k úpravě existující nástroje vývoj, aby pracovaly při spuštění před aplikací pro Windows Store.  Chcete-li tyto informace pochopili, je vhodné, že pokud jste obeznámeni s Common Language Runtime profilace rozhraním API pro, již jste použili toto rozhraní API v diagnostický nástroj, běží správně u aplikací klasické pracovní plochy Windows a vy jste nyní zajímá úprava nástroj Chcete-li spustit správně pro aplikace pro Windows Store.  
  
 Toto téma se skládá z následujících částí:  
  
 [Úvod](#Intro)  
 [Architektura a přehled terminologie](#Arch)  
 [Zařízení s Windows RT.](#RT)  
[Použití rozhraní API systému Windows Runtime](#Consuming)  
[Načítání knihovny DLL profileru](#Loading)  
 [Většinou je potřeba zvážit při spuštění a připojte zatížení](#Common)  
 [Spuštění zatížení](#Startup)  
 [Připojte zatížení](#Attach)  
[Spuštění v rámci aplikace pro Windows Store](#Running)  
 [Pokud chtěl rozhraní API pro aplikace Windows Store](#APIs)  
 [Omezená oprávnění](#Permissions)  
 [Komunikace mezi procesy](#Interprocess)  
 [Žádná oznámení vypnutí](#Shutdown)  
[Soubory metadat prostředí Windows Runtime](#Metadata)  
 [WinMDs spravovaných a nespravovaných](#WMDs)  
 [Soubory WinMD vypadat moduly CLR](#CLRModules)  
 [Načítání metadat z WinMDs](#Reading)  
 [Úprava metadata z WinMDs](#Modifying)  
 [Odkazy na sestavení s WinMDs řešení](#Resolving)  
[Profilery paměti](#Profilers)  
 [Forcegc – vytvoří spravovaná vlákna](#ForceGC)  
 [ConditionalWeakTableReferences](#WeakTable)  
[Uzavření](#Conclusion)  
[Prostředky](#Resources)  
  
<a name="Intro"></a>   
## <a name="introduction"></a>Úvod  
 Pokud jste provedli za úvodní odstavec, pak se seznámíte s rozhraním API profilace CLR.  Diagnostický nástroj, který funguje dobře u spravovaných aplikací klasické pracovní plochy již bylo zapsáno.  Nyní jste zvědaví co dělat, aby vaše nástroje funguje s spravované aplikace pro Windows Store.  Možná již pokusili jste se správnou a zjistit, že se nejedná o přehledné úloh.  Skutečně existuje několik aspektů, které nemusí být zřejmé pro všechny nástroje pro vývojáře.  Příklad:  
  
-   Spuštění aplikace pro Windows Store v kontextu s vážně sníženými oprávněními.  
  
-   Soubory metadat Windows mají jedinečných charakteristik, v porovnání s tradiční spravované moduly.  
  
-   Aplikace pro Windows Store mají která podporují pozastavení sami, kdy interaktivity přestane fungovat.  
  
-   Mechanismy vaší komunikace mezi procesy mohou fungovat už z různých důvodů.  
  
 Toto téma obsahuje seznam akcí, které budete muset mít na paměti a o tom, jak nakládat s nimi správně.  
  
 Pokud jste nové rozhraní API profilace CLR, přejděte dolů zdrojů na konci tohoto tématu pro vyhledání lépe úvodní informace.  
  
 Poskytuje podrobnosti o konkrétní rozhraní API systému Windows a jak mají být použity také je nad rámec tohoto tématu.  Zvažte Toto téma počáteční bod a odkazovat na webu MSDN Další informace o všech rozhraní API systému Windows, který je zde odkazuje.  
  
<a name="Arch"></a>   
## <a name="architecture-and-terminology"></a>Architektura a přehled terminologie  
 Diagnostický nástroj obvykle obsahuje architekturu stejný, jako je znázorněno na následujícím obrázku. Používá termín "profileru", ale celou řadu takových nástrojů přejít i nad rámec typické výkonu nebo profilace paměti do oblasti, například pokrytí kódu, model objektu architektury, čas cesta, ladění, aplikaci pro monitorování a tak dále.  Pro jednoduchost bude odkazovat na tyto nástroje jako profilery pokračovat v tomto tématu.  
  
 V tomto tématu slouží následující terminologií:  
  
 Aplikace  
 Toto je aplikace, která analyzuje profileru.  Většinou vývojáři této aplikace je nyní pomocí profileru pomohou diagnostikovat problémy s aplikací.  Tradičně tato aplikace bude aplikace systému Windows, ale v tomto tématu jsme díváte na aplikace pro Windows Store.  
  
 Profileru knihovny DLL  
 Toto je načte do procesního prostoru aplikace analyzované komponentou.  Tuto součást, také známé jako "agenta," profileru implementuje [icorprofilercallback –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)[icorprofilercallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)(2,3, atd.) rozhraní a odebírá [ Icorprofilerinfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)(2,3, atd.) rozhraní ke shromažďování dat o analyzovaných aplikaci a potenciálně upravit aspektů chování aplikace.  
  
 Profileru uživatelského rozhraní  
 Toto je aplikací plochy, která profileru uživatel komunikuje.  Je zodpovědná za zobrazení stav aplikace pro uživatele a umožní uživateli způsob, jak řídit chování analyzovaných aplikace.  Tato součást vždy spouští ve vlastním prostoru procesu, oddělený od procesního prostoru aplikace profilovaný.  Rozhraní profileru mohou chovat i jako "připojit aktivaci" je proces, který volá [iclrprofiling::attachprofiler –](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) metoda způsobit analyzovaných aplikaci načíst knihovnu DLL profileru v těchto případech, kde profileru DLL nebyla načíst při spuštění.  
  
> [!IMPORTANT]
>  Uživatelské rozhraní profileru by měla zůstat desktopová aplikace systému Windows, i když se používá k řízení a sestavy na aplikace pro Windows Store.  Nebudete moct balíček a dodávat vaše diagnostické nástroje ve službě Windows Store.  Vaše nástroje je potřeba provádět akce, které aplikace pro Windows Store nelze provést, a mnohé z těchto věcí nacházet uvnitř uživatelské rozhraní profileru.  
  
 V tomto dokumentu ukázkový kód předpokládá, že:  
  
-   Vaše knihovna DLL profileru je napsán v jazyce C++ protože musí být nativní knihovny DLL, podle požadavků profilace API CLR.  
  
-   Uživatelské rozhraní profileru je napsán v jazyce C#.  To není nezbytné, ale protože neexistují žádné požadavky na jazyk pro vaše uživatelské prostředí profileru procesu, vyberte jazyk, který se stručným a jednoduché Proč ne?  
  
<a name="RT"></a>   
### <a name="windows-rt-devices"></a>Zařízení s Windows RT.  
 Zařízení s Windows RT se poměrně uzamčené.  Profilery třetích stran jednoduše nelze načíst k takovým zařízením.  Tento dokument se zaměřuje na počítačích s Windows 8.  
  
<a name="Consuming"></a>   
## <a name="consuming-windows-runtime-apis"></a>Použití rozhraní API systému Windows Runtime  
 V různých scénářích popsaných v následující části stolní aplikace uživatelského rozhraní profileru musí využívat některé nové rozhraní API systému Windows Runtime.  Budete chtít v dokumentaci k zjistit, které rozhraní API systému Windows Runtime lze z aplikací klasické pracovní plochy, a zda jejich chování se liší při volání z aplikací klasické pracovní plochy a Windows Store aplikace.  
  
 Pokud je uživatelské rozhraní profileru zapsané ve spravovaném kódu, budou existovat několik kroků, které budete muset udělat, aby byly využívání těchto snadno Windows Runtime pro rozhraní API.  Najdete v článku [spravované aplikace klasické pracovní plochy a prostředí Windows Runtime](http://go.microsoft.com/fwlink/?LinkID=271858) Další informace najdete v článku.  
  
<a name="Loading"></a>   
## <a name="loading-the-profiler-dll"></a>Načítání knihovny DLL profileru  
 Tato část popisuje, jak způsobí, že vaše profileru uživatelského rozhraní aplikace pro Windows Store načíst vaše profileru knihovnu DLL.  Kód popsaných v této části patří vaší aplikace na ploše profileru uživatelského rozhraní a proto zahrnuje pomocí rozhraní API systému Windows, které jsou bezpečné pro aplikace klasické pracovní plochy, ale není nutně bezpečné pro přístup z aplikace pro Windows Store.  
  
 Uživatelské rozhraní profileru může způsobit vaše knihovna DLL profileru načíst do procesního prostoru aplikace dvěma způsoby:  
  
-   Při spuštění aplikace, jako řízené proměnné prostředí.  
  
-   Připojením k aplikaci po spuštění dokončení voláním [iclrprofiling::attachprofiler –](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) metoda.  
  
 Jeden z vaší první roadblocks bude získávání spuštění zatížení a připojte zatížení vaší knihovny DLL profileru správně fungovat s aplikací pro Windows Store.  Obě formy načítání sdílet společnou některé důležité informace, proto začněme s nimi.  
  
<a name="Common"></a>   
### <a name="common-considerations-for-startup-and-attach-loads"></a>Většinou je potřeba zvážit při spuštění a připojte zatížení  
 **Podepsání vaší profileru knihovny DLL**  
 Když se Windows pokusí načíst vaše profileru knihovnu DLL, tak ověří, že je vaše knihovna DLL profileru správně podepsaná.  Pokud ne, zatížení selže ve výchozím nastavení. Toto lze provést dvěma způsoby:  
  
-   Zkontrolujte, zda je vaše knihovna DLL profileru přihlášeni.  
  
-   Řekněte uživateli, že musí nainstalovat vývojáře licenci na své počítače Windows 8 před použitím vaše nástroje.  To můžete provést automaticky ze sady Visual Studio nebo ručně z příkazového řádku.  Další informace najdete v tématu [získat licenci vývojáře](https://msdn.microsoft.com/library/windows/apps/Hh974578.aspx).  
  
 **Oprávnění systému souborů**  
 Aplikace pro Windows Store musí mít oprávnění k načtení a provedení knihovny DLL profileru z umístění v systému souborů, ve kterém se nachází.  Ve výchozím nastavení aplikace pro Windows Store taková oprávnění nemá na většině adresáře a všechny neúspěšný pokus o načtení knihovny DLL profileru vytvoří záznam v protokolu událostí aplikace systému Windows, která vypadá přibližně takto:  
  
```Output  
NET Runtime version 4.0.30319.17929 - Loading profiler failed during CoCreateInstance.  Profiler CLSID: '{xxxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx}'.  HRESULT: 0x80070005.  Process ID (decimal): 4688.  Message ID: [0x2504].  
```  
  
 Obecně platí aplikace pro Windows Store jsou povoleny pouze pro přístup k omezenou sadu umístění na disku.  Každá aplikace Windows Store můžete přístup k vlastní složky data aplikací, jakož i několik dalších oblastí v systému souborů, pro které jsou všechny aplikace pro Windows Store udělen přístup.  Doporučujeme nainstalovat knihovnou DLL profileru a jeho závislosti někde v části programové soubory nebo programové soubory (x86), protože všechny aplikace pro Windows Store mají číst a spouštět oprávnění existuje ve výchozím nastavení.  
  
<a name="Startup"></a>   
### <a name="startup-load"></a>Spuštění zatížení  
 Obvykle v aplikace na ploše uživatelské rozhraní profileru zadání zatížení spuštění vaší profileru knihovny DLL pomocí inicializace bloku prostředí, který obsahuje požadované proměnné prostředí CLR profilace API (tj, `COR_PROFILER`, `COR_ENABLE_PROFILING`, a `COR_PROFILER_PATH`), a pak vytvořit nový proces s blokem tohoto prostředí.  To samé platí pro aplikace Windows Store, ale liší se na mechanismy.  
  
 **Nespouštět zvýšenými**  
 Pokud proces pokusí vytvořit aplikaci pro Windows Store proces B, proces A měl být spuštěn v střední integrity úrovně, nikoli na úrovni vysoká integrita, (který je, není se zvýšenými oprávněními).  To znamená, že buď uživatelské rozhraní profileru by však být spuštěna na úrovni střední integrity, nebo ho musíte vytvořit jiný proces klientů na úrovni střední integrity, která se postará o spuštění aplikace pro Windows Store.  
  
 **Výběr aplikace pro Windows Store do profilu**  
 Nejprve budete chtít požádejte vaší profileru uživatele, které aplikace pro Windows Store ke spuštění.  Aplikací klasické pracovní plochy pravděpodobně by zobrazit dialogové okno Procházet souboru, a uživatel by najděte a vyberte soubor s příponou .exe.  Ale aplikace pro Windows Store se liší a zobrazí se dialogové okno Procházet pomocí nemá smysl.  Místo toho je lepší se uživateli zobrazí seznam aplikací pro Windows Store pro tohoto uživatele k výběru nainstalována.  
  
 Můžete použít [PackageManager třída](https://msdn.microsoft.com/library/windows/apps/windows.management.deployment.packagemanager.aspx) ke generování tohoto seznamu.  `PackageManager`je třída prostředí Windows Runtime, která je k dispozici pro aplikace klasické pracovní plochy a ve skutečnosti je *pouze* k dispozici pro aplikace klasické pracovní plochy.  
  
 Následující příklad funkce ode z hypotetický uživatelského rozhraní profileru zapisují jako desktopová aplikace v C# yses `PackageManager` a vygenerujte seznam aplikací pro Windows:  
  
```csharp  
string currentUserSID = WindowsIdentity.GetCurrent().User.ToString();  
IAppxFactory appxFactory = (IAppxFactory) new AppxFactory();  
PackageManager packageManager = new PackageManager();  
IEnumerable<Package> packages = packageManager.FindPackagesForUser(currentUserSID);  
```  
  
 **Určení vlastního prostředí bloku**  
 Nové rozhraní modelu COM, [IPackageDebugSettings](https://msdn.microsoft.com/library/hh438393\(v=vs.85\).aspx), umožňuje přizpůsobit chování při spuštění aplikace Windows Store v zájmu snazší některé formy diagnostiky.  Jeden z jeho metody [EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=vs.85\).aspx), umožňuje předat bloku prostředí aplikace Windows Store při jeho spuštění, společně s další užitečné efekty jako zakázání automatického procesu pozastavení.  Blok prostředí je důležité, protože se jedná, kde je třeba zadat proměnné prostředí (`COR_PROFILER`, `COR_ENABLE_PROFILING`, a `COR_PROFILER_PATH)`) používá k načtení knihovny DLL profileru modulu CLR.  
  
 Vezměte v úvahu následující fragment kódu:  
  
```csharp  
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();  
pkgDebugSettings.EnableDebugging(packgeFullName, debuggerCommandLine,   
                                                                 (IntPtr)fixedEnvironmentPzz);  
```  
  
 Existuje několik položek, které budete muset získat správné:  
  
-   `packageFullName`můžete určit při iterování přes balíčky a metodou `package.Id.FullName`.  
  
-   `debuggerCommandLine`je vyzkoušíte zajímavější.  Chcete-li předat bloku vlastní prostředí do aplikace pro Windows Store, potřebujete napsat vlastní zneužívající vlastností prohlížeče fiktivní ladicí program.  Windows následujícímu tření aplikace pro Windows Store je pozastavit a potom připojí ladicí program spuštěním ladicí program s příkazovým řádkem jako v tomto příkladu:  
  
    ```Output  
    MyDummyDebugger.exe -p 1336 -tid 1424  
    ```  
  
     kde `-p 1336` znamená. 1336 ID procesu, má aplikace Windows Store a `-tid 1424` , znamená to 1424 ID vlákna vlákno, které je pozastaveno.  Fiktivní ladicí program byste analyzovat ID podprocesu z příkazového řádku, pokračovat v daném vláknu a poté ukončete.  
  
     Tady je několik příkladů kódu C++ k tomu (Nezapomeňte přidat Kontrola chyb!):  
  
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
  
     Budete potřebovat k nasazení této fiktivní ladicí program jako součást vaší instalace nástroje pro diagnostiku a pak zadejte cestu k této ladicím programu `debuggerCommandLine` parametr.  
  
 **Spuštění aplikace pro Windows Store**  
 Nakonec byl doručen v okamžiku spuštění aplikace pro Windows Store. Pokud jste již již zkusili sobě provádění, může dojít k tomu, [CreateProcess](https://msdn.microsoft.com/library/windows/desktop/ms682425\(v=vs.85\).aspx) není jak vytvořit proces aplikace Windows Store.  Místo toho budete muset použít [IApplicationActivationManager::ActivateApplication](https://msdn.microsoft.com/library/windows/desktop/Hh706903\(v=vs.85\).aspx) metoda.  K tomu, budete muset získat ID aplikace uživatele modelu aplikace Windows Store, která se spouští.  A to znamená, že budete muset provést trochu tápat prostřednictvím manifest.  
  
 Při iterování přes vlastních balíčků (najdete v části "Výběr úložiště aplikací k profilu Windows" v [spuštění zatížení](#Startup) výše v části), budete chtít získat sadu aplikací obsažených v aktuální balíček manifestu:  
  
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
  
 Ano, jeden balíček může mít několik aplikací a každá aplikace má vlastní ID modelu uživatele aplikace.  Proto budete chtít požádejte vaše uživatele, která aplikace do profilu a získat Application User Model ID z této konkrétní aplikace:  
  
```csharp  
while (appsEnum.GetHasCurrent() != 0)  
{  
    IAppxManifestApplication app = appsEnum.GetCurrent();  
    string appUserModelId = app.GetAppUserModelId();  
…  
```  
  
 Nakonec můžete mít nyní co je potřeba spustit aplikaci z Windows Store:  
  
```csharp  
IApplicationActivationManager appActivationMgr = new ApplicationActivationManager();  
appActivationMgr.ActivateApplication(appUserModelId, appArgs, ACTIVATEOPTIONS.AO_NONE, out pid);  
```  
  
 **Nezapomeňte volat DisableDebugging**  
 Když jste volali metodu [IPackageDebugSettings::EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=VS.85\).aspx), můžete provedeny promise, který by se vyčistit po sobě voláním [IPackageDebugSettings::DisableDebugging](https://msdn.microsoft.com/library/hh438394\(v=vs.85\).aspx) metoda, takže je nutné provést Když je relace profilování nad.  
  
<a name="Attach"></a>   
### <a name="attach-load"></a>Připojte zatížení  
 Uživatelské rozhraní profileru se chce připojit jeho DLL profileru k aplikaci, která už se spustilo spuštěna, používá [iclrprofiling::attachprofiler –](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md).  To samé platí s aplikací pro Windows Store.  Ale kromě společné aspekty uvedena i výše, ujistěte se, se, že cílové aplikace pro Windows Store není pozastaveno.  
  
 **EnableDebugging**  
 Stejně jako u zatížení spuštění volání [IPackageDebugSettings::EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=VS.85\).aspx) metoda.  Nepotřebujete pro předávání bloku prostředí, ale budete potřebovat jeden z jeho další funkce: zákaz automatického procesu pozastavení.  Jinak, pokud uživatelské rozhraní profileru volá [attachprofiler –](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md), může být pozastavený cílové aplikace pro Windows Store.  Ve skutečnosti je to pravděpodobně Pokud uživatel je nyní interakci s profileru uživatelské rozhraní a aplikace pro Windows Store není aktivní na žádném z obrazovky uživatele.  A pokud Windows Store, aplikace je pozastaveno, nebude moci reagovat na všechny signál, že modulu CLR odesílá do ní připojit vaše knihovna DLL profileru.  
  
 Proto budete chtít udělat přibližně takto:  
  
```csharp  
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();  
pkgDebugSettings.EnableDebugging(packgeFullName, null /* debuggerCommandLine */,   
                                                                 IntPtr.Zero /* environment */);  
```  
  
 Toto je stejný volání, které by provést pro případ, spuštění zatížení, s výjimkou nezadáte ladicí program příkazového řádku nebo bloku prostředí.  
  
 **DisableDebugging**  
 Jako vždy, nezapomeňte volat [IPackageDebugSettings::DisableDebugging](https://msdn.microsoft.com/library/hh438394\(v=vs.85\).aspx) po dokončení vaší relace profilování.  
  
<a name="Running"></a>   
## <a name="running-inside-the-windows-store-app"></a>Spuštění v rámci aplikace pro Windows Store  
 Aplikace pro Windows Store tak nakonec načetl vaše knihovna DLL profileru.  Nyní je vaše knihovna DLL profileru musí výukové jak přehrát podle různých pravidel vyžadované aplikací pro Windows Store, včetně, které jsou povolené rozhraní API a jak spustit s snížit oprávnění.  
  
<a name="APIs"></a>   
### <a name="stick-to-the-windows-store-app-apis"></a>Pokud chtěl rozhraní API pro aplikace Windows Store  
 Při procházení rozhraní API systému Windows, můžete si všimnout, že je každé rozhraní API popsané jako použitelné pro aplikace klasické pracovní plochy, aplikace pro Windows Store nebo obojí.  Například **požadavky** části dokumentace pro [InitializeCriticalSectionAndSpinCount](https://msdn.microsoft.com/library/windows/desktop/ms683476\(v=vs.85\).aspx) funkce naznačuje, že funkce používá k jenom aplikace klasické pracovní plochy. Naproti tomu [InitializeCriticalSectionEx](https://msdn.microsoft.com/library/windows/desktop/ms683477\(v=vs.85\).aspx) funkce je k dispozici pro aplikace klasické pracovní plochy a aplikace pro Windows Store.  
  
 Při vývoji vaší profileru knihovny DLL, s nimi zacházet, pokud je aplikace pro Windows Store a používat pouze rozhraní API, která jsou popsaná jako dostupné pro aplikace pro Windows Store.  Analýza svoje závislosti (například můžete spustit `link /dump /imports` proti knihovny DLL profileru auditovat) a potom vyhledejte dokumenty, které vaše závislosti jsou v pořádku, a které nejsou.  Ve většině případů vaší porušení odstraněny a nahradí je jednoduše s novější formuláře rozhraní API, která je popsána jako bezpečné (například nahrazení [InitializeCriticalSectionAndSpinCount](https://msdn.microsoft.com/library/windows/desktop/ms683476\(v=vs.85\).aspx) s [ InitializeCriticalSectionEx](https://msdn.microsoft.com/library/windows/desktop/ms683477\(v=vs.85\).aspx)).  
  
 Můžete si všimnout, že vaše knihovna DLL profileru volá některé rozhraní API, která platí pro aplikace klasické pracovní plochy pouze a ještě budou pravděpodobně fungovat, i když načtení knihovny DLL profileru uvnitř aplikace pro Windows Store.  Uvědomte si, že se jedná o rizikové použití jakéhokoli rozhraní API není zdokumentovaný pro použití s aplikací pro Windows Store v knihovně DLL profileru při načítání do procesu aplikace Windows Store:  
  
-   Taková rozhraní API není zaručena bezpečnost pro práci při volání v jedinečný kontextu, které používají aplikace pro Windows Store v.  
  
-   Taková rozhraní API nemusí fungovat konzistentně, když je volána v rámci různých procesů aplikace Windows Store.  
  
-   Taková rozhraní API může zdát, že bez problémů fungují z aplikace pro Windows Store v aktuální verzi systému Windows, ale je možné ukončit nebo zakázat v budoucích verzích systému Windows.  
  
 Je nejlepší Rady a opravte všechny porušení nedošlo k ohrožení.  
  
 Je možné, že absolutně nelze provést bez dané rozhraní API a nemůžete najít náhradní vhodný pro aplikace pro Windows Store.  V takovém případě minimálně:  
  
-   Test, test, test daylights životností mimo vaše používání tohoto rozhraní API.  
  
-   Zjistit, že rozhraní API může najednou přerušení nebo zmizí Pokud volána z uvnitř Windows Store aplikace v budoucích vezích systému Windows.  To nebude se zvažovat problém kompatibility společností Microsoft a podpora vašeho využití ho nebude prioritu.  
  
<a name="Permissions"></a>   
### <a name="reduced-permissions"></a>Omezená oprávnění  
 Je nad rámec tohoto tématu a seznamu všechny způsoby, které se liší od aplikace klasické pracovní plochy oprávnění aplikace Windows Store.  Ale určitě chování se liší pokaždé, když vaše knihovna DLL profileru (při načítání do aplikace pro Windows Store ve srovnání se aplikace na ploše) pokusí o přístup k žádným prostředkům.  Systém souborů je nejčastější.  Existuje ale několik umístí na disk, který je povolen přístup k dané aplikace pro Windows Store (viz [souboru oprávnění a přístupová práva (aplikace Windows Runtime](https://msdn.microsoft.com/library/windows/apps/hh967755.aspx)), a knihovny DLL profileru budou v rámci stejné omezení.  Důkladně otestujte svůj kód.  
  
<a name="Interprocess"></a>   
### <a name="inter-process-communication"></a>Komunikace mezi procesy  
 Jak je vidět v diagramu na začátku tohoto dokumentu, knihovny DLL profileru (načíst do procesního prostoru aplikace Windows Store) bude pravděpodobně potřeba komunikovat s profileru uživatelské rozhraní (spuštění v prostoru procesu samostatné aplikace na ploše) vlastní vlastní mezi procesem kanál komunikace (IPC).  Rozhraní profileru signály odesílá na knihovnu DLL profileru změnit její chování a knihovny DLL profileru odešle data z analyzovaných aplikace Windows Store zpět do rozhraní profileru po zpracování a zobrazení profileru uživateli.  
  
 Většina profilery musí pracovat tímto způsobem, ale vaše možnosti pro mechanismy IPC jsou omezenější při načtení knihovny DLL profileru do aplikace pro Windows Store.  Například pojmenované kanály nejsou součástí aplikace pro Windows Store SDK, abyste je nejde používat.  
  
 Ale samozřejmě soubory jsou pořád ještě v, i když způsobem omezenější.  Události jsou k dispozici.  
  
 **Komunikaci přes soubory**  
 Většina vašich dat bude pravděpodobně předat mezi profileru DLL a uživatelského rozhraní profileru prostřednictvím soubory.  Klíč je vybrat umístění souboru, který profileru DLL (v rámci aplikace pro Windows Store) i profileru uživatelského rozhraní mají čtení a zápis.  Například cesta dočasné složky je umístění, které profileru DLL a uživatelského rozhraní profileru získat přístup, ale žádný jiný balíček aplikace Windows Store přístup (tedy stínění. Další informace, které protokolu z jiné balíčky aplikací Windows Store).  
  
 Profileru uživatelského rozhraní a knihovny DLL profileru můžete tuto cestu určit nezávisle.  Profileru uživatelské rozhraní, když ho iteruje všechny balíčky nainstalované pro aktuálního uživatele (viz výše uvedeném ukázkovém kódu), získá přístup k `PackageId` třídy, ze kterého může být cesta ke složce dočasných odvozené kódem, podobně jako tento fragment kódu.  (Jako vždy Kontrola chyb je vynechaný jako stručný výtah.)  
  
```csharp  
// C# code for the Profiler UI.  
ApplicationData appData =  
    ApplicationDataManager.CreateForPackageFamily(  
        packageId.FamilyName);  
  
tempDir = appData.TemporaryFolder.Path;  
```  
  
 Mezitím, knihovny DLL profileru můžete provést v podstatě totéž, by to možné informace snadno získat k [ApplicationData](https://msdn.microsoft.com/library/windows/apps/windows.storage.applicationdata.aspx) pomocí [ApplicationData.Current](https://msdn.microsoft.com/library/windows/apps/windows.storage.applicationdata.current.aspx) vlastnost.  
  
 **Komunikaci přes události**  
 Pokud chcete jednoduché signalizační sémantiku mezi profileru uživatelského rozhraní a knihovny DLL profileru, můžete události v aplikacích pro Windows Store, jakož i aplikace klasické pracovní plochy.  
  
 Z vaší knihovny DLL profileru můžete jednoduše volat [CreateEventEx](https://msdn.microsoft.com/library/windows/desktop/ms682400\(v=vs.85\).aspx) funkce Vytvoření pojmenovaného události s libovolný název.  Příklad:  
  
```cpp  
// Profiler DLL in Windows Store app (C++).  
CreateEventEx(   
    NULL,  // Not inherited  
    "MyNamedEvent"  
    CREATE_EVENT_MANUAL_RESET, /* explicit ResetEvent() required; leave initial state unsignaled */  
    EVENT_ALL_ACCESS);  
```  
  
 Uživatelské rozhraní profileru je pak potřeba najít tuto událost s názvem pod oborem názvů aplikace pro Windows Store.  Například může volat uživatelské rozhraní profileru [CreateEventEx](https://msdn.microsoft.com/library/windows/desktop/ms682400\(v=vs.85\).aspx), zadání názvu událostí jako  
  
 `AppContainerNamedObjects\<acSid>\MyNamedEvent`  
  
 `<acSid>`je aplikace pro Windows Store AppContainer SID.  Výše uvedené části tohoto tématu vám ukázal, jak iterovat balíčky nainstalované pro aktuálního uživatele.  Z ukázkový kód můžete získat ID balíčku.  A z ID balíčku, můžete získat `<acSid>` podobné následujícím kódem:  
  
```csharp  
IntPtr acPSID;  
DeriveAppContainerSidFromAppContainerName(packageId.FamilyName, out acPSID);  
  
string acSid;  
ConvertSidToStringSid(acPSID, out acSid);  
  
string acDir;  
GetAppContainerFolderPath(acSid, out acDir);  
```  
  
<a name="Shutdown"></a>   
### <a name="no-shutdown-notifications"></a>Žádná oznámení vypnutí  
 Při spuštění v rámci aplikace pro Windows Store, knihovny DLL profileru neměli spoléhat na buď [icorprofilercallback::Shutdown –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md) nebo i [DllMain](https://msdn.microsoft.com/library/windows/desktop/ms682583\(v=vs.85\).aspx) (s `DLL_PROCESS_DETACH`) volaná oznámit vaše knihovna DLL profileru aby byl ukončen aplikace pro Windows Store.  Ve skutečnosti byste měli očekávat, že se nebude nikdy volat.  V minulosti mít mnoho knihoven DLL profileru použít tyto oznámení jako vhodného místa k vyprázdnění mezipaměti na disku, zavřete soubory, odesílání oznámení zpět do uživatelského rozhraní profileru atd.  Ale nyní vaší profileru DLL musí být uspořádaný trochu jinak.  
  
 Vaše knihovna DLL profileru by měl být informace o protokolování, protože probíhá.  Z důvodů výkonu můžete dávky informace v paměti a vyprázdnění ho na disk s růstem dávky ve velikosti za některých prahovou hodnotu.  Ale předpokládá, že může dojít ke ztrátě veškeré informace, které ještě nebyly vyprazdňuje na disk.  To znamená, že budete chtít dobře vyberte vaše prahovou hodnotu a že uživatelské rozhraní profileru musí být posílené jak nakládat s neúplné informace o zapsána knihovnou DLL profileru.  
  
<a name="Metadata"></a>   
## <a name="windows-runtime-metadata-files"></a>Soubory metadat prostředí Windows Runtime  
 Je mimo rozsah tohoto dokumentu přejděte do podrobností na jaké metadata prostředí Windows Runtime (WinMD) jsou soubory.    Tato část je omezený na jak zpracuje CLR profilace API jsou načteny WinMD soubory, které je vaše knihovna DLL profileru analýza aplikace Windows Store.  
  
<a name="WMDs"></a>   
### <a name="managed-and-non-managed-winmds"></a>WinMDs spravovaných a nespravovaných  
 Pokud vývojář používá Visual Studio k vytvoření nového projektu komponenty prostředí Windows Runtime, vytvoří sestavení tohoto projektu souboru WinMD, který popisuje metadata (popisech typu třídy, rozhraní, atd.) vytvořené sám vývojář.  Pokud tento projekt je spravovaný jazyk projektu napsané v C# nebo VB, že stejný soubor WinMD také obsahuje provádění těchto typů (což znamená, že obsahuje všechny IL kompilují ze zdrojového kódu pro vývojáře).  Tyto soubory se označují jako spravované WinMD soubory.  Jsou zajímavé v, že obsahují metadata prostředí Windows Runtime a základní implementaci.  
  
 Naproti tomu pokud vývojář vytvoří projekt komponenty prostředí Windows Runtime jazyka C++, sestavení tohoto projektu vytvoří WinMD soubor, který obsahuje pouze metadata a implementaci se zkompiluje do samostatné nativní knihovny DLL.  Podobně WinMD souborech, které jsou součástí ve Windows SDK obsahují pouze metadata, s implementací zkompilovat do samostatné nativních knihoven DLL, které se dodávají jako součást systému Windows.  
  
 Níže uvedené informace platí pro obě spravované WinMDs, které budou obsahovat metadata a implementace, a nespravované WinMDs, které obsahují pouze metadata.  
  
<a name="CLRModules"></a>   
### <a name="winmd-files-look-like-clr-modules"></a>Soubory WinMD vypadat moduly CLR  
 Co se týče modulu CLR, jsou všechny soubory WinMD moduly.  Profilace API CLR proto informuje knihovnou DLL profileru při načtení WinMD soubory a jaké jejich ModuleIDs jsou, stejně jako u jiných spravované moduly.  
  
 Vaše knihovna DLL profileru možné rozlišit WinMD soubory z ostatních modulů voláním [icorprofilerinfo3::getmoduleinfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md) metoda a zkontrolujete `pdwModuleFlags` výstupní parametr pro [COR_PRF_MODULE_WINDOWS_ Modul RUNTIME](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) příznak.  (Bude nastaveno pouze v případě ModuleID představuje WinMD.)  
  
<a name="Reading"></a>   
### <a name="reading-metadata-from-winmds"></a>Načítání metadat z WinMDs  
 WinMD souborech, jako jsou regulární moduly, obsahovat metadata, která lze číst pomocí [metadat rozhraní API](../../../../docs/framework/unmanaged-api/metadata/index.md).  Však modulu CLR mapuje typy prostředí Windows Runtime rozhraní .NET Framework typy při čtení souboru WinMD soubory tak, aby vývojáři, kteří programu ve spravovaném kódu a využívat souboru WinMD může mít více fyzických programovací prostředí.  Některé příklady tato mapování najdete v tématu [rozhraní .NET Framework podporu pro aplikace Windows Store a prostředí Windows Runtime](../../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md).  
  
 Proto zobrazení, které vaše profileru získáte, když používá metadat rozhraní API: nezpracovaná zobrazení prostředí Windows Runtime nebo namapované zobrazení rozhraní .NET Framework?  Odpověď: je to pro vás.  
  
 Při volání [icorprofilerinfo::getmodulemetadata –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) metodu WinMD k získání metadat rozhraní, jako například [imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), můžete nastavit [ofNoTransform](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)v `dwOpenFlags` parametr vypnout toto mapování.  Jinak výchozí mapování budou povoleny.  Obvykle profileru ponechá mapování povoleno, takže řetězce, které knihovny DLL profileru získává z metadat WinMD (například názvy typů) bude vypadat známé a přirozené profileru uživateli.  
  
<a name="Modifying"></a>   
### <a name="modifying-metadata-from-winmds"></a>Úprava metadata z WinMDs  
 Úprava metadat v WinMDs není podporována.  Když zavoláte [icorprofilerinfo::getmodulemetadata –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) metodu WinMD souboru a zadejte [ofWrite](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) v `dwOpenFlags` parametr nebo požádat o rozhraní zapisovatelné metadata, jako [ Imetadataemit –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md), [getmodulemetadata –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) se nezdaří.  To je zvláště důležité k přepisování IL profilery, které je třeba upravit metadata pro podporu jejich instrumentace (například přidat AssemblyRefs nebo nové metody).  Proto byste měli zkontrolovat pro [COR_PRF_MODULE_WINDOWS_RUNTIME](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) nejprve (jak je popsáno v předchozí části) a nepoužívejte žádostí o rozhraní zapisovatelné metadat na takové moduly.  
  
<a name="Resolving"></a>   
### <a name="resolving-assembly-references-with-winmds"></a>Odkazy na sestavení s WinMDs řešení  
 Mnoho profilery muset vyřešit odkazy na metadata ručně, které pomáhají s instrumentace nebo typ kontroly.  Takové profilery je potřeba vědět, jak modulu CLR přeloží odkazy na sestavení, které odkazují na WinMDs, protože tyto odkazy jsou vyřešeny zcela jiným způsobem než standardní odkazy na sestavení.  
  
<a name="Profilers"></a>   
## <a name="memory-profilers"></a>Profilery paměti  
 Systém uvolňování paměti a spravovaná halda nejsou podstatně liší v aplikaci Windows Store a aplikace na ploše.  Existují však určité rozdíly jemně, které je potřeba mít na paměti profileru autoři.  
  
<a name="ForceGC"></a>   
### <a name="forcegc-creates-a-managed-thread"></a>Forcegc – vytvoří spravovaná vlákna  
 Když to profilace paměti, knihovny DLL profileru obvykle vytvoří samostatné vlákno, ze kterého mají být volání [forcegc – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md) metoda.  To není nic nového.  Ale co může být překvapivé je, že v rámci provádění uvolňování uvnitř aplikace pro Windows Store může transformaci vašeho vlákna na spravovaná vlákna (například profilace ID podprocesu rozhraní API pro bude vytvořeno daném vláknu).  
  
 K chápu důsledky tohoto, je důležité znát rozdíly mezi synchronní a asynchronní volání podle definice rozhraní API profilace CLR. Všimněte si, že se jedná o velmi liší od koncept asynchronní volání v aplikacích pro Windows Store.  Naleznete v příspěvku blogu [proto máme CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](https://blogs.msdn.microsoft.com/davbr/2008/12/23/why-we-have-corprof_e_unsupported_call_sequence/) Další informace.  
  
 Relevantní bod je, že volání na vláken vytvořené vaší profileru jsou vždy považovány za synchronní, i když tyto volání z mimo implementace jednoho z knihovny DLL profileru [icorprofilercallback –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) metody.  Alespoň, který používá tento případ.  Teď, když modul CLR má převedena vaší profileru přístup z více vláken na spravovaná vlákna z důvodu volání do [forcegc – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md), že podproces považuje už vaše profileru přístup z více vláken.  Jako takový modulu CLR vynucuje přísnější definice co kvalifikují jako synchronní pro daném vláknu – konkrétně, volání musí pocházet z uvnitř jeden z knihovny DLL profileru [icorprofilercallback –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) metody pro kvalifikaci jako synchronní.  
  
 Co to znamená v praxi?  Většina [icorprofilerinfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) metody jsou bezpečné volat synchronně a okamžitě se jinak nezdaří.  Pokud vaše knihovna DLL profileru opětovně používá vaše [forcegc – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md) vlákno pro jiná volání obvykle probíhají vytvořené profileru vláken (například k [requestprofilerdetach –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md), [requestrejit –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md), nebo [requestrevert –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)), budete mít potíže.  I asynchronní bezpečných funkce, jako [dostacksnapshot –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) má zvláštní pravidla při volání z spravovaných vláknech. (Naleznete v příspěvku blogu [profileru zásobníku proti: základy a dále](https://blogs.msdn.microsoft.com/davbr/2005/10/06/profiler-stack-walking-basics-and-beyond/) Další informace.)  
  
 Proto doporučujeme, aby všechny vlákno knihovny DLL profileru vytvoří volat [forcegc – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md) slouží *pouze* za účelem spouštění GC a potom reakcí na globální Katalog zpětných volání.  Nesmí se volání do rozhraní API pro profilaci provést další úlohy, jako je zásobník vzorkování nebo odpojování.  
  
<a name="WeakTable"></a>   
### <a name="conditionalweaktablereferences"></a>ConditionalWeakTableReferences  
 Od verze rozhraní .NET Framework 4.5, je nové zpětné volání GC, [conditionalweaktableelementreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md), které poskytuje profileru více úplné informace o *závislé popisovače*. Tyto popisovače efektivně přidat odkaz z ke zdrojovému objektu objekt cíle pro účely správy životního cyklu GC.  Závislé popisovače jsou nic nového a vývojáře, kteří programu ve spravovaném kódu byly moct vytvořit pomocí vlastních závislé obslužné rutiny <xref:System.Runtime.CompilerServices.ConditionalWeakTable%602?displayProperty=nameWithType> třídy ani před Windows 8 a rozhraní .NET Framework 4.5.  
  
 Ale spravované aplikace pro XAML Windows Store teď hodně využívají závislé popisovače.  Konkrétně modulu CLR použije je k pomáhají se správou cykly odkaz mezi spravovaných a nespravovaných prostředí Windows Runtime objekty.  To znamená, že je důležitější teď než někdy pro profilery paměti na informace o těchto závislé popisovače tak, aby se můžete vizualizovat spolu s ostatními okraje v heap graph.  Vaše knihovna DLL profileru by měl používat [rootreferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md), [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), a [conditionalweaktableelementreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) dohromady a dokončení zobrazení grafu haldy .  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>Závěr  
 Je možné použít rozhraní API profilace CLR analýza spravovaného kódu běžících v rámci aplikace pro Windows Store.  Ve skutečnosti můžete využít existující profileru, které vyvíjíte a provést určité změny tak, aby ho můžete vybrat aplikace pro Windows Store.   Uživatelské rozhraní profileru měli používat nových rozhraní API pro aktivaci aplikace pro Windows Store v režimu ladění.  Ujistěte se, zda vaše knihovna DLL profileru využívá pouze API, použít pro aplikace pro Windows Store.  Tento mechanismus komunikace mezi profileru DLL a uživatelského rozhraní profileru by měly být zapsány s omezení rozhraní API aplikace Windows Store v paměti a sledování omezená oprávnění na místě pro aplikace Windows Store.  Vaše knihovna DLL profileru měli vědět, jak modul CLR pracuje WinMDs, a jak Garbage Collector chování se liší s ohledem na spravovaná vlákna.  
  
<a name="Resources"></a>   
## <a name="resources"></a>Prostředky  
 **Modul Common Language Runtime**  
 -   [Referenční dokumentace rozhraní API pro profilaci CLR](../../../../docs/framework/unmanaged-api/profiling/index.md)  
  
-   [Referenční dokumentace rozhraní API Metadata CLR](../../../../docs/framework/unmanaged-api/metadata/index.md)  
  
 **Modul CLR interakci s prostředí Windows Runtime**  
 [Podpora v rozhraní .NET framework pro aplikace pro Windows Store a prostředí Windows Runtime](../../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)  
  
 **Aplikace pro Windows Store**  
 -   [Přístup k souborům a oprávnění (aplikace pro prostředí Windows Runtime](https://msdn.microsoft.com/library/windows/apps/hh967755.aspx)  
  
-   [Získat licenci vývojáře](https://msdn.microsoft.com/library/windows/apps/Hh974578.aspx)  
  
-   [IPackageDebugSettings rozhraní](https://msdn.microsoft.com/library/hh438393\(v=vs.85\).aspx)  
  
## <a name="see-also"></a>Viz také  
 [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
