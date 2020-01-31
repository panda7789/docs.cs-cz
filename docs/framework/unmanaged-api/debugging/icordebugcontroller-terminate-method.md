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
ms.openlocfilehash: 851a127c117b826c271dd021c41cfdb36045a1ff
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783746"
---
# <a name="icordebugcontrollerterminate-method"></a>ICorDebugController::Terminate – metoda
Ukončí proces se zadaným ukončovacím kódem.  
  
> [!NOTE]
> Tato metoda je obálkou pro funkci Win32 `TerminateProcess`. Proto `Terminate` používá ukončovací kód stejným způsobem, jakým používá funkce Win32 `TerminateProcess`.  
  
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
 Pokud je proces zastaven při volání `Terminate`, proces by měl pokračovat pomocí metody [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) , aby ladicí program přijal potvrzení ukončení prostřednictvím zpětného volání [ICorDebugManagedCallback:: ExitProcess –](icordebugmanagedcallback-exitprocess-method.md) nebo [ICorDebugManagedCallback:: ExitAppDomain –](icordebugmanagedcallback-exitappdomain-method.md) .  
  
> [!NOTE]
> Tato metoda není implementována doménou aplikace. To znamená, že není implementován na úrovni <xref:System.AppDomain>.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
