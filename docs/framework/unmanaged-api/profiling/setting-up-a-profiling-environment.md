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
ms.openlocfilehash: 32ebb868ea64a24fba80133b1a0eb539f51cb411
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176965"
---
# <a name="setting-up-a-profiling-environment"></a>Nastavení prostředí profilace
> [!NOTE]
> Došlo k podstatným změnám profilování v rozhraní .NET Framework 4.  
  
 Při spuštění spravovaného procesu (aplikace nebo služby) načte za běhu společného jazyka (CLR). Když clr je inicializována, vyhodnotí následující dvě proměnné prostředí rozhodnout, zda proces by měl připojit k profiler:  
  
- COR_ENABLE_PROFILING: CLR se připojí k profileru pouze v případě, že tato proměnná prostředí existuje a je nastavena na 1.  
  
- COR_PROFILER: Pokud COR_ENABLE_PROFILING kontrola projde, CLR připojí k profiler, který má tento CLSID nebo ProgID, které musí být uloženy dříve v registru. Proměnná prostředí COR_PROFILER je definována jako řetězec, jak je znázorněno na následujících dvou příkladech.  
  
    ```cpp  
    set COR_PROFILER={32E2F4DA-1BEA-47ea-88F9-C5DAF691C94A}  
    set COR_PROFILER="MyProfiler"  
    ```  
  
 Chcete-li profilovat aplikaci CLR, musíte před spuštěním aplikace nastavit COR_ENABLE_PROFILING a COR_PROFILER proměnné prostředí. Musíte se také ujistit, že je registrována dll profiler.  
  
> [!NOTE]
> Počínaje rozhraním .NET Framework 4 nemusí být profilovací programy registrovány.  
  
> [!NOTE]
> Chcete-li použít profilovací programy rozhraní .NET Framework verze 2.0, 3.0 a 3.5 v rozhraní .NET Framework 4 a novějších verzích, je nutné nastavit proměnnou prostředí COMPLUS_ProfAPI_ProfilerCompatibilitySetting.  
  
## <a name="environment-variable-scope"></a>Rozsah proměnných prostředí  
 Způsob nastavení proměnných prostředí COR_ENABLE_PROFILING a COR_PROFILER určuje jejich rozsah vlivu. Tyto proměnné můžete nastavit jedním z následujících způsobů:  
  
- Pokud nastavíte proměnné v [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) volání, budou platit pouze pro aplikaci, která je spuštěna v té době. (Budou se vztahovat také na jiné aplikace spuštěné tímto použitím, které dědí prostředí.)  
  
- Pokud nastavíte proměnné v okně příkazového řádku, budou se vztahovat na všechny aplikace, které jsou spuštěny z tohoto okna.  
  
- Pokud nastavíte proměnné na úrovni uživatele, budou se vztahovat na všechny aplikace, které začnete s Průzkumníkem souborů. Okno příkazového řádku, které otevřete po nastavení proměnných, bude mít tato nastavení prostředí a stejně tak i všechny aplikace, které spustíte z tohoto okna. Chcete-li nastavit proměnné prostředí na úrovni uživatele, klepněte pravým tlačítkem myši na **položku Tento počítač**, klepněte na příkaz **Vlastnosti**, klepněte na kartu **Upřesnit,** klepněte na **položku Proměnné prostředí**a přidejte proměnné do seznamu Proměnné **uživatele.**  
  
- Pokud nastavíte proměnné na úrovni počítače, budou se vztahovat na všechny aplikace, které jsou spuštěny v tomto počítači. Okno příkazového řádku, které otevřete v tomto počítači, bude mít tato nastavení prostředí a stejně tak všechny aplikace, které spustíte z tohoto okna. To znamená, že každý spravovaný proces v tomto počítači začne s profilerem. Chcete-li nastavit proměnné prostředí na úrovni počítače, klepněte pravým tlačítkem myši na **položku Tento počítač**, klepněte na příkaz **Vlastnosti**, klepněte na kartu **Upřesnit,** klepněte na **položku Proměnné prostředí**, přidejte proměnné do seznamu Systémové **proměnné** a restartujte počítač. Po restartování budou proměnné k dispozici v celém systému.  
  
 Pokud profilujete službu systému Windows, je nutné restartovat počítač po nastavení proměnných prostředí a registraci dll profileru. Další informace o těchto aspektech naleznete v části [Profilování služby systému Windows](#windows_service).  
  
## <a name="additional-considerations"></a>Další důležité informace  
  
- Třída profiler implementuje rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md) a [ICorProfilerCallback2.](icorprofilercallback2-interface.md) V rozhraní .NET Framework verze 2.0 `ICorProfilerCallback2`musí profiler implementovat . Pokud tomu tak `ICorProfilerCallback2` není, nebude načten.  
  
