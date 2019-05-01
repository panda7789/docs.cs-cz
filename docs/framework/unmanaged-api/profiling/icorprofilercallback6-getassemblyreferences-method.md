---
title: ICorProfilerCallback6::GetAssemblyReferences – metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerCallback6.GetAssemblyReferences
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: 8b391afb-d79f-41bd-94ce-43ce62c6b5fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c5296fbab71c67572718a58fedb9f89b064f816
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62041493"
---
# <a name="icorprofilercallback6getassemblyreferences-method"></a>ICorProfilerCallback6::GetAssemblyReferences – metoda
[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]  
  
 Oznámí profileru, že sestavení ve velmi brzy načítá fáze, když modul CLR provede procházení uzavření odkaz sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetAssemblyReferences(        [in, string] const WCHAR* wszAssemblyPath,  
        [in] ICorProfilerAssemblyReferenceProvider* pAsmRefProvider  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszAssemblyPath`  
 [in] Cesta a název sestavení, jejichž metadata budou upraveny.  
  
 `pAsmRefProvider`  
 [in] Ukazatel na adresu [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) rozhraní, které určuje sestavení odkazuje přidat.  
  
## <a name="return-value"></a>Návratová hodnota  
 Návratové hodnoty v tomto zpětném volání jsou ignorovány.  
  
## <a name="remarks"></a>Poznámky  
 Toto zpětné volání je řízena nastavením [COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) příznak masky události při volání [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metody. Pokud profiler zaregistruje [icorprofilercallback6::getassemblyreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) metoda zpětného volání, modul runtime předá cestu a název sestavení, který se má načíst, spolu s ukazatelem na [ ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) objektu rozhraní k této metodě. Profiler pak volat [icorprofilerassemblyreferenceprovider::addassemblyreference –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) metody `COR_PRF_ASSEMBLY_REFERENCE_INFO` objekt pro každý cíl sestavení má odkazovat ze sestavení zadaná v `GetAssemblyReferences` zpětné volání.  
  
 Použití `GetAssemblyReferences` zpětného volání pouze v případě, že profiler má k úpravě metadat sestavení přidat odkazy na sestavení. (Všimněte si, že skutečné změna sestavení metadata se provádí na, ale [icorprofilercallback::moduleloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)metoda zpětného volání.) Profiler by měly implementovat `GetAssemblyReferences` metoda zpětného volání k informování common language runtime (CLR), se přidají odkazy na sestavení při načtení modulu.  To pomáhá zajistit, že sestavení sdílení rozhodnutí modulem CLR během této rané nadále platné, i když profiler má v plánu později změnit odkazy v metadatech sestavení.  To se můžete vyhnout nějaké instance, v které profileru způsobit změny metadat `SECURITY_E_INCOMPATIBLE_SHARE` chyby.  
  
 Profiler používá [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) objekt Poskytnutý tuto metodu za účelem přidání odkazů na sestavení pro walker uzavření odkaz na sestavení CLR.  [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) objektu by měla sloužit pouze z v rámci tohoto zpětného volání. Volání [icorprofilerassemblyreferenceprovider::addassemblyreference –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) metodu z tohoto zpětného volání není způsobit změny metadat, ale pouze v procházení uzavření upravené sestavení odkazu. Profiler bude muset nadále používat [imetadataassemblyemit –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) objekt explicitně přidat odkazy na sestavení v rámci [icorprofilercallback::moduleloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) zpětného volání pro odkazování sestavení, i v případě, že implementuje `GetAssemblyReferences` zpětného volání.  
  
 Profiler by měl být připraven pro příjem duplicitní volání tohoto zpětného volání pro stejného sestavení a by měl reagovat stejně jako u každé duplicitní volání (tím, že stejná sada [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) volání).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback6 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)
- [ModuleLoadFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
- [COR_PRF_ASSEMBLY_REFERENCE_INFO – struktura](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)
- [ICorProfilerAssemblyReferenceProvider – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)
