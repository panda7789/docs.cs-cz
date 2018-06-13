---
title: ICorDebugChain::GetCaller – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCaller
helpviewer_keywords:
- ICorDebugChain::GetCaller method [.NET Framework debugging]
- GetCaller method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: d0b8ab4b-d7d2-4fa0-945f-3d2b87e7e991
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a0b5d702e9718ce6ac537beae67fc190b152b9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405140"
---
# <a name="icordebugchaingetcaller-method"></a>ICorDebugChain::GetCaller – metoda
Získá řetězec, který volá tento řetězec.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCaller (  
    [out] ICorDebugChain      **ppChain  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppChain`  
 [out] Ukazatel na adresu ICorDebugChain objekt, který reprezentuje řetězu volání.  
  
 Pokud se tento řetězec samovolně volala (protože by byl tento případ, pokud se tento řetězec nebo ladicího programu inicializovat zásobníku volání), `ppChain` bude mít hodnotu null.  
  
## <a name="remarks"></a>Poznámky  
 Řetězu volání může být v jiném podprocesu, pokud bylo volání zařazené napříč vlákny.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
