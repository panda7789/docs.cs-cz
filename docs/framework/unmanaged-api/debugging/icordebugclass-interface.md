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
ms.openlocfilehash: d7417e8dc193172c77d23fe3fa72c8298d802b5c
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894045"
---
# <a name="icordebugclass-interface"></a>ICorDebugClass – rozhraní

Představuje typ, který může být základní nebo komplexní (tj. definovaný uživatelem). Pokud je typ obecný, představuje `ICorDebugClass` obecný typ bez instance.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetModule – metoda](icordebugclass-getmodule-method.md)|Získá modul, který definuje tuto třídu.|  
|[GetStaticFieldValue – metoda](icordebugclass-getstaticfieldvalue-method.md)|Získá hodnotu zadaného statického pole.|  
|[GetToken – metoda](icordebugclass-gettoken-method.md)|Získá token `TypeDef` metadat pro tuto třídu.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugClass` Rozhraní představuje obecný typ uninstanceed. Rozhraní ICorDebugType představuje obecný typ s instancemi. Například `Hashtable<K, V>` by `ICorDebugClass`představovala, že `Hashtable<Int32, String>` by představoval. `ICorDebugType`  
  
 Neobecné typy jsou reprezentovány v `ICorDebugClass` a `ICorDebugType`. Druhé rozhraní bylo zavedeno ve verzi .NET Framework 2,0, aby bylo možné řešit instance typu.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
