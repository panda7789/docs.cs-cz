---
title: ICorProfilerCallback8::DynamicMethodJITCompilationFinished – metoda
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49b5ead8b5428d855b7dab81dced1de6325fd07b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454994"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a>ICorProfilerCallback8::DynamicMethodJITCompilationFinished – metoda
[Podporované v rozhraní .NET Framework 4.7 a novějších verzích]  
  
Upozorní profileru vždy, když JIT – kompilace dynamické metody byla dokončena.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        hrStatus,   
     [in]  BOOL        fIsSafeToBlock   
);  
```  
  
#### <a name="parameters"></a>Parametry  
[v] `functionId`  
Identifikátor funkce v paměti, pro které JIT kompilace spuštění.   

[v] `hrStatus`   
Hodnota, která určuje, zda JIT – kompilace byla úspěšná.

[v] `fIsSafeToBlock`   
`true` k označení, že blokování může způsobit modulu runtime počkejte volající vlákno k návratu z této zpětného volání; `false` k označení, že blokování neovlivní operaci modulu runtime.  

## <a name="remarks"></a>Poznámky  

Tato zpětné volání se aktivuje vždy, když JIT – kompilace dynamické metody dokončení. To zahrnuje různé IL zástupných procedur a LCG metody. Jeho cílem je poskytnout dostatek informací k identifikaci kompilované metoda uživatelům profileru zapisovače.

> [!NOTE]
> `functionId` hodnoty nelze použít přeložit na jejich tokenů metadat, protože dynamické metody žádná metadata.

## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Viz také  
 [DynamicMethodJITCompilationStarted – metoda](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)  
 [ICorProfilerCallback8 rozhraní](icorprofilercallback8-interface.md)
