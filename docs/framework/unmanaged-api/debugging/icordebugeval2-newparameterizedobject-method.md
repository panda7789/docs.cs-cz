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
ms.openlocfilehash: c35baaee13782566c64dd8447c6a034f699b5cd0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479607"
---
# <a name="icordebugeval2newparameterizedobject-method"></a>ICorDebugEval2::NewParameterizedObject – metoda
Vytvoří nový objekt typ s parametry a volání metody konstruktoru objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
