---
title: ICorProfilerInfo::GetInprocInspectionInterface – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionInterface
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionInterface
helpviewer_keywords:
- GetInprocInspectionInterface method [.NET Framework profiling]
- ICorProfilerInfo::GetInprocInspectionInterface method [.NET Framework profiling]
ms.assetid: 22a92d1d-8849-4af6-8304-ecc53dd1d289
topic_type:
- apiref
ms.openlocfilehash: d3fcd859fb11f6a0c660751f16fa175e19e9d03b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439004"
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a>ICorProfilerInfo::GetInprocInspectionInterface – metoda
Získá objekt, na který lze zadat dotaz na rozhraní "ICorDebugProcess". Tato metoda je zastaralá ve verzi .NET Framework 2,0.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppicd`  
 objekt [out](/cpp/atl/iunknown) , na který lze zadat dotaz na rozhraní `ICorDebugProcess`.  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní API pro ladění modulu CLR (Common Language Runtime) podporuje omezené ladění v procesu .NET Framework verze 1,0. Ladění v rámci procesu povolilo profiler pro použití kontrolních částí rozhraní API pro ladění. V důsledku zpětné vazby od zákazníků se vnitroprocesové ladění odebralo z .NET Framework ve verzi 2,0 a nahrazuje se sadou funkcí, které jsou v souladu s rozhraním API profilování.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** 1,0  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
