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
ms.openlocfilehash: 40efe81f72a2043503bf521e3e47dad1a7f4530c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448448"
---
# <a name="cor_prf_static_type-enumeration"></a><span data-ttu-id="9c158-102">COR_PRF_STATIC_TYPE – výčet</span><span class="sxs-lookup"><span data-stu-id="9c158-102">COR_PRF_STATIC_TYPE Enumeration</span></span>
<span data-ttu-id="9c158-103">Označuje, zda je pole statické, a pokud ano, statická kvalita, která se vztahuje na pole.</span><span class="sxs-lookup"><span data-stu-id="9c158-103">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span> <span data-ttu-id="9c158-104">Tyto hodnoty mohou být kombinovány pomocí bitových nebo operací k označení toho, že pole má více různých statických vlastností.</span><span class="sxs-lookup"><span data-stu-id="9c158-104">These values can be combined using the bitwise OR operation to indicate that the field has multiple, different static qualities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c158-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c158-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_FIELD_NOT_A_STATIC = 0x0,  
    COR_PRF_FIELD_APP_DOMAIN_STATIC = 0x1,  
    COR_PRF_FIELD_THREAD_STATIC = 0x2,  
    COR_PRF_FIELD_CONTEXT_STATIC = 0x4,  
    COR_PRF_FIELD_RVA_STATIC = 0x8  
} COR_PRF_STATIC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="9c158-106">Členové</span><span class="sxs-lookup"><span data-stu-id="9c158-106">Members</span></span>  
  
|<span data-ttu-id="9c158-107">Člen</span><span class="sxs-lookup"><span data-stu-id="9c158-107">Member</span></span>|<span data-ttu-id="9c158-108">Popis</span><span class="sxs-lookup"><span data-stu-id="9c158-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_NOT_A_STATIC`|<span data-ttu-id="9c158-109">Pole není statické.</span><span class="sxs-lookup"><span data-stu-id="9c158-109">The field is not static.</span></span>|  
|`COR_PRF_FIELD_APP_DOMAIN_STATIC`|<span data-ttu-id="9c158-110">Pole je aplikační doména-static.</span><span class="sxs-lookup"><span data-stu-id="9c158-110">The field is application domain-static.</span></span>|  
|`COR_PRF_FIELD_THREAD_STATIC`|<span data-ttu-id="9c158-111">Pole je typu vlákno-static.</span><span class="sxs-lookup"><span data-stu-id="9c158-111">The field is thread-static.</span></span>|  
|`COR_PRF_FIELD_CONTEXT_STATIC`|<span data-ttu-id="9c158-112">Pole je Context – static.</span><span class="sxs-lookup"><span data-stu-id="9c158-112">The field is context-static.</span></span>|  
|`COR_PRF_FIELD_RVA_STATIC`|<span data-ttu-id="9c158-113">Pole je relativní virtuální adresa (RVA) – statická.</span><span class="sxs-lookup"><span data-stu-id="9c158-113">The field is relative virtual address (RVA)-static.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9c158-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9c158-114">Requirements</span></span>  
 <span data-ttu-id="9c158-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c158-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c158-116">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9c158-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9c158-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9c158-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c158-118">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c158-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c158-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9c158-119">See also</span></span>

- [<span data-ttu-id="9c158-120">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="9c158-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
