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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0288c9912125e20cfb9f9aaaac5003ae9e0b51e9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779790"
---
# <a name="iclrmetahostexitprocess-method"></a>ICLRMetaHost::ExitProcess – metoda
Pokusí se korektně vypnout všechny načtené moduly runtime a poté ukončí proces. Nahrazuje [corexitprocess –](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
## <a name="parameters"></a>Parametry  
 `iExitCode`  
 [in] Ukončovací kód procesu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda nikdy nevrátí, tak její návratová hodnota není definována.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRMetaHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
