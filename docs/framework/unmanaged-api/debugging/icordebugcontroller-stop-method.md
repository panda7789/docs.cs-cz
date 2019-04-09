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
ms.openlocfilehash: 724db8c5c8dbb5bf3ff8bc7202a60397180b7b38
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183388"
---
# <a name="icordebugcontrollerstop-method"></a>ICorDebugController::Stop – metoda
Provádí kooperativní stop na všech vláknech, na kterých běží spravovaný kód v procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwTimeoutIgnored`  
 Nepoužívá se.  
  
## <a name="remarks"></a>Poznámky  
 `Stop` provádí kooperativní stop na všech vláknech spuštění spravovaného kódu v procesu. Během ladicí relace pouze pro spravované, nespravované vláken může pokračovat se zrušeným (ale zablokuje při pokusu o volání spravovaného kódu). Během interop relaci ladění se také zastaví nespravovaného vlákna. `dwTimeoutIgnored` Hodnota je aktuálně ignorována a považována jako NEKONEČNÉ (-1). Pokud kooperativní stop nezdaří z důvodu zablokování, všechna vlákna jsou pozastavena a E_TIMEOUT se vrátí.  
  
> [!NOTE]
>  `Stop` je jenom synchronní metoda v rozhraní API pro ladění. Když `Stop` vrátí hodnotu S_OK, proces se zastaví. Upozorní moduly pro naslouchání ukončení dostane bez zpětného volání. Ladicí program musí volat [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) povolit pokračování procesu.  
  
 Ladicí program udržuje čítač stop. Pokud se čítač sníží na nulu, kontroleru se obnoví. Každé volání `Stop` nebo každého odeslaného zpětného volání zvýší čítač. Každé volání `ICorDebugController::Continue` dekrementuje čítače.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
