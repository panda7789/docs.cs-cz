---
title: ICorDebugStepper::Deactivate – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.Deactivate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::Deactivate
helpviewer_keywords:
- Deactivate method [.NET Framework debugging]
- ICorDebugStepper::Deactivate method [.NET Framework debugging]
ms.assetid: 855f4199-b62d-40ce-998e-1eb4a1772142
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bcd7bfb52cadf740d8fe3cb92a09b071f530b7ee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994328"
---
# <a name="icordebugstepperdeactivate-method"></a>ICorDebugStepper::Deactivate – metoda
Způsobí, že tento icordebugstepper – zrušení příkazu poslední krok, který obdržela.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Deactivate ();  
```  
  
## <a name="remarks"></a>Poznámky  
 Nový příkaz krokování vydávat po nedávno přijatého kroku příkaz byl zrušen.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
