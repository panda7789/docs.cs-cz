---
title: ICorDebugInternalFrame2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2
helpviewer_keywords:
- ICorDebugInternalFrame2 interface [.NET Framework debugging]
ms.assetid: d4755569-85b8-4ff4-bf50-0e608e76429f
topic_type:
- apiref
ms.openlocfilehash: 9e333d71505a055cfe27df2c79a102c939bafc9d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788480"
---
# <a name="icordebuginternalframe2-interface"></a>ICorDebugInternalFrame2 – rozhraní
Obsahuje informace o vnitřních rámečcích, včetně adresy zásobníku a pozice ve vztahu k ICorDebugFrame objektům.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetFrameAddress – metoda](icordebuginternalframe2-getframeaddress-method.md)|Vrátí adresu zásobníku interního rámce.|  
|[IsCloserToLeaf – metoda](icordebuginternalframe2-isclosertoleaf-method.md)|Kontroluje, zda je vnitřní rámec `this` blíž k listu, než je zadaný objekt ICorDebugFrame.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní rozšiřuje rozhraní ICorDebugInternalFrame.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
- [Ladění](index.md)
