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
ms.openlocfilehash: 648b641cbd2ec97305674451df06ce5be6a93a49
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183687"
---
# <a name="iassemblycachecreateassemblycacheitem-method"></a><span data-ttu-id="7d4b3-102">IAssemblyCache::CreateAssemblyCacheItem – metoda</span><span class="sxs-lookup"><span data-stu-id="7d4b3-102">IAssemblyCache::CreateAssemblyCacheItem Method</span></span>
<span data-ttu-id="7d4b3-103">Získá odkaz na novou [iassemblycacheitem –](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="7d4b3-103">Gets a reference to a new [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d4b3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d4b3-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyCacheItem (  
    [in]  DWORD dwFlags,  
    [in]  PVOID pvReserved,  
    [out] IAssemblyCacheItem **ppAsmItem,  
    [in, optional] LPCWSTR pszAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d4b3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d4b3-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="7d4b3-106">[in] Příznaky definované v Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="7d4b3-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="7d4b3-107">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="7d4b3-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="7d4b3-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="7d4b3-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
-   <span data-ttu-id="7d4b3-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0X00000002)</span><span class="sxs-lookup"><span data-stu-id="7d4b3-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="7d4b3-110">[in] Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="7d4b3-110">[in] Reserved for future extensibility.</span></span> `pvReserved` <span data-ttu-id="7d4b3-111">musí být referencí s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="7d4b3-111">must be a null reference.</span></span>  
  
 `ppAsmItem`  
 <span data-ttu-id="7d4b3-112">[out] Vrácený `IAssemblyCacheItem` ukazatele.</span><span class="sxs-lookup"><span data-stu-id="7d4b3-112">[out] The returned `IAssemblyCacheItem` pointer.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="7d4b3-113">[in, volitelné] Uncanonicalized, oddělené čárkami `name=value` dvojice.</span><span class="sxs-lookup"><span data-stu-id="7d4b3-113">[in, optional] Uncanonicalized, comma-separated `name=value` pairs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d4b3-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d4b3-114">Requirements</span></span>  
 <span data-ttu-id="7d4b3-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d4b3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d4b3-116">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="7d4b3-116">**Header:** Fusion.h</span></span>  
  
 **<span data-ttu-id="7d4b3-117">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="7d4b3-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7d4b3-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d4b3-118">See also</span></span>

- [<span data-ttu-id="7d4b3-119">IAssemblyCache – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7d4b3-119">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
- [<span data-ttu-id="7d4b3-120">IAssemblyCacheItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7d4b3-120">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
