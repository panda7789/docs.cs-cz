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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fc610f4cc34b256867396a3390d5ccd0822f6454
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450385"
---
# <a name="corprfstatictype-enumeration"></a><span data-ttu-id="3094c-102">COR_PRF_STATIC_TYPE – výčet</span><span class="sxs-lookup"><span data-stu-id="3094c-102">COR_PRF_STATIC_TYPE Enumeration</span></span>
<span data-ttu-id="3094c-103">Určuje, jestli je statická pole a pokud ano, statické kvality, která platí pro pole.</span><span class="sxs-lookup"><span data-stu-id="3094c-103">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span> <span data-ttu-id="3094c-104">Tyto hodnoty lze spojovat pomocí bitové operace OR indikující, zda má pole víc různých statických vlastností.</span><span class="sxs-lookup"><span data-stu-id="3094c-104">These values can be combined using the bitwise OR operation to indicate that the field has multiple, different static qualities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3094c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3094c-105">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_FIELD_NOT_A_STATIC = 0x0,  
    COR_PRF_FIELD_APP_DOMAIN_STATIC = 0x1,  
    COR_PRF_FIELD_THREAD_STATIC = 0x2,  
    COR_PRF_FIELD_CONTEXT_STATIC = 0x4,  
    COR_PRF_FIELD_RVA_STATIC = 0x8  
} COR_PRF_STATIC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="3094c-106">Členové</span><span class="sxs-lookup"><span data-stu-id="3094c-106">Members</span></span>  
  
|<span data-ttu-id="3094c-107">Člen</span><span class="sxs-lookup"><span data-stu-id="3094c-107">Member</span></span>|<span data-ttu-id="3094c-108">Popis</span><span class="sxs-lookup"><span data-stu-id="3094c-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_NOT_A_STATIC`|<span data-ttu-id="3094c-109">Pole nejsou statické.</span><span class="sxs-lookup"><span data-stu-id="3094c-109">The field is not static.</span></span>|  
|`COR_PRF_FIELD_APP_DOMAIN_STATIC`|<span data-ttu-id="3094c-110">Toto pole je aplikace statické domény.</span><span class="sxs-lookup"><span data-stu-id="3094c-110">The field is application domain-static.</span></span>|  
|`COR_PRF_FIELD_THREAD_STATIC`|<span data-ttu-id="3094c-111">Pole je statická přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="3094c-111">The field is thread-static.</span></span>|  
|`COR_PRF_FIELD_CONTEXT_STATIC`|<span data-ttu-id="3094c-112">Pole je statická kontextu.</span><span class="sxs-lookup"><span data-stu-id="3094c-112">The field is context-static.</span></span>|  
|`COR_PRF_FIELD_RVA_STATIC`|<span data-ttu-id="3094c-113">Toto pole je relativní virtuální adresy (RVA)-statické.</span><span class="sxs-lookup"><span data-stu-id="3094c-113">The field is relative virtual address (RVA)-static.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3094c-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3094c-114">Requirements</span></span>  
 <span data-ttu-id="3094c-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3094c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3094c-116">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3094c-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3094c-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3094c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3094c-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3094c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3094c-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="3094c-119">See Also</span></span>  
 [<span data-ttu-id="3094c-120">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="3094c-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
