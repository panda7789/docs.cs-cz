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
ms.openlocfilehash: c14d364320c82f061ef606a402563dacfce28139
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186235"
---
# <a name="icorpublishappdomainenumnext-method"></a><span data-ttu-id="15c3f-102">ICorPublishAppDomainEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="15c3f-102">ICorPublishAppDomainEnum::Next Method</span></span>
<span data-ttu-id="15c3f-103">Získá zadaný počet aplikačních doménách, které momentálně existují v procesu od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="15c3f-103">Gets the specified number of application domains that currently exist in the process, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15c3f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15c3f-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]   
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15c3f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="15c3f-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="15c3f-106">[in] Počet prvků který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="15c3f-106">[in] The number of elements to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="15c3f-107">[out] Načte ukazatel na pole [icorpublishappdomain –](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objektů, z nichž každý představuje doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="15c3f-107">[out] A pointer to the array of retrieved [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects, each of which represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="15c3f-108">[out] Ukazatel na počet skutečně vrácených domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="15c3f-108">[out] Pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="15c3f-109">Tato hodnota může mít hodnotu null Pokud `celt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="15c3f-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15c3f-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="15c3f-110">Requirements</span></span>  
 <span data-ttu-id="15c3f-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15c3f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15c3f-112">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="15c3f-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="15c3f-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15c3f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15c3f-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15c3f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15c3f-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15c3f-115">See also</span></span>

- [<span data-ttu-id="15c3f-116">ICorPublishAppDomainEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="15c3f-116">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)
