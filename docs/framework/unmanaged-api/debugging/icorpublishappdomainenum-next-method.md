---
title: ICorPublishAppDomainEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomainEnum::Next
helpviewer_keywords:
- Next method, ICorPublishAppDomainEnum interface [.NET Framework debugging]
- ICorPublishAppDomainEnum::Next method [.NET Framework debugging]
ms.assetid: ad37cd10-0339-4d08-9b0e-4b3428bb4dc3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac3c6698e4ca127257b7682f1f55acd663375280
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423725"
---
# <a name="icorpublishappdomainenumnext-method"></a><span data-ttu-id="ecc8f-102">ICorPublishAppDomainEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="ecc8f-102">ICorPublishAppDomainEnum::Next Method</span></span>
<span data-ttu-id="ecc8f-103">Získá zadaný počet domén aplikací, které momentálně existují v procesu, počínaje na aktuální pozici.</span><span class="sxs-lookup"><span data-stu-id="ecc8f-103">Gets the specified number of application domains that currently exist in the process, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecc8f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ecc8f-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]   
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ecc8f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ecc8f-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="ecc8f-106">[v] Počet prvků mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="ecc8f-106">[in] The number of elements to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="ecc8f-107">[out] Ukazatel na pole načíst [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objekty, z nichž každý představuje domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="ecc8f-107">[out] A pointer to the array of retrieved [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects, each of which represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="ecc8f-108">[out] Ukazatel na počet domén aplikace ve skutečnosti vrátila.</span><span class="sxs-lookup"><span data-stu-id="ecc8f-108">[out] Pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="ecc8f-109">Tato hodnota může být null. Pokud `celt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="ecc8f-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecc8f-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ecc8f-110">Requirements</span></span>  
 <span data-ttu-id="ecc8f-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecc8f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecc8f-112">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="ecc8f-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="ecc8f-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ecc8f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ecc8f-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecc8f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecc8f-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="ecc8f-115">See Also</span></span>  
 [<span data-ttu-id="ecc8f-116">ICorPublishAppDomainEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ecc8f-116">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)
