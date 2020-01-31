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
ms.openlocfilehash: 3a107176e48a88a0a04534f7044c1e416caf4091
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788897"
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
 `Stop` provádí kooperativní zastavení na všech vláknech spouštějících spravovaný kód v procesu. Během relace ladění jenom spravovaného kódu se můžou nespravované podprocesy dál spouštět (při pokusu o volání spravovaného kódu se ale zablokuje). Během relace ladění spolupráce dojde také k zastavení nespravovaných vláken. Hodnota `dwTimeoutIgnored` se aktuálně ignoruje a považuje se za INFINITou (-1). Pokud se kooperativní zastavení nepovede kvůli zablokování, všechna vlákna se pozastaví a vrátí se E_TIMEOUT.  
  
> [!NOTE]
> `Stop` je jediná synchronní metoda v rozhraní API pro ladění. Když `Stop` vrátí S_OK, proces se zastaví. Pro upozornění naslouchacího procesu zastavení není zadáno žádné zpětné volání. Aby bylo možné pokračovat v procesu, musí ladicí program volat funkci [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) .  
  
 Ladicí program udržuje čítač zastavení. Když počítadlo dosáhne nuly, kontroler se obnoví. Každé volání `Stop` nebo každé odeslané zpětné volání zvýší hodnotu čítače. Každé volání `ICorDebugController::Continue` sníží čítač.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
