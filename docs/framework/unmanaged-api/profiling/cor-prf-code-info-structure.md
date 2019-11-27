---
title: COR_PRF_CODE_INFO – struktura
ms.date: 03/30/2017
api_name:
- COR_PRF_CODE_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CODE_INFO
helpviewer_keywords:
- COR_PRF_CODE_INFO structure [.NET Framework profiling]
ms.assetid: cf30e27c-1f7e-43a2-ba1e-01e4137301db
topic_type:
- apiref
ms.openlocfilehash: 643c9d7104c374d9141a604083f3fdcd540156c4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428386"
---
# <a name="cor_prf_code_info-structure"></a><span data-ttu-id="b8533-102">COR_PRF_CODE_INFO – struktura</span><span class="sxs-lookup"><span data-stu-id="b8533-102">COR_PRF_CODE_INFO Structure</span></span>
<span data-ttu-id="b8533-103">Představuje jeden souvislý blok nativního kódu uložený v paměti.</span><span class="sxs-lookup"><span data-stu-id="b8533-103">Represents one contiguous block of native code stored in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8533-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8533-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_CODE_INFO {  
    UINT_PTR startAddress;  
    SIZE_T size;  
} COR_PRF_CODE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="b8533-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b8533-105">Members</span></span>  
  
|<span data-ttu-id="b8533-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b8533-106">Member</span></span>|<span data-ttu-id="b8533-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b8533-107">Description</span></span>|  
|------------|-----------------|  
|`startAddress`|<span data-ttu-id="b8533-108">Počáteční adresa souvislého bloku kódu.</span><span class="sxs-lookup"><span data-stu-id="b8533-108">The starting address of the contiguous block of code.</span></span>|  
|`size`|<span data-ttu-id="b8533-109">Velikost bloku</span><span class="sxs-lookup"><span data-stu-id="b8533-109">The size of the block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b8533-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b8533-110">Requirements</span></span>  
 <span data-ttu-id="b8533-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8533-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8533-112">**Hlavička:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="b8533-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="b8533-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b8533-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8533-114">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8533-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8533-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b8533-115">See also</span></span>

- [<span data-ttu-id="b8533-116">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="b8533-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
