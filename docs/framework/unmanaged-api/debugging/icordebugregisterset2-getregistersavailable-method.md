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
ms.openlocfilehash: 2149c985519b95f89af2c50d05753ae7259babe4
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378210"
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
 pro Velikost `availableRegChunks` pole.  
  
 `availableRegChunks`  
 mimo Pole bajtů, každý bit, který odpovídá registru. Pokud je k dispozici registr, je nastaven odpovídající bit registru.  
  
## <a name="remarks"></a>Poznámky  
 Hodnoty výčtu CorDebugRegister – určují Registry různých mikroprocesorů. Horních pět bitů každé hodnoty je index `availableRegChunks` pole bajtů. Dolní tři bity každé hodnoty identifikují bitovou pozici v rámci indexovaných bajtů. Vzhledem k `CorDebugRegister` hodnotě, která určuje konkrétní registr, je pozice registru v masce určena následujícím způsobem:  
  
1. Extrahujte index potřebný pro přístup ke správnému bajtu v `availableRegChunks` poli:  
  
     `CorDebugRegister`hodnota >> 3  
  
2. Extrahuje bitovou pozici v indexovaném bajtu, kde hodnota bitu nula je nejméně významnou bitovou hodnotou:  
  
     `CorDebugRegister`hodnota & 7  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugRegisterSet2 – rozhraní](icordebugregisterset2-interface.md)
- [ICorDebugRegisterSet – rozhraní](icordebugregisterset-interface.md)
