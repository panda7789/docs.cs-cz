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
ms.openlocfilehash: 00c9939b25f395010f6ea5832b405c3e9928a223
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792028"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a>ICorDebugRegisterSet2::GetRegistersAvailable – metoda
Získá pole bajtů, které poskytuje rastrový obrázek dostupných registrů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `numChunks`  
 pro Velikost pole `availableRegChunks`.  
  
 `availableRegChunks`  
 mimo Pole bajtů, každý bit, který odpovídá registru. Pokud je k dispozici registr, je nastaven odpovídající bit registru.  
  
## <a name="remarks"></a>Poznámky  
 Hodnoty výčtu CorDebugRegister – určují Registry různých mikroprocesorů. Horních pět bitů každé hodnoty je index v `availableRegChunks` poli bajtů. Dolní tři bity každé hodnoty identifikují bitovou pozici v rámci indexovaných bajtů. Vzhledem k hodnotě `CorDebugRegister`, která určuje konkrétní registr, je pozice registru v masce určena následujícím způsobem:  
  
1. Extrahujte index potřebný pro přístup ke správnému bajtu v `availableRegChunks` poli:  
  
     hodnota `CorDebugRegister` > > 3  
  
2. Extrahuje bitovou pozici v indexovaném bajtu, kde hodnota bitu nula je nejméně významnou bitovou hodnotou:  
  
     hodnota `CorDebugRegister` & 7  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugRegisterSet2 – rozhraní](icordebugregisterset2-interface.md)
- [ICorDebugRegisterSet – rozhraní](icordebugregisterset-interface.md)
