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
ms.openlocfilehash: 38cc98f1bfd966d1f764e43b30003a2bae66297d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793461"
---
# <a name="icordebugevalnewobject-method"></a>ICorDebugEval::NewObject – metoda
Přidělí novou instanci objektu a zavolá specifikovanou metodu konstruktoru.  
  
 Tato metoda je zastaralá ve verzi .NET Framework 2,0. Místo toho použijte [ICorDebugEval2:: newparameterizedobject –](icordebugeval2-newparameterizedobject-method.md) .  
  
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

- [NewParameterizedObject – metoda](icordebugeval2-newparameterizedobject-method.md)
