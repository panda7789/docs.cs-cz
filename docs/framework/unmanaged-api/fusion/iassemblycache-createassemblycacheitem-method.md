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
ms.openlocfilehash: 215eb3a508a746230d36fdda3e8ba992287be62c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796825"
---
# <a name="iassemblycachecreateassemblycacheitem-method"></a><span data-ttu-id="ad84e-102">IAssemblyCache::CreateAssemblyCacheItem – metoda</span><span class="sxs-lookup"><span data-stu-id="ad84e-102">IAssemblyCache::CreateAssemblyCacheItem Method</span></span>
<span data-ttu-id="ad84e-103">Získá odkaz na nový objekt [IAssemblyCacheItem](iassemblycacheitem-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="ad84e-103">Gets a reference to a new [IAssemblyCacheItem](iassemblycacheitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad84e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad84e-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyCacheItem (  
    [in]  DWORD dwFlags,  
    [in]  PVOID pvReserved,  
    [out] IAssemblyCacheItem **ppAsmItem,  
    [in, optional] LPCWSTR pszAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad84e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad84e-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="ad84e-106">pro Příznaky definované v Fusion. idl</span><span class="sxs-lookup"><span data-stu-id="ad84e-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="ad84e-107">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="ad84e-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="ad84e-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="ad84e-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
- <span data-ttu-id="ad84e-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="ad84e-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="ad84e-110">pro Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="ad84e-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="ad84e-111">`pvReserved`musí se jednat o odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="ad84e-111">`pvReserved` must be a null reference.</span></span>  
  
 `ppAsmItem`  
 <span data-ttu-id="ad84e-112">mimo Vrácený `IAssemblyCacheItem` ukazatel.</span><span class="sxs-lookup"><span data-stu-id="ad84e-112">[out] The returned `IAssemblyCacheItem` pointer.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="ad84e-113">[in, volitelné] Nekanonické páry oddělené `name=value` čárkami.</span><span class="sxs-lookup"><span data-stu-id="ad84e-113">[in, optional] Uncanonicalized, comma-separated `name=value` pairs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad84e-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ad84e-114">Requirements</span></span>  
 <span data-ttu-id="ad84e-115">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad84e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad84e-116">**Hlaviček** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="ad84e-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ad84e-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad84e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad84e-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ad84e-118">See also</span></span>

- [<span data-ttu-id="ad84e-119">IAssemblyCache – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ad84e-119">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="ad84e-120">IAssemblyCacheItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ad84e-120">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
