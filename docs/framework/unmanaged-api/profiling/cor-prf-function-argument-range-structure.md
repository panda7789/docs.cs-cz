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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c0c0679dac84089577a2698ed8b0b5497a1a81e8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753899"
---
# <a name="corprffunctionargumentrange-structure"></a><span data-ttu-id="dddcf-102">COR_PRF_FUNCTION_ARGUMENT_RANGE – struktura</span><span class="sxs-lookup"><span data-stu-id="dddcf-102">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>
<span data-ttu-id="dddcf-103">Představuje blok argumentů funkce, které jsou uložena souvisle v pořadí zleva doprava v paměti.</span><span class="sxs-lookup"><span data-stu-id="dddcf-103">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dddcf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dddcf-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_RANGE {  
    UINT_PTR startAddress;  
    ULONG length;  
} COR_PRF_FUNCTION_ARGUMENT_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="dddcf-105">Členové</span><span class="sxs-lookup"><span data-stu-id="dddcf-105">Members</span></span>  
  
|<span data-ttu-id="dddcf-106">Členové</span><span class="sxs-lookup"><span data-stu-id="dddcf-106">Members</span></span>|<span data-ttu-id="dddcf-107">Popis</span><span class="sxs-lookup"><span data-stu-id="dddcf-107">Description</span></span>|  
|-------------|-----------------|  
|`startAddress`|<span data-ttu-id="dddcf-108">Počáteční adresa bloku.</span><span class="sxs-lookup"><span data-stu-id="dddcf-108">The starting address of the block.</span></span>|  
|`length`|<span data-ttu-id="dddcf-109">Délka souvislém bloku.</span><span class="sxs-lookup"><span data-stu-id="dddcf-109">The length of the contiguous block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dddcf-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dddcf-110">Requirements</span></span>  
 <span data-ttu-id="dddcf-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dddcf-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dddcf-112">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="dddcf-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="dddcf-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dddcf-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dddcf-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dddcf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dddcf-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dddcf-115">See also</span></span>

- [<span data-ttu-id="dddcf-116">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="dddcf-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
