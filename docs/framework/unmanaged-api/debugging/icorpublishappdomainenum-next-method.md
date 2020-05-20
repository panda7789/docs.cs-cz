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
ms.openlocfilehash: c5ac38005410ae6ed9c2f4160e926987791ad604
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421212"
---
# <a name="icorpublishappdomainenumnext-method"></a><span data-ttu-id="6cd55-102">ICorPublishAppDomainEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="6cd55-102">ICorPublishAppDomainEnum::Next Method</span></span>
<span data-ttu-id="6cd55-103">Načte zadaný počet aplikačních domén, které aktuálně existují v procesu, počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="6cd55-103">Gets the specified number of application domains that currently exist in the process, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cd55-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6cd55-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6cd55-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6cd55-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="6cd55-106">pro Počet prvků, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="6cd55-106">[in] The number of elements to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="6cd55-107">mimo Ukazatel na pole načtených objektů [ICorPublishAppDomain](icorpublishappdomain-interface.md) , z nichž každý představuje doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="6cd55-107">[out] A pointer to the array of retrieved [ICorPublishAppDomain](icorpublishappdomain-interface.md) objects, each of which represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="6cd55-108">mimo Ukazatel na počet skutečně vrácených aplikačních domén.</span><span class="sxs-lookup"><span data-stu-id="6cd55-108">[out] Pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="6cd55-109">Tato hodnota může být null `celt` , pokud je jedna.</span><span class="sxs-lookup"><span data-stu-id="6cd55-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cd55-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6cd55-110">Requirements</span></span>  
 <span data-ttu-id="6cd55-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cd55-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cd55-112">**Hlavička:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="6cd55-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="6cd55-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6cd55-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6cd55-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cd55-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cd55-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="6cd55-115">See also</span></span>

- [<span data-ttu-id="6cd55-116">ICorPublishAppDomainEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6cd55-116">ICorPublishAppDomainEnum Interface</span></span>](icorpublishappdomainenum-interface.md)
