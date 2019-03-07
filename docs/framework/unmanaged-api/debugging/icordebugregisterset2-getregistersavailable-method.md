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
ms.openlocfilehash: 5ffa862ebe631471030e1e87a28645e278062d18
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469115"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a>ICorDebugRegisterSet2::GetRegistersAvailable – metoda
Získá pole bajtů, která poskytuje rastrový obrázek do dostupných registrů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
1.  Rozbalte potřebné pro přístup ke správné bajt v indexu `availableRegChunks` pole:  
  
     `CorDebugRegister` Hodnota >> 3  
  
2.  Extrahujte bitové pozice v indexovaných byte, kde bit nula je nejméně významných bitů:  
  
     `CorDebugRegister` Hodnota & 7  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorDebugRegisterSet2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [ICorDebugRegisterSet – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
