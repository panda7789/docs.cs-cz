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
ms.openlocfilehash: fd65de77209f5a981c0a4c291f8573a61cf6335b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645276"
---
# <a name="icordebugchaingetcaller-method"></a>ICorDebugChain::GetCaller – metoda
Získá řetězec, který volá tento řetězec.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCaller (  
    [out] ICorDebugChain      **ppChain  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppChain`  
 [out] Ukazatel na adresa icordebugchain – objekt, který představuje řetěz volání.  
  
 Pokud se tento řetězec byla volána samovolně (jako by tomu bylo-li tento řetězec nebo ladicí program inicializován zásobníku volání), `ppChain` bude mít hodnotu null.  
  
## <a name="remarks"></a>Poznámky  
 Volání řetězce může být v jiném vlákně, pokud bylo volání zařazen napříč vlákny.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
