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
ms.openlocfilehash: 86720cb1739e3f193cd1d5081577d69bca1cf0f9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427048"
---
# <a name="setting-up-a-profiling-environment"></a>Nastavení prostředí profilace
> [!NOTE]
> V .NET Framework 4 byly zásadní změny profilace.  
  
 Při spuštění spravovaného procesu (aplikace nebo služby) načte modul CLR (Common Language Runtime). Při inicializaci modulu CLR vyhodnotí následující dvě proměnné prostředí k rozhodnutí, zda se má proces připojit k profileru:  
  
- COR_ENABLE_PROFILING: CLR se připojí k profileru jenom v případě, že tato proměnná prostředí existuje a je nastavená na 1.  
  
- COR_PROFILER: Pokud COR_ENABLE_PROFILING projde, CLR se připojí k profileru, který má tento identifikátor CLSID nebo ProgID, který musí být uložen dříve v registru. Proměnná prostředí COR_PROFILER je definována jako řetězec, jak je znázorněno v následujících dvou příkladech.  
  
    ```cpp  
    set COR_PROFILER={32E2F4DA-1BEA-47ea-88F9-C5DAF691C94A}  
    set COR_PROFILER="MyProfiler"  
    ```  
  
 Chcete-li profilovat aplikaci CLR, je nutné před spuštěním aplikace nastavit proměnné prostředí COR_ENABLE_PROFILING a COR_PROFILER. Musíte se také ujistit, že je knihovna DLL profileru zaregistrovaná.  
  
> [!NOTE]
> Od .NET Framework 4 se profilery nemusí registrovat.  
  
> [!NOTE]
> Chcete-li použít .NET Framework verze 2,0, 3,0 a 3,5 profilery v .NET Framework 4 a novějších verzích, je nutné nastavit proměnnou prostředí COMPLUS_ProfAPI_ProfilerCompatibilitySetting.  
  
## <a name="environment-variable-scope"></a>Rozsah proměnné prostředí  
 Způsob nastavení COR_ENABLE_PROFILING a proměnné prostředí COR_PROFILER určují jejich rozsah vlivu. Tyto proměnné můžete nastavit jedním z následujících způsobů:  
  
- Pokud jste nastavili proměnné v volání [ICorDebug:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) , budou se vztahovat jenom na aplikaci, kterou používáte v daném okamžiku. (Budou platit také pro ostatní aplikace spuštěné aplikací, které dědí prostředí.)  
  
- Pokud jste nastavili proměnné v okně příkazového řádku, budou platit pro všechny aplikace, které jsou spuštěny z tohoto okna.  
  
- Pokud jste nastavili proměnné na úrovni uživatele, použijí se na všechny aplikace, které spustíte v Průzkumníkovi souborů. Okno příkazového řádku, které otevřete po nastavení proměnných, bude mít tato nastavení prostředí, a takže bude mít všechny aplikace spouštěné z tohoto okna. Chcete-li nastavit proměnné prostředí na úrovni uživatele, klikněte pravým tlačítkem myši na položku **Tento počítač**, klikněte na příkaz **vlastnosti**, klikněte na kartu **Upřesnit** , klikněte na položku **proměnné prostředí**a přidejte proměnné do seznamu **uživatelské proměnné** .  
  
