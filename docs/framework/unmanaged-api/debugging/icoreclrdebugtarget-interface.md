---
title: ICoreClrDebugTarget – rozhraní
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget interface
- Silverlight, remote debugging
ms.assetid: 7cfaee76-e284-4a66-a431-8e33f0f60038
topic_type:
- apiref
ms.openlocfilehash: 83afe121b6bf0de3c5542695e38b6605db7a8b6d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121820"
---
# <a name="icoreclrdebugtarget-interface"></a>ICoreClrDebugTarget – rozhraní
Poskytuje metody, které řídí počty odkazů, vytváří výčet procesů a uvolňuje paměť přidruženou k ladicímu programu, který je připojen ke vzdálenému počítači se službou Silverlight.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
class ICoreClrDebugTarget {  
      HRESULT EnumProcesses (  
          [out] DWORD*                    pcProcs,  
          [out] CoreClrDebugProcInfo**    ppProcs  
      );  
  
      HRESULT EnumRuntimes (  
      [in]  DWORD                      dwInternalProcessID,  
      [out] DWORD*                     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**  ppRuntimes  
      );  
  
      void FreeMemory (  
      [in] void*      pMemory  
    );  
};  
```  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ICoreClrDebugTarget::EnumProcesses – metoda](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md)|Vytvoří výčet procesů, které jsou spuštěny na vzdáleném počítači.|  
|[ICoreClrDebugTarget::EnumRuntimes – metoda](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md)|Vytvoří výčet modulu CLR (Common Language Runtime) (CLRs) v zadaném procesu na vzdáleném počítači.|  
|[ICoreClrDebugTarget::FreeMemory – metoda](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md)|Uvolní paměť, která je přidělena metodami výčtu v této třídě.|  
  
## <a name="remarks"></a>Poznámky  
 V současné době je tato funkce podporována pouze pro ladění cíle aplikace založeného na programu Silverlight, který je spuštěn ve vzdáleném počítači se systémem Macintosh.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Knihovna:** mscordbi_macx86. dll  
  
 **Verze .NET Framework:** 3,5 SP1  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugRemoteTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
