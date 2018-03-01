---
title: "CorDebugNGenPolicy – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- cpp
api_name:
- CorDebugNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugNGenPolicy
helpviewer_keywords:
- CorDebugNgenPolicy enumeration [.NET Framework debugging]
ms.assetid: edb4e4d2-3166-44d4-8b17-bf302f7ea093
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 89767da7178319ed1add3dda0620062893487bfd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugngenpolicy-enumeration"></a>CorDebugNGenPolicy – výčet
Obsahuje hodnotu, která určuje, zda ladicí program načte nativní bitové kopie (NGen) z mezipaměť nativních bitových kopií.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a>Členové  
  
|Název členu|Popis|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|V [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] aplikace, použijte bitových kopií z mezipaměti v místní nativních bitových kopií je zakázána. V aplikace na ploše toto nastavení nemá žádný vliv.|  
  
## <a name="remarks"></a>Poznámky  
 `CorDebugNGENPolicy` Výčet je používán [icordebugprocess5::enablengenpolicy –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) metoda. Zákaz použití bitové kopie z mezipaměti v místní nativních bitových kopií poskytuje pro ladění konzistentního prostředí tím, že zajistí, že ladicí program načte debuggable kompilována bitové kopie místo optimalizované nativní bitové kopie.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
