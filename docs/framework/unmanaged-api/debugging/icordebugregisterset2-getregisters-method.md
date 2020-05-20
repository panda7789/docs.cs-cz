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
ms.openlocfilehash: 71b9d59621efb547713cb4a6c9df7a7142f4a677
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615186"
---
# <a name="icordebugregisterset2getregisters-method"></a>ICorDebugRegisterSet2:: GetRegisters – metoda

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
 pro Velikost pole v bajtech `mask` .  
  
 `mask`  
 pro Pole bajtů, každý bit, který odpovídá registru. Pokud je bit 1, načte se odpovídající hodnota registru.  
  
 `regCount`  
 pro Počet hodnot registru, které mají být načteny.  
  
 `regBuffer`  
 mimo Pole `CORDB_REGISTER` objektů, z nichž každý přijímá hodnotu registru.  
  
## <a name="remarks"></a>Poznámky

 `GetRegisters`Metoda vrací pole hodnot z registrů, které jsou určeny maskou. Pole neobsahuje hodnoty pro registry, jejichž bit maskování není nastaven. Proto `regBuffer` musí být velikost pole rovna počtu 1 v masce. Pokud `regCount` je hodnota příliš malá pro počet registrů, které jsou označeny maskou, hodnoty z vyšších očíslovaných registrů se ze sady zkrátí. Pokud `regCount` je příliš velké, nepoužívané `regBuffer` prvky nebudou změněny.  
  
 Pokud je nedostupný registr označen maskou, bude pro tento registr vrácena neurčitá hodnota.  
  
 `ICorDebugRegisterSet2::GetRegisters`Metoda je nezbytná pro platformy, které mají více než 64 registrů. Například IA64 má 128 registrů pro obecné účely a 128 registrů s plovoucí desetinnou čárkou, takže potřebujete více než 64 bitů v bitové masce.  
  
 Pokud nemáte více než 64 registrů, stejně jako v případě platforem, jako je například x86, `GetRegisters` metoda pouze překládá bajty v poli `mask` bajtů do `ULONG64` a a poté volá metodu [ICorDebugRegisterSet:: GetRegisters](icordebugregisterset-getregisters-method.md) , která přebírá `ULONG64` masku.  
  
## <a name="requirements"></a>Požadavky

 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugRegisterSet2 – rozhraní](icordebugregisterset2-interface.md)
- [ICorDebugRegisterSet – rozhraní](icordebugregisterset-interface.md)
