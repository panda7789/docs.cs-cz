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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697742"
---
# <a name="iassemblycacheuninstallassembly-method"></a><span data-ttu-id="80ce0-102">IAssemblyCache::UninstallAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="80ce0-102">IAssemblyCache::UninstallAssembly Method</span></span>
<span data-ttu-id="80ce0-103">Odinstaluje zadané sestavení z globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="80ce0-103">Uninstalls the specified assembly from the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80ce0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80ce0-104">Syntax</span></span>  
  
```  
HRESULT UninstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData,  
    [out, optional] ULONG *pulDisposition  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80ce0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="80ce0-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="80ce0-106">[in] Příznaky definované v Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="80ce0-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="80ce0-107">[in] Název sestavení, chcete-li odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="80ce0-107">[in] The name of the assembly to uninstall.</span></span>  
  
 `pRefData`  
 <span data-ttu-id="80ce0-108">[in] A [fusion_install_reference –](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) strukturu, která obsahuje data o instalaci pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="80ce0-108">[in] A [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure that contains the installation data for the assembly.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="80ce0-109">[out, volitelné] Jedna z hodnot dispozice definované v Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="80ce0-109">[out, optional] One of the disposition values defined in Fusion.idl.</span></span> <span data-ttu-id="80ce0-110">Možné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="80ce0-110">Possible values include the following:</span></span>  
  
- <span data-ttu-id="80ce0-111">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED (1)</span><span class="sxs-lookup"><span data-stu-id="80ce0-111">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED (1)</span></span>  
  
- <span data-ttu-id="80ce0-112">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE (2)</span><span class="sxs-lookup"><span data-stu-id="80ce0-112">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE (2)</span></span>  
  
- <span data-ttu-id="80ce0-113">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED (3)</span><span class="sxs-lookup"><span data-stu-id="80ce0-113">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED (3)</span></span>  
  
- <span data-ttu-id="80ce0-114">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING (4)</span><span class="sxs-lookup"><span data-stu-id="80ce0-114">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING (4)</span></span>  
  
- <span data-ttu-id="80ce0-115">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES (5)</span><span class="sxs-lookup"><span data-stu-id="80ce0-115">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES (5)</span></span>  
  
- <span data-ttu-id="80ce0-116">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND (6)</span><span class="sxs-lookup"><span data-stu-id="80ce0-116">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND (6)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80ce0-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="80ce0-117">Requirements</span></span>  
 <span data-ttu-id="80ce0-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80ce0-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80ce0-119">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="80ce0-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="80ce0-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80ce0-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80ce0-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="80ce0-121">See also</span></span>

- [<span data-ttu-id="80ce0-122">IAssemblyCache – rozhraní</span><span class="sxs-lookup"><span data-stu-id="80ce0-122">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
