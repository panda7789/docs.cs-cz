---
title: StackTrace_SimpleContext – struktura
ms.date: 03/30/2017
api_name:
- StackTrace_SimpleContext
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SimpleContext
helpviewer_keywords:
- SimpleContext structure [.NET Framework debugging]
- StackTrace_SimpleContext structure [.NET Framework debugging]
ms.assetid: d4cef11f-a8ca-49bc-a1b8-6631f9e28f3e
topic_type:
- apiref
ms.openlocfilehash: 1cd3c34fc292e4a050fa8a75078283e34425fc8f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139132"
---
# <a name="stacktrace_simplecontext-structure"></a><span data-ttu-id="70dcb-102">StackTrace_SimpleContext – struktura</span><span class="sxs-lookup"><span data-stu-id="70dcb-102">StackTrace_SimpleContext Structure</span></span>
<span data-ttu-id="70dcb-103">Poskytuje jednoduchý kontext, který lze použít místo úplné `CONTEXT` struktury.</span><span class="sxs-lookup"><span data-stu-id="70dcb-103">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70dcb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70dcb-104">Syntax</span></span>  
  
```cpp  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a><span data-ttu-id="70dcb-105">Členové</span><span class="sxs-lookup"><span data-stu-id="70dcb-105">Members</span></span>  
  
|<span data-ttu-id="70dcb-106">Člen</span><span class="sxs-lookup"><span data-stu-id="70dcb-106">Member</span></span>|<span data-ttu-id="70dcb-107">Popis</span><span class="sxs-lookup"><span data-stu-id="70dcb-107">Description</span></span>|  
|------------|-----------------|  
|`StackOffset`|<span data-ttu-id="70dcb-108">Ukazatel zásobníku nebo ukazatel na vložení zásobníku (ESP) na platformách x86.</span><span class="sxs-lookup"><span data-stu-id="70dcb-108">The stack pointer, or the enter stack pointer (ESP) on x86 platforms.</span></span>|  
|`FrameOffset`|<span data-ttu-id="70dcb-109">Posun snímku nebo EBP registr na platformách x86.</span><span class="sxs-lookup"><span data-stu-id="70dcb-109">The frame offset, or the EBP register on x86 platforms.</span></span>|  
|`InstructionOffset`|<span data-ttu-id="70dcb-110">Ukazatel na instrukci nebo ukazatel na instrukci ENTER (EIP) na platformách x86.</span><span class="sxs-lookup"><span data-stu-id="70dcb-110">The instruction pointer, or the enter instruction pointer (EIP) on x86 platforms.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70dcb-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="70dcb-111">Remarks</span></span>  
 <span data-ttu-id="70dcb-112">Vzhledem k tomu, že funkce trasování zásobníku obvykle potřebují vracet pouze adresu, posun snímku a adresu zásobníku, můžete místo velké `CONTEXT` struktury použít `SimpleContext` strukturu.</span><span class="sxs-lookup"><span data-stu-id="70dcb-112">Because stack trace functions typically need to return only the address, frame offset, and stack address, you can optionally use the `SimpleContext` structure instead of a large `CONTEXT` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70dcb-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="70dcb-113">Requirements</span></span>  
 <span data-ttu-id="70dcb-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70dcb-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70dcb-115">**Hlavička:** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="70dcb-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="70dcb-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70dcb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70dcb-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70dcb-117">See also</span></span>

- [<span data-ttu-id="70dcb-118">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="70dcb-118">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="70dcb-119">Ladění</span><span class="sxs-lookup"><span data-stu-id="70dcb-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
