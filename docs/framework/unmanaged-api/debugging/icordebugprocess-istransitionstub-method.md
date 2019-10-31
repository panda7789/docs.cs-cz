---
title: ICorDebugProcess::IsTransitionStub – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsTransitionStub
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsTransitionStub
helpviewer_keywords:
- ICorDebugProcess::IsTransitionStub method [.NET Framework debugging]
- IsTransitionStub method [.NET Framework debugging]
ms.assetid: f7653317-7e48-4163-be03-f50f1a4b0f70
topic_type:
- apiref
ms.openlocfilehash: 852c77be0dc8ef91933bacbbd3d6b3f5a69ae8c8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139384"
---
# <a name="icordebugprocessistransitionstub-method"></a>ICorDebugProcess::IsTransitionStub – metoda
Získá hodnotu, která označuje, zda je adresa uvnitř zástupné procedury, která způsobí přechod ke spravovanému kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
## <a name="parameters"></a>Parametry  
 `address`  
 pro Hodnota `CORDB_ADDRESS`, která určuje konkrétní adresu.  
  
 `pbTransitionStub`  
 mimo Ukazatel na logickou hodnotu, která je `true`, pokud je zadaná adresa uvnitř zástupné procedury, která způsobí přechod ke spravovanému kódu; v opačném případě *`pbTransitionStub` `false`.  
  
## <a name="remarks"></a>Poznámky  
 Metodu `IsTransitionStub` lze použít nespravovaným kódem krokování k rozhodnutí, kdy vrátit řízení krokování spravovanému stepper.  
  
 Pomocí informací v přenositelném spustitelném souboru (PE) můžete také převést zástupné procedury pro převod identity.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
