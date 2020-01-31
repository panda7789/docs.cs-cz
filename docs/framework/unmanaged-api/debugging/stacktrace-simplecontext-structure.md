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
ms.openlocfilehash: c81a5787eb06971e3d52aff5d1c1154a72564daf
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790338"
---
# <a name="stacktrace_simplecontext-structure"></a><span data-ttu-id="903b1-102">StackTrace_SimpleContext – struktura</span><span class="sxs-lookup"><span data-stu-id="903b1-102">StackTrace_SimpleContext Structure</span></span>
<span data-ttu-id="903b1-103">Poskytuje jednoduchý kontext, který lze použít místo úplné `CONTEXT` struktury.</span><span class="sxs-lookup"><span data-stu-id="903b1-103">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="903b1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="903b1-104">Syntax</span></span>  
  
```cpp  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a><span data-ttu-id="903b1-105">Členové</span><span class="sxs-lookup"><span data-stu-id="903b1-105">Members</span></span>  
  
|<span data-ttu-id="903b1-106">Člen</span><span class="sxs-lookup"><span data-stu-id="903b1-106">Member</span></span>|<span data-ttu-id="903b1-107">Popis</span><span class="sxs-lookup"><span data-stu-id="903b1-107">Description</span></span>|  
|------------|-----------------|  
|`StackOffset`|<span data-ttu-id="903b1-108">Ukazatel zásobníku nebo ukazatel na vložení zásobníku (ESP) na platformách x86.</span><span class="sxs-lookup"><span data-stu-id="903b1-108">The stack pointer, or the enter stack pointer (ESP) on x86 platforms.</span></span>|  
|`FrameOffset`|<span data-ttu-id="903b1-109">Posun snímku nebo EBP registr na platformách x86.</span><span class="sxs-lookup"><span data-stu-id="903b1-109">The frame offset, or the EBP register on x86 platforms.</span></span>|  
|`InstructionOffset`|<span data-ttu-id="903b1-110">Ukazatel na instrukci nebo ukazatel na instrukci ENTER (EIP) na platformách x86.</span><span class="sxs-lookup"><span data-stu-id="903b1-110">The instruction pointer, or the enter instruction pointer (EIP) on x86 platforms.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="903b1-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="903b1-111">Remarks</span></span>  
 <span data-ttu-id="903b1-112">Vzhledem k tomu, že funkce trasování zásobníku obvykle potřebují vracet pouze adresu, posun snímku a adresu zásobníku, můžete místo velké `CONTEXT` struktury použít `SimpleContext` strukturu.</span><span class="sxs-lookup"><span data-stu-id="903b1-112">Because stack trace functions typically need to return only the address, frame offset, and stack address, you can optionally use the `SimpleContext` structure instead of a large `CONTEXT` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="903b1-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="903b1-113">Requirements</span></span>  
 <span data-ttu-id="903b1-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="903b1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="903b1-115">**Hlavička:** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="903b1-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="903b1-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="903b1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="903b1-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="903b1-117">See also</span></span>

- [<span data-ttu-id="903b1-118">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="903b1-118">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="903b1-119">Ladění</span><span class="sxs-lookup"><span data-stu-id="903b1-119">Debugging</span></span>](index.md)
