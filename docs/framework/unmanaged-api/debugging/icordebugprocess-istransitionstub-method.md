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
ms.openlocfilehash: ab2121605f974fdf3f9053214a4d29d8b0dd72db
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210777"
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
 pro `CORDB_ADDRESS`Hodnota, která určuje konkrétní adresu.  
  
 `pbTransitionStub`  
 mimo Ukazatel na logickou hodnotu, která je `true` v případě, že zadaná adresa je uvnitř zástupné procedury, která způsobí přechod ke spravovanému kódu; v opačném případě * `pbTransitionStub` je `false` .  
  
## <a name="remarks"></a>Poznámky  
 `IsTransitionStub`Metoda může být použita nespravovaným kódem krokování k rozhodnutí, kdy vrátit řízení krokování spravovanému stepper.  
  
 Pomocí informací v přenositelném spustitelném souboru (PE) můžete také převést zástupné procedury pro převod identity.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
