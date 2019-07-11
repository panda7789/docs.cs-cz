---
title: ICorDebugThread2::GetActiveFunctions – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetActiveFunctions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetActiveFunctions
helpviewer_keywords:
- GetActiveFunctions method [.NET Framework debugging]
- ICorDebugThread2::GetActiveFunctions method [.NET Framework debugging]
ms.assetid: 27fae01a-ecec-423a-973e-24f8de55826c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fdf3998d7430348cb71af8e7dd75cf2203d380ce
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769030"
---
# <a name="icordebugthread2getactivefunctions-method"></a>ICorDebugThread2::GetActiveFunctions – metoda
Získá informace o funkci aktivní ve všech snímků toto vlákno.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetActiveFunctions (  
    [in]   ULONG32             cFunctions,  
    [out]  ULONG32             *pcFunctions,  
    [in, out, size_is(cFunctions), length_is(*pcFunctions)]  
        COR_ACTIVE_FUNCTION    pFunctions[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cFunctions`  
 [in] Velikost `pFunctions` pole.  
  
 `pcFunctions`  
 [out] Ukazatel na počet objektů vrácených v `pFunctions` pole. Počet objektů vrácených bude rovnat počtu spravovaných rámců v zásobníku.  
  
 `pFunctions`  
 [out v] Pole objektů cor_active_function –, z nichž každý obsahuje informace o funkcích aktivní v rámcích toto vlákno.  
  
 První prvek se použije pro než pro rámce a tak dále zpět do kořenového adresáře do zásobníku.  
  
## <a name="remarks"></a>Poznámky  
 Pokud `pFunctions` má hodnotu null na vstupu `GetActiveFunctions` vrátí počet funkcí, které jsou v zásobníku. To znamená pokud `pFunctions` má hodnotu null na vstupu `GetActiveFunctions` vrací hodnotu pouze v `pcFunctions`.  
  
 `GetActiveFunctions` Metody slouží jako optimalizace za získání stejných informací z rámců v zásobníku a obsahuje pouze rámce, které by měly objekt ICorDebugILFrame jejich úplné trasování zásobníku.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
