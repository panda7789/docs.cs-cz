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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 27001f8560dcd128b5d737ed0f219387be86d6e2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672303"
---
# <a name="iassemblycachecreateassemblycacheitem-method"></a><span data-ttu-id="b2467-102">IAssemblyCache::CreateAssemblyCacheItem – metoda</span><span class="sxs-lookup"><span data-stu-id="b2467-102">IAssemblyCache::CreateAssemblyCacheItem Method</span></span>
<span data-ttu-id="b2467-103">Získá odkaz na novou [iassemblycacheitem –](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="b2467-103">Gets a reference to a new [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2467-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2467-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyCacheItem (  
    [in]  DWORD dwFlags,  
    [in]  PVOID pvReserved,  
    [out] IAssemblyCacheItem **ppAsmItem,  
    [in, optional] LPCWSTR pszAssemblyName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b2467-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b2467-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="b2467-106">[in] Příznaky definované v Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="b2467-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="b2467-107">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="b2467-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="b2467-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="b2467-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
-   <span data-ttu-id="b2467-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0X00000002)</span><span class="sxs-lookup"><span data-stu-id="b2467-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="b2467-110">[in] Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="b2467-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="b2467-111">`pvReserved` musí být referencí s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="b2467-111">`pvReserved` must be a null reference.</span></span>  
  
 `ppAsmItem`  
 <span data-ttu-id="b2467-112">[out] Vrácený `IAssemblyCacheItem` ukazatele.</span><span class="sxs-lookup"><span data-stu-id="b2467-112">[out] The returned `IAssemblyCacheItem` pointer.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="b2467-113">[in, volitelné] Uncanonicalized, oddělené čárkami `name=value` dvojice.</span><span class="sxs-lookup"><span data-stu-id="b2467-113">[in, optional] Uncanonicalized, comma-separated `name=value` pairs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2467-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b2467-114">Requirements</span></span>  
 <span data-ttu-id="b2467-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2467-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2467-116">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="b2467-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b2467-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2467-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2467-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b2467-118">See also</span></span>
- [<span data-ttu-id="b2467-119">IAssemblyCache – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b2467-119">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
- [<span data-ttu-id="b2467-120">IAssemblyCacheItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b2467-120">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
