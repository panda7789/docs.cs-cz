---
title: "ICorDebugModuleEnum::Next – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModuleEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModuleEnum::Next
helpviewer_keywords:
- ICorDebugModuleEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 9ff3fcd6-38fe-41f8-bfd3-f0ab6c7d77ca
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 917707135f2159b020d9d3c7afb7d70ae466e3e0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmoduleenumnext-method"></a>ICorDebugModuleEnum::Next – metoda
Získá počet instancí "ICorDebugModule" určeného `celt` z výčtu, počínaje na aktuální pozici.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugModule *modules[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 [v] Počet `ICorDebugModule` instancí, které mají být načteny.  
  
 `modules`  
 [out] Ukazatele, každý z nich odkazuje na pole `ICorDebugModule` objektu.  
  
 `pceltFetched`  
 [out] Ukazatel na počet `ICorDebugModule` instancí vrácených ve skutečnosti. Tato hodnota může být null. Pokud `celt` je jedna.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 