- Pouze jeden profiler může profilovat proces najednou v daném prostředí. Můžete zaregistrovat dva různé profilovací programy v různých prostředích, ale každý musí profilovat samostatné procesy. Profiler musí být implementován jako neprocesová klientská dll serveru COM, která je mapována do stejného adresního prostoru jako proces, který je profilován. To znamená, že profiler běží v procesu. Rozhraní .NET Framework nepodporuje žádný jiný typ serveru COM. Například pokud profiler chce sledovat aplikace ze vzdáleného počítače, musí implementovat agenty kolektoru v každém počítači. Tito agenti budou dávkové výsledky a sdělit je do počítače centrální sběr dat.  
  
- Vzhledem k tomu, že profiler je objekt COM, který je vytvořena instance v procesu, každá profilovaná aplikace bude mít vlastní kopii profileru. Proto jeden profiler instance nemusí zpracovávat data z více aplikací. Budete však muset přidat logiku kódu protokolování profileru, abyste zabránili přepsání souboru protokolu z jiných profilovaných aplikací.  
  
## <a name="initializing-the-profiler"></a>Inicializace profileru  
 Při průchodu obou kontrol proměnných prostředí clr vytvoří instanci profileru podobným způsobem jako funkce COM. `CoCreateInstance` Profiler není načten prostřednictvím přímého volání `CoCreateInstance`. Proto volání `CoInitialize`, který vyžaduje nastavení modelu zřetězení, je zabráněno. CLR pak volá [Metodu ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) v profileru. Podpis této metody je následující.  
  
```cpp  
HRESULT Initialize(IUnknown *pICorProfilerInfoUnk)  
```  
  
 Profiler musí `pICorProfilerInfoUnk` dotaz na ukazatel rozhraní [ICorProfilerInfo](icorprofilerinfo-interface.md) nebo [ICorProfilerInfo2](icorprofilerinfo2-interface.md) a uložit jej tak, aby jej můžete požádat o další informace později během profilování.  
  
## <a name="setting-event-notifications"></a>Nastavení oznámení událostí  
 Profiler pak volá [metodu ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) a určuje, které kategorie oznámení se zajímá. Například pokud profiler má zájem pouze o funkci zadejte a zanechat oznámení a oznámení o uvolnění paměti, určuje následující.  
  
```cpp  
ICorProfilerInfo* pInfo;  
pICorProfilerInfoUnk->QueryInterface(IID_ICorProfilerInfo, (void**)&pInfo);  
pInfo->SetEventMask(COR_PRF_MONITOR_ENTERLEAVE | COR_PRF_MONITOR_GC)  
```  
  
 Nastavením masky oznámení tímto způsobem profiler můžete omezit, která oznámení obdrží. Tento přístup pomáhá uživateli vytvořit jednoduchý nebo speciální profilování. Také snižuje čas procesoru, který by byl promarněn odesíláním oznámení, která by profiler prostě ignoroval.  
  
 Některé události profileru jsou neměnné. To znamená, že jakmile jsou tyto `ICorProfilerCallback::Initialize` události nastaveny v zpětném volání, nelze je vypnout a nové události nelze zapnout. Pokusy o změnu neměnné `ICorProfilerInfo::SetEventMask` události bude mít za následek vrácení neúspěšné HRESULT.  
  
<a name="windows_service"></a>
## <a name="profiling-a-windows-service"></a>Profilování služby systému Windows  
 Profilování služby systému Windows je jako profilování aplikace za běhu běžného jazyka. Obě operace profilování jsou povoleny prostřednictvím proměnných prostředí. Vzhledem k tomu, že služba systému Windows je spuštěna při spuštění operačního systému, proměnné prostředí popsané dříve v tomto tématu musí být již k dispozici a nastavit na požadované hodnoty před spuštěním systému. Kromě toho musí být profilování DLL již registrována v systému.  
  
 Po nastavení COR_ENABLE_PROFILING a COR_PROFILER proměnných prostředí a registraci dll profileru byste měli restartovat cílový počítač, aby služba systému Windows mohla tyto změny rozpoznat.  
  
 Všimněte si, že tyto změny umožní profilování na základě celého systému. Chcete-li zabránit profilování všech spravovaných aplikací, které následně spustí, měli byste po restartování cílového počítače odstranit proměnné systémového prostředí.  
  
 Tato technika také vede k tomu, že se každý proces CLR profiluje. Profiler by měl přidat logiku jeho [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) zpětné volání zjistit, zda aktuální proces je zajímavé. Pokud tomu tak není, profiler může selhat zpětné volání bez provedení inicializace.  
  
## <a name="see-also"></a>Viz také

- [Přehled profilování](profiling-overview.md)
