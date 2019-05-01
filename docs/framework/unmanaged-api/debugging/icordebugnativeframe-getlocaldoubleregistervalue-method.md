---
title: ICorDebugNativeFrame::GetLocalDoubleRegisterValue – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalDoubleRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue method [.NET Framework debugging]
- GetLocalDoubleRegisterValue method [.NET Framework debugging]
ms.assetid: 1f838215-ac8a-434f-8ce6-03021d3098d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13e1e3369c4e7a185c2167facc8514b5cfc85a85
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994692"
---
# <a name="icordebugnativeframegetlocaldoubleregistervalue-method"></a>ICorDebugNativeFrame::GetLocalDoubleRegisterValue – metoda
Získá hodnotu argumentu nebo místní proměnná, která je uložena v dvě zadané registrů pro tuto nativní rámce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetLocalDoubleRegisterValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CorDebugRegister   lowWordReg,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `highWordReg`  
 [in] Hodnota, která určuje do registru, které obsahují slovo vysoké hodnoty výčtu "cordebugregister –".  
  
 `lowWordReg`  
 [in] Hodnota `CorDebugRegister` výčet, který určuje do registru, které obsahují slovo nízké hodnoty.  
  
 `cbSigBlob`  
 [in] Celé číslo, které určuje velikost podpisu binární metadat, který se odkazuje `pvSigBlob` parametru.  
  
 `pvSigBlob`  
 [in] A `PCCOR_SIGNATURE` hodnotu, která odkazuje na podpis metadat binární typ hodnoty.  
  
 `ppValue`  
 [out] Ukazatel na adresu "ICorDebugValue" objekt představující načtené hodnoty uložené v zadané registrů.  
  
## <a name="remarks"></a>Poznámky  
 `GetLocalDoubleRegisterValue` Metodu je možné použít ve službě je nativní rámec nebo just-in-time (JIT)-zkompilován rámce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
