---
title: ICorDebugAppDomain3 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3
helpviewer_keywords:
- ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 875ef5be-c1e7-4d95-97e9-d3a667aeaba0
topic_type:
- apiref
ms.openlocfilehash: 1aaccb37ec61ed1ba6a7e6e1f508704973117cca
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784887"
---
# <a name="icordebugappdomain3-interface"></a>ICorDebugAppDomain3 – rozhraní
Poskytuje metody pro načtení informací o spravovaných reprezentace prostředí Windows Runtime typů, které jsou aktuálně načteny v doméně aplikace. Toto rozhraní je rozšířením rozhraní ICorDebugAppDomain a ICorDebugAppDomain2.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ICorDebugAppDomain3::GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md)|Získá enumerátor pro všechny typy prostředí Windows Runtime v mezipaměti.|  
|[ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs](icordebugappdomain3-getcachedwinrttypesforiids-method.md)|Načte enumerátor pro prostředí Windows Runtime typy v mezipaměti aplikace na základě jejich identifikátorů rozhraní.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní je určeno pro použití ladicím programem ve spojení se voláním vyhodnocení funkce pro `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`. Když metoda načte identifikátory rozhraní podporované objektem prostředí Windows Runtime serveru, ladicí program může použít metody definované v tomto rozhraní k namapování na spravované typy, které odpovídají těmto rozhraním.  
  
 Chcete-li načíst instanci tohoto rozhraní, spusťte `QueryInterface` v instanci rozhraní ICorDebugAppDomain nebo ICorDebugAppDomain2.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** prostředí Windows Runtime  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
