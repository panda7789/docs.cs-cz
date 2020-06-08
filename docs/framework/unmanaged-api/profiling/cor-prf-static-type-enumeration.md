---
title: COR_PRF_STATIC_TYPE – výčet
ms.date: 03/30/2017
api_name:
- COR_PRF_STATIC_TYPE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_STATIC_TYPE
helpviewer_keywords:
- COR_PRF_STATIC_TYPE enumeration [.NET Framework profiling]
ms.assetid: 441d7809-5b65-41a5-ba64-2910a8008315
topic_type:
- apiref
ms.openlocfilehash: 80d72aefc736054afcee152c55e941c0f8f3c6a8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500764"
---
# <a name="cor_prf_static_type-enumeration"></a><span data-ttu-id="91397-102">COR_PRF_STATIC_TYPE – výčet</span><span class="sxs-lookup"><span data-stu-id="91397-102">COR_PRF_STATIC_TYPE Enumeration</span></span>
<span data-ttu-id="91397-103">Označuje, zda je pole statické, a pokud ano, statická kvalita, která se vztahuje na pole.</span><span class="sxs-lookup"><span data-stu-id="91397-103">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span> <span data-ttu-id="91397-104">Tyto hodnoty mohou být kombinovány pomocí bitových nebo operací k označení toho, že pole má více různých statických vlastností.</span><span class="sxs-lookup"><span data-stu-id="91397-104">These values can be combined using the bitwise OR operation to indicate that the field has multiple, different static qualities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91397-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91397-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_FIELD_NOT_A_STATIC = 0x0,  
    COR_PRF_FIELD_APP_DOMAIN_STATIC = 0x1,  
    COR_PRF_FIELD_THREAD_STATIC = 0x2,  
    COR_PRF_FIELD_CONTEXT_STATIC = 0x4,  
    COR_PRF_FIELD_RVA_STATIC = 0x8  
} COR_PRF_STATIC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="91397-106">Členové</span><span class="sxs-lookup"><span data-stu-id="91397-106">Members</span></span>  
  
|<span data-ttu-id="91397-107">Člen</span><span class="sxs-lookup"><span data-stu-id="91397-107">Member</span></span>|<span data-ttu-id="91397-108">Description</span><span class="sxs-lookup"><span data-stu-id="91397-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_NOT_A_STATIC`|<span data-ttu-id="91397-109">Pole není statické.</span><span class="sxs-lookup"><span data-stu-id="91397-109">The field is not static.</span></span>|  
|`COR_PRF_FIELD_APP_DOMAIN_STATIC`|<span data-ttu-id="91397-110">Pole je aplikační doména-static.</span><span class="sxs-lookup"><span data-stu-id="91397-110">The field is application domain-static.</span></span>|  
|`COR_PRF_FIELD_THREAD_STATIC`|<span data-ttu-id="91397-111">Pole je typu vlákno-static.</span><span class="sxs-lookup"><span data-stu-id="91397-111">The field is thread-static.</span></span>|  
|`COR_PRF_FIELD_CONTEXT_STATIC`|<span data-ttu-id="91397-112">Pole je Context – static.</span><span class="sxs-lookup"><span data-stu-id="91397-112">The field is context-static.</span></span>|  
|`COR_PRF_FIELD_RVA_STATIC`|<span data-ttu-id="91397-113">Pole je relativní virtuální adresa (RVA) – statická.</span><span class="sxs-lookup"><span data-stu-id="91397-113">The field is relative virtual address (RVA)-static.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="91397-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="91397-114">Requirements</span></span>  
 <span data-ttu-id="91397-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91397-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91397-116">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="91397-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="91397-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="91397-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91397-118">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91397-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91397-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91397-119">See also</span></span>

- [<span data-ttu-id="91397-120">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="91397-120">Profiling Enumerations</span></span>](profiling-enumerations.md)
