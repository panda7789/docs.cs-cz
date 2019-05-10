---
title: Nastavení prostředí profilace
ms.date: 03/30/2017
helpviewer_keywords:
- environment variables, profiling API
- profiling API [.NET Framework], setting up environment
- COR_PROFILER environment variable
- Windows Service applications, profiling
- profiling API [.NET Framework], Windows Service applications
- COR_ENABLE_PROFILING environment variable
- profiling API [.NET Framework], enabling
ms.assetid: fefca07f-7555-4e77-be86-3c542e928312
author: mairaw
ms.author: mairaw
ms.openlocfilehash: af68041cd016b457c449c283601bd5a0d4258c8e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64666056"
---
# <a name="setting-up-a-profiling-environment"></a>Nastavení prostředí profilace
> [!NOTE]
>  Byly provedeny podstatné změny profilování v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
 Při spuštění spravovaného procesu (aplikace nebo služby) načte modul CLR (CLR). Když je modul CLR inicializován, vyhodnocuje dvě následující proměnné prostředí se rozhodnout, jestli se má proces připojit k profileru:  
  
- COR_ENABLE_PROFILING: Modul CLR se připojí k profileru pouze v případě, že tato proměnná prostředí existuje a je nastaven na hodnotu 1.  
  
- COR_PROFILER: Pokud COR_ENABLE_PROFILING kontrolovat PASS, CLR se připojí k profileru, který má tento identifikátor CLSID nebo ProgID, který musí být již uložen v registru. Proměnná prostředí COR_PROFILER je definována jako řetězec, jak je znázorněno v následující dva příklady.  
  
    ```  
    set COR_PROFILER={32E2F4DA-1BEA-47ea-88F9-C5DAF691C94A}  
    set COR_PROFILER="MyProfiler"  
    ```  
  
 Chcete-li Profilovat aplikaci CLR, musíte nastavit proměnné prostředí COR_ENABLE_PROFILING a COR_PROFILER před spuštěním aplikace. Také musíte zkontrolovat, že profiler DLL registrován.  
  
> [!NOTE]
>  Počínaje [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], profilovací programy není třeba registrovat.  
  
> [!NOTE]
>  Použití rozhraní .NET Framework verze 2.0, 3.0 a 3.5 profilerů v [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] a novější verze, musíte nastavit proměnnou prostředí COMPLUS_ProfAPI_ProfilerCompatibilitySetting.  
  
## <a name="environment-variable-scope"></a>Rozsah proměnné prostředí  
 Jak je nastavit proměnné prostředí COR_ENABLE_PROFILING a COR_PROFILER, určí jejich rozsah vlivu. Tyto proměnné můžete nastavit v jednom z následujících způsobů:  
  
- Pokud jste nastavili proměnné [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) volání, použijí se jenom na aplikace, která spustíte v době. (Budou také použity k ostatním aplikacím spuštěné aplikací, které dědí prostředí.)  
  
- Pokud jste nastavili proměnné v okně příkazového řádku, použijí se na všechny aplikace, které jsou spuštěny z tohoto okna.  
  
- Pokud jste nastavili proměnné na úrovni uživatele, použijí se na všechny aplikace, které spustíte pomocí Průzkumníka souborů. Okno příkazového řádku otevřete po nastavení proměnných, bude mít tato nastavení prostředí, a stejně tomu bude u všech aplikací, které spustíte z tohoto okna. Chcete-li nastavit proměnné prostředí na úrovni uživatele, klikněte pravým tlačítkem na **tento počítač**, klikněte na tlačítko **vlastnosti**, klikněte na tlačítko **Upřesnit** klikněte na tlačítko **prostředí Proměnné**a přidejte proměnné do **uživatelské proměnné** seznamu.  
  
