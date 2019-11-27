---
title: ICorProfilerFunctionControl::SetILInstrumentedCodeMap – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetIILInstrumentedCodeMap method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: ecf56646-7e5f-46c4-8340-f3a04e88920f
topic_type:
- apiref
ms.openlocfilehash: 11ce2fdccbf24fd688376cc3256f6db79a7cc352
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447855"
---
# <a name="icorprofilerfunctioncontrolsetilinstrumentedcodemap-method"></a>ICorProfilerFunctionControl::SetILInstrumentedCodeMap – metoda
Nastaví mapu kódu pro určenou funkci pomocí zadaných položek mapování Common Intermediate Language (CIL).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetILInstrumentedCodeMap(  
    [in]   ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cILMapEntries`  
 pro Počet položek v mapě.  
  
 `rgILMapEntries`  
 pro Pole přidělené volajícím položkám COR_IL_MAP. Výklad těchto položek je stejný jako u metody [ICorProfilerInfo:: SetILInstrumentedCodeMap –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) .  
  
## <a name="remarks"></a>Poznámky  
 Nastavení mapování voláním této metody umožňuje ladicímu programu načíst mapování voláním [ICorDebugILCode2:: GetInstrumentedILMap –](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md). Umožňuje také, aby ladicí program používal mapování interně při výpočtu posunu IL pro trasování zásobníku a pro dobu života proměnných.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
