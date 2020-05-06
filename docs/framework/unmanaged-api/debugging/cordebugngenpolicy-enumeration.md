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
ms.openlocfilehash: 036d3f12b38c19259fefaba674d0f9025a58d688
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795752"
---
# <a name="cordebugngenpolicy-enumeration"></a>CorDebugNGenPolicy – výčet
Poskytuje hodnotu, která určuje, zda ladicí program načte nativní bitové kopie (NGen) z mezipaměti nativních imagí.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a>Členové  
  
|Název členu|Popis|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|V aplikaci pro Windows 8. x Store je použití imagí z místní mezipaměti nativních imagí zakázané. V desktopové aplikaci nemá toto nastavení žádný vliv.|  
  
## <a name="remarks"></a>Poznámky  
 `CorDebugNGENPolicy` Výčet je používán metodou [ICorDebugProcess5:: EnableNGENPolicy –](icordebugprocess5-enablengenpolicy-method.md) . Zakázání použití imagí z místní mezipaměti nativních imagí poskytuje konzistentní možnosti ladění tím, že zajistí, že ladicí program načte místo optimalizovaných nativních imagí laditelné obrázky kompilované JIT.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Ladění výčtů](debugging-enumerations.md)
