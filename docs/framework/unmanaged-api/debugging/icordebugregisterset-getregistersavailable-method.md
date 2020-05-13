---
title: ICorDebugRegisterSet::GetRegistersAvailable – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable
helpviewer_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable method [.NET Framework debugging]
- GetRegistersAvailable method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 4ba08ffa-55a2-4662-9d6d-4738f1db60c9
topic_type:
- apiref
ms.openlocfilehash: 74eef0c1ec456d647e5a58e5009d2c77e5002289
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378294"
---
# <a name="icordebugregistersetgetregistersavailable-method"></a>ICorDebugRegisterSet::GetRegistersAvailable – metoda
Načte bitovou masku, která označuje, které Registry v tomto [ICorDebugRegisterSet](icordebugregisterset-interface.md) jsou aktuálně k dispozici.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [out] ULONG64   *pAvailable  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pAvailable`  
 mimo Bitová maska, která označuje, které Registry jsou aktuálně k dispozici.  
  
## <a name="remarks"></a>Poznámky  
 Registr může být nedostupný, pokud jeho hodnotu nelze určit pro danou situaci.  
  
 Vrácená maska obsahuje bit pro každý registr (1 << index registru). Bitová hodnota je 1, pokud je registr k dispozici, nebo 0, pokud není k dispozici.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugRegisterSet – rozhraní](icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2 – rozhraní](icordebugregisterset2-interface.md)
