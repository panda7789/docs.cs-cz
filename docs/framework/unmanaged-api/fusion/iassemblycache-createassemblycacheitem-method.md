---
title: IAssemblyCache::CreateAssemblyCacheItem – metoda
ms.date: 03/30/2017
api_name:
- IAssemblyCache.CreateAssemblyCacheItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::CreateAssemblyCacheItem
helpviewer_keywords:
- IAssemblyCache::CreateAssemblyCacheItem method [.NET Framework fusion]
- CreateAssemblyCacheItem method [.NET Framework fusion]
ms.assetid: 017a7ba5-aaaf-44e2-9cbe-ceebef259df0
topic_type:
- apiref
ms.openlocfilehash: e3e50538bde8fe3509b49e3dbcb031875e6863e5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127122"
---
# <a name="iassemblycachecreateassemblycacheitem-method"></a>IAssemblyCache::CreateAssemblyCacheItem – metoda
Získá odkaz na nový objekt [IAssemblyCacheItem](iassemblycacheitem-interface.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateAssemblyCacheItem (  
    [in]  DWORD dwFlags,  
    [in]  PVOID pvReserved,  
    [out] IAssemblyCacheItem **ppAsmItem,  
    [in, optional] LPCWSTR pszAssemblyName  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwFlags`  
 pro Příznaky definované v Fusion. idl Podporovány jsou následující hodnoty:  
  
- IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)  
  
- IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)  
  
 `pvReserved`  
 pro Vyhrazeno pro budoucí rozšíření. `pvReserved` musí být odkaz s hodnotou null.  
  
 `ppAsmItem`  
 mimo Vrácený ukazatel `IAssemblyCacheItem`.  
  
 `pszAssemblyName`  
 [in, volitelné] Nekanonické páry `name=value` oddělených čárkami.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Fusion. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IAssemblyCache – rozhraní](iassemblycache-interface.md)
- [IAssemblyCacheItem – rozhraní](iassemblycacheitem-interface.md)
