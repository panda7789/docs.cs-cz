---
title: CorDebugRegister – výčet
ms.date: 03/30/2017
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
ms.openlocfilehash: d182476130e611e57df232c9652cda4bec002c31
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132773"
---
# <a name="cordebugregister-enumeration"></a><span data-ttu-id="856b0-102">CorDebugRegister – výčet</span><span class="sxs-lookup"><span data-stu-id="856b0-102">CorDebugRegister Enumeration</span></span>
<span data-ttu-id="856b0-103">Určuje Registry přidružené k dané architektuře procesoru.</span><span class="sxs-lookup"><span data-stu-id="856b0-103">Specifies the registers associated with a given processor architecture.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="856b0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="856b0-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="856b0-105">Členové</span><span class="sxs-lookup"><span data-stu-id="856b0-105">Members</span></span>  
  
|<span data-ttu-id="856b0-106">Člen</span><span class="sxs-lookup"><span data-stu-id="856b0-106">Member</span></span>|<span data-ttu-id="856b0-107">Popis</span><span class="sxs-lookup"><span data-stu-id="856b0-107">Description</span></span>|  
|------------|-----------------|  
|`REGISTER_INSTRUCTION_POINTER`|<span data-ttu-id="856b0-108">Registr ukazatele na instrukce pro libovolný procesor.</span><span class="sxs-lookup"><span data-stu-id="856b0-108">An instruction pointer register on any processor.</span></span>|  
|`REGISTER_STACK_POINTER`|<span data-ttu-id="856b0-109">Registr ukazatele zásobníku na jakémkoli procesoru.</span><span class="sxs-lookup"><span data-stu-id="856b0-109">A stack pointer register on any processor.</span></span>|  
|`REGISTER_FRAME_POINTER`|<span data-ttu-id="856b0-110">Registr ukazatele na rámec u libovolného procesoru.</span><span class="sxs-lookup"><span data-stu-id="856b0-110">A frame pointer register on any processor.</span></span>|  
|`REGISTER_X86_EIP`|<span data-ttu-id="856b0-111">Registr ukazatele na instrukce pro procesor x86.</span><span class="sxs-lookup"><span data-stu-id="856b0-111">The instruction pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_ESP`|<span data-ttu-id="856b0-112">Registr ukazatele zásobníku v procesoru x86.</span><span class="sxs-lookup"><span data-stu-id="856b0-112">The stack pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_EBP`|<span data-ttu-id="856b0-113">Základní ukazatel se registruje v procesoru x86.</span><span class="sxs-lookup"><span data-stu-id="856b0-113">The base pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_EAX`|<span data-ttu-id="856b0-114">Záznam dat v procesoru x86.</span><span class="sxs-lookup"><span data-stu-id="856b0-114">The A data register on the x86 processor.</span></span>|  
|`REGISTER_X86_ECX`|<span data-ttu-id="856b0-115">Registr dat C v procesoru x86.</span><span class="sxs-lookup"><span data-stu-id="856b0-115">The C data register on the x86 processor.</span></span>|  
|`REGISTER_X86_EDX`|<span data-ttu-id="856b0-116">Registr dat D v procesoru x86.</span><span class="sxs-lookup"><span data-stu-id="856b0-116">The D data register on the x86 processor.</span></span>|  
|`REGISTER_X86_EBX`|<span data-ttu-id="856b0-117">Registr dat B v procesoru x86.</span><span class="sxs-lookup"><span data-stu-id="856b0-117">The B data register on the x86 processor.</span></span>|  
|`REGISTER_X86_ESI`|<span data-ttu-id="856b0-118">Registr zdrojového indexu v procesoru x86.</span><span class="sxs-lookup"><span data-stu-id="856b0-118">The source index register on the x86 processor.</span></span>|  
|`REGISTER_X86_EDI`|<span data-ttu-id="856b0-119">Registr cílového indexu v procesoru x86.</span><span class="sxs-lookup"><span data-stu-id="856b0-119">The destination index register on the x86 processor.</span></span>|  
|`REGISTER_X86_FPSTACK_0`|<span data-ttu-id="856b0-120">Registr zásobníku 0 v procesoru s plovoucí desetinnou čárkou (FP) x86.</span><span class="sxs-lookup"><span data-stu-id="856b0-120">The stack register 0 on the x86 floating-point (FP) processor.</span></span>|  
|`REGISTER_X86_FPSTACK_1`|<span data-ttu-id="856b0-121">#1 registr zásobníku na procesoru x86 FP.</span><span class="sxs-lookup"><span data-stu-id="856b0-121">The #1 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_2`|<span data-ttu-id="856b0-122">#2 registr zásobníku na procesoru x86 FP.</span><span class="sxs-lookup"><span data-stu-id="856b0-122">The #2 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_3`|<span data-ttu-id="856b0-123">#3 registr zásobníku na procesoru x86 FP.</span><span class="sxs-lookup"><span data-stu-id="856b0-123">The #3 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_4`|<span data-ttu-id="856b0-124">#4 registr zásobníku na procesoru x86 FP.</span><span class="sxs-lookup"><span data-stu-id="856b0-124">The #4 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_5`|<span data-ttu-id="856b0-125">#5 registr zásobníku na procesoru x86 FP.</span><span class="sxs-lookup"><span data-stu-id="856b0-125">The #5 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_6`|<span data-ttu-id="856b0-126">#6 registr zásobníku na procesoru x86 FP.</span><span class="sxs-lookup"><span data-stu-id="856b0-126">The #6 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_7`|<span data-ttu-id="856b0-127">#7 registr zásobníku na procesoru x86 FP.</span><span class="sxs-lookup"><span data-stu-id="856b0-127">The #7 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_AMD64_RIP`|<span data-ttu-id="856b0-128">Registr ukazatele na instrukce pro procesor AMD64.</span><span class="sxs-lookup"><span data-stu-id="856b0-128">The instruction pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RSP`|<span data-ttu-id="856b0-129">Registr ukazatele zásobníku v procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="856b0-129">The stack pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RBP`|<span data-ttu-id="856b0-130">Základní ukazatel se registruje na procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="856b0-130">The base pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RAX`|<span data-ttu-id="856b0-131">Záznam dat na procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="856b0-131">The A data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RCX`|<span data-ttu-id="856b0-132">Registr dat C v procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="856b0-132">The C data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RDX`|<span data-ttu-id="856b0-133">Registr dat D v procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="856b0-133">The D data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RBX`|<span data-ttu-id="856b0-134">Registr dat B v procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="856b0-134">The B data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RSI`|<span data-ttu-id="856b0-135">Registr zdrojového indexu v procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="856b0-135">The source index register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RDI`|<span data-ttu-id="856b0-136">Registr cílového indexu v procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="856b0-136">The destination index register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R8`|<span data-ttu-id="856b0-137">#8 registraci dat v procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="856b0-137">The #8 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R9`|<span data-ttu-id="856b0-138">#9 registraci dat v procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="856b0-138">The #9 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R10`|<span data-ttu-id="856b0-139">#10 registraci dat v procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="856b0-139">The #10 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R11`|<span data-ttu-id="856b0-140">#11 registraci dat v procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="856b0-140">The #11 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R12`|<span data-ttu-id="856b0-141">#12 registraci dat v procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="856b0-141">The #12 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R13`|<span data-ttu-id="856b0-142">#13 registraci dat v procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="856b0-142">The #13 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R14`|<span data-ttu-id="856b0-143">#14 registraci dat v procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="856b0-143">The #14 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R15`|<span data-ttu-id="856b0-144">#15 registraci dat v procesoru AMD64.</span><span class="sxs-lookup"><span data-stu-id="856b0-144">The #15 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM0`|<span data-ttu-id="856b0-145">Registr #0 multimédií na procesorech AMD64.</span><span class="sxs-lookup"><span data-stu-id="856b0-145">The #0 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM1`|<span data-ttu-id="856b0-146">Registr #1 multimédií na procesorech AMD64.</span><span class="sxs-lookup"><span data-stu-id="856b0-146">The #1 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM2`|<span data-ttu-id="856b0-147">Registr #2 multimédií na procesorech AMD64.</span><span class="sxs-lookup"><span data-stu-id="856b0-147">The #2 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM3`|<span data-ttu-id="856b0-148">Registr #3 multimédií na procesorech AMD64.</span><span class="sxs-lookup"><span data-stu-id="856b0-148">The #3 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM4`|<span data-ttu-id="856b0-149">Registr #4 multimédií na procesorech AMD64.</span><span class="sxs-lookup"><span data-stu-id="856b0-149">The #4 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM5`|<span data-ttu-id="856b0-150">Registr #5 multimédií na procesorech AMD64.</span><span class="sxs-lookup"><span data-stu-id="856b0-150">The #5 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM6`|<span data-ttu-id="856b0-151">Registr #6 multimédií na procesorech AMD64.</span><span class="sxs-lookup"><span data-stu-id="856b0-151">The #6 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM7`|<span data-ttu-id="856b0-152">Registr #7 multimédií na procesorech AMD64.</span><span class="sxs-lookup"><span data-stu-id="856b0-152">The #7 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM8`|<span data-ttu-id="856b0-153">Registr #8 multimédií na procesorech AMD64.</span><span class="sxs-lookup"><span data-stu-id="856b0-153">The #8 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM9`|<span data-ttu-id="856b0-154">Registr #9 multimédií na procesorech AMD64.</span><span class="sxs-lookup"><span data-stu-id="856b0-154">The #9 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM10`|<span data-ttu-id="856b0-155">Registr #10 multimédií na procesorech AMD64.</span><span class="sxs-lookup"><span data-stu-id="856b0-155">The #10 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM11`|<span data-ttu-id="856b0-156">Registr #11 multimédií na procesorech AMD64.</span><span class="sxs-lookup"><span data-stu-id="856b0-156">The #11 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM12`|<span data-ttu-id="856b0-157">Registr #12 multimédií na procesorech AMD64.</span><span class="sxs-lookup"><span data-stu-id="856b0-157">The #12 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM13`|<span data-ttu-id="856b0-158">Registr #13 multimédií na procesorech AMD64.</span><span class="sxs-lookup"><span data-stu-id="856b0-158">The #13 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM14`|<span data-ttu-id="856b0-159">Registr #14 multimédií na procesorech AMD64.</span><span class="sxs-lookup"><span data-stu-id="856b0-159">The #14 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM15`|<span data-ttu-id="856b0-160">Registr #15 multimédií na procesorech AMD64.</span><span class="sxs-lookup"><span data-stu-id="856b0-160">The #15 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_IA64_BSP`|<span data-ttu-id="856b0-161">Registr ukazatele zásobníku v procesoru IA-64.</span><span class="sxs-lookup"><span data-stu-id="856b0-161">The stack pointer register on the IA-64 processor.</span></span>|  
|`REGISTER_IA64_R0`|<span data-ttu-id="856b0-162">#0 registraci dat v procesoru IA-64.</span><span class="sxs-lookup"><span data-stu-id="856b0-162">The #0 data register on the IA-64 processor.</span></span>|  
|`REGISTER_IA64_F0`|<span data-ttu-id="856b0-163">Registr dat #0 FP v procesoru IA-64.</span><span class="sxs-lookup"><span data-stu-id="856b0-163">The #0 FP data register on the IA-64 processor.</span></span>|  
|`REGISTER_ARM_PC`|<span data-ttu-id="856b0-164">Registr čítače programu (R15) na procesoru ARM.</span><span class="sxs-lookup"><span data-stu-id="856b0-164">The program counter register (R15) on the ARM processor.</span></span>|  
|`REGISTER_ARM_SP`|<span data-ttu-id="856b0-165">Registr ukazatele zásobníku (R13) na procesoru ARM.</span><span class="sxs-lookup"><span data-stu-id="856b0-165">The stack pointer register (R13) on the ARM processor.</span></span>|  
|`REGISTER_ARM_R0`|<span data-ttu-id="856b0-166">R0 registru dat na procesor ARM.</span><span class="sxs-lookup"><span data-stu-id="856b0-166">Data register R0 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R1`|<span data-ttu-id="856b0-167">Registrace dat R1 v procesoru ARM.</span><span class="sxs-lookup"><span data-stu-id="856b0-167">Data register R1 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R2`|<span data-ttu-id="856b0-168">Data Registry R2 na procesoru ARM.</span><span class="sxs-lookup"><span data-stu-id="856b0-168">Data register R2 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R3`|<span data-ttu-id="856b0-169">Data Register R3 na procesoru ARM.</span><span class="sxs-lookup"><span data-stu-id="856b0-169">Data register R3 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R4`|<span data-ttu-id="856b0-170">Registrace R4 na procesoru ARM.</span><span class="sxs-lookup"><span data-stu-id="856b0-170">Register R4 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R5`|<span data-ttu-id="856b0-171">Zaregistrujte R5 na procesor ARM.</span><span class="sxs-lookup"><span data-stu-id="856b0-171">Register R5 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R6`|<span data-ttu-id="856b0-172">Zaregistrujte R6 na procesor ARM.</span><span class="sxs-lookup"><span data-stu-id="856b0-172">Register R6 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R7`|<span data-ttu-id="856b0-173">Zaregistrujte R7 (ukazatel na rámec jezdce) na procesoru ARM.</span><span class="sxs-lookup"><span data-stu-id="856b0-173">Register R7 (the THUMB frame pointer) on the ARM processor.</span></span>|  
|`REGISTER_ARM_R8`|<span data-ttu-id="856b0-174">Zaregistrujte R8 na procesoru ARM.</span><span class="sxs-lookup"><span data-stu-id="856b0-174">Register R8 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R9`|<span data-ttu-id="856b0-175">Zaregistrujte R9 na procesor ARM.</span><span class="sxs-lookup"><span data-stu-id="856b0-175">Register R9 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R10`|<span data-ttu-id="856b0-176">Zaregistrujte R10 na procesor ARM.</span><span class="sxs-lookup"><span data-stu-id="856b0-176">Register R10 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R11`|<span data-ttu-id="856b0-177">Ukazatel na rámec na procesoru ARM.</span><span class="sxs-lookup"><span data-stu-id="856b0-177">The frame pointer on the ARM processor.</span></span>|  
|`REGISTER_ARM_R12`|<span data-ttu-id="856b0-178">Zaregistrujte R12 na procesor ARM.</span><span class="sxs-lookup"><span data-stu-id="856b0-178">Register R12 on the ARM processor.</span></span>|  
|`REGISTER_ARM_LR`|<span data-ttu-id="856b0-179">Registr odkazů (R14) na procesoru ARM.</span><span class="sxs-lookup"><span data-stu-id="856b0-179">The link register (R14) on the ARM processor.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="856b0-180">Poznámky</span><span class="sxs-lookup"><span data-stu-id="856b0-180">Remarks</span></span>  
 <span data-ttu-id="856b0-181">Pro procesor IA-64 jsou k dispozici 128 datových registrů pro obecné účely a 128 datových registrů s plovoucí desetinnou čárkou, ale jsou k dispozici pouze hodnoty `REGISTER_IA64_R0` a `REGISTER_IA64_F0`.</span><span class="sxs-lookup"><span data-stu-id="856b0-181">There are 128 general-purpose data registers and 128 floating-point data registers on the IA-64 processor, but only values `REGISTER_IA64_R0` and `REGISTER_IA64_F0` are provided.</span></span> <span data-ttu-id="856b0-182">Ostatní hodnoty lze určit následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="856b0-182">The other values can be determined as follows:</span></span>  
  
