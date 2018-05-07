---
title: ICorDebugRegisterSet2::GetRegistersAvailable – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegistersAvailable
helpviewer_keywords:
- GetRegistersAvailable method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegistersAvailable method [.NET Framework debugging]
ms.assetid: f3ed344b-0d3a-44e8-8000-2a97e0805a2c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3a9cdb49c1a44dbc68cd4b7ccf4d4781ce5c539
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugregisterset2getregistersavailable-method"></a>ICorDebugRegisterSet2::GetRegistersAvailable – metoda
Získá pole bajtů, které poskytuje rastrový obrázek k dispozici registrů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `numChunks`  
 [v] Velikost `availableRegChunks` pole.  
  
 `availableRegChunks`  
 [out] Pole bajtů, každý bit odpovídá registraci. Pokud do registru je k dispozici, je nastavena odpovídající bit registru.  
  
## <a name="remarks"></a>Poznámky  
 Zadejte hodnoty CorDebugRegister – výčet registry různé procesory. Horní pět bits každé hodnoty jsou indexem `availableRegChunks` pole bajtů. Nižší tři bits každou hodnotu identifikovat bit pozici v rámci indexované bajtů. Vzhledem `CorDebugRegister` hodnotu, která určuje konkrétní registrace, pozice registru v maska je stanoven následujícím způsobem:  
  
1.  Extrahování potřebné pro přístup k správné bajtů v indexu `availableRegChunks` pole:  
  
     `CorDebugRegister` Hodnota >> 3  
  
2.  Extrahujte bit pozici v rámci indexované bajtů, kde je bit nula nejméně významný bit:  
  
     `CorDebugRegister` Hodnota & 7  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugRegisterSet2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 [ICorDebugRegisterSet – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
