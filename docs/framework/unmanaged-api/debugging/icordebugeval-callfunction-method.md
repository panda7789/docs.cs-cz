---
title: ICorDebugEval::CallFunction – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CallFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CallFunction
helpviewer_keywords:
- ICorDebugEval::CallFunction method [.NET Framework debugging]
- CallFunction method [.NET Framework debugging]
ms.assetid: 7f470c5c-e1c0-4d8d-aad8-830f113ae751
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86d48461c601b53d4461331a11a0e0ac7ddc6e7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412543"
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
 [CallParameterizedFunction – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)
