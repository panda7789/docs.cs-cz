---
title: "CorDebugRegister – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorDebugRegister
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugRegister
helpviewer_keywords:
- CorDebugRegister enumeration [.NET Framework debugging]
ms.assetid: 003bb138-7960-4291-ac88-0d87e470ff70
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3f168e686a127b2763099d2cfaea7ff396c4e734
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugregister-enumeration"></a><span data-ttu-id="a5154-102">CorDebugRegister – výčet</span><span class="sxs-lookup"><span data-stu-id="a5154-102">CorDebugRegister Enumeration</span></span>
<span data-ttu-id="a5154-103">Určuje registry spojené s danou procesoru architektura.</span><span class="sxs-lookup"><span data-stu-id="a5154-103">Specifies the registers associated with a given processor architecture.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5154-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5154-104">Syntax</span></span>  
  
```  
typedef enum CorDebugRegister {  
  
    REGISTER_INSTRUCTION_POINTER = 0,  
    REGISTER_STACK_POINTER,  
    REGISTER_FRAME_POINTER,  
  
    REGISTER_X86_EIP = 0,  
    REGISTER_X86_ESP,  
    REGISTER_X86_EBP,  
  
    REGISTER_X86_EAX,  
    REGISTER_X86_ECX,  
    REGISTER_X86_EDX,  
    REGISTER_X86_EBX,  
  
    REGISTER_X86_ESI,  
    REGISTER_X86_EDI,  
  
    REGISTER_X86_FPSTACK_0,  
    REGISTER_X86_FPSTACK_1,  
    REGISTER_X86_FPSTACK_2,  
    REGISTER_X86_FPSTACK_3,  
    REGISTER_X86_FPSTACK_4,  
    REGISTER_X86_FPSTACK_5,  
    REGISTER_X86_FPSTACK_6,  
    REGISTER_X86_FPSTACK_7,  
  
    REGISTER_AMD64_RIP = 0,  
    REGISTER_AMD64_RSP,  
    REGISTER_AMD64_RBP,  
    REGISTER_AMD64_RAX,  
    REGISTER_AMD64_RCX,  
    REGISTER_AMD64_RDX,  
    REGISTER_AMD64_RBX,  
    REGISTER_AMD64_RSI,  
    REGISTER_AMD64_RDI,  
    REGISTER_AMD64_R8,  
    REGISTER_AMD64_R9,  
    REGISTER_AMD64_R10,  
    REGISTER_AMD64_R11,  
    REGISTER_AMD64_R12,  
    REGISTER_AMD64_R13,  
    REGISTER_AMD64_R14,  
    REGISTER_AMD64_R15,  
  
    REGISTER_AMD64_XMM0,  
    REGISTER_AMD64_XMM1,  
    REGISTER_AMD64_XMM2,  
    REGISTER_AMD64_XMM3,  
    REGISTER_AMD64_XMM4,  
    REGISTER_AMD64_XMM5,  
    REGISTER_AMD64_XMM6,  
    REGISTER_AMD64_XMM7,  
    REGISTER_AMD64_XMM8,  
    REGISTER_AMD64_XMM9,  
    REGISTER_AMD64_XMM10,  
    REGISTER_AMD64_XMM11,  
    REGISTER_AMD64_XMM12,  
    REGISTER_AMD64_XMM13,  
    REGISTER_AMD64_XMM14,  
    REGISTER_AMD64_XMM15,  
  
    REGISTER_IA64_BSP = REGISTER_FRAME_POINTER,  
    REGISTER_IA64_R0  = REGISTER_IA64_BSP + 1,  
    REGISTER_IA64_F0  = REGISTER_IA64_R0  + 128,  
    REGISTER_ARM_PC = 0,  
    REGISTER_ARM_SP,  
    REGISTER_ARM_R0,  
    REGISTER_ARM_R1,  
    REGISTER_ARM_R2,  
    REGISTER_ARM_R3,  
    REGISTER_ARM_R4,  
    REGISTER_ARM_R5,  
    REGISTER_ARM_R6,  
    REGISTER_ARM_R7,  
    REGISTER_ARM_R8,  
    REGISTER_ARM_R9,  
    REGISTER_ARM_R10,  
    REGISTER_ARM_R11,  
    REGISTER_ARM_R12,  
    REGISTER_ARM_LR,  
  
} CorDebugRegister;  
```  
  
