---
title: "ICorDebugEval::CallFunction – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.CallFunction
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::CallFunction
helpviewer_keywords:
- ICorDebugEval::CallFunction method [.NET Framework debugging]
- CallFunction method [.NET Framework debugging]
ms.assetid: 7f470c5c-e1c0-4d8d-aad8-830f113ae751
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 72713d81931b53e8d61fb39cee146fd30a59bfcc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugevalcallfunction-method"></a>ICorDebugEval::CallFunction – metoda
Nastaví volání zadanou funkci.  
  
 Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0. Použití [icordebugeval2::callparameterizedfunction –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md) místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CallFunction (  
    [in] ICorDebugFunction  *pFunction,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pFunction`  
 [v] Ukazatel na ICorDebugFunction objekt, který určuje funkce, která má být volána.  
  
 `nArgs`  
 [v] Počet argumentů pro funkci.  
  
 `ppArgs`  
 [v] Pole ukazatele, každý z nich odkazuje na objekt ICorDebugValue, který určuje argument mají být předány funkce.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je virtuální, funkce `CallFunction` provede virtuální odesílání. Pokud je v doméně jinou aplikaci, přechod dojde, pokud jsou všechny argumenty také v této doméně.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** WindowSee [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** 1.1, 1.0  
  
## <a name="see-also"></a>Viz také  
 [Callparameterizedfunction – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)
