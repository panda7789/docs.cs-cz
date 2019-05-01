---
title: ICorProfilerInfo::BeginInprocDebugging – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.BeginInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::BeginInprocDebugging
helpviewer_keywords:
- BeginInprocDebugging method [.NET Framework profiling]
- ICorProfilerInfo::BeginInprocDebugging method [.NET Framework profiling]
ms.assetid: c5c82c69-99f8-4447-aee0-42cca0a5eb5c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f12442eb5596ff3dca49cf24e27040f3e92d3a7c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991923"
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a>ICorProfilerInfo::BeginInprocDebugging – metoda
Inicializuje podporu ladění v procesu. Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
## <a name="parameters"></a>Parametry  
 `fThisThreadOnly`  
 [in] Nastavte tuto hodnotu na `true` inicializovat podporu ladění pro pouze aktuální vlákno, nastavte ho na `false` inicializovat podporu ladění pro všemi vlákny.  
  
 `pdwProfilerContext`  
 [out] Ukazatel na vrácené hodnoty, který identifikuje relace ladění.  
  
## <a name="remarks"></a>Poznámky  
 Ladění služby CLR nepodporuje omezené vnitroprocesové ladění v rozhraní .NET Framework verze 1.0 a 1.1. Vnitroprocesové ladění povolit profiler použití kontroly části rozhraní API pro ladění. Ale z důvodu zpětné vazby od zákazníků, vnitroprocesové ladění má byla odebrána z rozhraní .NET Framework verze 2.0 a jsme nahradili sadou funkcí, které jsou více tato rozhraní API profilování.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** 1.0  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
