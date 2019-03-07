---
title: ICorDebugRegisterSet::GetRegisters – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetRegisters method [.NET Framework debugging]
ms.assetid: fdf91864-48ea-4aa6-b70c-361b7a3184c7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4887d44f0ac5603280efa0abdbd7e65c71fc3ca
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485448"
---
# <a name="icordebugregistersetgetregisters-method"></a>ICorDebugRegisterSet::GetRegisters – metoda
Získá hodnotu každý registr (na počítači, který aktuálně spouští kód), která je určená bitová maska.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetRegisters (  
    [in] ULONG64       mask,   
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `mask`  
 [in] Bitová maska, která určuje, které registru jsou hodnoty, který se má načíst. Každý bit odpovídá registru. Pokud je o něco nastavená na jednu, načte do registru hodnota; v opačném případě se načíst hodnotu do registru.  
  
 `regCount`  
 [in] Počet hodnot registru, který se má načíst.  
  
 `regBuffer`  
 [out] Pole `CORDB_REGISTER` objektů, z nichž každý přijímá hodnotu z registru.  
  
## <a name="remarks"></a>Poznámky  
 Velikost pole by měl být roven počtu bitů nastavena na jednu v bitové masce. `regCount` Parametr určuje počet prvků ve vyrovnávací paměti, která bude dostávat hodnot registru. Pokud `regCount` hodnota je příliš malý počet registrů indikován maska, vyšší číslované registrů se zkrátí ze sady. Pokud `regCount` hodnota je příliš velká, nepoužívané `regBuffer` prvky bude bez úprav.  
  
 Pokud bit masky určuje registru, který je k dispozici, `GetRegisters` vrátí neurčitá hodnota pro tento registr.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorDebugRegisterSet – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
