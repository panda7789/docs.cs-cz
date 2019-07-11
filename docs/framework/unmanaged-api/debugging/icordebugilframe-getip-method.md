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
ms.openlocfilehash: 4d7eca3c2825707c9190436377bba7e4bb0d5447
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757970"
---
# <a name="icordebugilframegetip-method"></a>ICorDebugILFrame::GetIP – metoda
Získá hodnotu ukazatele na instrukci a bitová kombinace hodnotu, která popisuje, jak byla získána hodnota ukazatele na instrukci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
