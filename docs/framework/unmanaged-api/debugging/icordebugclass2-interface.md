---
title: ICorDebugClass2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugClass2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2
helpviewer_keywords:
- ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 5416de70-43f2-4cdf-a11f-d570759c9c0c
topic_type:
- apiref
ms.openlocfilehash: ff15297eb479f7474c9f07123a29263fb4da3205
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893978"
---
# <a name="icordebugclass2-interface"></a>ICorDebugClass2 – rozhraní

Představuje obecnou třídu nebo třídu s parametrem metody typu <xref:System.Type>. Toto rozhraní rozšiřuje [ICorDebugClass](icordebugclass-interface.md).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetParameterizedType – metoda](icordebugclass2-getparameterizedtype-method.md)|Získá deklaraci typu pro tuto třídu.|  
|[SetJMCStatus – metoda](icordebugclass2-setjmcstatus-method.md)|Pro každou metodu této třídy nastaví hodnotu, která označuje, zda je metoda uživatelem definovaným kódem.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugClass – rozhraní](icordebugclass-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
