---
title: 'ICorDebugVariableHome:: getregister – metoda'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetRegister
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetRegister
helpviewer_keywords:
- ICorDebugVariableHome::GetRegister method [.NET Framework debugging]
- GetRegister method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: a5eecd7b-b04c-4266-bff2-7c8771d519a8
topic_type:
- apiref
ms.openlocfilehash: 396dd9c017fca6dc7037b43355ba7f726d7390ea
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790980"
---
# <a name="icordebugvariablehomegetregister-method"></a>ICorDebugVariableHome:: getregister – metoda
Získá registr, který obsahuje proměnnou s typem umístění `VLT_REGISTER`a základní registr pro proměnnou s typem umístění `VLT_REGISTER_RELATIVE`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pRegister`  
 mimo Hodnota výčtu CorDebugRegister –, která označuje registr pro proměnnou s typem umístění `VLT_REGISTER`a základní registr pro proměnnou s typem umístění `VLT_REGISTER_RELATIVE`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací následující hodnoty:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Proměnná je v registru označeném argumentem `pRegister`.|  
|`E_FAIL`|Proměnná není v registru ani v relativním umístění registru.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [VariableLocationType – výčet](variablelocationtype-enumeration.md)
- [ICorDebugVariableHome – rozhraní](icordebugvariablehome-interface.md)
