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
ms.openlocfilehash: 539a8edf6d7248235a6e672edc9464679a2eab82
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134502"
---
# <a name="iassemblycacheuninstallassembly-method"></a><span data-ttu-id="78198-102">IAssemblyCache::UninstallAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="78198-102">IAssemblyCache::UninstallAssembly Method</span></span>
<span data-ttu-id="78198-103">Odinstaluje zadané sestavení z globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="78198-103">Uninstalls the specified assembly from the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78198-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78198-104">Syntax</span></span>  
  
```cpp  
HRESULT UninstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData,  
    [out, optional] ULONG *pulDisposition  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78198-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="78198-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="78198-106">pro Příznaky definované v Fusion. idl</span><span class="sxs-lookup"><span data-stu-id="78198-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="78198-107">pro Název sestavení, které chcete odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="78198-107">[in] The name of the assembly to uninstall.</span></span>  
  
 `pRefData`  
 <span data-ttu-id="78198-108">pro Struktura [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) , která obsahuje instalační data pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="78198-108">[in] A [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) structure that contains the installation data for the assembly.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="78198-109">[out, volitelné] Jedna z dispozičních hodnot definovaných v Fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="78198-109">[out, optional] One of the disposition values defined in Fusion.idl.</span></span> <span data-ttu-id="78198-110">Možné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="78198-110">Possible values include the following:</span></span>  
  
- <span data-ttu-id="78198-111">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED (1)</span><span class="sxs-lookup"><span data-stu-id="78198-111">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED (1)</span></span>  
  
- <span data-ttu-id="78198-112">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE (2)</span><span class="sxs-lookup"><span data-stu-id="78198-112">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE (2)</span></span>  
  
- <span data-ttu-id="78198-113">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED (3)</span><span class="sxs-lookup"><span data-stu-id="78198-113">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED (3)</span></span>  
  
- <span data-ttu-id="78198-114">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING (4)</span><span class="sxs-lookup"><span data-stu-id="78198-114">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING (4)</span></span>  
  
- <span data-ttu-id="78198-115">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES (5)</span><span class="sxs-lookup"><span data-stu-id="78198-115">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES (5)</span></span>  
  
- <span data-ttu-id="78198-116">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND (6)</span><span class="sxs-lookup"><span data-stu-id="78198-116">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND (6)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78198-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="78198-117">Requirements</span></span>  
 <span data-ttu-id="78198-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78198-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78198-119">**Hlavička:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="78198-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="78198-120">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78198-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78198-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="78198-121">See also</span></span>

- [<span data-ttu-id="78198-122">IAssemblyCache – rozhraní</span><span class="sxs-lookup"><span data-stu-id="78198-122">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
