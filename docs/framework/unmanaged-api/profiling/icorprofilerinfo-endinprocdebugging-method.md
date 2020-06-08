---
title: ICorProfilerInfo::EndInprocDebugging – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.EndInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::EndInprocDebugging
helpviewer_keywords:
- ICorProfilerInfo::EndInprocDebugging method [.NET Framework profiling]
- EndInprocDebugging method [.NET Framework profiling]
ms.assetid: 35bc1188-9767-4141-8038-60ea015b99ac
topic_type:
- apiref
ms.openlocfilehash: afbb007b6293e6e9cff92281a6f5e93b1e7924ec
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502974"
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a>ICorProfilerInfo::EndInprocDebugging – metoda
Ukončí relaci ladění v procesu. Tato metoda je zastaralá ve verzi .NET Framework 2,0.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwProfilerContext`  
 pro Hodnota, která identifikuje relaci ladění. Tato hodnota musí být stejná jako ta, která byla přijata v metodě [ICorProfilerInfo:: BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) .  
  
## <a name="remarks"></a>Poznámky  
 Je nutné volat [ICorProfilerInfo:: BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) a `EndInprocDebugging` v rámci stejné metody zpětného volání.  
  
 Služba ladění CLR podporuje omezené vnitroprocesové ladění v .NET Framework verzích 1,0 a 1,1. Ladění v rámci procesu povolilo profiler pro použití kontrolních částí rozhraní API pro ladění. Z důvodu zpětné vazby od zákazníků jsme ale vnitroprocesové ladění odebrali z .NET Framework ve verzi 2,0 a nahradili sadu funkcí, která je v souladu s rozhraním API profilování.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** 1,0  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](icorprofilerinfo-interface.md)
