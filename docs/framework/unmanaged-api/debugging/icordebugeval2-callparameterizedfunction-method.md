---
title: "ICorDebugEval2::CallParameterizedFunction – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2.CallParameterizedFunction
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2::CallParameterizedFunction
helpviewer_keywords:
- ICorDebugEval2::CallParameterizedFunction method [.NET Framework debugging]
- CallParameterizedFunction method [.NET Framework debugging]
ms.assetid: 72f54a45-dbe6-4bb4-8c99-e879a27368e5
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 055ded7f3309ff1011d1ca390daf353cba870376
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugeval2callparameterizedfunction-method"></a>ICorDebugEval2::CallParameterizedFunction – metoda
Nastavuje volání do zadané ICorDebugFunction, což může být vnořena ve třídu, jejíž konstruktor přijímá <xref:System.Type> parametry, nebo může sám sebe trvat <xref:System.Type> parametry.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `pFunction`  
 [v] Ukazatel na `ICorDebugFunction` objekt, který reprezentuje funkce, která má být volána.  
  
 `nTypeArgs`  
 [v] Počet argumentů, které funkce přijímá.  
  
 `ppTypeArgs`  
 [v] Pole ukazatele, každý z nich odkazuje na objekt ICorDebugType, který představuje argument funkce.  
  
 `nArgs`  
 [v] Počet hodnot, je předaná funkci.  
  
 `ppArgs`  
 [v] Pole ukazatele, každý z nich odkazuje na objekt ICorDebugValue, který reprezentuje hodnotu předáno v argumentu funkce.  
  
## <a name="remarks"></a>Poznámky  
 `CallParameterizedFunction`je třeba [icordebugeval::CallFunction –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md) s tím rozdílem, že funkce může být uvnitř tříd pomocí parametrů typu, může sám sebe trvat parametry typu nebo obojí. Argumenty typu by měly mít nejprve pro třídu a potom pro funkci.  
  
 Pokud je v doméně jinou aplikaci, dojde k přechodu. Všechny argumenty typu a hodnoty musí však být v cílové doméně aplikace.  
  
 Vyhodnocení funkce lze provést jenom v situacích, omezené. Pokud `CallParameterizedFunction` nebo `ICorDebugEval::CallFunction` selže, vrácený HRESULT označí nejobecnější možný důvod selhání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
