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
ms.openlocfilehash: e3e50538bde8fe3509b49e3dbcb031875e6863e5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127122"
---
# <a name="iassemblycachecreateassemblycacheitem-method"></a><span data-ttu-id="950bd-102">IAssemblyCache::CreateAssemblyCacheItem – metoda</span><span class="sxs-lookup"><span data-stu-id="950bd-102">IAssemblyCache::CreateAssemblyCacheItem Method</span></span>
<span data-ttu-id="950bd-103">Získá odkaz na nový objekt [IAssemblyCacheItem](iassemblycacheitem-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="950bd-103">Gets a reference to a new [IAssemblyCacheItem](iassemblycacheitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="950bd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="950bd-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyCacheItem (  
    [in]  DWORD dwFlags,  
    [in]  PVOID pvReserved,  
    [out] IAssemblyCacheItem **ppAsmItem,  
    [in, optional] LPCWSTR pszAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="950bd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="950bd-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="950bd-106">pro Příznaky definované v Fusion. idl</span><span class="sxs-lookup"><span data-stu-id="950bd-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="950bd-107">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="950bd-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="950bd-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="950bd-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
- <span data-ttu-id="950bd-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="950bd-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="950bd-110">pro Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="950bd-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="950bd-111">`pvReserved` musí být odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="950bd-111">`pvReserved` must be a null reference.</span></span>  
  
 `ppAsmItem`  
 <span data-ttu-id="950bd-112">mimo Vrácený ukazatel `IAssemblyCacheItem`.</span><span class="sxs-lookup"><span data-stu-id="950bd-112">[out] The returned `IAssemblyCacheItem` pointer.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="950bd-113">[in, volitelné] Nekanonické páry `name=value` oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="950bd-113">[in, optional] Uncanonicalized, comma-separated `name=value` pairs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="950bd-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="950bd-114">Requirements</span></span>  
 <span data-ttu-id="950bd-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="950bd-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="950bd-116">**Hlavička:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="950bd-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="950bd-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="950bd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="950bd-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="950bd-118">See also</span></span>

- [<span data-ttu-id="950bd-119">IAssemblyCache – rozhraní</span><span class="sxs-lookup"><span data-stu-id="950bd-119">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="950bd-120">IAssemblyCacheItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="950bd-120">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
