---
title: ICLRDebugManager::GetDacl – metoda
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.GetDacl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::GetDacl
helpviewer_keywords:
- GetDacl method [.NET Framework hosting]
- ICLRDebugManager::GetDacl method [.NET Framework hosting]
ms.assetid: 7115e920-aaff-440a-824e-39497139c6f6
topic_type:
- apiref
ms.openlocfilehash: 933edf734a0e02b4ac9c88d9f193277d963adada
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615793"
---
# <a name="iclrdebugmanagergetdacl-method"></a>ICLRDebugManager::GetDacl – metoda
Tato metoda není implementována.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetDacl (  
    [out] PACL* ppacl  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppacl`  
 mimo Ukazatel rozhraní na seznam Access Control (ACL).  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|E_NOTIMPL|Metoda není implementována.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRControl – rozhraní](iclrcontrol-interface.md)
- [ICLRDebugManager – rozhraní](iclrdebugmanager-interface.md)
- [SetDacl – metoda](iclrdebugmanager-setdacl-method.md)
- [IHostControl – rozhraní](ihostcontrol-interface.md)
