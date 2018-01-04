---
title: "ICorDebugModule::EnableJITDebugging – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.EnableJITDebugging
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::EnableJITDebugging
helpviewer_keywords:
- ICorDebugModule::EnableJITDebugging method [.NET Framework debugging]
- EnableJITDebugging method [.NET Framework debugging]
ms.assetid: 0a65e2a4-5bb6-496c-ae6f-40474426b5a6
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7a699f32d8ec4b2418c6af815c22f35470bede3d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmoduleenablejitdebugging-method"></a>ICorDebugModule::EnableJITDebugging – metoda
Určuje, zda kompilátoru za běhu (JIT) uchovává informace o ladění pro metod v rámci tohoto modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bTrackJITInfo`  
 [v] Nastavte hodnotu `true` povolení JIT kompilátoru zachovat informace o mapování mezi verze Microsoft (MSIL intermediate language) a verzí kompilována jednotlivých metod v tomto modulu.  
  
 `bAllowJitOpts`  
 [v] Nastavte hodnotu `true` povolení JIT kompilátoru pro generování kódu s určitým optimalizace JIT specifické pro ladění.  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení pro všechny moduly, které jsou načteny, když je aktivní ladicí program je povoleno ladění JIT. Prostřednictvím kódu programu povolení nebo zakázání nastavení přepsání globální nastavení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
