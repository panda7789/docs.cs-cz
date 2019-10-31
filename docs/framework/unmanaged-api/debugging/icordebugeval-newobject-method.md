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
ms.openlocfilehash: 68a7e911c2bd1798ea8f34f6a6e24299fe68775d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137624"
---
# <a name="icordebugevalnewobject-method"></a>ICorDebugEval::NewObject – metoda
Přidělí novou instanci objektu a zavolá specifikovanou metodu konstruktoru.  
  
 Tato metoda je zastaralá ve verzi .NET Framework 2,0. Místo toho použijte [ICorDebugEval2:: newparameterizedobject –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pConstructor`  
 pro Konstruktor, který má být volán.  
  
 `nArgs`  
 pro Velikost pole `ppArgs`.  
  
 `ppArgs`  
 pro Pole objektů ICorDebugValue, z nichž každý představuje argument, který má být předán konstruktoru.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** 1,1, 1,0  
  
## <a name="see-also"></a>Viz také:

- [NewParameterizedObject – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)
