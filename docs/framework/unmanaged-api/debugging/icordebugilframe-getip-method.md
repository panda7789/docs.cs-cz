---
title: "ICorDebugILFrame::GetIP – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 79b18c6fe15e28b2cec07ef9dfaa06ee295ab42d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframegetip-method"></a>ICorDebugILFrame::GetIP – metoda
Získá hodnotu ukazatel instrukce a bitovou kombinaci hodnotu, která popisuje, jak byla získána hodnota ukazatele instrukcí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,   
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pnOffset`  
 [out] Hodnota ukazatele instrukcí.  
  
 `pMappingResult`  
 [out] Ukazatel na bitová kombinace hodnot výčtu CorDebugMappingResult, které popisují, jak byla získána hodnota ukazatele instrukcí.  
  
## <a name="remarks"></a>Poznámky  
 Ukazatel instrukce hodnotu rámce zásobníku odsazení kód funkce Microsoft (MSIL intermediate language). Pokud rámce zásobníku je aktivní, tato adresa se další pokyny k provedení. Pokud rámce zásobníku není aktivní, tato adresa se další pokyny k provedení při opětovné aktivaci rámce zásobníku.  
  
 Pokud je tento rámeček rámeček kompilované za běhu (JIT), hodnota ukazatele instrukce určí mapování zpětné z ukazatel na skutečné nativní instrukce, takže hodnota může být jen přibližné.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
