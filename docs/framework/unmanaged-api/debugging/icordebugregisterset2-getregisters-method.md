---
title: ICorDebugRegisterSet2::GetRegisters – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegisters method [.NET Framework debugging]
ms.assetid: dbc498a8-ba3f-42f2-bdd9-b623c77a1019
topic_type:
- apiref
ms.openlocfilehash: 54a5fb50a0177fe9886582c112f16ce871ea9df4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792065"
---
# <a name="icordebugregisterset2getregisters-method"></a>ICorDebugRegisterSet2::GetRegisters – metoda
Získá hodnotu každého registru (pro platformu, na které je aktuálně spuštěn kód), který je určen pomocí dané bitové masky.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `maskCount`  
 pro Velikost pole `mask` v bajtech  
  
 `mask`  
 pro Pole bajtů, každý bit, který odpovídá registru. Pokud je bit 1, načte se odpovídající hodnota registru.  
  
 `regCount`  
 pro Počet hodnot registru, které mají být načteny.  
  
 `regBuffer`  
 mimo Pole objektů `CORDB_REGISTER`, z nichž každý přijímá hodnotu registru.  
  
## <a name="remarks"></a>Poznámky  
 Metoda `GetRegisters` vrací pole hodnot z registrů, které jsou určeny maskou. Pole neobsahuje hodnoty pro registry, jejichž bit maskování není nastaven. Proto musí být velikost pole `regBuffer` rovna počtu 1 v masce. Pokud je hodnota `regCount` příliš malá pro počet registrů, které jsou označeny maskou, hodnoty vyšších očíslovaných registrů se ze sady zkrátí. Pokud je `regCount` příliš velká, nepoužívané prvky `regBuffer` nebudou změněny.  
  
 Pokud je nedostupný registr označen maskou, bude pro tento registr vrácena neurčitá hodnota.  
  
 Metoda `ICorDebugRegisterSet2::GetRegisters` je nezbytná pro platformy, které mají více než 64 registrů. Například IA64 má 128 registrů pro obecné účely a 128 registrů s plovoucí desetinnou čárkou, takže potřebujete více než 64-bitů v bitové masce.  
  
 Pokud nemáte více než 64 registrů, stejně jako v případě platforem, jako je například x86, metoda `GetRegisters` skutečně překládá bajty v poli `mask` bajtů do `ULONG64` a poté volá metodu [ICorDebugRegisterSet:: GetRegisters](icordebugregisterset-getregisters-method.md) , která používá masku `ULONG64`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugRegisterSet2 – rozhraní](icordebugregisterset2-interface.md)
- [ICorDebugRegisterSet – rozhraní](icordebugregisterset-interface.md)
