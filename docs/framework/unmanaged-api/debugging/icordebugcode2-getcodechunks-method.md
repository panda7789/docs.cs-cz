---
title: ICorDebugCode2::GetCodeChunks – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCodeChunks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCodeChunks
helpviewer_keywords:
- GetCodeChunks method [.NET Framework debugging]
- ICorDebugCode2::GetCodeChunks method [.NET Framework debugging]
ms.assetid: 210a2f02-2678-4555-bc4a-78a0408764c8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1bdaf6391ca5c19f073708d6258ad5775bec9824
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700732"
---
# <a name="icordebugcode2getcodechunks-method"></a>ICorDebugCode2::GetCodeChunks – metoda

Získá bloky kódu, ze kterých je tento objekt kódu sestaven.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetCodeChunks (
    [in]  ULONG32     cbufSize,
    [out] ULONG32     *pcnumChunks,
    [out, size_is(cbufSize), length_is(*pcnumChunks)]
        CodeChunkInfo chunks[]
);
```

## <a name="parameters"></a>Parametry

 `cbufSize`  
 pro Velikost pole `chunks`

 `pcnumChunks`  
 mimo Počet bloků vrácených v poli `chunks`

 `chunks`  
 mimo Pole struktur "Codechunkinfo –", z nichž každý představuje jeden blok kódu. Pokud je hodnota `cbufSize` 0, tento parametr může mít hodnotu null.

## <a name="remarks"></a>Poznámky

 Bloky kódu se nikdy nepřekrývají a budou postupovat podle pořadí, ve kterém by byly zřetězeny pomocí [ICorDebugCode:: GetCode](icordebugcode-getcode-method.md). Objekt kódu jazyka MSIL (Microsoft Intermediate Language) ve verzi .NET Framework 2,0 bude obsahovat jeden blok kódu.

## <a name="requirements"></a>Požadavky

 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).

 **Hlavička:** CorDebug. idl, CorDebug. h

 **Knihovna:** CorGuids. lib

 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
 