## <a name="members"></a><span data-ttu-id="a5154-105">Členové</span><span class="sxs-lookup"><span data-stu-id="a5154-105">Members</span></span>  
  
|<span data-ttu-id="a5154-106">Člen</span><span class="sxs-lookup"><span data-stu-id="a5154-106">Member</span></span>|<span data-ttu-id="a5154-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a5154-107">Description</span></span>|  
|------------|-----------------|  
|`REGISTER_INSTRUCTION_POINTER`|<span data-ttu-id="a5154-108">Ukazatele instrukce zaregistrovat na jakýkoli procesor.</span><span class="sxs-lookup"><span data-stu-id="a5154-108">An instruction pointer register on any processor.</span></span>|  
|`REGISTER_STACK_POINTER`|<span data-ttu-id="a5154-109">Ukazatel zásobníku zaregistrovat na jakýkoli procesor.</span><span class="sxs-lookup"><span data-stu-id="a5154-109">A stack pointer register on any processor.</span></span>|  
|`REGISTER_FRAME_POINTER`|<span data-ttu-id="a5154-110">Ukazatel na rámec zaregistrovat na jakýkoli procesor.</span><span class="sxs-lookup"><span data-stu-id="a5154-110">A frame pointer register on any processor.</span></span>|  
|`REGISTER_X86_EIP`|<span data-ttu-id="a5154-111">Registrace ukazatel instrukce na x86 procesoru.</span><span class="sxs-lookup"><span data-stu-id="a5154-111">The instruction pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_ESP`|<span data-ttu-id="a5154-112">Registrace ukazatel zásobníku na x86 procesoru.</span><span class="sxs-lookup"><span data-stu-id="a5154-112">The stack pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_EBP`|<span data-ttu-id="a5154-113">Registr základní ukazatele na x86 procesoru.</span><span class="sxs-lookup"><span data-stu-id="a5154-113">The base pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_EAX`|<span data-ttu-id="a5154-114">A data zaregistrujte na x86 procesoru.</span><span class="sxs-lookup"><span data-stu-id="a5154-114">The A data register on the x86 processor.</span></span>|  
|`REGISTER_X86_ECX`|<span data-ttu-id="a5154-115">C data zaregistrovat na x86 procesoru.</span><span class="sxs-lookup"><span data-stu-id="a5154-115">The C data register on the x86 processor.</span></span>|  
|`REGISTER_X86_EDX`|<span data-ttu-id="a5154-116">D data zaregistrovat na x86 procesoru.</span><span class="sxs-lookup"><span data-stu-id="a5154-116">The D data register on the x86 processor.</span></span>|  
|`REGISTER_X86_EBX`|<span data-ttu-id="a5154-117">B data zaregistrovat na x86 procesoru.</span><span class="sxs-lookup"><span data-stu-id="a5154-117">The B data register on the x86 processor.</span></span>|  
|`REGISTER_X86_ESI`|<span data-ttu-id="a5154-118">Index registrace zdroje na x86 procesoru.</span><span class="sxs-lookup"><span data-stu-id="a5154-118">The source index register on the x86 processor.</span></span>|  
|`REGISTER_X86_EDI`|<span data-ttu-id="a5154-119">Registrace index cílového na x86 procesoru.</span><span class="sxs-lookup"><span data-stu-id="a5154-119">The destination index register on the x86 processor.</span></span>|  
|`REGISTER_X86_FPSTACK_0`|<span data-ttu-id="a5154-120">Procesor registrace 0 na s plovoucí desetinnou čárkou x86 (FP) zásobníku.</span><span class="sxs-lookup"><span data-stu-id="a5154-120">The stack register 0 on the x86 floating-point (FP) processor.</span></span>|  
|`REGISTER_X86_FPSTACK_1`|<span data-ttu-id="a5154-121">Zásobník #1 zaregistrovat na x86 FP procesoru.</span><span class="sxs-lookup"><span data-stu-id="a5154-121">The #1 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_2`|<span data-ttu-id="a5154-122">Zásobník #2 zaregistrovat na x86 FP procesoru.</span><span class="sxs-lookup"><span data-stu-id="a5154-122">The #2 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_3`|<span data-ttu-id="a5154-123">Zásobník #3 zaregistrovat na x86 FP procesoru.</span><span class="sxs-lookup"><span data-stu-id="a5154-123">The #3 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_4`|<span data-ttu-id="a5154-124">Zásobník #4 zaregistrovat na x86 FP procesoru.</span><span class="sxs-lookup"><span data-stu-id="a5154-124">The #4 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_5`|<span data-ttu-id="a5154-125">Zásobník #5 zaregistrovat na x86 FP procesoru.</span><span class="sxs-lookup"><span data-stu-id="a5154-125">The #5 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_6`|<span data-ttu-id="a5154-126">Zásobník #6 zaregistrovat na x86 FP procesoru.</span><span class="sxs-lookup"><span data-stu-id="a5154-126">The #6 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_7`|<span data-ttu-id="a5154-127">Zásobník #7 zaregistrovat na x86 FP procesoru.</span><span class="sxs-lookup"><span data-stu-id="a5154-127">The #7 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_AMD64_RIP`|<span data-ttu-id="a5154-128">Ukazatel instrukce zaregistrovat na procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="a5154-128">The instruction pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RSP`|<span data-ttu-id="a5154-129">Ukazatel zásobníku zaregistrovat na procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="a5154-129">The stack pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RBP`|<span data-ttu-id="a5154-130">Základní ukazatele zaregistrovat na procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="a5154-130">The base pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RAX`|<span data-ttu-id="a5154-131">A data zaregistrovat na procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="a5154-131">The A data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RCX`|<span data-ttu-id="a5154-132">C data zaregistrovat na procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="a5154-132">The C data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RDX`|<span data-ttu-id="a5154-133">D data zaregistrovat na procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="a5154-133">The D data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RBX`|<span data-ttu-id="a5154-134">B data zaregistrovat na procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="a5154-134">The B data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RSI`|<span data-ttu-id="a5154-135">Index zdroje zaregistrovat na procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="a5154-135">The source index register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RDI`|<span data-ttu-id="a5154-136">Cílový index zaregistrovat na procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="a5154-136">The destination index register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R8`|<span data-ttu-id="a5154-137">Data #8 zaregistrovat na procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="a5154-137">The #8 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R9`|<span data-ttu-id="a5154-138">Data #9 zaregistrovat na procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="a5154-138">The #9 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R10`|<span data-ttu-id="a5154-139">Data #10 zaregistrovat na procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="a5154-139">The #10 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R11`|<span data-ttu-id="a5154-140">Data #11 zaregistrovat na procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="a5154-140">The #11 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R12`|<span data-ttu-id="a5154-141">Data #12 zaregistrovat na procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="a5154-141">The #12 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R13`|<span data-ttu-id="a5154-142">Data #13 zaregistrovat na procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="a5154-142">The #13 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R14`|<span data-ttu-id="a5154-143">Data #14 zaregistrovat na procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="a5154-143">The #14 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R15`|<span data-ttu-id="a5154-144">Data #15 zaregistrovat na procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="a5154-144">The #15 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM0`|<span data-ttu-id="a5154-145">Multimediální #0 zaregistrovat na procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="a5154-145">The #0 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM1`|<span data-ttu-id="a5154-146">Multimediální #1 zaregistrovat na procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="a5154-146">The #1 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM2`|<span data-ttu-id="a5154-147">Multimediální #2 zaregistrovat na procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="a5154-147">The #2 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM3`|<span data-ttu-id="a5154-148">Multimediální #3 zaregistrovat na procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="a5154-148">The #3 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM4`|<span data-ttu-id="a5154-149">Multimediální #4 zaregistrovat na procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="a5154-149">The #4 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM5`|<span data-ttu-id="a5154-150">Multimediální #5 zaregistrovat na procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="a5154-150">The #5 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM6`|<span data-ttu-id="a5154-151">Multimediální #6 zaregistrovat na procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="a5154-151">The #6 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM7`|<span data-ttu-id="a5154-152">Multimediální #7 zaregistrovat na procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="a5154-152">The #7 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM8`|<span data-ttu-id="a5154-153">Multimediální #8 zaregistrovat na procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="a5154-153">The #8 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM9`|<span data-ttu-id="a5154-154">Multimediální #9 zaregistrovat na procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="a5154-154">The #9 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM10`|<span data-ttu-id="a5154-155">Multimediální #10 zaregistrovat na procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="a5154-155">The #10 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM11`|<span data-ttu-id="a5154-156">Multimediální #11 zaregistrovat na procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="a5154-156">The #11 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM12`|<span data-ttu-id="a5154-157">Multimediální #12 zaregistrovat na procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="a5154-157">The #12 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM13`|<span data-ttu-id="a5154-158">Multimediální #13 zaregistrovat na procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="a5154-158">The #13 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM14`|<span data-ttu-id="a5154-159">Multimediální #14 zaregistrovat na procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="a5154-159">The #14 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM15`|<span data-ttu-id="a5154-160">Multimediální #15 zaregistrovat na procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="a5154-160">The #15 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_IA64_BSP`|<span data-ttu-id="a5154-161">Ukazatel zásobníku zaregistrovat na procesoru IA-64.</span><span class="sxs-lookup"><span data-stu-id="a5154-161">The stack pointer register on the IA-64 processor.</span></span>|  
|`REGISTER_IA64_R0`|<span data-ttu-id="a5154-162">Data #0 zaregistrovat na procesoru IA-64.</span><span class="sxs-lookup"><span data-stu-id="a5154-162">The #0 data register on the IA-64 processor.</span></span>|  
|`REGISTER_IA64_F0`|<span data-ttu-id="a5154-163">Data FP #0 zaregistrovat na procesoru IA-64.</span><span class="sxs-lookup"><span data-stu-id="a5154-163">The #0 FP data register on the IA-64 processor.</span></span>|  
|`REGISTER_ARM_PC`|<span data-ttu-id="a5154-164">Čítač programu zaregistrovat na procesor ARM (R15).</span><span class="sxs-lookup"><span data-stu-id="a5154-164">The program counter register (R15) on the ARM processor.</span></span>|  
|`REGISTER_ARM_SP`|<span data-ttu-id="a5154-165">Ukazatel zásobníku zaregistrovat na procesor ARM (R13).</span><span class="sxs-lookup"><span data-stu-id="a5154-165">The stack pointer register (R13) on the ARM processor.</span></span>|  
|`REGISTER_ARM_R0`|<span data-ttu-id="a5154-166">Data zaregistrovat R0 na procesor ARM.</span><span class="sxs-lookup"><span data-stu-id="a5154-166">Data register R0 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R1`|<span data-ttu-id="a5154-167">Data zaregistrovat R1 na procesor ARM.</span><span class="sxs-lookup"><span data-stu-id="a5154-167">Data register R1 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R2`|<span data-ttu-id="a5154-168">Data zaregistrovat R2 na procesor ARM.</span><span class="sxs-lookup"><span data-stu-id="a5154-168">Data register R2 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R3`|<span data-ttu-id="a5154-169">Data zaregistrovat R3 na procesor ARM.</span><span class="sxs-lookup"><span data-stu-id="a5154-169">Data register R3 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R4`|<span data-ttu-id="a5154-170">Zaregistrujte R4 na procesor ARM.</span><span class="sxs-lookup"><span data-stu-id="a5154-170">Register R4 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R5`|<span data-ttu-id="a5154-171">Zaregistrujte R5 na procesor ARM.</span><span class="sxs-lookup"><span data-stu-id="a5154-171">Register R5 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R6`|<span data-ttu-id="a5154-172">Zaregistrujte R6 na procesor ARM.</span><span class="sxs-lookup"><span data-stu-id="a5154-172">Register R6 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R7`|<span data-ttu-id="a5154-173">Zaregistrovat R7 (Flash ukazatel na rámec) v procesoru ARM.</span><span class="sxs-lookup"><span data-stu-id="a5154-173">Register R7 (the THUMB frame pointer) on the ARM processor.</span></span>|  
|`REGISTER_ARM_R8`|<span data-ttu-id="a5154-174">Zaregistrujte R8 na procesor ARM.</span><span class="sxs-lookup"><span data-stu-id="a5154-174">Register R8 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R9`|<span data-ttu-id="a5154-175">Zaregistrujte R9 na procesor ARM.</span><span class="sxs-lookup"><span data-stu-id="a5154-175">Register R9 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R10`|<span data-ttu-id="a5154-176">Zaregistrujte R10 na procesor ARM.</span><span class="sxs-lookup"><span data-stu-id="a5154-176">Register R10 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R11`|<span data-ttu-id="a5154-177">Ukazatele na rámec u procesoru ARM.</span><span class="sxs-lookup"><span data-stu-id="a5154-177">The frame pointer on the ARM processor.</span></span>|  
|`REGISTER_ARM_R12`|<span data-ttu-id="a5154-178">Zaregistrujte r 12 na procesor ARM.</span><span class="sxs-lookup"><span data-stu-id="a5154-178">Register R12 on the ARM processor.</span></span>|  
|`REGISTER_ARM_LR`|<span data-ttu-id="a5154-179">Odkaz zaregistrovat na procesor ARM (R14).</span><span class="sxs-lookup"><span data-stu-id="a5154-179">The link register (R14) on the ARM processor.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5154-180">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a5154-180">Remarks</span></span>  
 <span data-ttu-id="a5154-181">Existují 128 pro obecné účely datových registrů a 128 s plovoucí desetinnou čárkou datových registrů na procesoru IA-64, ale pouze hodnoty `REGISTER_IA64_R0` a `REGISTER_IA64_F0` jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="a5154-181">There are 128 general-purpose data registers and 128 floating-point data registers on the IA-64 processor, but only values `REGISTER_IA64_R0` and `REGISTER_IA64_F0` are provided.</span></span> <span data-ttu-id="a5154-182">Ostatní hodnoty lze se určí takto:</span><span class="sxs-lookup"><span data-stu-id="a5154-182">The other values can be determined as follows:</span></span>  
  
