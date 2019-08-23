---
title: ICorDebugClass – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass
helpviewer_keywords:
- ICorDebugClass interface [.NET Framework debugging]
ms.assetid: 03a6facb-f12f-49be-9839-e73b9c791cd5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc5099af23a2b706694bfcb655d295607c97ea8a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969269"
---
# <a name="icordebugclass-interface"></a>ICorDebugClass – rozhraní

Představuje typ, který může být základní nebo komplexní (tj. definovaný uživatelem). Pokud je typ obecný, představuje `ICorDebugClass` obecný typ bez instance.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetModule – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|Získá modul, který definuje tuto třídu.|  
|[GetStaticFieldValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md)|Získá hodnotu zadaného statického pole.|  
|[GetToken – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-gettoken-method.md)|Získá token `TypeDef` metadat pro tuto třídu.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugClass` Rozhraní představuje obecný typ uninstanceed. Rozhraní ICorDebugType představuje obecný typ s instancemi. Například `Hashtable<K, V>` by `Hashtable<Int32, String>` představovala `ICorDebugClass` ,`ICorDebugType`že by představoval.  
  
 Neobecné typy jsou reprezentovány v `ICorDebugClass` a `ICorDebugType`. Druhé rozhraní bylo zavedeno ve verzi .NET Framework 2,0, aby bylo možné řešit instance typu.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** CorDebug. idl, CorDebug. h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
