---
title: ICorDebugFrame::CreateStepper – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.CreateStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::CreateStepper
helpviewer_keywords:
- ICorDebugFrame::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 689e7f28-20c1-4d5c-9baa-17441cd63a88
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd105a5cbdb857aaa902e60968ff1d94473259b6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754237"
---
# <a name="icordebugframecreatestepper-method"></a>ICorDebugFrame::CreateStepper – metoda
Získá krokovač, umožňující ladicího programu k provádění operací krokování vzhledem k této ICorDebugFrame.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppStepper`  
 [out] Ukazatel na adresu icordebugstepper – objekt, který umožňuje ladicího programu k provádění operací krokování vzhledem k aktuální rámec.  
  
## <a name="remarks"></a>Poznámky  
 Pokud rámce není aktivní, obvykle muset objekt krokovač vrátit na snímek před dokončení tohoto kroku.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
