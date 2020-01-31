---
title: ICorPublish::GetProcess – metoda
ms.date: 03/30/2017
api_name:
- ICorPublish.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::GetProcess
helpviewer_keywords:
- ICorPublish::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorPublish interface [.NET Framework debugging]
ms.assetid: c5143805-2eb7-45b8-85ed-c8fb34df1084
topic_type:
- apiref
ms.openlocfilehash: 0368349e6c6a566cb569738bf3bda40eb9f5de96
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790736"
---
# <a name="icorpublishgetprocess-method"></a>ICorPublish::GetProcess – metoda
Získá instanci [ICorPublishProcess](icorpublishprocess-interface.md) , která představuje proces se zadaným identifikátorem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetProcess(  
    [in] unsigned              pid,   
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pid`  
 pro Identifikátor procesu  
  
 `ppProcess`  
 mimo Ukazatel na adresu `ICorPublishProcess` instance, která představuje proces.  
  
## <a name="remarks"></a>Poznámky  
 `GetProcess` dojde k chybě, pokud proces neexistuje nebo se nejedná o spravovaný proces, který může ladit aktuální uživatel.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorPub. idl, CorPub. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorPublish – rozhraní](icorpublish-interface.md)
