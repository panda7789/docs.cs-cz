---
title: ICorDebugEval2::CallParameterizedFunction – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CallParameterizedFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CallParameterizedFunction
helpviewer_keywords:
- ICorDebugEval2::CallParameterizedFunction method [.NET Framework debugging]
- CallParameterizedFunction method [.NET Framework debugging]
ms.assetid: 72f54a45-dbe6-4bb4-8c99-e879a27368e5
topic_type:
- apiref
ms.openlocfilehash: ab31ab8f83a71372c8e12b460458a26996f65ff5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782978"
---
# <a name="icordebugeval2callparameterizedfunction-method"></a>ICorDebugEval2::CallParameterizedFunction – metoda
Nastaví volání na zadaný ICorDebugFunction, který může být vnořen do třídy, jejíž konstruktor přebírá parametry <xref:System.Type>, nebo může přebírat <xref:System.Type> parametry.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CallParameterizedFunction (  
    [in] ICorDebugFunction     *pFunction,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pFunction`  
 pro Ukazatel na objekt `ICorDebugFunction`, který představuje funkci, která má být volána.  
  
 `nTypeArgs`  
 pro Počet argumentů, které funkce trvá.  
  
 `ppTypeArgs`  
 pro Pole ukazatelů, z nichž každý odkazuje na objekt ICorDebugType, který představuje argument funkce.  
  
 `nArgs`  
 pro Počet hodnot předaných ve funkci.  
  
 `ppArgs`  
 pro Pole ukazatelů, z nichž každý odkazuje na objekt ICorDebugValue, který představuje hodnotu předanou v argumentu funkce.  
  
## <a name="remarks"></a>Poznámky  
 `CallParameterizedFunction` jako [ICorDebugEval:: CallFunction –](icordebugeval-callfunction-method.md) s tím rozdílem, že funkce může být uvnitř třídy s parametry typu, může sám převzít parametry typu nebo obojí. Argumenty typu by měly být zadány jako první pro třídu a potom pro funkci.  
  
 Pokud je funkce v jiné doméně aplikace, dojde k přechodu. Všechny argumenty Type a Value však musí být v cílové doméně aplikace.  
  
 Vyhodnocení funkce se dá provádět jenom v omezených scénářích. Pokud `CallParameterizedFunction` nebo `ICorDebugEval::CallFunction` selže, vrátí vrácená hodnota HRESULT nejobecnější možný důvod selhání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
