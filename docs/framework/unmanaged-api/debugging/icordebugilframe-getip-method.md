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
ms.openlocfilehash: 3890cb4236f113bc6efc23bfb606d19a525ec234
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210264"
---
# <a name="icordebugilframegetip-method"></a>ICorDebugILFrame::GetIP – metoda
Získá hodnotu ukazatele na instrukci a bitovou kombinaci hodnoty, která popisuje, jak byla získána hodnota ukazatele na instrukci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pnOffset`  
 mimo Hodnota ukazatele na instrukci.  
  
 `pMappingResult`  
 mimo Ukazatel na bitovou kombinaci hodnot výčtu CorDebugMappingResult –, které popisují, jak byla získána hodnota ukazatele na instrukci.  
  
## <a name="remarks"></a>Poznámky  
 Hodnota ukazatele na instrukci je posun rámce zásobníku do kódu jazyka MSIL (Microsoft Intermediate Language) funkce. Pokud je rámec zásobníku aktivní, je tato adresa další instrukcí, která se má provést. Pokud není rámec zásobníku aktivní, jedná se o další instrukci, která se má provést, když se rámec zásobníku znovu aktivuje.  
  
 Pokud je tento rámec kompilovaným snímkem just-in-time (JIT), hodnota ukazatele na instrukci bude určena mapováním zpět od skutečného nativního ukazatele instrukcí, takže hodnota může být pouze přibližná.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
