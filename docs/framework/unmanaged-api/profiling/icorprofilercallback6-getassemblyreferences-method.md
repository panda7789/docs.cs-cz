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
ms.openlocfilehash: 0717ef5fdb6c0447ceeb801f239be08f8cca5988
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865048"
---
# <a name="icorprofilercallback6getassemblyreferences-method"></a>ICorProfilerCallback6::GetAssemblyReferences – metoda
[Podporované v .NET Framework 4.5.2 a novějších verzích]  
  
 Upozorní profileru, že sestavení je ve fázi brzkého nasazování, pokud modul CLR provádí procházení zavřením odkazu na sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetAssemblyReferences(        [in, string] const WCHAR* wszAssemblyPath,  
        [in] ICorProfilerAssemblyReferenceProvider* pAsmRefProvider  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszAssemblyPath`  
 pro Cesta a název sestavení, jehož metadata budou změněna.  
  
 `pAsmRefProvider`  
 pro Ukazatel na adresu rozhraní [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) , které určuje odkazy na sestavení, které se mají přidat.  
  
## <a name="return-value"></a>Návratová hodnota  
 Návratové hodnoty z tohoto zpětného volání jsou ignorovány.  
  
## <a name="remarks"></a>Poznámky  
 Toto zpětné volání je řízeno nastavením příznaku masky události [COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](cor-prf-high-monitor-enumeration.md) při volání metody [Icorprofilercallback5 –:: SetEventMask2 –](icorprofilerinfo5-seteventmask2-method.md) . Pokud profiler registruje pro metodu zpětného volání [ICorProfilerCallback6:: GetAssemblyReferences –](icorprofilercallback6-getassemblyreferences-method.md) , modul runtime předá cestu a název sestavení, které mají být načteny, spolu s ukazatelem na objekt rozhraní [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) k této metodě. Profiler pak může zavolat metodu [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference –](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) s objektem `COR_PRF_ASSEMBLY_REFERENCE_INFO` pro každé cílové sestavení, které plánuje odkazovat ze sestavení zadaného ve `GetAssemblyReferences` zpětného volání.  
  
 Použití zpětného volání `GetAssemblyReferences` pouze v případě, že Profiler musí upravit metadata sestavení pro přidání odkazů na sestavení. (Ale Všimněte si, že skutečná úprava metadat sestavení se provádí v metodě zpětného volání [ICorProfilerCallback:: ModuleLoadFinished –](icorprofilercallback-moduleloadfinished-method.md).) Profiler by měl implementovat metodu `GetAssemblyReferences` zpětného volání pro informování společného jazykového modulu runtime (CLR), který se přidá k odkazům na sestavení při načtení modulu.  To pomáhá zajistit, že rozhodnutí o sdílení sestavení, která provedla CLR v rámci této úvodní fáze, zůstávají platná, i když Profiler plánuje změnit odkazy na sestavení metadat později.  To se může vyhnout některým instancím, ve kterých změny metadat profileru způsobují chybu `SECURITY_E_INCOMPATIBLE_SHARE`.  
  
 Profiler používá objekt [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) poskytnutý touto metodou pro přidání odkazů na sestavení do prohlížeč ukončení odkazu sestavení CLR.  Objekt [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) by měl být použit pouze v rámci tohoto zpětného volání. Volání metody [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference –](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) z tohoto zpětného volání nemají za následek změněná metadata, ale pouze v rámci upraveného procházení odkazu na sestavení. Profiler bude stále muset použít objekt [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) k explicitnímu přidání odkazů na sestavení z zpětného volání [ICorProfilerCallback:: ModuleLoadFinished –](icorprofilercallback-moduleloadfinished-method.md) pro referenční sestavení, i když implementuje zpětné volání `GetAssemblyReferences`.  
  
 Profiler by měl být přizpůsobený tak, aby přijímal duplicitní volání tohoto zpětného volání pro stejné sestavení a měl by odpovědět identicky pro každé takové duplicitní volání (provedením stejné sady volání [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference –](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) ).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback6 – rozhraní](icorprofilercallback6-interface.md)
- [ModuleLoadFinished – metoda](icorprofilercallback-moduleloadfinished-method.md)
- [COR_PRF_ASSEMBLY_REFERENCE_INFO – struktura](cor-prf-assembly-reference-info-structure.md)
- [ICorProfilerAssemblyReferenceProvider – rozhraní](icorprofilerassemblyreferenceprovider-interface.md)
