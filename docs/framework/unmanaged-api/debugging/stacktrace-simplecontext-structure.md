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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc0fc18e31b89b22ffd30d99a8b079ed7b87fa1b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752499"
---
# <a name="stacktracesimplecontext-structure"></a><span data-ttu-id="49cd9-102">StackTrace_SimpleContext – struktura</span><span class="sxs-lookup"><span data-stu-id="49cd9-102">StackTrace_SimpleContext Structure</span></span>
<span data-ttu-id="49cd9-103">Poskytuje jednoduchý kontext, který jde použít místo úplné `CONTEXT` struktury.</span><span class="sxs-lookup"><span data-stu-id="49cd9-103">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49cd9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49cd9-104">Syntax</span></span>  
  
```cpp  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a><span data-ttu-id="49cd9-105">Členové</span><span class="sxs-lookup"><span data-stu-id="49cd9-105">Members</span></span>  
  
|<span data-ttu-id="49cd9-106">Člen</span><span class="sxs-lookup"><span data-stu-id="49cd9-106">Member</span></span>|<span data-ttu-id="49cd9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="49cd9-107">Description</span></span>|  
|------------|-----------------|  
|`StackOffset`|<span data-ttu-id="49cd9-108">Ukazatel zásobníku a ukazatel zásobníku enter (ESP) na x86 platformy.</span><span class="sxs-lookup"><span data-stu-id="49cd9-108">The stack pointer, or the enter stack pointer (ESP) on x86 platforms.</span></span>|  
|`FrameOffset`|<span data-ttu-id="49cd9-109">Odsazení rámce nebo registru EBP na x86 platformy.</span><span class="sxs-lookup"><span data-stu-id="49cd9-109">The frame offset, or the EBP register on x86 platforms.</span></span>|  
|`InstructionOffset`|<span data-ttu-id="49cd9-110">Ukazatele na instrukci nebo ukazatele na instrukci enter (EIP) na x86 platformy.</span><span class="sxs-lookup"><span data-stu-id="49cd9-110">The instruction pointer, or the enter instruction pointer (EIP) on x86 platforms.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49cd9-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="49cd9-111">Remarks</span></span>  
 <span data-ttu-id="49cd9-112">Protože funkce trasování zásobníku je obvykle potřeba vrátit pouze adresy, odsazení rámce a adresy zásobníku, můžete volitelně použít `SimpleContext` struktura místo velké `CONTEXT` struktury.</span><span class="sxs-lookup"><span data-stu-id="49cd9-112">Because stack trace functions typically need to return only the address, frame offset, and stack address, you can optionally use the `SimpleContext` structure instead of a large `CONTEXT` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49cd9-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="49cd9-113">Requirements</span></span>  
 <span data-ttu-id="49cd9-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49cd9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49cd9-115">**Záhlaví:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="49cd9-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="49cd9-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49cd9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49cd9-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="49cd9-117">See also</span></span>

- [<span data-ttu-id="49cd9-118">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="49cd9-118">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="49cd9-119">Ladění</span><span class="sxs-lookup"><span data-stu-id="49cd9-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
