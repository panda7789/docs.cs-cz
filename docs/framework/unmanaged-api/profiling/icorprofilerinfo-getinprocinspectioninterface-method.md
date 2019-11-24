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
Gets an object that can be queried for an "ICorDebugProcess" interface. This method is obsolete in the .NET Framework version 2.0.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppicd`  
 [out](/cpp/atl/iunknown) object that can be queried for an `ICorDebugProcess` interface.  
  
## <a name="remarks"></a>Poznámky  
 The common language runtime (CLR) debugging API supported limited in-process debugging in the .NET Framework version 1.0. In-process debugging enabled a profiler to use the inspection portions of the debugging API. As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.  
  
## <a name="requirements"></a>Požadavky  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorProf.idl, CorProf.h  
  
 **Library:** CorGuids.lib  
  
 **.NET Framework Version:** 1.0  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
