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
ms.openlocfilehash: 7ac588591222a1abbc7b99ec7e973284c055f95e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784172"
---
# <a name="icordebugclass-interface"></a>ICorDebugClass – rozhraní

Představuje typ, který může být základní nebo komplexní (tj. definovaný uživatelem). Pokud je typ obecný, `ICorDebugClass` představuje obecný typ bez instancí.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetModule – metoda](icordebugclass-getmodule-method.md)|Získá modul, který definuje tuto třídu.|  
|[GetStaticFieldValue – metoda](icordebugclass-getstaticfieldvalue-method.md)|Získá hodnotu zadaného statického pole.|  
|[GetToken – metoda](icordebugclass-gettoken-method.md)|Získá token metadat `TypeDef` pro tuto třídu.|  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní `ICorDebugClass` představuje obecný typ uninstanceed. Rozhraní ICorDebugType představuje obecný typ s instancemi. Například `Hashtable<K, V>` by představoval `ICorDebugClass`, zatímco `Hashtable<Int32, String>` by představoval `ICorDebugType`.  
  
 Neobecné typy jsou reprezentovány `ICorDebugClass` i `ICorDebugType`. Druhé rozhraní bylo zavedeno ve verzi .NET Framework 2,0, aby bylo možné řešit instance typu.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
