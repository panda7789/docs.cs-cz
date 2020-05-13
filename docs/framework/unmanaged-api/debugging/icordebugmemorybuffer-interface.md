---
title: ICorDebugMemoryBuffer – rozhraní
ms.date: 03/30/2017
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
ms.openlocfilehash: 60f3b0c3230c524ca7d308d3cb80e50b0693715d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212331"
---
# <a name="icordebugmemorybuffer-interface"></a>ICorDebugMemoryBuffer – rozhraní
Představuje vyrovnávací paměť v paměti.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetSize – metoda](icordebugmemorybuffer-getsize-method.md)|Získá velikost vyrovnávací paměti v bajtech.|  
|[GetStartAddress – metoda](icordebugmemorybuffer-getstartaddress-method.md)|Získá počáteční adresu vyrovnávací paměti.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní je dostupné jenom pro .NET Native. Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
