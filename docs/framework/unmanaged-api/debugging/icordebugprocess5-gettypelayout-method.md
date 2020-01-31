---
title: ICorDebugProcess5::GetTypeLayout – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeLayout
helpviewer_keywords:
- ICorDebugProcess5::GetTypeLayout method [.NET Framework debugging]
- GetTypeLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: bd62f5d1-e874-41f1-81e5-a29a7572c15d
topic_type:
- apiref
ms.openlocfilehash: 306d881c05c2fcdb15a53a439bfce6eff3afffa8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792316"
---
# <a name="icordebugprocess5gettypelayout-method"></a>ICorDebugProcess5::GetTypeLayout – metoda
Načte informace o rozložení objektu v paměti na základě jeho identifikátoru typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetTypeLayout(    [in] COR_TYPEID id,     [out] COR_TYPE_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a>Parametry  
 `id`  
 pro Token [COR_TYPEID](cor-typeid-structure.md) , který určuje typ, jehož rozložení se požaduje.  
  
 `pLayout`  
 mimo Ukazatel na strukturu [COR_TYPE_LAYOUT](cor-type-layout-structure.md) , která obsahuje informace o rozložení objektu v paměti.  
  
## <a name="remarks"></a>Poznámky  
 Metoda `ICorDebugProcess5::GetTypeLayout` poskytuje informace o objektu na základě jeho [COR_TYPEID](cor-typeid-structure.md), který je vrácen řadou dalších metod [ICorDebugProcess5](icordebugprocess5-interface.md) . Informace jsou poskytovány [COR_TYPE_LAYOUT](cor-type-layout-structure.md) strukturou, která je naplněna metodou.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [COR_TYPE_LAYOUT – struktura](cor-type-layout-structure.md)
- [ICorDebugProcess5 – rozhraní](icordebugprocess5-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