- <span data-ttu-id="856b0-183">Přidejte číslo registru, které se má `REGISTER_IA64_R0` pro hodnoty `REGISTER_IA64_R1` prostřednictvím `REGISTER_IA64_R127`, které odpovídají #1 registraci dat prostřednictvím #127 registru pro procesor IA-64.</span><span class="sxs-lookup"><span data-stu-id="856b0-183">Add the register number to `REGISTER_IA64_R0` for values `REGISTER_IA64_R1` through `REGISTER_IA64_R127`, which correspond to the #1 data register through the #127 data register on the IA-64 processor.</span></span>  
  
- <span data-ttu-id="856b0-184">Přidejte číslo registru, které se má `REGISTER_IA64_F0` pro hodnoty `REGISTER_IA64_F1` prostřednictvím `REGISTER_IA64_F127`, které odpovídají registru #1 FP v rámci registru s daty #127 FP v procesoru IA-64.</span><span class="sxs-lookup"><span data-stu-id="856b0-184">Add the register number to `REGISTER_IA64_F0` for values `REGISTER_IA64_F1` through `REGISTER_IA64_F127`, which correspond to the #1 FP data register through the #127 FP data register on the IA-64 processor.</span></span>  
  
 <span data-ttu-id="856b0-185">Pokud například potřebujete zadat #83 registru dat v procesoru IA-64, použijte `REGISTER_IA64_R0` + 83.</span><span class="sxs-lookup"><span data-stu-id="856b0-185">For example, if you need to specify the #83 data register on the IA-64 processor, use `REGISTER_IA64_R0` + 83.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="856b0-186">Požadavky</span><span class="sxs-lookup"><span data-stu-id="856b0-186">Requirements</span></span>  
 <span data-ttu-id="856b0-187">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="856b0-187">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="856b0-188">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="856b0-188">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="856b0-189">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="856b0-189">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="856b0-190">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="856b0-190">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="856b0-191">Viz také:</span><span class="sxs-lookup"><span data-stu-id="856b0-191">See also</span></span>

- [<span data-ttu-id="856b0-192">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="856b0-192">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
