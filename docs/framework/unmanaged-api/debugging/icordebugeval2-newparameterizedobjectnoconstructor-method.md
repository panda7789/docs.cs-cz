---
title: ICorDebugEval2::NewParameterizedObjectNoConstructor – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObjectNoConstructor
helpviewer_keywords:
- NewParameterizedObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObjectNoConstructor method [.NET Framework debugging]
ms.assetid: f15b5b78-94f4-4eb9-b3b3-a621272f357c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4434f5d0eaa45c9cfcbadb20b29564f0643a2dc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754445"
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a>ICorDebugEval2::NewParameterizedObjectNoConstructor – metoda
Vytvoří nový objekt typ s parametry ze zadané třídy bez pokusu o volání metody konstruktoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT NewParameterizedObjectNoConstructor (  
    [in] ICorDebugClass        *pClass,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pClass`  
 [in] Ukazatel na objekt ICorDebugClass, který představuje třídu objektu, který má být vytvořena.  
  
 `nTypeArgs`  
 [in] Byl předán počet argumentů typu.  
  
 `ppTypeArgs`  
 [in] Pole ukazatelů, každý z nich odkazuje na objekt ICorDebugType, který představuje argument typu pro objekt, který je vytvořena instance.  
  
## <a name="remarks"></a>Poznámky  
 `NewParameterizedObjectNoConstructor` Metoda selže, pokud nesprávný počet argumentů typu nebo jsou předány nesprávné typy argumentů typu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
