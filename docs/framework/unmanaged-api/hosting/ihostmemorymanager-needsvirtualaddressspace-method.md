---
title: IHostMemoryManager::NeedsVirtualAddressSpace – metoda
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.NeedsVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace method [.NET Framework hosting]
- NeedsVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: 71f0eab5-0170-46f8-9f88-1df5abdeb34a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 87c97a678fce4c25a113670a4668515a898e5251
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a>IHostMemoryManager::NeedsVirtualAddressSpace – metoda
Aby modul CLR (CLR) bude pokus o použití zadaná paměťová upozorní hostitele.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `startAddress`  
 [v] Počáteční adresa paměti.  
  
 `size`  
 [v] Velikost v bajtech paměti.  
  
## <a name="remarks"></a>Poznámky  
 `NeedsVirtualAddressSpace` Metoda je metoda zpětného volání a musí být implementována zapisovačem hostitelskou aplikaci. Je volána metodou modulu CLR.  
  
 Pokud hostitel nechce CLR použití zadané paměti, může vrátit E_OUTOFMEMORY HRESULT.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IHostMemoryManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
