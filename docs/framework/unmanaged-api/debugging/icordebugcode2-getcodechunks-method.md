---
title: "ICorDebugCode2::GetCodeChunks – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode2.GetCodeChunks
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode2::GetCodeChunks
helpviewer_keywords:
- GetCodeChunks method [.NET Framework debugging]
- ICorDebugCode2::GetCodeChunks method [.NET Framework debugging]
ms.assetid: 210a2f02-2678-4555-bc4a-78a0408764c8
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4b90913f05cc2e0a3e98a5890f76a41eb2eafc6d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcode2getcodechunks-method"></a>ICorDebugCode2::GetCodeChunks – metoda
Získá bloky kódu, ze kterých je tento objekt kódu sestaven.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCodeChunks (  
    [in]  ULONG32     cbufSize,  
    [out] ULONG32     *pcnumChunks,  
    [out, size_is(cbufSize), length_is(*pcnumChunks)]   
        CodeChunkInfo chunks[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cbufSize`  
 [v] Velikost `chunks` pole.  
  
 `pcnumChunks`  
 [out] Číslo, vrátí se v bloků dat `chunks` pole.  
  
 `chunks`  
 [out] Pole "Codechunkinfo –" struktury, z nichž každý představuje jeden blok kódu. Pokud hodnota `cbufSize` je 0, tento parametr může mít hodnotu null.  
  
## <a name="remarks"></a>Poznámky  
 Bloky kódu se nikdy překrývají a jejich bude postupovat podle pořadí, ve kterém se by mít byla zřetězených podle [icordebugcode::getcode –](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md). Objekt Microsoft (MSIL intermediate language) kódu v rozhraní .NET Framework verze 2.0 bude tvoří jeden kód bloku.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 
