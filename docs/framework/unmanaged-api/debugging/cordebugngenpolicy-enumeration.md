---
title: CorDebugNGenPolicy – výčet
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca922d8b582c0608073d4fd0ba986167ae470e34
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61599505"
---
# <a name="cordebugngenpolicy-enumeration"></a>CorDebugNGenPolicy – výčet
Poskytuje hodnotu, která určuje, zda ladicí program načítá nativní bitové kopie (NGen) z mezipaměti nativních bitových kopií.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a>Členové  
  
|Název členu|Popis|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|V [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] aplikaci, používání imagí z mezipaměti nativní bitové kopie místní aplikace je zakázaná. V desktopové aplikaci toto nastavení nemá žádný vliv.|  
  
## <a name="remarks"></a>Poznámky  
 `CorDebugNGENPolicy` Výčet je používán [icordebugprocess5::enablengenpolicy –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) metody. Zákaz použití obrázky z místní mezipaměti zajišťující konzistentní možnosti ladění tím, že zajišťuje, že ladicí program načte laditelné zkompilovaný pomocí kompilátoru JIT obrázky místo optimalizované nativní bitové kopie.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
