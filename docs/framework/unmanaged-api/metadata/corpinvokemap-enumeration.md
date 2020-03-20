---
title: CorPinvokeMap – výčet
ms.date: 03/30/2017
api_name:
- CorPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPinvokeMap
helpviewer_keywords:
- CorPinvokeMap enumeration [.NET Framework metadata]
ms.assetid: f14f986e-f6ce-42bc-aa23-18150c46d28c
topic_type:
- apiref
ms.openlocfilehash: 8216dc3030b18428ab52fbf8385d392f81057aa0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176146"
---
# <a name="corpinvokemap-enumeration"></a><span data-ttu-id="72748-102">CorPinvokeMap – výčet</span><span class="sxs-lookup"><span data-stu-id="72748-102">CorPinvokeMap Enumeration</span></span>
<span data-ttu-id="72748-103">Určuje možnosti pro volání PInvoke.</span><span class="sxs-lookup"><span data-stu-id="72748-103">Specifies options for a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72748-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72748-104">Syntax</span></span>  
  
```cpp  
typedef enum  CorPinvokeMap {  
  
    pmNoMangle          = 0x0001,  
  
    pmCharSetMask       = 0x0006,  
    pmCharSetNotSpec    = 0x0000,  
    pmCharSetAnsi       = 0x0002,  
    pmCharSetUnicode    = 0x0004,  
    pmCharSetAuto       = 0x0006,  
  
    pmBestFitUseAssem   = 0x0000,  
    pmBestFitEnabled    = 0x0010,  
    pmBestFitDisabled   = 0x0020,  
    pmBestFitMask       = 0x0030,  
  
    pmThrowOnUnmappableCharUseAssem   = 0x0000,  
    pmThrowOnUnmappableCharEnabled    = 0x1000,  
    pmThrowOnUnmappableCharDisabled   = 0x2000,  
    pmThrowOnUnmappableCharMask       = 0x3000,  
  
    pmSupportsLastError = 0x0040,
  
    pmCallConvMask      = 0x0700,  
    pmCallConvWinapi    = 0x0100,  
    pmCallConvCdecl     = 0x0200,  
    pmCallConvStdcall   = 0x0300,  
    pmCallConvThiscall  = 0x0400,  
    pmCallConvFastcall  = 0x0500,  
  
    pmMaxValue          = 0xFFFF  
  
} CorPinvokeMap;  
```  
  
## <a name="members"></a><span data-ttu-id="72748-105">Členové</span><span class="sxs-lookup"><span data-stu-id="72748-105">Members</span></span>  
  
