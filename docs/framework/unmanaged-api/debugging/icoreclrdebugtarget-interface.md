---
title: "ICoreClrDebugTarget – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICoreClrDebugTarget
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: ICoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget interface
- Silverlight, remote debugging
ms.assetid: 7cfaee76-e284-4a66-a431-8e33f0f60038
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 62d43121efbc039b8fad0b78bed7ec4a655efabb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icoreclrdebugtarget-interface"></a>ICoreClrDebugTarget – rozhraní
Poskytuje metody, které řídí počty odkazů, výčet procesy a uvolnit paměť, přidružené ladicí program, který je připojen k vzdálený cíl Macintosh Silverlight.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|[ICoreClrDebugTarget::EnumProcesses – metoda](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md)|Vytvoří výčet procesů, které běží na vzdáleném počítači.|  
|[ICoreClrDebugTarget::EnumRuntimes – metoda](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md)|Vytvoří výčet běžné moduly runtime jazyka (CLRs) v zadané procesu ve vzdáleném počítači.|  
|[ICoreClrDebugTarget::FreeMemory – metoda](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md)|Uvolní paměť, která je přidělena výčtu metody v této třídě.|  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce je v současné době podporována pouze pro ladění aplikace založená na technologii Silverlight cíl, který běží na vzdáleném počítači Macintosh.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Knihovna:** mscordbi_macx86.dll  
  
 **Verze rozhraní .NET framework:** 3.5 SP1  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugRemoteTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
