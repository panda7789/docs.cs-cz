---
title: ICorDebugManagedCallback::Break – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Break
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Break
helpviewer_keywords:
- Break method [.NET Framework debugging]
- ICorDebugManagedCallback::Break method [.NET Framework debugging]
ms.assetid: 7d78a301-82b3-43b2-9d65-3cda3285ae97
topic_type:
- apiref
ms.openlocfilehash: f70a88df00d15729a6bde06b49417b6439f7c0ec
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212461"
---
# <a name="icordebugmanagedcallbackbreak-method"></a>ICorDebugManagedCallback::Break – metoda

Upozorní ladicí program, když <xref:System.Reflection.Emit.OpCodes.Break> je proveden pokyn v datovém proudu kódu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Break (
    [in] ICorDebugAppDomain *pAppDomain,
    [in] ICorDebugThread    *thread
);
```

## <a name="parameters"></a>Parametry

`pAppDomain`\
pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující instrukci Break.

`thread`\
pro Ukazatel na objekt ICorDebugThread, který představuje vlákno, které obsahuje instrukci Break.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlavička:** CorDebug. idl, CorDebug. h

**Knihovna:** CorGuids. lib

**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Viz také

- [ICorDebugManagedCallback – rozhraní](icordebugmanagedcallback-interface.md)
