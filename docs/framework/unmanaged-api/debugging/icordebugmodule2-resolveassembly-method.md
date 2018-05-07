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
ms.openlocfilehash: 44a6596807b98e6c8b8624b5df18f78dbf8d0711
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmodule2resolveassembly-method"></a>ICorDebugModule2::ResolveAssembly – metoda
Přeloží sestavení odkazuje token Zadaná metadata.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ResolveAssembly (  
    [in]  mdToken             tkAssemblyRef,  
    [out] ICorDebugAssembly   **ppAssembly  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `tkAsemblyRef`  
 [v] `mdToken` Hodnotu, která odkazuje na sestavení.  
  
 `ppAssembly`  
 [out] Ukazatel na adresu ICorDebugAssembly objekt, který představuje sestavení.  
  
## <a name="remarks"></a>Poznámky  
 Pokud sestavení dosud není načtený při `ResolveAssembly` nazývá HRESULT je vrácena hodnota CORDBG_E_CANNOT_RESOLVE_ASSEMBLY.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
