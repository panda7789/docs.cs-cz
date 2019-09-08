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
ms.openlocfilehash: 63c1cb3c417e8e521c6ac8417d260ccb937863f8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796754"
---
# <a name="iassemblycacheuninstallassembly-method"></a><span data-ttu-id="c35ff-102">IAssemblyCache::UninstallAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="c35ff-102">IAssemblyCache::UninstallAssembly Method</span></span>
<span data-ttu-id="c35ff-103">Odinstaluje zadané sestavení z globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="c35ff-103">Uninstalls the specified assembly from the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c35ff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c35ff-104">Syntax</span></span>  
  
```cpp  
HRESULT UninstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData,  
    [out, optional] ULONG *pulDisposition  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c35ff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c35ff-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="c35ff-106">pro Příznaky definované v Fusion. idl</span><span class="sxs-lookup"><span data-stu-id="c35ff-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="c35ff-107">pro Název sestavení, které chcete odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="c35ff-107">[in] The name of the assembly to uninstall.</span></span>  
  
 `pRefData`  
 <span data-ttu-id="c35ff-108">pro Struktura [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) , která obsahuje instalační data pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="c35ff-108">[in] A [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) structure that contains the installation data for the assembly.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="c35ff-109">[out, volitelné] Jedna z dispozičních hodnot definovaných v Fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="c35ff-109">[out, optional] One of the disposition values defined in Fusion.idl.</span></span> <span data-ttu-id="c35ff-110">Možné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="c35ff-110">Possible values include the following:</span></span>  
  
- <span data-ttu-id="c35ff-111">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED (1)</span><span class="sxs-lookup"><span data-stu-id="c35ff-111">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED (1)</span></span>  
  
- <span data-ttu-id="c35ff-112">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE (2)</span><span class="sxs-lookup"><span data-stu-id="c35ff-112">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE (2)</span></span>  
  
- <span data-ttu-id="c35ff-113">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED (3)</span><span class="sxs-lookup"><span data-stu-id="c35ff-113">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED (3)</span></span>  
  
- <span data-ttu-id="c35ff-114">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING (4)</span><span class="sxs-lookup"><span data-stu-id="c35ff-114">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING (4)</span></span>  
  
- <span data-ttu-id="c35ff-115">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES (5)</span><span class="sxs-lookup"><span data-stu-id="c35ff-115">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES (5)</span></span>  
  
- <span data-ttu-id="c35ff-116">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND (6)</span><span class="sxs-lookup"><span data-stu-id="c35ff-116">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND (6)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c35ff-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c35ff-117">Requirements</span></span>  
 <span data-ttu-id="c35ff-118">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c35ff-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c35ff-119">**Hlaviček** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="c35ff-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="c35ff-120">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c35ff-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c35ff-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c35ff-121">See also</span></span>

- [<span data-ttu-id="c35ff-122">IAssemblyCache – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c35ff-122">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
