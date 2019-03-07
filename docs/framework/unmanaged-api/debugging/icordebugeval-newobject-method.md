---
title: ICorDebugEval::NewObject – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObject
helpviewer_keywords:
- NewObject method [.NET Framework debugging]
- ICorDebugEval::NewObject method [.NET Framework debugging]
ms.assetid: ce3025e8-defa-4c5e-8298-f49d71fa5736
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 97217421d30ee4065aa1b2500e9486405e438902
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471365"
---
# <a name="icordebugevalnewobject-method"></a>ICorDebugEval::NewObject – metoda
Přidělí novou instanci objektu a volá metodu zadaný konstruktor.  
  
 Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0. Použití [icordebugeval2::newparameterizedobject –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pConstructor`  
 [in] Konstruktor, který má být volána.  
  
 `nArgs`  
 [in] Velikost `ppArgs` pole.  
  
 `ppArgs`  
 [in] Pole objektů ICorDebugValue, z nichž každý představuje argument předaný do konstruktoru.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** 1.1, 1.0  
  
## <a name="see-also"></a>Viz také:
- [NewParameterizedObject – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)
