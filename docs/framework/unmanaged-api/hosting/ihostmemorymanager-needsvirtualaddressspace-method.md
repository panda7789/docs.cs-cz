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
ms.openlocfilehash: bb13c7329c558aa92ec65237aa8a9963c82fe1dc
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804515"
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a>IHostMemoryManager::NeedsVirtualAddressSpace – metoda
Upozorňuje hostitele, že se bude modul CLR (Common Language Runtime) pokoušet použít zadanou paměť.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `startAddress`  
 pro Počáteční adresa paměti.  
  
 `size`  
 pro Velikost paměti (v bajtech).  
  
## <a name="remarks"></a>Poznámky  
 `NeedsVirtualAddressSpace`Metoda je metoda zpětného volání a musí být implementována zapisovačí hostující aplikace. Je volána modulem CLR.  
  
 Pokud hostitel nechce, aby CLR používal zadanou paměť, může vrátit E_OUTOFMEMORY HRESULT.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IHostMemoryManager – rozhraní](ihostmemorymanager-interface.md)
