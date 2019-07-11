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
ms.openlocfilehash: 5d4ab49aaccd77fac497bd86413915e82c99ed3e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744903"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a>ICorDebugRegisterSet2::GetRegistersAvailable – metoda
Získá pole bajtů, která poskytuje rastrový obrázek do dostupných registrů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `numChunks`  
 [in] Velikost `availableRegChunks` pole.  
  
 `availableRegChunks`  
 [out] Pole bajtů, každý bit odpovídá registru. Pokud je k dispozici registru, odpovídající bit do registru je nastavena.  
  
## <a name="remarks"></a>Poznámky  
 Hodnoty cordebugregister – výčet zadejte registrů různých mikroprocesory. Horní pět bitů jednotlivé hodnoty jsou index do `availableRegChunks` pole bajtů. Nižší tři bity každé hodnoty identifikovat bitová pozice v rámci indexované bajtů. Zadaný `CorDebugRegister` hodnota, která určuje konkrétní registru do registru pozice v maska je stanoven následujícím způsobem:  
  
1. Rozbalte potřebné pro přístup ke správné bajt v indexu `availableRegChunks` pole:  
  
     `CorDebugRegister` Hodnota >> 3  
  
2. Extrahujte bitové pozice v indexovaných byte, kde bit nula je nejméně významných bitů:  
  
     `CorDebugRegister` Hodnota & 7  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugRegisterSet2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [ICorDebugRegisterSet – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
