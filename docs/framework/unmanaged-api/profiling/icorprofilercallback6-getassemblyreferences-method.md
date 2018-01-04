---
title: "ICorProfilerCallback6::GetAssemblyReferences – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorProfilerCallback6.GetAssemblyReferences
api_location:
- mscorwks.dll
- corprof.idl
api_type: COM
ms.assetid: 8b391afb-d79f-41bd-94ce-43ce62c6b5fc
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bc2e80d6d8207a869d43beb46cc9448bdd86dfec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback6getassemblyreferences-method"></a>ICorProfilerCallback6::GetAssemblyReferences – metoda
[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]  
  
 Upozorní profileru, že sestavení v velmi brzy načítá fáze, když modul common language runtime provede procházení uzavření odkaz na sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetAssemblyReferences(        [in, string] const WCHAR* wszAssemblyPath,  
        [in] ICorProfilerAssemblyReferenceProvider* pAsmRefProvider  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `wszAssemblyPath`  
 [v] Cesta a název sestavení, jejichž metadata budou upraveny.  
  
 `pAsmRefProvider`  
 [v] Ukazatel na adresu [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) rozhraní, které určuje sestavení odkazuje na Přidat.  
  
## <a name="return-value"></a>Návratová hodnota  
 Návratové hodnoty z této zpětné volání se ignorují.  
  
## <a name="remarks"></a>Poznámky  
 Tato zpětné volání je řízena nastavením [COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) příznak maska událostí při volání metody [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metoda. Pokud profileru zaregistruje [icorprofilercallback6::getassemblyreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) metoda zpětného volání, modul runtime předá cestu a název sestavení, která má být načten, spolu s odkazy [ ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) rozhraní objektu do dané metody. Potom můžete volat profileru [icorprofilerassemblyreferenceprovider::addassemblyreference –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) metoda s `COR_PRF_ASSEMBLY_REFERENCE_INFO` objekt pro každý cíl sestavení se plánuje odkazovat z sestavení zadané v `GetAssemblyReferences` zpětné volání.  
  
 Použití `GetAssemblyReferences` zpětného volání pouze v případě, že má profileru ke změně metadat sestavení přidat odkazy na sestavení. (Všimněte si, že skutečné úpravy sestavení metadat se provádí v, ale [icorprofilercallback::moduleloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)metoda zpětného volání.) Profileru by měla implementovat `GetAssemblyReferences` metoda zpětného volání k informování common language runtime (CLR), odkazy na sestavení bude přidáno, jakmile se načetl modul.  To pomáhá zajistit, že sestavení sdílení rozhodnutí CLR během této fáze časná dál platné i když profileru plánuje později upravit odkazy na metadata sestavení.  To se můžete vyhnout některých případech, ve které profileru způsobit změny metadata `SECURITY_E_INCOMPATIBLE_SHARE` chyby.  
  
 Používá profileru [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) objekt Poskytnutý tuto metodu za účelem přidání odkazů na sestavení pro uzavření walkera CLR sestavení odkaz.  [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) objekt by měl použít pouze v rámci této zpětného volání. Volání [icorprofilerassemblyreferenceprovider::addassemblyreference –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) metoda z této zpětného volání nezpůsobují v upravené metadata, ale jenom v procházení uzavření odkaz upravené sestavení. Profileru bude muset nadále používat [imetadataassemblyemit –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) objekt, který chcete explicitně přidat odkazy na sestavení z uvnitř [icorprofilercallback::moduleloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) zpětné volání pro odkazujícího sestavení, i když se implementuje `GetAssemblyReferences` zpětného volání.  
  
 Profileru musí být připravené pro příjem duplicitní volání této zpětného volání pro stejného sestavení a má odpovědět stejně jako pro každé takové duplicitní volání (tím, že stejnou sadu [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) volání).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerCallback6 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)  
 [ModuleLoadFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)  
 [COR_PRF_ASSEMBLY_REFERENCE_INFO – struktura](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)  
 [ICorProfilerAssemblyReferenceProvider – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)
