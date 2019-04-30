---
title: ICorDebug::DebugActiveProcess – metoda
ms.date: 03/30/2017
api_name:
- ICorDebug.DebugActiveProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::DebugActiveProcess
helpviewer_keywords:
- DebugActiveProcess method [.NET Framework debugging]
- ICorDebug::DebugActiveProcess method [.NET Framework debugging]
ms.assetid: fdab0ade-7f56-4fa2-b3ef-f7a1d2852bba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b880358ed0d7bce4896217bc07c6ef6268d62962
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786396"
---
# <a name="icordebugdebugactiveprocess-method"></a>ICorDebug::DebugActiveProcess – metoda
Připojí ladicí program k existujícímu procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DebugActiveProcess (  
    [in]  DWORD               id,  
    [in]  BOOL                win32Attach,  
    [out] ICorDebugProcess    **ppProcess  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `id`  
 [in] ID procesu, ke kterému je ladicí program připojit.  
  
 `win32Attach`  
 [in] Logická hodnota, která je nastavena na `true` Pokud ladicí program by měl chovat jako ladicí program systému Win32 pro proces a odeslání nespravované zpětná volání; v opačném případě `false`.  
  
 `ppProcess`  
 [out] Ukazatel na adresu "ICorDebugProcess" objekt, který představuje proces, ke kterému je připojen ladicí program.  
  
## <a name="remarks"></a>Poznámky  
 Definiční ladění není podporováno na platformách Win9x a x x86, jako jsou založené na IA-64 a AMD64 podle platformy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
