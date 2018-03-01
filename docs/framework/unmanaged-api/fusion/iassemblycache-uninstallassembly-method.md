---
title: "IAssemblyCache::UninstallAssembly – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d34b2793de58721c7d4863855106d4b231bccc54
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblycacheuninstallassembly-method"></a><span data-ttu-id="261d8-102">IAssemblyCache::UninstallAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="261d8-102">IAssemblyCache::UninstallAssembly Method</span></span>
<span data-ttu-id="261d8-103">Odinstaluje zadaný sestavení z globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="261d8-103">Uninstalls the specified assembly from the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="261d8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="261d8-104">Syntax</span></span>  
  
```  
HRESULT UninstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData,  
    [out, optional] ULONG *pulDisposition  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="261d8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="261d8-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="261d8-106">[v] Příznaky definované v Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="261d8-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="261d8-107">[v] Název sestavení, chcete-li odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="261d8-107">[in] The name of the assembly to uninstall.</span></span>  
  
 `pRefData`  
 <span data-ttu-id="261d8-108">[v] A [fusion_install_reference –](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) struktura, která obsahuje data instalace pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="261d8-108">[in] A [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure that contains the installation data for the assembly.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="261d8-109">[na víc systémů, volitelné] Jedna z hodnot dispozice definované v Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="261d8-109">[out, optional] One of the disposition values defined in Fusion.idl.</span></span> <span data-ttu-id="261d8-110">Možné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="261d8-110">Possible values include the following:</span></span>  
  
-   <span data-ttu-id="261d8-111">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED (1)</span><span class="sxs-lookup"><span data-stu-id="261d8-111">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED (1)</span></span>  
  
-   <span data-ttu-id="261d8-112">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE (2)</span><span class="sxs-lookup"><span data-stu-id="261d8-112">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE (2)</span></span>  
  
-   <span data-ttu-id="261d8-113">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED (3)</span><span class="sxs-lookup"><span data-stu-id="261d8-113">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED (3)</span></span>  
  
-   <span data-ttu-id="261d8-114">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING (4)</span><span class="sxs-lookup"><span data-stu-id="261d8-114">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING (4)</span></span>  
  
-   <span data-ttu-id="261d8-115">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES (5)</span><span class="sxs-lookup"><span data-stu-id="261d8-115">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES (5)</span></span>  
  
-   <span data-ttu-id="261d8-116">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND (6)</span><span class="sxs-lookup"><span data-stu-id="261d8-116">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND (6)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="261d8-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="261d8-117">Requirements</span></span>  
 <span data-ttu-id="261d8-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="261d8-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="261d8-119">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="261d8-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="261d8-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="261d8-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="261d8-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="261d8-121">See Also</span></span>  
 [<span data-ttu-id="261d8-122">IAssemblyCache – rozhraní</span><span class="sxs-lookup"><span data-stu-id="261d8-122">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
