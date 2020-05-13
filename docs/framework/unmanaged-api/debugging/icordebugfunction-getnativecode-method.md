---
title: ICorDebugFunction::GetNativeCode – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetNativeCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetNativeCode
helpviewer_keywords:
- GetNativeCode method [.NET Framework debugging]
- ICorDebugFunction::GetNativeCode method [.NET Framework debugging]
ms.assetid: c8a34916-0eef-4987-8d29-c8bcb4be9cf6
topic_type:
- apiref
ms.openlocfilehash: 98aee38415709974d84873df50c39263490f2f23
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213267"
---
# <a name="icordebugfunctiongetnativecode-method"></a>ICorDebugFunction::GetNativeCode – metoda
Získá nativní kód pro funkci, která je reprezentovaná touto instancí ICorDebugFunction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppCode`  
 mimo Ukazatel na instanci ICorDebugCode, která představuje nativní kód pro tuto funkci, nebo hodnotu null, pokud je tato funkce kód jazyka MSIL (Microsoft Intermediate Language), který nebyl zkompilován za běhu (just-in-time).  
  
## <a name="remarks"></a>Poznámky  
 Pokud byla funkce reprezentovaná touto `ICorDebugFunction` instancí JIT zkompilována více než jednou, jako u obecných typů, `GetNativeCode` vrátí objekt náhodného nativního kódu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
