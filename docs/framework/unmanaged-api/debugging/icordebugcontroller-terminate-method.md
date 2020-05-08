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
ms.openlocfilehash: eade3fd5d946c44ae4a77c571f762709de3cef40
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976561"
---
# <a name="icordebugcontrollerterminate-method"></a>ICorDebugController::Terminate – metoda
Ukončí proces se zadaným ukončovacím kódem.  
  
> [!NOTE]
> Tato metoda je obálkou pro funkci Win32 `TerminateProcess` . Proto `Terminate` používá ukončovací kód stejným způsobem, jaký používá funkce Win32 `TerminateProcess` .  
  
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
 Pokud je `Terminate` proces zastaven při volání, proces by měl pokračovat pomocí metody [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) , aby ladicí program přijal potvrzení ukončení prostřednictvím zpětného volání [ICorDebugManagedCallback:: ExitProcess –](icordebugmanagedcallback-exitprocess-method.md) nebo [ICorDebugManagedCallback:: ExitAppDomain –](icordebugmanagedcallback-exitappdomain-method.md) .  
  
> [!NOTE]
> Tato metoda není implementována doménou aplikace. To znamená, že není implementován na <xref:System.AppDomain> úrovni.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také
