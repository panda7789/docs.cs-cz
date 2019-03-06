---
title: ICorDebugModule2::ResolveAssembly – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ResolveAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ResolveAssembly
helpviewer_keywords:
- ICorDebugModule2::ResolveAssembly method [.NET Framework debugging]
- ResolveAssembly method [.NET Framework debugging]
ms.assetid: ddf9085c-7161-44bd-9609-cd2732b9009f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd899422287d34407778f67e5b4dfd2f33ffd00c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57359689"
---
# <a name="icordebugmodule2resolveassembly-method"></a>ICorDebugModule2::ResolveAssembly – metoda

Přeloží sestavení odkazuje token Zadaná metadata.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT ResolveAssembly (
    [in]  mdToken             tkAssemblyRef,
    [out] ICorDebugAssembly   **ppAssembly
);
```

## <a name="parameters"></a>Parametry

`tkAssemblyRef`\
[in] `mdToken` Hodnotu, která odkazuje na sestavení.

`ppAssembly`\
[out] Ukazatel na adresu icordebugassembly – objekt, který představuje sestavení.

## <a name="remarks"></a>Poznámky

Pokud sestavení ještě není zaveden při `ResolveAssembly` nazývá HRESULT je vrácena hodnota CORDBG_E_CANNOT_RESOLVE_ASSEMBLY.

## <a name="requirements"></a>Požadavky

**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

**Záhlaví:** CorDebug.idl, CorDebug.h

**Knihovna:** CorGuids.lib

**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
