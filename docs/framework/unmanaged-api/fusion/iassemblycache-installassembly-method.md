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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd420f0f166b0b17e5fbaf08d6bedd6651188b1c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778751"
---
# <a name="iassemblycacheinstallassembly-method"></a><span data-ttu-id="b3b9e-102">IAssemblyCache::InstallAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="b3b9e-102">IAssemblyCache::InstallAssembly Method</span></span>
<span data-ttu-id="b3b9e-103">Nainstaluje zadané sestavení v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="b3b9e-103">Installs the specified assembly in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3b9e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3b9e-104">Syntax</span></span>  
  
```cpp  
HRESULT InstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszManifestFilePath,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3b9e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b3b9e-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="b3b9e-106">[in] Příznaky definované v Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="b3b9e-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="b3b9e-107">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="b3b9e-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="b3b9e-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="b3b9e-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
- <span data-ttu-id="b3b9e-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0X00000002)</span><span class="sxs-lookup"><span data-stu-id="b3b9e-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pszManifestFilePath`  
 <span data-ttu-id="b3b9e-110">[in] Cesta k manifestu pro sestavení určené k instalaci.</span><span class="sxs-lookup"><span data-stu-id="b3b9e-110">[in] The path to the manifest for the assembly to install.</span></span>  
  
 `pRefData`  
 <span data-ttu-id="b3b9e-111">[in] A [fusion_install_reference –](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) strukturu, která obsahuje data pro instalaci.</span><span class="sxs-lookup"><span data-stu-id="b3b9e-111">[in] A [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure that contains data for the installation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3b9e-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b3b9e-112">Requirements</span></span>  
 <span data-ttu-id="b3b9e-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3b9e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3b9e-114">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="b3b9e-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b3b9e-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3b9e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3b9e-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3b9e-116">See also</span></span>

- [<span data-ttu-id="b3b9e-117">IAssemblyCache – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b3b9e-117">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
