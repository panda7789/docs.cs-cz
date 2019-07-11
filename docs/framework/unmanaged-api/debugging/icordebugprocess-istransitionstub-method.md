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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ec29aa748c437199434fa1394e1a00c82154447
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766874"
---
# <a name="icordebugprocessistransitionstub-method"></a>ICorDebugProcess::IsTransitionStub – metoda
Získá hodnotu, která určuje, zda je adresa uvnitř zástupnou proceduru, která způsobí, že s přechodem na spravovaný kód.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
## <a name="parameters"></a>Parametry  
 `address`  
 [in] A `CORDB_ADDRESS` hodnotu, která určuje dotyčný adresu.  
  
 `pbTransitionStub`  
 [out] Ukazatel na logickou hodnotu, která je `true` Pokud zadaná adresa je uvnitř zástupnou proceduru, která způsobí, že s přechodem na spravovaný kód; v opačném případě *`pbTransitionStub` je `false`.  
  
## <a name="remarks"></a>Poznámky  
 `IsTransitionStub` Metoda umožňuje nespravovaným krokování kódem při rozhodování, kdy se vraťte do spravované krokovač krokování ovládacího prvku.  
  
 Můžete také zástupné procedury přechod identity zobrazením informací do přenosného spustitelného souboru (PE).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
