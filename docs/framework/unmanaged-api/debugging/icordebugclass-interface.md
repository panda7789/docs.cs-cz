---
title: ICorDebugClass Interface1
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
ms.openlocfilehash: d12d952fe540b2ec36d058ae2100f0cf5c8e6bcf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710212"
---
# <a name="icordebugclass-interface1"></a>ICorDebugClass Interface1
Představuje typ, který může být základní nebo komplexní (tj. definovaný uživatelem). Pokud je typ obecný, `ICorDebugClass` představuje obecný typ bez instancí.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetModule – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|Získá modul, který definuje tuto třídu.|  
|[GetStaticFieldValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md)|Získá hodnotu zadané statické pole.|  
|[GetToken – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-gettoken-method.md)|Získá `TypeDef` tokenu metadat pro tuto třídu.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugClass` Rozhraní představuje obecný typ bez instancí. Icordebugtype – rozhraní představuje instanci obecného typu. Například `Hashtable<K, V>` by být reprezentována `ICorDebugClass`, zatímco `Hashtable<Int32, String>` by být reprezentována `ICorDebugType`.  
  
 Neobecné typy jsou reprezentovány obě `ICorDebugClass` a `ICorDebugType`. Druhá možnost rozhraní byla zavedena v rozhraní .NET Framework verze 2.0 k vytvoření instance typu řešení.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
