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
ms.openlocfilehash: 45ae947cda5b4ddadfb10f5b2bdc78a95f031703
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420681"
---
# <a name="stacktrace_simplecontext-structure"></a><span data-ttu-id="65dcd-102">StackTrace_SimpleContext – struktura</span><span class="sxs-lookup"><span data-stu-id="65dcd-102">StackTrace_SimpleContext Structure</span></span>
<span data-ttu-id="65dcd-103">Poskytuje jednoduchý kontext, který lze použít místo úplné `CONTEXT` struktury.</span><span class="sxs-lookup"><span data-stu-id="65dcd-103">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65dcd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65dcd-104">Syntax</span></span>  
  
```cpp  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a><span data-ttu-id="65dcd-105">Členové</span><span class="sxs-lookup"><span data-stu-id="65dcd-105">Members</span></span>  
  
|<span data-ttu-id="65dcd-106">Člen</span><span class="sxs-lookup"><span data-stu-id="65dcd-106">Member</span></span>|<span data-ttu-id="65dcd-107">Popis</span><span class="sxs-lookup"><span data-stu-id="65dcd-107">Description</span></span>|  
|------------|-----------------|  
|`StackOffset`|<span data-ttu-id="65dcd-108">Ukazatel zásobníku nebo ukazatel na vložení zásobníku (ESP) na platformách x86.</span><span class="sxs-lookup"><span data-stu-id="65dcd-108">The stack pointer, or the enter stack pointer (ESP) on x86 platforms.</span></span>|  
|`FrameOffset`|<span data-ttu-id="65dcd-109">Posun snímku nebo EBP registr na platformách x86.</span><span class="sxs-lookup"><span data-stu-id="65dcd-109">The frame offset, or the EBP register on x86 platforms.</span></span>|  
|`InstructionOffset`|<span data-ttu-id="65dcd-110">Ukazatel na instrukci nebo ukazatel na instrukci ENTER (EIP) na platformách x86.</span><span class="sxs-lookup"><span data-stu-id="65dcd-110">The instruction pointer, or the enter instruction pointer (EIP) on x86 platforms.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65dcd-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="65dcd-111">Remarks</span></span>  
 <span data-ttu-id="65dcd-112">Vzhledem k tomu, že funkce trasování zásobníku obvykle potřebují vracet pouze adresu, posun snímku a adresu zásobníku, můžete `SimpleContext` místo velké struktury použít strukturu `CONTEXT` .</span><span class="sxs-lookup"><span data-stu-id="65dcd-112">Because stack trace functions typically need to return only the address, frame offset, and stack address, you can optionally use the `SimpleContext` structure instead of a large `CONTEXT` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65dcd-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="65dcd-113">Requirements</span></span>  
 <span data-ttu-id="65dcd-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65dcd-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65dcd-115">**Hlavička:** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="65dcd-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="65dcd-116">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65dcd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65dcd-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="65dcd-117">See also</span></span>

- [<span data-ttu-id="65dcd-118">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="65dcd-118">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="65dcd-119">Ladění</span><span class="sxs-lookup"><span data-stu-id="65dcd-119">Debugging</span></span>](index.md)
