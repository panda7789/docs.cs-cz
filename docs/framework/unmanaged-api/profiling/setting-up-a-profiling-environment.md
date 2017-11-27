---
title: "Nastavení prostředí profilace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- environment variables, profiling API
- profiling API [.NET Framework], setting up environment
- COR_PROFILER environment variable
- Windows Service applications, profiling
- profiling API [.NET Framework], Windows Service applications
- COR_ENABLE_PROFILING environment variable
- profiling API [.NET Framework], enabling
ms.assetid: fefca07f-7555-4e77-be86-3c542e928312
caps.latest.revision: "29"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7ff2c57be82166ecf5eb8a012491044eb2cb79d4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="setting-up-a-profiling-environment"></a>Nastavení prostředí profilace
> [!NOTE]
>  Byly provedeny významné změny profilace v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
 Když se spustí spravovaného procesu (aplikace nebo služba), načte modul CLR (CLR). Při inicializaci modulu CLR, vyhodnotí následující dvě proměnné prostředí se rozhodnout, jestli by se měly připojit proces profileru:  
  
-   Cor_enable_profiling –: Modulu CLR se připojí k profileru pouze v případě, že je tato proměnná prostředí existuje a je nastaven na hodnotu 1.  
  
-   Cor_profiler –: Pokud je kontrola cor_enable_profiling – úspěšně projde, modul CLR připojí se k profileru, který má tento CLSID nebo ProgID, který musí mít dříve uloženou v registru. Cor_profiler – proměnná prostředí je definován jako řetězec, jak je znázorněno v následující dva příklady.  
  
    ```  
    set COR_PROFILER={32E2F4DA-1BEA-47ea-88F9-C5DAF691C94A}  
    set COR_PROFILER="MyProfiler"  
    ```  
  
 Do profilu aplikace CLR, je nutné nastavit cor_enable_profiling – a cor_profiler – proměnné prostředí před spuštěním aplikace. Musí se také ujistěte, zda je zaregistrován profileru knihovny DLL.  
  
> [!NOTE]
>  Od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], profilery nemusí být zaregistrován.  
  
> [!NOTE]
>  Použití rozhraní .NET Framework verze 2.0, 3.0 a 3.5 profilery v [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] a novější verze, musíte nastavit proměnnou prostředí COMPLUS_ProfAPI_ProfilerCompatibilitySetting.  
  
## <a name="environment-variable-scope"></a>Obor proměnné prostředí  
 Nastavení proměnných prostředí cor_enable_profiling – a cor_profiler – určí, že jejich obor vliv. Tyto proměnné můžete nastavit v jednom z následujících způsobů:  
  
-   Pokud nastavíte proměnné [icordebug::CreateProcess –](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) volání, použijí se jenom na aplikace, kterou používáte v době. (Bude také vztahují k ostatním aplikacím spuštění této aplikace, které dědí prostředí.)  
  
-   Pokud jste nastavili proměnné v okně příkazového řádku, použijí se na všechny aplikace, které jsou spuštěné z dané okno.  
  
-   Pokud jste nastavili proměnné na úrovni uživatele, použijí se na všechny aplikace, které začínají Průzkumníka souborů. Okno příkazového řádku otevřete po nastavení proměnné budou mít tato nastavení prostředí, a proto budou všechny aplikace, které začínají toto okno. Nastavení proměnných prostředí na úrovni uživatele, klikněte pravým tlačítkem na **Můj počítač**, klikněte na tlačítko **vlastnosti**, klikněte na tlačítko **Upřesnit** , klikněte na **prostředí Proměnné**a přidat proměnné, které chcete **uživatelské proměnné** seznamu.  
  
