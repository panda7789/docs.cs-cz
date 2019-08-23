---
title: ICorDebugController::Terminate – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugController.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Terminate
helpviewer_keywords:
- Terminate method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Terminate method [.NET Framework debugging]
ms.assetid: 4275af0c-b5a7-4e4c-97c9-7e41f36b2dd8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee1c30809567097e67b6b1e40f5534429d748abd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964373"
---
# <a name="icordebugcontrollerterminate-method"></a>ICorDebugController::Terminate – metoda
Ukončí proces se zadaným ukončovacím kódem.  
  
> [!NOTE]
> Tato metoda je obálkou pro funkci Win32 `TerminateProcess` . Proto používá ukončovací kód stejným způsobem, jaký používá funkce Win32 `TerminateProcess`. `Terminate`  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `exitCode`  
 pro Číselná hodnota, která je ukončovacím kódem. Platné číselné hodnoty jsou definovány v Winbase. h.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je proces zastaven při `Terminate` volání, proces by měl pokračovat pomocí metody [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) , aby ladicí program přijal potvrzení ukončení prostřednictvím [ICorDebugManagedCallback:: ExitProcess –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) nebo [ICorDebugManagedCallback:: ExitAppDomain –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) zpětné volání.  
  
> [!NOTE]
> Tato metoda není implementována doménou aplikace. To znamená, že není implementován na <xref:System.AppDomain> úrovni.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** CorDebug. idl, CorDebug. h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
