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
ms.openlocfilehash: 362ae813846ab31f170ae49288735996eb1e9555
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531756"
---
# <a name="icordebugcontrollerterminate-method"></a>ICorDebugController::Terminate – metoda
Ukončí proces s uvedený ukončovací kód.  
  
> [!NOTE]
>  Tato metoda je obálka pro Win32 `TerminateProcess` funkce. Proto `Terminate` používá ukončovací kód procesu ve stejném způsobu, jakým Win32 `TerminateProcess` funkce použije.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `exitCode`  
 [in] Číselná hodnota, která je ukončovací kód. Platné číselné hodnoty jsou definovány v Winbase.h.  
  
## <a name="remarks"></a>Poznámky  
 Zastavení procesu, kdy `Terminate` je volána, proces by měly pokračovat s použitím [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) metodu tak, aby ladicí program přijímá potvrzení ukončení prostřednictvím [ Icordebugmanagedcallback::exitprocess –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) nebo [icordebugmanagedcallback::exitappdomain –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) zpětného volání.  
  
> [!NOTE]
>  Tato metoda není implementována podle domény aplikace. To znamená, že není implementovaná v <xref:System.AppDomain> úroveň.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

