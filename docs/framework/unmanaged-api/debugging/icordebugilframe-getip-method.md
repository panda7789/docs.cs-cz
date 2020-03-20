---
title: ICorDebugILFrame::GetIP – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::GetIP method [.NET Framework debugging]
ms.assetid: 18217ba1-1776-4297-a3b9-f77e64b0fead
topic_type:
- apiref
ms.openlocfilehash: f30516a8f59b90de9b4c052d92a8c88575ace3c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178828"
---
# <a name="icordebugilframegetip-method"></a>ICorDebugILFrame::GetIP – metoda
Získá hodnotu ukazatele instrukce a bitové kombinace hodnotu, která popisuje, jak byla získána hodnota ukazatele instrukce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pnOffset`  
 [out] Hodnota ukazatele instrukce.  
  
 `pMappingResult`  
 [out] Ukazatel na bitovou kombinaci hodnot výčtu CorDebugMappingResult, které popisují, jak byla získána hodnota ukazatele instrukce.  
  
## <a name="remarks"></a>Poznámky  
 Hodnota ukazatele instrukce je posun rámce zásobníku do kódu zprostředkujícího jazyka Microsoft (MSIL). Pokud je aktivní rámec zásobníku, tato adresa je další instrukce ke spuštění. Pokud rámec zásobníku není aktivní, tato adresa je další instrukce provést při opětovné aktivaci rámce zásobníku.  
  
 Pokud tento rámec je kompilovaný rámec just-in-time (JIT), hodnota ukazatele instrukce bude určena mapováním zpět od skutečného ukazatele nativní instrukce, takže hodnota může být pouze přibližná.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
