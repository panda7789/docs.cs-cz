---
title: "ICorDebugRemoteTarget – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRemoteTarget
api_location: CorDebug.dll
api_type: COM
f1_keywords: ICorDebugRemoteTarget
helpviewer_keywords: ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: bd9936a6-cc24-4869-8761-0988664464e6
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fcfdab2857745dee7c40823ad25592de5dc833ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugremotetarget-interface"></a>ICorDebugRemoteTarget – rozhraní
Poskytuje metody, které vývojářům umožňuje ladit aplikace založená na technologii Silverlight v běžné prostředí runtime (CLR) jazyk.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
interface ICorDebugRemoteTarget  : IUnknown  
{  
    HRESULT GetHostName (  
        [in]  ULONG32                    cchHostName,  
        [out] ULONG32*                   pcchHostName,  
        [out, size_is(cchHostName),  
              length_is(*pcchHostName)]  
                  WCHAR szHostName[]  
        );  
};  
```  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ICorDebugRemoteTarget::GetHostName – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-gethostname-method.md)|Vrátí název hostitele nebo IP adresu vzdáleného počítače.|  
  
## <a name="remarks"></a>Poznámky  
 Ladění ve smíšeném režimu (to znamená, spravovaná a nativní kód) není podporována v systému Windows 95, Windows 98 nebo Windows ME nebo na jiný x86 platformy (například IA-64 a AMD64).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl  
  
 **Knihovna:** : CorGuids.lib  
  
 **Verze rozhraní .NET framework:** 3.5 SP1  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugRemote – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
