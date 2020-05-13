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
ms.openlocfilehash: e064a7db131a671adc4d0b6df522f3456e3a31d5
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83377155"
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
 pro Velikost `pFunctions` pole.  
  
 `pcFunctions`  
 mimo Ukazatel na počet objektů vrácených v `pFunctions` poli. Počet vrácených objektů bude roven počtu spravovaných snímků v zásobníku.  
  
 `pFunctions`  
 [in, out] Pole objektů COR_ACTIVE_FUNCTION, z nichž každý obsahuje informace o aktivních funkcích v rámečcích tohoto vlákna.  
  
 První prvek bude použit pro listový rámec a tak dále zpět do kořenového adresáře zásobníku.  
  
## <a name="remarks"></a>Poznámky  
 Pokud `pFunctions` je u vstupu hodnota null, `GetActiveFunctions` vrátí pouze počet funkcí, které jsou v zásobníku. To znamená, že pokud `pFunctions` je u vstupu hodnota null, `GetActiveFunctions` vrátí hodnotu pouze v `pcFunctions` .  
  
 `GetActiveFunctions`Metoda je určena jako optimalizace při získávání stejných informací z snímků v trasování zásobníku a zahrnuje pouze rámce, které by měly mít pro sebe objekt ICorDebugILFrame v plném trasování zásobníku.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
