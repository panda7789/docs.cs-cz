---
title: ICorDebugController::Stop – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugController.Stop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Stop
helpviewer_keywords:
- Stop method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Stop method [.NET Framework debugging]
ms.assetid: c34e79be-a7fb-479e-8dec-d126a4c330e5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 363d8f7d8cf960fb23210225c4545f73d597d663
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912847"
---
# <a name="icordebugcontrollerstop-method"></a>ICorDebugController::Stop – metoda
Provede kooperativní zastavení na všech vláknech, na kterých běží spravovaný kód v procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwTimeoutIgnored`  
 Nepoužívá se.  
  
## <a name="remarks"></a>Poznámky  
 `Stop`provede kooperativní zastavení na všech vláknech spouštějících spravovaný kód v procesu. Během relace ladění jenom spravovaného kódu se můžou nespravované podprocesy dál spouštět (při pokusu o volání spravovaného kódu se ale zablokuje). Během relace ladění spolupráce dojde také k zastavení nespravovaných vláken. `dwTimeoutIgnored` Hodnota je aktuálně ignorována a považována za infinitou (-1). Pokud se kooperativní zastavení nepovede kvůli zablokování, všechna vlákna se pozastaví a vrátí se E_TIMEOUT.  
  
> [!NOTE]
> `Stop`je jedinou synchronní metodou v rozhraní API pro ladění. Při `Stop` vrácení S_OK se proces zastaví. Pro upozornění naslouchacího procesu zastavení není zadáno žádné zpětné volání. Aby bylo možné pokračovat v procesu, musí ladicí program volat funkci [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) .  
  
 Ladicí program udržuje čítač zastavení. Když počítadlo dosáhne nuly, kontroler se obnoví. Každé volání `Stop` nebo každé odeslané zpětné volání zvýší hodnotu čítače. Každé volání `ICorDebugController::Continue` snižující počítadlo.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** CorDebug. idl, CorDebug. h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
