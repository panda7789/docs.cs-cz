---
title: "CorPinvokeMap – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorPinvokeMap
api_location: mscoree.dll
api_type: COM
f1_keywords: CorPinvokeMap
helpviewer_keywords: CorPinvokeMap enumeration [.NET Framework metadata]
ms.assetid: f14f986e-f6ce-42bc-aa23-18150c46d28c
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9c6e1a49d18cde768884ab3d92eaa6593e2955c0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="corpinvokemap-enumeration"></a><span data-ttu-id="2a180-102">CorPinvokeMap – výčet</span><span class="sxs-lookup"><span data-stu-id="2a180-102">CorPinvokeMap Enumeration</span></span>
<span data-ttu-id="2a180-103">Určuje možnosti pro volání PInvoke.</span><span class="sxs-lookup"><span data-stu-id="2a180-103">Specifies options for a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a180-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2a180-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="2a180-105">Členové</span><span class="sxs-lookup"><span data-stu-id="2a180-105">Members</span></span>  
  
|<span data-ttu-id="2a180-106">Člen</span><span class="sxs-lookup"><span data-stu-id="2a180-106">Member</span></span>|<span data-ttu-id="2a180-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2a180-107">Description</span></span>|  
|------------|-----------------|  
|`pmNoMangle`|<span data-ttu-id="2a180-108">Každý název členu použijte jako zadaný.</span><span class="sxs-lookup"><span data-stu-id="2a180-108">Use each member name as specified.</span></span>|  
|`pmCharSetMask`|<span data-ttu-id="2a180-109">Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="2a180-109">Reserved.</span></span>|  
|`pmCharSetNotSpec`|<span data-ttu-id="2a180-110">Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="2a180-110">Reserved.</span></span>|  
|`pmCharSetAnsi`|<span data-ttu-id="2a180-111">Zařazování řetězců jako více bajtové znakové řetězce.</span><span class="sxs-lookup"><span data-stu-id="2a180-111">Marshal strings as multiple-byte character strings.</span></span>|  
|`pmCharSetUnicode`|<span data-ttu-id="2a180-112">Zařazování řetězců jako 2bajtová znaky znakové sady Unicode.</span><span class="sxs-lookup"><span data-stu-id="2a180-112">Marshal strings as Unicode 2-byte characters.</span></span>|  
|`pmCharSetAuto`|<span data-ttu-id="2a180-113">Automaticky zařazování řetězců pro cílový operační systém.</span><span class="sxs-lookup"><span data-stu-id="2a180-113">Automatically marshal strings appropriately for the target operating system.</span></span> <span data-ttu-id="2a180-114">Výchozí hodnota je kódování Unicode v systému Windows NT, Windows 2000, Windows XP a řady Windows Server 2003; Výchozí hodnota je ANSI na Windows 98 a Windows Me.</span><span class="sxs-lookup"><span data-stu-id="2a180-114">The default is Unicode on Windows NT, Windows 2000, Windows XP, and the Windows Server 2003 family; the default is ANSI on Windows 98 and Windows Me.</span></span>|  
|`pmBestFitUseAssem`|<span data-ttu-id="2a180-115">Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="2a180-115">Reserved.</span></span>|  
|`pmBestFitEnabled`|<span data-ttu-id="2a180-116">Proveďte přizpůsobená mapování znaky Unicode, která nemají přesnou shodu v znakovou sadu ANSI.</span><span class="sxs-lookup"><span data-stu-id="2a180-116">Perform best-fit mapping of Unicode characters that lack an exact match in the ANSI character set.</span></span>|  
|`pmBestFitDisabled`|<span data-ttu-id="2a180-117">Neprovádějte přizpůsobený mapování znaky Unicode.</span><span class="sxs-lookup"><span data-stu-id="2a180-117">Do not perform best-fit mapping of Unicode characters.</span></span> <span data-ttu-id="2a180-118">V takovém případě budou nahrazeny všechny unmappable znaky '?'.</span><span class="sxs-lookup"><span data-stu-id="2a180-118">In this case, all unmappable characters will be replaced by a ‘?’.</span></span>|  
|`pmBestFitMask`|<span data-ttu-id="2a180-119">Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="2a180-119">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharUseAssem`|<span data-ttu-id="2a180-120">Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="2a180-120">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharEnabled`|<span data-ttu-id="2a180-121">Způsobí výjimku, když dojde spolupráce vláken unmappable znak.</span><span class="sxs-lookup"><span data-stu-id="2a180-121">Throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharDisabled`|<span data-ttu-id="2a180-122">Když spolupráce vláken dojde unmappable znak není vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="2a180-122">Do not throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharMask`|<span data-ttu-id="2a180-123">Vyhrazené</span><span class="sxs-lookup"><span data-stu-id="2a180-123">Reserved</span></span>|  
|`pmSupportsLastError`|<span data-ttu-id="2a180-124">Povolit volaného volání Win32 `SetLastError` funkce před návratem od metodu s atributy.</span><span class="sxs-lookup"><span data-stu-id="2a180-124">Allow the callee to call the Win32 `SetLastError` function before returning from the attributed method.</span></span>|  
|`pmCallConvMask`|<span data-ttu-id="2a180-125">Vyhrazené</span><span class="sxs-lookup"><span data-stu-id="2a180-125">Reserved</span></span>|  
|`pmCallConvWinapi`|<span data-ttu-id="2a180-126">Použijte výchozí platformu konvence volání.</span><span class="sxs-lookup"><span data-stu-id="2a180-126">Use the default platform calling convention.</span></span> <span data-ttu-id="2a180-127">Například v systému Windows, výchozí hodnota je `StdCall` a na Windows CE .NET je `Cdecl`.</span><span class="sxs-lookup"><span data-stu-id="2a180-127">For example, on Windows the default is `StdCall` and on Windows CE .NET it is `Cdecl`.</span></span>|  
|`pmCallConvCdecl`|<span data-ttu-id="2a180-128">Použití `Cdecl` konvence volání.</span><span class="sxs-lookup"><span data-stu-id="2a180-128">Use the `Cdecl` calling convention.</span></span> <span data-ttu-id="2a180-129">V takovém případě volající vyčistí zásobníku.</span><span class="sxs-lookup"><span data-stu-id="2a180-129">In this case, the caller cleans the stack.</span></span> <span data-ttu-id="2a180-130">To umožňuje volání funkcí s `varargs` (to znamená, funkce, které přijímají proměnný počet parametrů).</span><span class="sxs-lookup"><span data-stu-id="2a180-130">This enables calling functions with `varargs` (that is, functions that accept a variable number of parameters).</span></span>|  
|`pmCallConvStdcall`|<span data-ttu-id="2a180-131">Použití `StdCall` konvence volání.</span><span class="sxs-lookup"><span data-stu-id="2a180-131">Use the `StdCall` calling convention.</span></span> <span data-ttu-id="2a180-132">V takovém případě volaného vyčistí zásobníku.</span><span class="sxs-lookup"><span data-stu-id="2a180-132">In this case, the callee cleans the stack.</span></span> <span data-ttu-id="2a180-133">Toto je výchozí konvenci pro vyvolání volání nespravovaných funkcí s platformou.</span><span class="sxs-lookup"><span data-stu-id="2a180-133">This is the default convention for calling unmanaged functions with platform invoke.</span></span>|  
|`pmCallConvThiscall`|<span data-ttu-id="2a180-134">Použití `ThisCall` konvence volání.</span><span class="sxs-lookup"><span data-stu-id="2a180-134">Use the `ThisCall` calling convention.</span></span> <span data-ttu-id="2a180-135">V takovém případě je první parametr `this` ukazatel a je uložen v registru ECX.</span><span class="sxs-lookup"><span data-stu-id="2a180-135">In this case, the first parameter is the `this` pointer and is stored in register ECX.</span></span> <span data-ttu-id="2a180-136">Další parametry jsou nabídnutých v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="2a180-136">Other parameters are pushed on the stack.</span></span> <span data-ttu-id="2a180-137">`ThisCall` Konvence volání se používá k volání metody na třídách exportovány z nespravovaných knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="2a180-137">The `ThisCall` calling convention is used to call methods on classes exported from an unmanaged DLL.</span></span>|  
|`pmCallConvFastcall`|<span data-ttu-id="2a180-138">Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="2a180-138">Reserved.</span></span>|  
|`pmMaxValue`|<span data-ttu-id="2a180-139">Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="2a180-139">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2a180-140">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2a180-140">Requirements</span></span>  
 <span data-ttu-id="2a180-141">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a180-141">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a180-142">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="2a180-142">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="2a180-143">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a180-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a180-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="2a180-144">See Also</span></span>  
 [<span data-ttu-id="2a180-145">Výčty metadat</span><span class="sxs-lookup"><span data-stu-id="2a180-145">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
