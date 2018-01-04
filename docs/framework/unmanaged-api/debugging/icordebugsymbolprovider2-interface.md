---
title: "ICorDebugSymbolProvider2 rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 1c9c3d92-f0de-4d4d-87f1-0c702a4808af
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7666b8d64b689d3640594f07614be97b72e85a8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovider2-interface"></a>ICorDebugSymbolProvider2 rozhraní
Logicky rozšiřuje [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) rozhraní k načtení informací o symbolu další ladění.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetFrameProps – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getframeprops-method.md)|Vrátí metodu počáteční relativní virtuální adresa metodu a nadřazeného rámce zadaný relativní virtuální adresu kódu.|  
|[GetGenericDictionaryInfo – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getgenericdictionaryinfo-method.md)|Načte mapu obecné slovníku.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Toto rozhraní je k dispozici s .NET Native jenom. Pokud budete implementovat toto rozhraní pro scénáře ICorDebug mimo .NET Native, modul CLR bude ignorovat toto rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugSymbolProvider – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
