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
ms.openlocfilehash: 9b9a301714ea60b4e3220eb75721e56e39bd9659
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139931"
---
# <a name="icordebugthread2getactivefunctions-method"></a>ICorDebugThread2::GetActiveFunctions – metoda
Načte informace o aktivní funkci v každém z rámců tohoto vlákna.  
  
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
 pro Velikost pole `pFunctions`.  
  
 `pcFunctions`  
 mimo Ukazatel na počet objektů vrácených v poli `pFunctions`. Počet vrácených objektů bude roven počtu spravovaných snímků v zásobníku.  
  
 `pFunctions`  
 [in, out] Pole objektů COR_ACTIVE_FUNCTION, z nichž každá obsahuje informace o aktivních funkcích v rámečcích tohoto vlákna.  
  
 První prvek bude použit pro listový rámec a tak dále zpět do kořenového adresáře zásobníku.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je u vstupu `pFunctions` null, `GetActiveFunctions` vrátí pouze počet funkcí, které jsou v zásobníku. To znamená, že pokud `pFunctions` pro vstup hodnotu null, `GetActiveFunctions` vrátí hodnotu pouze v `pcFunctions`.  
  
 Metoda `GetActiveFunctions` je určena jako optimalizace při získávání stejných informací z snímků v trasování zásobníku a zahrnuje pouze rámce, které by měly mít pro sebe objekt ICorDebugILFrame v plném trasování zásobníku.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
