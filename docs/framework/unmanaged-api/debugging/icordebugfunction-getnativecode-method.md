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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1cb073c1f93c6d60d86e5160dcfb0cbdaf1cd33
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugfunctiongetnativecode-method"></a>ICorDebugFunction::GetNativeCode – metoda
Získá nativní kód pro funkce, která je reprezentována tuto instanci ICorDebugFunction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppCode`  
 [out] Ukazatel na ICorDebugCode instanci, která reprezentuje nativní kód pro tuto funkci, nebo hodnota null, pokud je tato funkce Microsoft (MSIL intermediate language) kód, který nebyl v běhu (JIT) zkompilovat.  
  
## <a name="remarks"></a>Poznámky  
 Pokud funkce, která je reprezentována to `ICorDebugFunction` instance byl kompilována více než jednou, jako v případě obecné typy `GetNativeCode` vrátí objekt náhodných nativního kódu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
