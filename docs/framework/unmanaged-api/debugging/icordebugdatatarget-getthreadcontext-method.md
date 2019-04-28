---
title: ICorDebugDataTarget::GetThreadContext – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetThreadContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetThreadContext
helpviewer_keywords:
- ICorDebugDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: c8954268-1821-4b23-b665-dbb55f2af31b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2db073f6bde3ded27f8e1aa41bfcb87e764745f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61748939"
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a>ICorDebugDataTarget::GetThreadContext – metoda
Vrátí kontext aktuálního vlákna pro zadaný podproces.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwThreadID`  
 [in] Identifikátor vlákna, jehož rámci má být načtena. Identifikátor je definován v operačním systému.  
  
 `contextFlags`  
 [in] Bitová kombinace příznaků závislého na platformě, které označují, které části kontextu byste si měli přečíst.  
  
 `contextSize`  
 [in] Velikost `pContext`.  
  
 `pContext`  
 [out] Vyrovnávací paměť, kam se má kontext vlákna uložit.  
  
## <a name="remarks"></a>Poznámky  
 Na platformách Windows `pContext` musí být `CONTEXT` strukturu (definované v souboru WinNT.h), který je vhodný pro typ počítače určené [icordebugdatatarget::getplatform –](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) metody. `contextFlags` musí mít stejné hodnoty jako `ContextFlags` pole `CONTEXT` struktury. `CONTEXT` Struktura je specifické pro procesor, naleznete v souboru WinNT.h souboru podrobnosti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugDataTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
