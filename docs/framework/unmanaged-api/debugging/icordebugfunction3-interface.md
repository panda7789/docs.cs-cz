---
title: Rozhraní ICorDebugFunction3
ms.date: 03/30/2017
api_name:
- ICorDebugFunction3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b22717b9-ead5-4eea-887e-789b52d613dc
topic_type:
- apiref
ms.openlocfilehash: 71aa482cc2268da17f1376d8c305dd6a818d92d0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213163"
---
# <a name="icordebugfunction3-interface"></a>Rozhraní ICorDebugFunction3
[Podporované v .NET Framework 4.5.2 a novějších verzích]  
  
 Logicky rozšiřuje rozhraní ICorDebugFunction a poskytuje přístup k kódu z požadavku ReJIT.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetActiveReJitRequestILCode – metoda](icordebugfunction3-getactiverejitrequestilcode-method.md)|Získá ukazatel rozhraní na [ICorDebugILCode](icordebugilcode-interface.md) , který obsahuje Il z aktivní žádosti ReJIT.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
- [ReJIT: Průvodce](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
