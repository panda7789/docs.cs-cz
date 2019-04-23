---
title: ICorDebugNativeFrame2::IsChild – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.IsChild Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::IsChild
helpviewer_keywords:
- IsChild method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsChild method [.NET Framework debugging]
ms.assetid: 9e2aae09-49cb-4fbd-81e5-e29cd864a88b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9503c12da9e98fbd43f3904aad25c5d10655cec2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59075558"
---
# <a name="icordebugnativeframe2ischild-method"></a>ICorDebugNativeFrame2::IsChild – metoda
Určuje, zda aktuální rámec je podřízený blok.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT IsChild([out] BOOL * pIsChild);  
```  
  
## <a name="parameters"></a>Parametry  
 `pIsChild`  
 [out] Logická hodnota určující, zda je aktuální rámec podřízený blok.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Stav podřízeného byla úspěšně vrácena.|  
|E_FAIL|Stav podřízeného nebylo možné vrátit.|  
|E_INVALIDARG|`pIsChild` má hodnotu null.|  
  
## <a name="exceptions"></a>Výjimky  
  
## <a name="remarks"></a>Poznámky  
 `IsChild` Vrátí metoda `true` Pokud orámovat objekt, na kterém je zavolat metodu je podřízeným prvkem jiného snímku. Pokud tomu tak, [ismatchingparentframe –](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) metodu ke kontrole, zda blok je jeho nadřazeným prvkem.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugNativeFrame2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