-   Pokud jste nastavili proměnné na úrovni počítače, použijí se na všechny aplikace, které jsou spuštěny na tomto počítači. Které na tomto počítači otevřít okno příkazového řádku se mají tato nastavení prostředí a proto budou všechny aplikace, které začínají toto okno. To znamená, že bude každého spravovaného procesu na tomto počítači spustit s vaší profileru. Nastavení proměnných prostředí na úrovni počítače, klikněte pravým tlačítkem na **Můj počítač**, klikněte na tlačítko **vlastnosti**, klikněte na tlačítko **Upřesnit** , klikněte na **prostředí Proměnné**, proměnné, které chcete přidat **systémové proměnné** seznamu a pak restartujte počítač. Proměnné po restartování počítače se bude k dispozici celý systém.  
  
 Pokud jsou profilování služby systému Windows, je nutné restartovat počítač po nastavení proměnných prostředí a zaregistrovat profileru knihovny DLL. Další informace o těchto aspektů, najdete v části [profilace služby systému Windows](#windows_service).  
  
## <a name="additional-considerations"></a>Další informace  
  
-   Třída implementuje profileru [icorprofilercallback –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) a [icorprofilercallback2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) rozhraní. V rozhraní .NET Framework verze 2.0, musí implementovat profileru `ICorProfilerCallback2`. Pokud tomu tak není, `ICorProfilerCallback2` nenačte se.  
  
-   Pouze jeden profileru můžete profil proces v jednom okamžiku v daném prostředí. Dva různé profilery můžete zaregistrovat v různých prostředích, ale každý musí profilu samostatné procesy. Jako server COM v procesu knihovny DLL, která se mapuje do stejné adresní prostor jako proces, který je profilovaný musí být implementované profileru. To znamená, že profileru běží v procesu. Rozhraní .NET Framework nepodporuje žádný jiný druh COM server. Například pokud profileru chce monitorování aplikací ze vzdáleného počítače, musí implementovat kolekce agentů na každém počítači. Tyto agenty bude dávky výsledky a předávat je počítač centrální data kolekce.  
  
-   Protože profileru je objekt modelu COM, který je instancí procesu, každá PROFILOVANÉHO aplikace bude mít vlastní kopii profileru. Instance jednoho profileru proto není nutné zpracovat data z více aplikací. Nicméně budete muset přidat logiku ke kódu protokolování profileru aby souboru protokolu přepíše od ostatních PROFILOVANÉHO aplikací.  
  
## <a name="initializing-the-profiler"></a>Inicializace profileru  
 Při předávání obou kontrol proměnné prostředí, modul CLR vytvoří instanci profileru podobným způsobem jako do knihovny COM `CoCreateInstance` funkce. Profileru není načten prostřednictvím přímého volání `CoCreateInstance`. Proto volání `CoInitialize`, což vyžaduje, aby nastavení modelu vláken je vyhnout. Modul CLR pak zavolá [icorprofilercallback::Initialize –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) metoda v profileru. Podpis tato metoda je následující.  
  
```  
HRESULT Initialize(IUnknown *pICorProfilerInfoUnk)  
```  
  
 Profileru musí dotaz `pICorProfilerInfoUnk` pro [icorprofilerinfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) nebo [ICorProfilerInfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md) rozhraní ukazatel a uložit ho tak, aby ho může požádat o další informace později v průběhu vytváření profilů.  
  
## <a name="setting-event-notifications"></a>Nastavení oznámení událostí  
 Pak zavolá profileru [icorprofilerinfo::seteventmask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metoda k určení, které kategorie oznámení, která je zájmu v. Například pokud profileru pouze ve funkci, zadejte a nechat oznámení a oznámení pro uvolňování paměti, určuje následující.  
  
```  
ICorProfilerInfo* pInfo;  
pICorProfilerInfoUnk->QueryInterface(IID_ICorProfilerInfo, (void**)&pInfo);  
pInfo->SetEventMask(COR_PRF_MONITOR_ENTERLEAVE | COR_PRF_MONITOR_GC)  
```  
  
 Nastavením maska oznámení tímto způsobem můžete omezit profileru oznámení, která obdrží. Tento přístup pomůže sestavit jednoduchý nebo speciální profileru uživatele. Také snižuje čas procesoru, který by dojít ke znehodnocení části odesílání oznámení, které by profileru právě ignorovat.  
  
 Určité události profileru jsou neměnné. To znamená, že hned, jak tyto události jsou nastavené `ICorProfilerCallback::Initialize` zpětné volání, nemůže být je vypnuté a nové události nelze zapnout. Pokusy o změnu neměnné událost způsobí `ICorProfilerInfo::SetEventMask` vrácení neúspěšné HRESULT.  
  
<a name="windows_service"></a>   
## <a name="profiling-a-windows-service"></a>Profilace služby systému Windows  
 Profilace služby systému Windows je jako profilace běžné aplikace runtime jazyka. Prostřednictvím proměnné prostředí jsou k dispozici obě profilování operace. Protože služba systému Windows je spuštěn, když už musí být spuštěný operační systém, proměnné prostředí, jak jsme vysvětlili výše v tomto tématu nastavte požadované hodnoty před spuštění systému a k dispozici. Kromě toho musí být profilování DLL již zaregistrován v systému.  
  
 Po nastavení proměnných prostředí cor_enable_profiling – a cor_profiler – a zaregistrujte profileru knihovny DLL, je třeba restartovat cílový počítač tak, aby služba systému Windows můžete zjistit tyto změny.  
  
 Všimněte si, že se tyto změny povolit profilace v rámci celého systému. Pokud chcete zabránit každé následně spuštěné z profilovaný spravované aplikace, byste měli odstranit proměnných prostředí systému po restartování cílového počítače.  
  
 Tento postup také vede k každých CLR proces získávání profilovaným. Profileru by měl přidejte logiku pro jeho [icorprofilercallback::Initialize –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) zpětné volání pro zjistí, zda je aktuální proces zájmu. Pokud není, profileru může selhat zpětné volání bez provedení inicializace.  
  
## <a name="see-also"></a>Viz také  
 [Přehled profilace](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)
