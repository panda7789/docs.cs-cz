---
title: ICorDebugCode2::GetCodeChunks – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCodeChunks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCodeChunks
helpviewer_keywords:
- GetCodeChunks method [.NET Framework debugging]
- ICorDebugCode2::GetCodeChunks method [.NET Framework debugging]
ms.assetid: 210a2f02-2678-4555-bc4a-78a0408764c8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf8bc747f643819eb82448b4ad6b7fab696c9c91
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572497"
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
 [in] Velikost `chunks` pole.  
  
 `pcnumChunks`  
 [out] Počet bloků, které jsou vráceny v `chunks` pole.  
  
 `chunks`  
 [out] Pole struktur "codechunkinfo –", z nichž každý představuje jediný neodkazovaný blok kódu. Pokud hodnota `cbufSize` je 0, tento parametr může mít hodnotu null.  
  
## <a name="remarks"></a>Poznámky  
 Bloky kódu nikdy se překrývají a jejich brzo bude následovat pořadí, ve kterém jsou by mít byla zřetězených podle [icordebugcode::getcode –](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md). Objekt Microsoft intermediate language (MSIL) kódu v rozhraní .NET Framework verze 2.0 bude tvořit jeden blok.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

