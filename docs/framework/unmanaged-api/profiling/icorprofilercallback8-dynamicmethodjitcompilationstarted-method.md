---
title: ICorProfilerCallback8::DynamicMethodJITCompilationStarted – metoda
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad74eeb4deeae73be40b3a0bc0f6a18ec2299780
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a>ICorProfilerCallback8::DynamicMethodJITCompilationStarted – metoda
[Podporované v rozhraní .NET Framework 4.7 a novějších verzích]  
  
Upozorní profileru vždy, když bylo zahájeno JIT – kompilace dynamické metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        fIsSafeToBlock,   
     [in]  LPCBYTE     pILHeader,   
     [in]  LONG        cbILHeader   
);  
```  
  
#### <a name="parameters"></a>Parametry  
[v] `functionId`  
Identifikátor funkce v paměti, pro které JIT kompilace spuštění.   

[v] `fIsSafeToBlock`   
`true` k označení, že blokování může způsobit modulu runtime počkejte volající vlákno k návratu z této zpětného volání; `false` k označení, že blokování neovlivní operaci modulu runtime.  

[v] `pILHeader`    
Ukazatel do prvního bajtu metoda IL hlavičky.   

[v] `cbILHeader`    
Počet bajtů v hlavičce IL. 

## <a name="remarks"></a>Poznámky  

Vždy, když je dynamická metoda kompilována, aktivuje se tato zpětného volání. To zahrnuje různé IL zástupných procedur a LCG metody. Jeho cílem je poskytnout dostatek informací k identifikaci kompilované metoda uživatelům profileru zapisovače.

> [!NOTE]
> `functionId` hodnoty nelze použít přeložit na jejich tokenů metadat, protože dynamické metody žádná metadata.

`pILHeader` Ukazatel je platná pouze během zpětného volání.

## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Viz také  
 [DynamicMethodJITCompilationFinished – metoda](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)  
 [ICorProfilerCallback8 rozhraní](icorprofilercallback8-interface.md)
