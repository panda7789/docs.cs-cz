---
title: "ICorDebugDataTarget::GetThreadContext – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugDataTarget.GetThreadContext Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugDataTarget::GetThreadContext
helpviewer_keywords:
- ICorDebugDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: c8954268-1821-4b23-b665-dbb55f2af31b
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 44543ca3546827b38643cab0e047032a96be9ea6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a>ICorDebugDataTarget::GetThreadContext – metoda
Vrátí aktuální vlákno kontext pro zadaný vlákno.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwThreadID`  
 [v] Identifikátor vlákno, jehož kontext je mají být načteny. Identifikátor je definována v operačním systému.  
  
 `contextFlags`  
 [v] Bitová kombinace příznaky závislé na platformy, které označují, které části kontextu byste si měli přečíst.  
  
 `contextSize`  
 [v] Velikost `pContext`.  
  
 `pContext`  
 [out] Vyrovnávací paměť, kde bude uložena kontext přístup z více vláken.  
  
## <a name="remarks"></a>Poznámky  
 U platforem Windows `pContext` musí být `CONTEXT` struktury (definovanou v souboru WinNT.h), který je vhodný pro typ počítače určeného [icordebugdatatarget::getplatform –](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) metoda. `contextFlags`musí mít stejné hodnoty jako `ContextFlags` pole z `CONTEXT` struktura. `CONTEXT` Struktura je specifické pro procesor, naleznete v souboru WinNT.h souboru podrobnosti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugDataTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
