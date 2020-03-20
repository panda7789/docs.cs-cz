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
ms.openlocfilehash: 6f7f400c51ded0b98c0c2286cb6f90bbd77e47d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178400"
---
# <a name="icorpublishappdomainenumnext-method"></a><span data-ttu-id="057d0-102">ICorPublishAppDomainEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="057d0-102">ICorPublishAppDomainEnum::Next Method</span></span>
<span data-ttu-id="057d0-103">Získá zadaný počet aplikačních domén, které aktuálně existují v procesu, počínaje aktuální pozici.</span><span class="sxs-lookup"><span data-stu-id="057d0-103">Gets the specified number of application domains that currently exist in the process, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="057d0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="057d0-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="057d0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="057d0-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="057d0-106">[v] Počet prvků, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="057d0-106">[in] The number of elements to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="057d0-107">[out] Ukazatel na pole načtených objektů [ICorPublishAppDomain,](icorpublishappdomain-interface.md) z nichž každý představuje doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="057d0-107">[out] A pointer to the array of retrieved [ICorPublishAppDomain](icorpublishappdomain-interface.md) objects, each of which represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="057d0-108">[out] Ukazatel na počet skutečně vrácených aplikačních domén.</span><span class="sxs-lookup"><span data-stu-id="057d0-108">[out] Pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="057d0-109">Tato hodnota může `celt` být null, pokud je jeden.</span><span class="sxs-lookup"><span data-stu-id="057d0-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="057d0-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="057d0-110">Requirements</span></span>  
 <span data-ttu-id="057d0-111">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="057d0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="057d0-112">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="057d0-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="057d0-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="057d0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="057d0-114">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="057d0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="057d0-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="057d0-115">See also</span></span>

- [<span data-ttu-id="057d0-116">ICorPublishAppDomainEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="057d0-116">ICorPublishAppDomainEnum Interface</span></span>](icorpublishappdomainenum-interface.md)
