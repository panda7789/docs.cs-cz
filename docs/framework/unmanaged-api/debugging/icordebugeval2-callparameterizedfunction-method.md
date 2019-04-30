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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cba4eb2b76d7057a5ed66a35342a79615cb8539f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934820"
---
# <a name="icordebugeval2callparameterizedfunction-method"></a>ICorDebugEval2::CallParameterizedFunction – metoda
Nastaví volání zadané ICorDebugFunction, které mohou být vnořené uvnitř třídy, jejíž konstruktor přijímá <xref:System.Type> parametry nebo může samotné trvat <xref:System.Type> parametry.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [in] Ukazatel `ICorDebugFunction` objekt, který reprezentuje funkce, která se má volat.  
  
 `nTypeArgs`  
 [in] Počet argumentů, které provede funkci.  
  
 `ppTypeArgs`  
 [in] Pole ukazatelů, každý z nich odkazuje na objekt ICorDebugType, který představuje argument funkce.  
  
 `nArgs`  
 [in] Ve funkci byl předán počet hodnot.  
  
 `ppArgs`  
 [in] Pole ukazatelů, každý z nich odkazuje na objekt ICorDebugValue, který představuje hodnotu předaného argumentu funkce.  
  
## <a name="remarks"></a>Poznámky  
 `CallParameterizedFunction` je třeba [icordebugeval::CallFunction –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md) s tím rozdílem, že funkce mohou být uvnitř třídy s parametry typu, samotné trvat parametry typu, nebo obojí. Argumenty typu by se měly provádět první třídy a funkce.  
  
 Pokud je funkce v různých aplikační domény, bude docházet k přechodu. Nicméně všechny argumenty typu a hodnoty musí být v cílové doméně aplikace.  
  
 Vyhodnocení funkce lze provést pouze v omezených scénářích. Pokud `CallParameterizedFunction` nebo `ICorDebugEval::CallFunction` selže, vrácená hodnota HRESULT označí nejobecnější důvod selhání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
