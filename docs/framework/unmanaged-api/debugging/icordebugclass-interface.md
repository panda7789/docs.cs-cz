---
title: ICorDebugClass Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugClass
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugClass
helpviewer_keywords: ICorDebugClass interface [.NET Framework debugging]
ms.assetid: 03a6facb-f12f-49be-9839-e73b9c791cd5
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 79e93a44f2cc532286a7e9b01fa32292a4e1c69a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugclass-interface1"></a>ICorDebugClass Interface1
Představuje typ, který může být základní nebo komplexní (tj. definovaný uživatelem). Pokud je typ Obecné, `ICorDebugClass` představuje bez instancí obecného typu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Getmodule – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|Získá modul, který definuje tuto třídu.|  
|[Getstaticfieldvalue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md)|Získá hodnotu zadaného pole statické.|  
|[Gettoken – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-gettoken-method.md)|Získá `TypeDef` token metadata pro tuto třídu.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugClass` Rozhraní představuje bez instancí obecného typu. ICorDebugType rozhraní představuje instanci obecného typu. Například `Hashtable<K, V>` by být reprezentovaná `ICorDebugClass`, zatímco `Hashtable<Int32, String>` by být reprezentovaná `ICorDebugType`.  
  
 Jak jsou reprezentována non obecné typy `ICorDebugClass` a `ICorDebugType`. Rozhraní pozdější byla zavedena v rozhraní .NET Framework verze 2.0, jak nakládat s vytvoření instance typu.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Ladění v rozhraní](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
