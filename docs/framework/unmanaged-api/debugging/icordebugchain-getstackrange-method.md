---
title: ICorDebugChain::GetStackRange – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetStackRange
helpviewer_keywords:
- ICorDebugChain::GetStackRange method [.NET Framework debugging]
- GetStackRange method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 554284e7-3f6c-4d40-8da5-1c9317fbd484
topic_type:
- apiref
ms.openlocfilehash: 40ecc183c32500ad9e88ceb1bfc0528d717430e8
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894458"
---
# <a name="icordebugchaingetstackrange-method"></a>ICorDebugChain::GetStackRange – metoda
Získá rozsah adres segmentu zásobníku pro tento řetěz.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pStart`  
 mimo Ukazatel na `CORDB_ADDRESS` hodnotu, která je počáteční adresou segmentu zásobníku.  
  
 `pEnd`  
 mimo Ukazatel na `CORDB_ADDRESS` hodnotu, která je koncovou adresou segmentu zásobníku.  
  
## <a name="remarks"></a>Poznámky  
 Číselný rozsah má smysl pouze pro porovnání umístění rámce zásobníku. Nemůžete dělat žádné předpoklady o tom, co je ve skutečnosti uložené v zásobníku.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
