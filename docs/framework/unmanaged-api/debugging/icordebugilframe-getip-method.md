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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a7b8985e7580282d0e38205f9b1d6078f86cee6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988608"
---
# <a name="icordebugilframegetip-method"></a>ICorDebugILFrame::GetIP – metoda
Získá hodnotu ukazatele na instrukci a bitová kombinace hodnotu, která popisuje, jak byla získána hodnota ukazatele na instrukci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,   
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pnOffset`  
 [out] Hodnota ukazatele na instrukci.  
  
 `pMappingResult`  
 [out] Ukazatel na bitová kombinace hodnot výčtu cordebugmappingresult –, které popisují, jak byla získána hodnota ukazatele na instrukci.  
  
## <a name="remarks"></a>Poznámky  
 Hodnota ukazatele na instrukci je odsazení rámce zásobníku do kód funkce Microsoft intermediate language (MSIL). Pokud je aktivní rámec zásobníku, tato adresa je další instrukci k provedení. Pokud není aktivní rámec zásobníku, tato adresa je další instrukci má provést, když se znovu aktivuje rámce zásobníku.  
  
 Pokud je tento rámeček blok kompilované just-in-time (JIT), hodnota ukazatele na instrukci určí zpětné mapování z ukazatele na instrukci skutečná nativní, takže hodnota může být pouze přibližná.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
