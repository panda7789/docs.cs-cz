---
title: COR_PRF_FUNCTION_ARGUMENT_RANGE – struktura
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION_ARGUMENT_RANGE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION_ARGUMENT_RANGE
helpviewer_keywords:
- COR_PRF_FUNCTION_ARGUMENT_RANGE structure [.NET Framework profiling'
ms.assetid: 9f469eac-ac66-419b-8668-fe705bc1a51f
topic_type:
- apiref
ms.openlocfilehash: 223ad57f0b317bf75778d4e5355ec129185f5a29
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449483"
---
# <a name="cor_prf_function_argument_range-structure"></a><span data-ttu-id="95abd-102">COR_PRF_FUNCTION_ARGUMENT_RANGE – struktura</span><span class="sxs-lookup"><span data-stu-id="95abd-102">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>
<span data-ttu-id="95abd-103">Představuje blok argumentů funkce uložených souvisle v pořadí v paměti zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="95abd-103">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95abd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95abd-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_RANGE {  
    UINT_PTR startAddress;  
    ULONG length;  
} COR_PRF_FUNCTION_ARGUMENT_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="95abd-105">Members</span><span class="sxs-lookup"><span data-stu-id="95abd-105">Members</span></span>  
  
|<span data-ttu-id="95abd-106">Members</span><span class="sxs-lookup"><span data-stu-id="95abd-106">Members</span></span>|<span data-ttu-id="95abd-107">Popis</span><span class="sxs-lookup"><span data-stu-id="95abd-107">Description</span></span>|  
|-------------|-----------------|  
|`startAddress`|<span data-ttu-id="95abd-108">Počáteční adresa bloku.</span><span class="sxs-lookup"><span data-stu-id="95abd-108">The starting address of the block.</span></span>|  
|`length`|<span data-ttu-id="95abd-109">Délka souvislého bloku</span><span class="sxs-lookup"><span data-stu-id="95abd-109">The length of the contiguous block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="95abd-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="95abd-110">Requirements</span></span>  
 <span data-ttu-id="95abd-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95abd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95abd-112">**Hlavička:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="95abd-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="95abd-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="95abd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95abd-114">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95abd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95abd-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="95abd-115">See also</span></span>

- [<span data-ttu-id="95abd-116">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="95abd-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
