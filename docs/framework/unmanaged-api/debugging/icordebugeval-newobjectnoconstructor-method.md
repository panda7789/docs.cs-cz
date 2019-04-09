---
title: ICorDebugEval::NewObjectNoConstructor – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObjectNoConstructor
helpviewer_keywords:
- NewObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval::NewObjectNoConstructor method [.NET Framework debugging]
ms.assetid: 80d509ca-b5e3-4c46-9c14-800db73d9bf7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6846b866fd47674ca6b5fd187b580fd28e080fd0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162303"
---
# <a name="icordebugevalnewobjectnoconstructor-method"></a>ICorDebugEval::NewObjectNoConstructor – metoda
Přidělí novou instanci objektu zadaného typu, bez pokusu o volání metody konstruktoru.  
  
 Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0. Použití [icordebugeval2::newparameterizedobjectnoconstructor –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT NewObjectNoConstructor (  
    [in] ICorDebugClass     *pClass  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pClass`  
 [in] Ukazatel na objekt ICorDebugClass, který představuje typ objektu, který má být vytvořena.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** 1.1, 1.0  
  
## <a name="see-also"></a>Viz také:

- [NewParameterizedObjectNoConstructor – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)
