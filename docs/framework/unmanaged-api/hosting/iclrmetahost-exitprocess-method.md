---
title: ICLRMetaHost::ExitProcess – metoda
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.ExitProcess
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::ExitProcess
helpviewer_keywords:
- ICLRMetaHost::ExitProcess method [.NET Framework hosting]
- ExitProcess method, ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: b4df98cc-4e4e-407b-b8f4-e0076afef3a4
topic_type:
- apiref
ms.openlocfilehash: d8643c54950486b6374045ff83928c8c7fb568a9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140948"
---
# <a name="iclrmetahostexitprocess-method"></a>ICLRMetaHost::ExitProcess – metoda
Pokusí se řádně vypnout všechny načtené běhové moduly a pak proces ukončí. Nahrazuje funkci [CorExitProcess –](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
## <a name="parameters"></a>Parametry  
 `iExitCode`  
 pro Ukončovací kód procesu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda se nikdy nevrátí, takže vrácená hodnota je nedefinovaná.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRMetaHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
