---
title: IGCThreadControl::SuspensionEnding – metoda
ms.date: 03/30/2017
api_name:
- IGCThreadControl.SuspensionEnding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SuspensionEnding
helpviewer_keywords:
- IGCThreadControl::SuspensionEnding method [.NET Framework hosting]
- SuspensionEnding method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 70814265-c734-4ddc-9502-fe8b28d2b414
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d0986645a8ce4076c27f39f2ae8004ef20bb4bdb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="igcthreadcontrolsuspensionending-method"></a>IGCThreadControl::SuspensionEnding – metoda
Upozorní hostitele, že je modul runtime obnovování vláken po uvolnění paměti nebo jiných pozastavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `Generation`  
 [v] Generování, na kterém byla provedena uvolnění paměti.  
  
## <a name="remarks"></a>Poznámky  
 Není změnit plán žádné podprocesy během `SuspensionEnding` zpětného volání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IGCThreadControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