- Pokud jste nastavili proměnné na úrovni počítače, budou platit pro všechny aplikace, které jsou na tomto počítači spuštěné. Okno příkazového řádku, které otevřete na tomto počítači, bude mít tato nastavení prostředí, a takže bude mít všechny aplikace, které z tohoto okna spustíte. To znamená, že všechny spravované procesy v tomto počítači budou začínat vaším profilerem. Chcete-li nastavit proměnné prostředí na úrovni počítače, klikněte pravým tlačítkem myši na položku **Tento počítač**, klikněte na příkaz **vlastnosti**, klikněte na kartu **Upřesnit** , klikněte na položku **proměnné prostředí**, přidejte proměnné do seznamu **systémové proměnné** a pak restartujte počítač. Po restartování budou proměnné dostupné v rámci systému.  
  
 Pokud vytváříte profilaci služby systému Windows, musíte restartovat počítač po nastavení proměnných prostředí a registraci knihovny DLL profileru. Další informace o těchto doporučeních najdete v části [profilování služby systému Windows](#windows_service).  
  
## <a name="additional-considerations"></a>Další požadavky  
  
- Třída profileru implementuje rozhraní [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) a [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) . V .NET Framework verze 2,0 musí Profiler implementovat `ICorProfilerCallback2`. Pokud tomu tak není, `ICorProfilerCallback2` nebudou načteny.  
  
- Pouze jeden profiler může profilovat proces v jednom okamžiku v daném prostředí. V různých prostředích můžete registrovat dva různé profilery, ale každý musí profilovat samostatné procesy. Profiler se musí implementovat jako vnitroprocesové knihovna DLL COM serveru, která je namapovaná do stejného adresního prostoru jako proces, který se profiluje. To znamená, že Profiler běží vnitroprocesově. .NET Framework nepodporuje žádný jiný typ serveru COM. Pokud profiler chce například monitorovat aplikace ze vzdáleného počítače, musí implementovat agenty kolektoru na každém počítači. Tito agenti budou mít za následek dávkování výsledků a oznámí je centrálnímu počítači pro shromažďování dat.  
  
- Vzhledem k tomu, že Profiler je objekt modelu COM, který je vytvořen v procesu, každá profilovaná aplikace bude mít svou vlastní kopii profileru. Proto jedna instance profileru nemusí zpracovávat data z více aplikací. Budete však muset přidat logiku k kódu protokolování profileru, abyste zabránili přepsání souboru protokolu z jiných profilových aplikací.  
  
## <a name="initializing-the-profiler"></a>Inicializuje se Profiler.  
 Když obě kontroly proměnné prostředí přejdou, vytvoří CLR instanci profileru podobným způsobem jako funkce `CoCreateInstance` COM. Profiler není načten prostřednictvím přímého volání `CoCreateInstance`. Proto volání `CoInitialize`, které vyžaduje nastavení modelu vláken, se vyhne. Modul CLR pak zavolá metodu [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) v profileru. Signatura této metody je následující.  
  
```cpp  
HRESULT Initialize(IUnknown *pICorProfilerInfoUnk)  
```  
  
 Profiler musí zadat dotaz na `pICorProfilerInfoUnk` pro ukazatel rozhraní [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) nebo [ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md) a uložit ho tak, aby si mohl vyžádat další informace později během profilace.  
  
## <a name="setting-event-notifications"></a>Nastavení oznámení událostí  
 Profiler pak zavolá metodu [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) k určení kategorií oznámení, která vás zajímá. Například pokud má Profiler zajímat pouze oznámení o vstupu a opuštění funkce a oznámení o uvolňování paměti, určuje následující.  
  
```cpp  
ICorProfilerInfo* pInfo;  
pICorProfilerInfoUnk->QueryInterface(IID_ICorProfilerInfo, (void**)&pInfo);  
pInfo->SetEventMask(COR_PRF_MONITOR_ENTERLEAVE | COR_PRF_MONITOR_GC)  
```  
  
 Nastavením masky oznámení tímto způsobem může Profiler omezit, která oznámení obdrží. Tento přístup pomáhá uživateli vytvořit jednoduchý Profiler nebo profil pro speciální účely. Zároveň se tím zkrátí čas procesoru, který by využíval zasílání oznámení o tom, že Profiler bude jenom ignorovat.  
  
 Některé události profileru jsou neměnné. To znamená, že jakmile budou tyto události nastaveny ve `ICorProfilerCallback::Initialize` zpětného volání, nelze je vypnout a nové události nelze zapnout. Pokusy o změnu neměnných událostí budou mít za následek `ICorProfilerInfo::SetEventMask` vrácení neúspěšného HRESULT.  
  
<a name="windows_service"></a>   
## <a name="profiling-a-windows-service"></a>Profilace služby systému Windows  
 Profilování služby systému Windows je jako profilace aplikace modulu CLR (Common Language Runtime). Operace profilování jsou povolené prostřednictvím proměnných prostředí. Vzhledem k tomu, že je spuštěna služba systému Windows při spuštění operačního systému, proměnné prostředí popsané dříve v tomto tématu již musí být přítomny a nastaveny na požadované hodnoty před spuštěním systému. Kromě toho musí být profilace DLL již v systému registrována.  
  
 Po nastavení proměnných prostředí COR_ENABLE_PROFILING a COR_PROFILER a registraci knihovny DLL profileru byste měli cílový počítač restartovat, aby služba systému Windows mohla tyto změny detekovat.  
  
 Všimněte si, že tyto změny umožní profilaci na úrovni systému. Chcete-li zabránit každé spravované aplikaci, která je následně spouštěna profilování, měli byste po restartování cílového počítače odstranit proměnné prostředí systému.  
  
 Tato technika také vede ke každému procesu CLR s profilací. Profiler by měl přidat logiku do svého [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) zpětného volání pro zjištění, zda je aktuální proces důležité. V opačném případě může Profiler selhání zpětného volání bez provedení inicializace.  
  
## <a name="see-also"></a>Viz také:

- [Přehled profilace](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)
