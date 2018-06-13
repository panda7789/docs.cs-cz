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
ms.openlocfilehash: f7ed7787f0302826cab67664780177f05e551199
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421103"
---
# <a name="icordebugthread2getactivefunctions-method"></a>ICorDebugThread2::GetActiveFunctions – metoda
Získá informace o funkci active v každé z tohoto podprocesu rámce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetActiveFunctions (  
    [in]   ULONG32             cFunctions,  
    [out]  ULONG32             *pcFunctions,  
    [in, out, size_is(cFunctions), length_is(*pcFunctions)]  
        COR_ACTIVE_FUNCTION    pFunctions[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cFunctions`  
 [v] Velikost `pFunctions` pole.  
  
 `pcFunctions`  
 [out] Ukazatel na počet objektů vrácený v `pFunctions` pole. Počet vrácených objektů bude rovnat počtu spravovaných rámce v zásobníku.  
  
 `pFunctions`  
 [ve out] Pole objektů cor_active_function –, z nichž každý obsahuje informace o active funkcí v tohoto podprocesu rámce.  
  
 První prvek se použije pro rámce typu list a tak dále zpět do kořenového adresáře zásobníku.  
  
## <a name="remarks"></a>Poznámky  
 Pokud `pFunctions` má hodnotu null na vstupu `GetActiveFunctions` vrátí pouze počet funkcí, které jsou v zásobníku. To znamená pokud `pFunctions` má hodnotu null na vstupu `GetActiveFunctions` vrací hodnotu pouze v `pcFunctions`.  
  
 `GetActiveFunctions` Metoda slouží jako optimalizace přes získávání stejné informace z rámce v trasování zásobníku a obsahuje pouze rámce, které by neměly mít objekt ICorDebugILFrame pro ně v trasování zásobníku úplné.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
