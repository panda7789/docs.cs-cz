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
ms.openlocfilehash: 7199fbc0c8760354269a50b647952729860c805b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697547"
---
# <a name="iassemblycacheinstallassembly-method"></a><span data-ttu-id="b1d10-102">IAssemblyCache::InstallAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="b1d10-102">IAssemblyCache::InstallAssembly Method</span></span>
<span data-ttu-id="b1d10-103">Nainstaluje zadané sestavení v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="b1d10-103">Installs the specified assembly in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1d10-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1d10-104">Syntax</span></span>  
  
```  
HRESULT InstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszManifestFilePath,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1d10-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b1d10-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="b1d10-106">[in] Příznaky definované v Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="b1d10-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="b1d10-107">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="b1d10-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="b1d10-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="b1d10-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
- <span data-ttu-id="b1d10-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0X00000002)</span><span class="sxs-lookup"><span data-stu-id="b1d10-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pszManifestFilePath`  
 <span data-ttu-id="b1d10-110">[in] Cesta k manifestu pro sestavení určené k instalaci.</span><span class="sxs-lookup"><span data-stu-id="b1d10-110">[in] The path to the manifest for the assembly to install.</span></span>  
  
 `pRefData`  
 <span data-ttu-id="b1d10-111">[in] A [fusion_install_reference –](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) strukturu, která obsahuje data pro instalaci.</span><span class="sxs-lookup"><span data-stu-id="b1d10-111">[in] A [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure that contains data for the installation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1d10-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b1d10-112">Requirements</span></span>  
 <span data-ttu-id="b1d10-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1d10-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1d10-114">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="b1d10-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b1d10-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1d10-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1d10-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1d10-116">See also</span></span>

- [<span data-ttu-id="b1d10-117">IAssemblyCache – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b1d10-117">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
