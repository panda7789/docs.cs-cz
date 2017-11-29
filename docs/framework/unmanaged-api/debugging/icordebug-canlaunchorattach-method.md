---
title: "ICorDebug::CanLaunchOrAttach – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.CanLaunchOrAttach
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug::CanLaunchOrAttach
helpviewer_keywords:
- ICorDebug::CanLaunchOrAttach method [.NET Framework debugging]
- CanLaunchOrAttach method [.NET Framework debugging]
ms.assetid: ca7723db-7c07-4cdd-bd92-fba34928b623
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5bd657c73dfaf7643405b4b657edeffa6e33cd68
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcanlaunchorattach-method"></a>ICorDebug::CanLaunchOrAttach – metoda
Vrátí hodnotu určující, zda je možné v rámci aktuální konfiguraci počítače a prostředí runtime spouštění nového procesu nebo připojení k zadané stávajícího procesu HRESULT.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwProcessId`  
 [v] ID existujícího procesu.  
  
 `win32DebuggingEnabled`  
 [v] Předejte `true` Pokud plánujete spouštět s povoleným laděním Win32, nebo se připojit s laděním Win32 povoleno; jinak hodnota předejte `false`.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK Pokud ladění služeb zjistit nový proces spouštění nebo připojení k dané proces je možné, zadané informace o aktuální konfiguraci počítače a prostředí runtime. Možné hodnoty HRESULT jsou:  
  
-   S_OK  
  
-   CORDBG_E_DEBUGGING_NOT_POSSIBLE  
  
-   CORDBG_E_KERNEL_DEBUGGER_PRESENT  
  
-   CORDBG_E_KERNEL_DEBUGGER_ENABLED  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je pouze informační. Rozhraní neukončí nezabráníte ve spouštění nebo připojení k procesu, bez ohledu na hodnotu vrácený `CanLaunchOrAttach`.  
  
 Pokud budete chtít spustit s povoleným laděním Win32 nebo připojení s povoleným laděním Win32, předat `true` pro `win32DebuggingEnabled`. Hodnota HRESULT vrácený `CanLaunchOrAttach` může lišit, pokud použijete tuto možnost.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebug – rozhraní rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
