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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2f236a74da04dfddef852514eccb02215ad2d15a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752385"
---
# <a name="corprfcodeinfo-structure"></a><span data-ttu-id="259e0-102">COR_PRF_CODE_INFO – struktura</span><span class="sxs-lookup"><span data-stu-id="259e0-102">COR_PRF_CODE_INFO Structure</span></span>
<span data-ttu-id="259e0-103">Představuje jeden souvislý blok nativní kód uložen v paměti.</span><span class="sxs-lookup"><span data-stu-id="259e0-103">Represents one contiguous block of native code stored in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="259e0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="259e0-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_CODE_INFO {  
    UINT_PTR startAddress;  
    SIZE_T size;  
} COR_PRF_CODE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="259e0-105">Členové</span><span class="sxs-lookup"><span data-stu-id="259e0-105">Members</span></span>  
  
|<span data-ttu-id="259e0-106">Člen</span><span class="sxs-lookup"><span data-stu-id="259e0-106">Member</span></span>|<span data-ttu-id="259e0-107">Popis</span><span class="sxs-lookup"><span data-stu-id="259e0-107">Description</span></span>|  
|------------|-----------------|  
|`startAddress`|<span data-ttu-id="259e0-108">Počáteční adresa souvislém bloku kódu.</span><span class="sxs-lookup"><span data-stu-id="259e0-108">The starting address of the contiguous block of code.</span></span>|  
|`size`|<span data-ttu-id="259e0-109">Velikost bloku.</span><span class="sxs-lookup"><span data-stu-id="259e0-109">The size of the block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="259e0-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="259e0-110">Requirements</span></span>  
 <span data-ttu-id="259e0-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="259e0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="259e0-112">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="259e0-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="259e0-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="259e0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="259e0-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="259e0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="259e0-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="259e0-115">See also</span></span>

- [<span data-ttu-id="259e0-116">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="259e0-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
