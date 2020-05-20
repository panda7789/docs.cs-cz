---
title: Výčet ILCodeKind
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ILCodeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b91765e4-82db-46f9-a6dc-6b80610276af
topic_type:
- apiref
ms.openlocfilehash: 0586b9e184a0958b978837601db002e035881cbc
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421030"
---
# <a name="ilcodekind-enumeration"></a>Výčet ILCodeKind
[Podporované v .NET Framework 4.5.2 a novějších verzích]  
  
 Poskytuje hodnoty, které určují, jestli má ladicí program přístup k místním proměnným nebo kódu přidanému v profileru ReJIT instrumentace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef enum ILCodeKind {  
   ILCODE_ORIGINAL_IL = 0x1,  
   ILCODE_REJIT_IL = 0x2,  
} ILCodeKind;  
```  
  
## <a name="members"></a>Členové  
  
|Název členu|Popis|  
|-----------------|-----------------|  
|`ILCODE_ORIGINAL_IL`|Ladicí program nemá přístup k informacím z instrumentace ReJIT.|  
|`ILCODE_REJIT_IL`|Ladicí program má přístup k informacím z instrumentace ReJIT.|  
  
## <a name="remarks"></a>Poznámky  
 Člen `ILCodeKind` výčtu může být předán metodám [Enumeratelocalvariablesex –](icordebugilframe4-enumeratelocalvariablesex-method.md) a [getlocalvariableex –](icordebugilframe4-getlocalvariableex-method.md) k určení, zda ladicí program může přistupovat k proměnným přidaným do instrumentace ReJIT profileru a k metodě [getcodeex –](icordebugilframe4-getcodeex-method.md) k určení, zda ladicí program může získat přístup k instrumentované Il.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Ladění výčtů](debugging-enumerations.md)
- [Rozhraní ICorDebugILFrame4](icordebugilframe4-interface.md)
- [ReJIT: Průvodce](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
