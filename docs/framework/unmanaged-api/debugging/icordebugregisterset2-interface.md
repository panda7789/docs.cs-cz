---
title: "ICorDebugRegisterSet2 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet2
helpviewer_keywords: ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: d7fbccbf-3b6b-4db8-a96d-768e1cb6b1a6
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 26967f50ded62f935a705c25eed58314b77bedd8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugregisterset2-interface"></a>ICorDebugRegisterSet2 – rozhraní
Rozšiřuje možnosti [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) rozhraní pro hardwarových platforem, které mají víc než 64 Registry.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Getregisters – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregisters-method.md)|Získá hodnotu každý registrace (v počítači, který je aktuálně provádění kódu), který je určen podle bit masky.|  
|[Getregistersavailable – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregistersavailable-method.md)|Získá pole bajtů, které poskytuje rastrový obrázek k dispozici registrů.|  
|[Setregisters – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-setregisters-method.md)|Není implementováno v rozhraní .NET Framework verze 2.0.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Ladění v rozhraní](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ICorDebugRegisterSet – rozhraní rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
