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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986645"
---
# <a name="icorpublishappdomainenumnext-method"></a><span data-ttu-id="6d0fa-102">ICorPublishAppDomainEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="6d0fa-102">ICorPublishAppDomainEnum::Next Method</span></span>
<span data-ttu-id="6d0fa-103">Získá zadaný počet aplikačních doménách, které momentálně existují v procesu od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="6d0fa-103">Gets the specified number of application domains that currently exist in the process, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d0fa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d0fa-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]   
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d0fa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6d0fa-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="6d0fa-106">[in] Počet prvků který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="6d0fa-106">[in] The number of elements to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="6d0fa-107">[out] Načte ukazatel na pole [icorpublishappdomain –](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objektů, z nichž každý představuje doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="6d0fa-107">[out] A pointer to the array of retrieved [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects, each of which represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="6d0fa-108">[out] Ukazatel na počet skutečně vrácených domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="6d0fa-108">[out] Pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="6d0fa-109">Tato hodnota může mít hodnotu null Pokud `celt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="6d0fa-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d0fa-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6d0fa-110">Requirements</span></span>  
 <span data-ttu-id="6d0fa-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d0fa-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d0fa-112">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="6d0fa-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="6d0fa-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d0fa-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d0fa-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d0fa-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d0fa-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6d0fa-115">See also</span></span>

- [<span data-ttu-id="6d0fa-116">ICorPublishAppDomainEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6d0fa-116">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)