- Pokud jste nastavili proměnné na úrovni počítače, použijí se na všechny aplikace, které jsou spuštěny v počítači. Okno příkazového řádku, které otevřete na tomto počítači bude mít tato nastavení prostředí a stejně tomu bude u všech aplikací, které spustíte z tohoto okna. To znamená, že všechny spravované procesy v tomto počítači se spustí s vaším profilerem. Chcete-li nastavit proměnné prostředí na úrovni počítače, klikněte pravým tlačítkem na **tento počítač**, klikněte na tlačítko **vlastnosti**, klikněte na tlačítko **Upřesnit** klikněte na tlačítko **prostředí Proměnné**, přidejte proměnné do **systémové proměnné** seznamu a pak restartujte počítač. Po restartování počítače se budou proměnné k dispozici celý systém.  
  
 Pokud profilujete službu Windows, musí se po nastavení proměnných prostředí a registraci profileru DLL restartovat počítač. Další informace o těchto možnostech najdete v části [profilování služby Windows](#windows_service).  
  
## <a name="additional-considerations"></a>Další informace  
  
- Třída profileru implementuje [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) a [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) rozhraní. V rozhraní .NET Framework verze 2.0 musí profiler implementovat `ICorProfilerCallback2`. Pokud ne, `ICorProfilerCallback2` nebudou načteny.  
  
- Pouze jeden profiler může Profilovat proces v jednom okamžiku v daném prostředí. V různých prostředích můžete zaregistrovat dva různé profilovací programy, ale každý musí Profilovat samostatné procesy. Profiler musí být implementován jako modelu COM v procesový server knihovny DLL, která je namapována na stejném adresním prostoru jako proces, který je právě profilována. To znamená, že profiler běží v procesu. Rozhraní .NET Framework nepodporuje žádný jiný typ serveru COM. Například pokud profiler chce sledovat aplikace ze vzdáleného počítače, musí implementovat kolektor agentů v každém počítači. Tito agenti budou dávkovat výsledky a sdělovat počítač centrální kolekce dat.  
  
- Protože profiler je objekt modelu COM, který je vytvořeny během procesu, každá profilovaná aplikace bude mít svou vlastní kopii profileru. Proto jediná instance profileru nemusí zpracovávat data z více aplikací. Musíte však přidat logiku pro kód protokolování profileru Chcete-li zabránit souboru protokolu v přepsání z jiných profilovaných aplikací.  
  
## <a name="initializing-the-profiler"></a>Inicializuje Profiler  
 Když obě kontroly proměnné prostředí projdou, CLR vytvoří instanci okna profilování podobným způsobem jako do modelu COM `CoCreateInstance` funkce. Profiler není načten pomocí přímého volání `CoCreateInstance`. Proto volání `CoInitialize`, což vyžaduje nastavení modelu vláken, je vyloučeno. CLR pak zavolá [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) metoda v profileru. Signatura této metody je následující.  
  
```  
HRESULT Initialize(IUnknown *pICorProfilerInfoUnk)  
```  
  
 Profiler se musí dotazovat `pICorProfilerInfoUnk` pro [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) nebo [ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md) ukazatele rozhraní a uložte ho tak, aby mohl požadovat další informace později při profilování.  
  
## <a name="setting-event-notifications"></a>Nastavení oznámení události  
 Profiler pak zavolá [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metodu k určení, které kategorie oznámení ho zajímají. Například pokud se profiler zajímá pouze funkce a opuštění oznámení a oznámení pro kolekci paměti, určuje následující.  
  
```  
ICorProfilerInfo* pInfo;  
pICorProfilerInfoUnk->QueryInterface(IID_ICorProfilerInfo, (void**)&pInfo);  
pInfo->SetEventMask(COR_PRF_MONITOR_ENTERLEAVE | COR_PRF_MONITOR_GC)  
```  
  
 Nastavením masky upozornění tímto způsobem může profiler omezit, která oznámení obdrží. Tento přístup pomáhá uživateli vytvářet jednoduchý nebo speciální profiler. Také snižuje čas procesoru, který by byl vyplýtván odesíláním oznámení, které by profiler ignoroval.  
  
 Některé události profileru jsou neměnné. To znamená, že jakmile tyto události jsou nastaveny `ICorProfilerCallback::Initialize` zpětné volání, není možné zapnout a nové události nelze zapnout. Výsledkem bude pokusy o změnu neměnné události `ICorProfilerInfo::SetEventMask` vrátí selhání HRESULT.  
  
<a name="windows_service"></a>   
## <a name="profiling-a-windows-service"></a>Profilování služby Windows  
 Profilování služby Windows je jako profilování aplikace common language runtime. Prostřednictvím proměnných prostředí jsou povoleny obě operace profilování. Protože služba Windows se spustí při spuštění operačního systému, proměnné prostředí uvedené dříve v tomto tématu již musí být přítomny a nastaveny na požadované hodnoty před spuštěním systému. Kromě toho musí být profilování DLL již registrován v systému.  
  
 Po nastavení proměnných prostředí COR_ENABLE_PROFILING a COR_PROFILER a zaregistrování profileru DLL je třeba restartovat cílový počítač tak, aby služba Windows mohla rozpoznat tyto změny.  
  
 Všimněte si, že tyto změny umožní profilování v celého systému. Aby se zabránilo všechny spravované aplikace, které jsou následně spuštěny, profilovány, byste měli odstranit systémové proměnné prostředí po restartování cílového počítače.  
  
 Tato technika také vede k každý proces CLR profilován. Profiler by měl přidat logiku pro jeho [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) zpětného volání k detekci, zda je aktuální proces zájmu. Pokud není, profiler může selhat při zpětném volání bez provedení inicializace.  
  
## <a name="see-also"></a>Viz také:

- [Přehled profilace](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)
