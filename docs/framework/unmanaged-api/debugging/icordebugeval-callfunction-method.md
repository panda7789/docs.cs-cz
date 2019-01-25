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
ms.openlocfilehash: 493b4850436b3724287210878992d1d8ce8fe168
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589396"
---
# <a name="icordebugevalcallfunction-method"></a>ICorDebugEval::CallFunction – metoda
Nastaví zadanou funkci volání.  
  
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
 [in] Ukazatel na objekt ICorDebugFunction, který určuje funkci, která se má volat.  
  
 `nArgs`  
 [in] Počet argumentů pro funkce.  
  
 `ppArgs`  
 [in] Pole ukazatelů, každý z nich odkazuje na objekt ICorDebugValue, který určuje argument předaný do funkce.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je virtuální, funkce `CallFunction` provede virtuální odeslání. Pokud je funkce v různých aplikační domény, přechod dojde, pokud jsou všechny argumenty také v této doméně aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** WindowSee [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** 1.1, 1.0  
  
## <a name="see-also"></a>Viz také:
- [CallParameterizedFunction – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)
