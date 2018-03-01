---
title: "IAssemblyCache::CreateAssemblyCacheItem – metoda"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 65431425afb6a666679d29f9c1bbc9691caa0afb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblycachecreateassemblycacheitem-method"></a><span data-ttu-id="53c88-102">IAssemblyCache::CreateAssemblyCacheItem – metoda</span><span class="sxs-lookup"><span data-stu-id="53c88-102">IAssemblyCache::CreateAssemblyCacheItem Method</span></span>
<span data-ttu-id="53c88-103">Získá odkaz na novou [iassemblycacheitem –](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="53c88-103">Gets a reference to a new [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53c88-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53c88-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyCacheItem (  
    [in]  DWORD dwFlags,  
    [in]  PVOID pvReserved,  
    [out] IAssemblyCacheItem **ppAsmItem,  
    [in, optional] LPCWSTR pszAssemblyName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="53c88-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="53c88-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="53c88-106">[v] Příznaky definované v Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="53c88-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="53c88-107">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="53c88-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="53c88-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0X00000001)</span><span class="sxs-lookup"><span data-stu-id="53c88-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
-   <span data-ttu-id="53c88-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0X00000002)</span><span class="sxs-lookup"><span data-stu-id="53c88-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="53c88-110">[v] Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="53c88-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="53c88-111">`pvReserved`musí být odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="53c88-111">`pvReserved` must be a null reference.</span></span>  
  
 `ppAsmItem`  
 <span data-ttu-id="53c88-112">[out] Vrácený `IAssemblyCacheItem` ukazatel.</span><span class="sxs-lookup"><span data-stu-id="53c88-112">[out] The returned `IAssemblyCacheItem` pointer.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="53c88-113">[v, optional] Uncanonicalized, oddělených čárkami `name=value` páry.</span><span class="sxs-lookup"><span data-stu-id="53c88-113">[in, optional] Uncanonicalized, comma-separated `name=value` pairs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53c88-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="53c88-114">Requirements</span></span>  
 <span data-ttu-id="53c88-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53c88-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53c88-116">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="53c88-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="53c88-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53c88-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53c88-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="53c88-118">See Also</span></span>  
 [<span data-ttu-id="53c88-119">IAssemblyCache – rozhraní</span><span class="sxs-lookup"><span data-stu-id="53c88-119">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 [<span data-ttu-id="53c88-120">IAssemblyCacheItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="53c88-120">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
