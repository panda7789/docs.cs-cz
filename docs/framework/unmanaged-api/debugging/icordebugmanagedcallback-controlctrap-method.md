---
title: ICorDebugManagedCallback::ControlCTrap – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ControlCTrap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ControlCTrap
helpviewer_keywords:
- ICorDebugManagedCallback::ControlCTrap method [.NET Framework debugging]
- ControlCTrap method [.NET Framework debugging]
ms.assetid: 0500854e-2121-43d9-a028-64312da35258
topic_type:
- apiref
ms.openlocfilehash: 33a68d11a8d17e46533b4f83bbf87aafe171e612
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212396"
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a>ICorDebugManagedCallback::ControlCTrap – metoda
Upozorní ladicí program, že kombinace kláves CTRL + C je zachycena v procesu, který je právě laděn.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pProcess`  
 pro Ukazatel na objekt ICorDebugProcess, který představuje proces, ve kterém je nachycena kombinace kláves CTRL + C.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Ladicí program zpracuje soutisk v kombinaci kláves CTRL + C.|  
|S_FALSE|Ladicí program nebude zpracovávat depeši CTRL + C.|  
  
## <a name="remarks"></a>Poznámky  
 Všechny domény aplikace v rámci procesu jsou pro toto zpětné volání zastaveny.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugManagedCallback – rozhraní](icordebugmanagedcallback-interface.md)
