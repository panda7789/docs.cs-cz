---
title: "ICorDebug::DebugActiveProcess – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.DebugActiveProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug::DebugActiveProcess
helpviewer_keywords:
- DebugActiveProcess method [.NET Framework debugging]
- ICorDebug::DebugActiveProcess method [.NET Framework debugging]
ms.assetid: fdab0ade-7f56-4fa2-b3ef-f7a1d2852bba
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 10cb2a5323db67c6f5664e13cb1f97d1a807d20c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdebugactiveprocess-method"></a>ICorDebug::DebugActiveProcess – metoda
Připojí ladicí program pro existující proces.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DebugActiveProcess (  
    [in]  DWORD               id,  
    [in]  BOOL                win32Attach,  
    [out] ICorDebugProcess    **ppProcess  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `id`  
 [v] ID procesu, ke kterému má být připojen ladicí program.  
  
 `win32Attach`  
 [v] Logická hodnota, která je nastavena na `true` Pokud ladicí program by měl chovat jako Win32 ladicí program pro proces a odesílání nespravované zpětná volání; jinak `false`.  
  
 `ppProcess`  
 [out] Ukazatel na adresu "ICorDebugProcess" objekt, který představuje proces, který byl připojen ladicí program.  
  
## <a name="remarks"></a>Poznámky  
 Spolupráce ladění není podporována v systémech Windows 9 x a jiný x86 platforem, jako je platformu IA-64 a na základě AMD64 platformy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
