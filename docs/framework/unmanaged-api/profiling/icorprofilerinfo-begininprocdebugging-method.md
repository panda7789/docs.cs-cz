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
ms.openlocfilehash: c14979fa711145b9f1a134f90d7450b24e6d8a15
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864294"
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a>ICorProfilerInfo::BeginInprocDebugging – metoda
Inicializuje podporu ladění v procesu. Tato metoda je zastaralá ve verzi .NET Framework 2,0.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
## <a name="parameters"></a>Parametry  
 `fThisThreadOnly`  
 pro Nastavte tuto hodnotu na `true` pro inicializaci podpory ladění pouze pro aktuální vlákno; nastavte ji na `false` pro inicializaci podpory ladění pro všechna vlákna.  
  
 `pdwProfilerContext`  
 mimo Ukazatel na vrácenou hodnotu, která identifikuje relaci ladění.  
  
## <a name="remarks"></a>Poznámky  
 Služba ladění CLR podporuje omezené vnitroprocesové ladění v .NET Framework verzích 1,0 a 1,1. Ladění v rámci procesu povolilo profiler pro použití kontrolních částí rozhraní API pro ladění. Z důvodu zpětné vazby od zákazníků jsme ale vnitroprocesové ladění odebrali z .NET Framework ve verzi 2,0 a nahradili sadu funkcí, která je v souladu s rozhraním API profilování.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** 1,0  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](icorprofilerinfo-interface.md)
