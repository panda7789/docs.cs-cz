---
title: ICorDebugEval2::NewParameterizedObject – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObject
helpviewer_keywords:
- NewParameterizedObject method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObject method [.NET Framework debugging]
ms.assetid: 3d705463-e640-4249-8036-4e8206d03cfe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aae5f4c79acd6f92d42c2890ba64fa66e1b4bfbe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753586"
---
# <a name="icordebugeval2newparameterizedobject-method"></a>ICorDebugEval2::NewParameterizedObject – metoda
Vytvoří nový objekt typ s parametry a volání metody konstruktoru objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT NewParameterizedObject (  
    [in] ICorDebugFunction     *pConstructor,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pConstructor`  
 [in] Ukazatel na objekt ICorDebugFunction představující konstruktor objektu má být vytvořena.  
  
 `nTypeArgs`  
 [in] Byl předán počet argumentů typu.  
  
 `ppTypeArgs`  
 [in] Pole ukazatelů, každý z nich odkazuje na objekt ICorDebugType, který představuje argument typu pro objekt, který je vytvořena instance.  
  
 `nArgs`  
 [in] Počet argumentů předaný konstruktoru.  
  
 `ppArgs`  
 [in] Pole ukazatelů, každý z nich odkazuje na objekt ICorDebugValue, který reprezentuje hodnota argumentu, který je předán konstruktoru.  
  
## <a name="remarks"></a>Poznámky  
 Konstruktor objektu může trvat <xref:System.Type> parametry.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