|<span data-ttu-id="72748-106">Člen</span><span class="sxs-lookup"><span data-stu-id="72748-106">Member</span></span>|<span data-ttu-id="72748-107">Popis</span><span class="sxs-lookup"><span data-stu-id="72748-107">Description</span></span>|  
|------------|-----------------|  
|`pmNoMangle`|<span data-ttu-id="72748-108">Použijte každý název člena, jak je zadáno.</span><span class="sxs-lookup"><span data-stu-id="72748-108">Use each member name as specified.</span></span>|  
|`pmCharSetMask`|<span data-ttu-id="72748-109">Vyhrazeno.</span><span class="sxs-lookup"><span data-stu-id="72748-109">Reserved.</span></span>|  
|`pmCharSetNotSpec`|<span data-ttu-id="72748-110">Vyhrazeno.</span><span class="sxs-lookup"><span data-stu-id="72748-110">Reserved.</span></span>|  
|`pmCharSetAnsi`|<span data-ttu-id="72748-111">Řetězce marshaljako vícebajtové řetězce znaků.</span><span class="sxs-lookup"><span data-stu-id="72748-111">Marshal strings as multiple-byte character strings.</span></span>|  
|`pmCharSetUnicode`|<span data-ttu-id="72748-112">Řetězce marshal jako dvoubajtové znaky Unicode.</span><span class="sxs-lookup"><span data-stu-id="72748-112">Marshal strings as Unicode 2-byte characters.</span></span>|  
|`pmCharSetAuto`|<span data-ttu-id="72748-113">Automaticky zařazují řetězce vhodně pro cílový operační systém.</span><span class="sxs-lookup"><span data-stu-id="72748-113">Automatically marshal strings appropriately for the target operating system.</span></span> <span data-ttu-id="72748-114">Výchozí hodnota je Unicode v systémech Windows NT, Windows 2000, Windows XP a Windows Server 2003; Výchozí hodnota je ANSI v systémech Windows 98 a Windows ME.</span><span class="sxs-lookup"><span data-stu-id="72748-114">The default is Unicode on Windows NT, Windows 2000, Windows XP, and the Windows Server 2003 family; the default is ANSI on Windows 98 and Windows Me.</span></span>|  
|`pmBestFitUseAssem`|<span data-ttu-id="72748-115">Vyhrazeno.</span><span class="sxs-lookup"><span data-stu-id="72748-115">Reserved.</span></span>|  
|`pmBestFitEnabled`|<span data-ttu-id="72748-116">Proveďte nejvhodnější mapování znaků Unicode, které v znakové sadě ANSI nemají přesnou shodu.</span><span class="sxs-lookup"><span data-stu-id="72748-116">Perform best-fit mapping of Unicode characters that lack an exact match in the ANSI character set.</span></span>|  
|`pmBestFitDisabled`|<span data-ttu-id="72748-117">Neprovádějte nejvhodnější mapování znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="72748-117">Do not perform best-fit mapping of Unicode characters.</span></span> <span data-ttu-id="72748-118">V tomto případě budou všechny nezamísťující znaky nahrazeny znakem '?'.</span><span class="sxs-lookup"><span data-stu-id="72748-118">In this case, all unmappable characters will be replaced by a ‘?’.</span></span>|  
|`pmBestFitMask`|<span data-ttu-id="72748-119">Vyhrazeno.</span><span class="sxs-lookup"><span data-stu-id="72748-119">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharUseAssem`|<span data-ttu-id="72748-120">Vyhrazeno.</span><span class="sxs-lookup"><span data-stu-id="72748-120">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharEnabled`|<span data-ttu-id="72748-121">Vyvolání výjimky, když interop zařazovač narazí na nemappable znak.</span><span class="sxs-lookup"><span data-stu-id="72748-121">Throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharDisabled`|<span data-ttu-id="72748-122">Nevyvolávejte výjimku, když interop zařazovač narazí na nemappable znak.</span><span class="sxs-lookup"><span data-stu-id="72748-122">Do not throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharMask`|<span data-ttu-id="72748-123">Vyhrazeno</span><span class="sxs-lookup"><span data-stu-id="72748-123">Reserved</span></span>|  
|`pmSupportsLastError`|<span data-ttu-id="72748-124">Povolte volavce volat funkci `SetLastError` Win32 před návratem z přiřazené metody.</span><span class="sxs-lookup"><span data-stu-id="72748-124">Allow the callee to call the Win32 `SetLastError` function before returning from the attributed method.</span></span>|  
|`pmCallConvMask`|<span data-ttu-id="72748-125">Vyhrazeno</span><span class="sxs-lookup"><span data-stu-id="72748-125">Reserved</span></span>|  
|`pmCallConvWinapi`|<span data-ttu-id="72748-126">Použijte výchozí konvence volání platformy.</span><span class="sxs-lookup"><span data-stu-id="72748-126">Use the default platform calling convention.</span></span> <span data-ttu-id="72748-127">Například v systému `StdCall` Windows výchozí je a `Cdecl`na Windows CE .NET je .</span><span class="sxs-lookup"><span data-stu-id="72748-127">For example, on Windows the default is `StdCall` and on Windows CE .NET it is `Cdecl`.</span></span>|  
|`pmCallConvCdecl`|<span data-ttu-id="72748-128">Použijte `Cdecl` konvence volání.</span><span class="sxs-lookup"><span data-stu-id="72748-128">Use the `Cdecl` calling convention.</span></span> <span data-ttu-id="72748-129">V tomto případě volající čistí zásobníku.</span><span class="sxs-lookup"><span data-stu-id="72748-129">In this case, the caller cleans the stack.</span></span> <span data-ttu-id="72748-130">To umožňuje volání `varargs` funkcí s (to znamená, že funkce, které přijímají proměnný počet parametrů).</span><span class="sxs-lookup"><span data-stu-id="72748-130">This enables calling functions with `varargs` (that is, functions that accept a variable number of parameters).</span></span>|  
|`pmCallConvStdcall`|<span data-ttu-id="72748-131">Použijte `StdCall` konvence volání.</span><span class="sxs-lookup"><span data-stu-id="72748-131">Use the `StdCall` calling convention.</span></span> <span data-ttu-id="72748-132">V tomto případě volaný čistí zásobníku.</span><span class="sxs-lookup"><span data-stu-id="72748-132">In this case, the callee cleans the stack.</span></span> <span data-ttu-id="72748-133">Toto je výchozí konvence pro volání nespravovaných funkcí s vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="72748-133">This is the default convention for calling unmanaged functions with platform invoke.</span></span>|  
|`pmCallConvThiscall`|<span data-ttu-id="72748-134">Použijte `ThisCall` konvence volání.</span><span class="sxs-lookup"><span data-stu-id="72748-134">Use the `ThisCall` calling convention.</span></span> <span data-ttu-id="72748-135">V tomto případě je prvním `this` parametrem ukazatel a je uložen v registru ECX.</span><span class="sxs-lookup"><span data-stu-id="72748-135">In this case, the first parameter is the `this` pointer and is stored in register ECX.</span></span> <span data-ttu-id="72748-136">Ostatní parametry jsou tlačeny do zásobníku.</span><span class="sxs-lookup"><span data-stu-id="72748-136">Other parameters are pushed on the stack.</span></span> <span data-ttu-id="72748-137">Konvence `ThisCall` volání se používá k volání metod na třídy exportované z nespravované dll.</span><span class="sxs-lookup"><span data-stu-id="72748-137">The `ThisCall` calling convention is used to call methods on classes exported from an unmanaged DLL.</span></span>|  
|`pmCallConvFastcall`|<span data-ttu-id="72748-138">Vyhrazeno.</span><span class="sxs-lookup"><span data-stu-id="72748-138">Reserved.</span></span>|  
|`pmMaxValue`|<span data-ttu-id="72748-139">Vyhrazeno.</span><span class="sxs-lookup"><span data-stu-id="72748-139">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="72748-140">Požadavky</span><span class="sxs-lookup"><span data-stu-id="72748-140">Requirements</span></span>  
 <span data-ttu-id="72748-141">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72748-141">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72748-142">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="72748-142">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="72748-143">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72748-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72748-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="72748-144">See also</span></span>

- [<span data-ttu-id="72748-145">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="72748-145">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
