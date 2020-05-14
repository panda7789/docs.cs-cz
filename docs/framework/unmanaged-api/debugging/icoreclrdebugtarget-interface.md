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
ms.openlocfilehash: c44a12ef377d29e0b33b8be86aa1d8f0aa9d26bd
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397159"
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
|[ICoreClrDebugTarget::EnumProcesses – metoda](icoreclrdebugtarget-enumprocesses-method.md)|Vytvoří výčet procesů, které jsou spuštěny na vzdáleném počítači.|  
|[ICoreClrDebugTarget::EnumRuntimes – metoda](icoreclrdebugtarget-enumruntimes-method.md)|Vytvoří výčet modulu CLR (Common Language Runtime) (CLRs) v zadaném procesu na vzdáleném počítači.|  
|[ICoreClrDebugTarget::FreeMemory – metoda](icoreclrdebugtarget-freememory-method.md)|Uvolní paměť, která je přidělena metodami výčtu v této třídě.|  
  
## <a name="remarks"></a>Poznámky  
 V současné době je tato funkce podporována pouze pro ladění cíle aplikace založeného na programu Silverlight, který je spuštěn ve vzdáleném počítači se systémem Macintosh.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Knihovna:** mscordbi_macx86. dll  
  
 **Verze .NET Framework:** 3,5 SP1  
  
## <a name="see-also"></a>Viz také

- [ICorDebugRemoteTarget – rozhraní](icordebugremotetarget-interface.md)
- [ICorDebug – rozhraní](icordebug-interface.md)

- [Debugging – rozhraní](debugging-interfaces.md)
