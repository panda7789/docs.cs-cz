---
title: ICorDebugCode2::GetCompilerFlags – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCompilerFlags
helpviewer_keywords:
- GetCompilerFlags method [.NET Framework debugging]
- ICorDebugCode2::GetCompilerFlags method [.NET Framework debugging]
ms.assetid: 532e9dfd-d114-4c75-b952-1accce102643
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1605ee92c8743606ff0e958f112a2d90af43e03a
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700719"
---
# <a name="icordebugcode2getcompilerflags-method"></a>ICorDebugCode2::GetCompilerFlags – metoda

Získá příznaky určující podmínky, za kterých byl tento objekt kódu buď kompilován just-in-time (JIT), nebo generován pomocí generátoru nativních bitových kopií (Ngen.exe).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetCompilerFlags (
    [out] DWORD *pdwFlags
);
```

## <a name="parameters"></a>Parametry

 `pdwFlags`  
 mimo Ukazatel na hodnotu výčtu [CorDebugJITCompilerFlags –](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) , která určuje chování kompilátoru JIT nebo nativního generátoru obrázků.

## <a name="requirements"></a>Požadavky

 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

 **Hlavička:** CorDebug. idl, CorDebug. h

 **Knihovna:** CorGuids. lib

 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
 
