---
title: IAssemblyCache::UninstallAssembly – metoda
ms.date: 03/30/2017
api_name:
- IAssemblyCache.UninstallAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::UninstallAssembly
helpviewer_keywords:
- UninstallAssembly method [.NET Framework fusion]
- IAssemblyCache::UninstallAssembly method [.NET Framework fusion]
ms.assetid: 973b2c44-8dfc-40c1-9035-10f4846627e9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75ef24162adbb653671ed070587e7155fae6b949
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59079107"
---
# <a name="iassemblycacheuninstallassembly-method"></a>IAssemblyCache::UninstallAssembly – metoda
Odinstaluje zadané sestavení z globální mezipaměti sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT UninstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData,  
    [out, optional] ULONG *pulDisposition  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwFlags`  
 [in] Příznaky definované v Fusion.idl.  
  
 `pszAssemblyName`  
 [in] Název sestavení, chcete-li odinstalovat.  
  
 `pRefData`  
 [in] A [fusion_install_reference –](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) strukturu, která obsahuje data o instalaci pro sestavení.  
  
 `pulDisposition`  
 [out, volitelné] Jedna z hodnot dispozice definované v Fusion.idl. Možné hodnoty patří:  
  
-   IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED (1)  
  
-   IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE (2)  
  
-   IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED (3)  
  
-   IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING (4)  
  
-   IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES (5)  
  
-   IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND (6)  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Fusion.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IAssemblyCache – rozhraní](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
