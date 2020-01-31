---
title: ICorDebugAppDomain – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain
helpviewer_keywords:
- ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: be7ae711-1217-4a44-be40-166e29641b77
topic_type:
- apiref
ms.openlocfilehash: da7c0fb472df89d94fa702a13eff968a4c7e68e3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785031"
---
# <a name="icordebugappdomain-interface"></a>ICorDebugAppDomain – rozhraní

Poskytuje metody pro ladění domén aplikace. Toto rozhraní je podtřídou třídy ICorDebugController.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Attach – metoda](icordebugappdomain-attach-method.md)|Připojí ladicí program k doméně aplikace.|  
|[EnumerateAssemblies – metoda](icordebugappdomain-enumerateassemblies-method.md)|Získá enumerátor pro sestavení v doméně aplikace.|  
|[EnumerateBreakpoints – metoda](icordebugappdomain-enumeratebreakpoints-method.md)|Získá enumerátor pro všechny aktivní zarážky v doméně aplikace.|  
|[EnumerateSteppers – metoda](icordebugappdomain-enumeratesteppers-method.md)|Získá enumerátor pro všechny aktivní prvky krokování v doméně aplikace.|  
|[GetId – metoda](icordebugappdomain-getid-method.md)|Získá jedinečné ID domény aplikace.|  
|[GetModuleFromMetaDataInterface – metoda](icordebugappdomain-getmodulefrommetadatainterface-method.md)|Získá objekt ICorDebugModule se zadaným rozhraním metadat.|  
|[GetName – metoda](icordebugappdomain-getname-method.md)|Získá název domény aplikace.|  
|[GetObject – metoda](icordebugappdomain-getobject-method.md)|Načte ukazatel rozhraní do aplikační domény modulu CLR (Common Language Runtime).|  
|[GetProcess – metoda](icordebugappdomain-getprocess-method.md)|Získá proces obsahující doménu aplikace.|  
|[IsAttached – metoda](icordebugappdomain-isattached-method.md)|Určuje, zda je ladicí program připojen k doméně aplikace.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
