---
title: IAssemblyCache::InstallAssembly – metoda
ms.date: 03/30/2017
api_name:
- IAssemblyCache.InstallAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::InstallAssembly
helpviewer_keywords:
- InstallAssembly method [.NET Framework fusion]
- IAssemblyCache::InstallAssembly method [.NET Framework fusion]
ms.assetid: 33c1d269-c85e-4cb1-b0e6-1c510c8fb5fa
topic_type:
- apiref
ms.openlocfilehash: ec08c786992996ec6f44038ff3c1596cada88484
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127073"
---
# <a name="iassemblycacheinstallassembly-method"></a>IAssemblyCache::InstallAssembly – metoda
Nainstaluje zadané sestavení do globální mezipaměti sestavení (GAC).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT InstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszManifestFilePath,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwFlags`  
 pro Příznaky definované v Fusion. idl Podporovány jsou následující hodnoty:  
  
- IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)  
  
- IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)  
  
 `pszManifestFilePath`  
 pro Cesta k manifestu pro sestavení, které má být nainstalováno.  
  
 `pRefData`  
 pro Struktura [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) , která obsahuje data pro instalaci.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Fusion. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IAssemblyCache – rozhraní](iassemblycache-interface.md)