-   <span data-ttu-id="a5154-183">Přidat číslo registrace pro `REGISTER_IA64_R0` pro hodnoty `REGISTER_IA64_R1` prostřednictvím `REGISTER_IA64_R127`, které odpovídají registr #1 dat prostřednictvím registrace #127 data na procesoru IA-64.</span><span class="sxs-lookup"><span data-stu-id="a5154-183">Add the register number to `REGISTER_IA64_R0` for values `REGISTER_IA64_R1` through `REGISTER_IA64_R127`, which correspond to the #1 data register through the #127 data register on the IA-64 processor.</span></span>  
  
-   <span data-ttu-id="a5154-184">Přidat číslo registrace pro `REGISTER_IA64_F0` pro hodnoty `REGISTER_IA64_F1` prostřednictvím `REGISTER_IA64_F127`, které odpovídají registr dat FP #1 až #127 FP registr dat na procesoru IA-64.</span><span class="sxs-lookup"><span data-stu-id="a5154-184">Add the register number to `REGISTER_IA64_F0` for values `REGISTER_IA64_F1` through `REGISTER_IA64_F127`, which correspond to the #1 FP data register through the #127 FP data register on the IA-64 processor.</span></span>  
  
 <span data-ttu-id="a5154-185">Například pokud je třeba zadat registr #83 dat na procesoru IA-64, použijte `REGISTER_IA64_R0` + 83.</span><span class="sxs-lookup"><span data-stu-id="a5154-185">For example, if you need to specify the #83 data register on the IA-64 processor, use `REGISTER_IA64_R0` + 83.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5154-186">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a5154-186">Requirements</span></span>  
 <span data-ttu-id="a5154-187">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5154-187">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5154-188">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a5154-188">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5154-189">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5154-189">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5154-190">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5154-190">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5154-191">Viz také</span><span class="sxs-lookup"><span data-stu-id="a5154-191">See Also</span></span>  
 [<span data-ttu-id="a5154-192">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="a5154-192">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
