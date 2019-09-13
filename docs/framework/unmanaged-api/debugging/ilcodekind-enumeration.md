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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fea08331fffb85c91721d60764bae8bfe8b30e27
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928806"
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
 Člen `ILCodeKind` výčtu může být předán metodám [enumeratelocalvariablesex –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md) a [getlocalvariableex –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md) , aby bylo možné určit, zda ladicí program může přistupovat k proměnným přidaným do instrumentace ReJIT profileru a k [ Metoda Getcodeex –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md) k určení, zda ladicí program může získat přístup k instrumentované Il.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** CorDebug. idl, CorDebug. h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [ICorDebugILFrame4 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [ReJIT: Průvodce postupy](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)
