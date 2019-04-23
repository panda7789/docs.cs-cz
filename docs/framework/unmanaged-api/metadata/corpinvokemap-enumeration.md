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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 951941092f67f66c5b17c8ae592569c2a8e6a675
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59079627"
---
# <a name="corpinvokemap-enumeration"></a><span data-ttu-id="d6dfe-102">CorPinvokeMap – výčet</span><span class="sxs-lookup"><span data-stu-id="d6dfe-102">CorPinvokeMap Enumeration</span></span>
<span data-ttu-id="d6dfe-103">Určuje možnosti pro volání PInvoke.</span><span class="sxs-lookup"><span data-stu-id="d6dfe-103">Specifies options for a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6dfe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6dfe-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="d6dfe-105">Členové</span><span class="sxs-lookup"><span data-stu-id="d6dfe-105">Members</span></span>  
  
|<span data-ttu-id="d6dfe-106">Člen</span><span class="sxs-lookup"><span data-stu-id="d6dfe-106">Member</span></span>|<span data-ttu-id="d6dfe-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d6dfe-107">Description</span></span>|  
|------------|-----------------|  
|`pmNoMangle`|<span data-ttu-id="d6dfe-108">Každý název člena použijte uvedené.</span><span class="sxs-lookup"><span data-stu-id="d6dfe-108">Use each member name as specified.</span></span>|  
|`pmCharSetMask`|<span data-ttu-id="d6dfe-109">Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="d6dfe-109">Reserved.</span></span>|  
|`pmCharSetNotSpec`|<span data-ttu-id="d6dfe-110">Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="d6dfe-110">Reserved.</span></span>|  
|`pmCharSetAnsi`|<span data-ttu-id="d6dfe-111">Zařazování řetězců v kódu jako více bajtové znaky řetězce.</span><span class="sxs-lookup"><span data-stu-id="d6dfe-111">Marshal strings as multiple-byte character strings.</span></span>|  
|`pmCharSetUnicode`|<span data-ttu-id="d6dfe-112">Zařazování řetězců v kódu jako 2bajtové znaky kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="d6dfe-112">Marshal strings as Unicode 2-byte characters.</span></span>|  
|`pmCharSetAuto`|<span data-ttu-id="d6dfe-113">Automaticky zařazovat řetězce pro cílový operační systém.</span><span class="sxs-lookup"><span data-stu-id="d6dfe-113">Automatically marshal strings appropriately for the target operating system.</span></span> <span data-ttu-id="d6dfe-114">Výchozí hodnota je kódování Unicode v systému Windows NT, Windows 2000, Windows XP a řady Windows Server 2003; Výchozí hodnota je ANSI na Windows 98 a Windows Me.</span><span class="sxs-lookup"><span data-stu-id="d6dfe-114">The default is Unicode on Windows NT, Windows 2000, Windows XP, and the Windows Server 2003 family; the default is ANSI on Windows 98 and Windows Me.</span></span>|  
|`pmBestFitUseAssem`|<span data-ttu-id="d6dfe-115">Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="d6dfe-115">Reserved.</span></span>|  
|`pmBestFitEnabled`|<span data-ttu-id="d6dfe-116">Provedení přizpůsobený mapování znaků Unicode, které nemají přesnou shodu v znakovou sadu ANSI.</span><span class="sxs-lookup"><span data-stu-id="d6dfe-116">Perform best-fit mapping of Unicode characters that lack an exact match in the ANSI character set.</span></span>|  
|`pmBestFitDisabled`|<span data-ttu-id="d6dfe-117">Neprovádějte nejlepšího mapování znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="d6dfe-117">Do not perform best-fit mapping of Unicode characters.</span></span> <span data-ttu-id="d6dfe-118">V takovém případě budou nahrazeny všechny nemapovatelný znaky "?".</span><span class="sxs-lookup"><span data-stu-id="d6dfe-118">In this case, all unmappable characters will be replaced by a ‘?’.</span></span>|  
|`pmBestFitMask`|<span data-ttu-id="d6dfe-119">Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="d6dfe-119">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharUseAssem`|<span data-ttu-id="d6dfe-120">Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="d6dfe-120">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharEnabled`|<span data-ttu-id="d6dfe-121">Vyvolání výjimky, když se interoperační zařazovač setká nemapovatelný znak.</span><span class="sxs-lookup"><span data-stu-id="d6dfe-121">Throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharDisabled`|<span data-ttu-id="d6dfe-122">Když se interoperační zařazovač setká nemapovatelný znak není vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="d6dfe-122">Do not throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharMask`|<span data-ttu-id="d6dfe-123">Vyhrazeno</span><span class="sxs-lookup"><span data-stu-id="d6dfe-123">Reserved</span></span>|  
|`pmSupportsLastError`|<span data-ttu-id="d6dfe-124">Povolit volaný volání Win32 `SetLastError` funkce před návratem z metody s atributy.</span><span class="sxs-lookup"><span data-stu-id="d6dfe-124">Allow the callee to call the Win32 `SetLastError` function before returning from the attributed method.</span></span>|  
|`pmCallConvMask`|<span data-ttu-id="d6dfe-125">Vyhrazeno</span><span class="sxs-lookup"><span data-stu-id="d6dfe-125">Reserved</span></span>|  
|`pmCallConvWinapi`|<span data-ttu-id="d6dfe-126">Používejte výchozí platformu konvence volání.</span><span class="sxs-lookup"><span data-stu-id="d6dfe-126">Use the default platform calling convention.</span></span> <span data-ttu-id="d6dfe-127">Například na Windows výchozí hodnota je `StdCall` a na Windows CE .NET je `Cdecl`.</span><span class="sxs-lookup"><span data-stu-id="d6dfe-127">For example, on Windows the default is `StdCall` and on Windows CE .NET it is `Cdecl`.</span></span>|  
|`pmCallConvCdecl`|<span data-ttu-id="d6dfe-128">Použití `Cdecl` konvence volání.</span><span class="sxs-lookup"><span data-stu-id="d6dfe-128">Use the `Cdecl` calling convention.</span></span> <span data-ttu-id="d6dfe-129">V takovém případě volající vyčistí zásobník.</span><span class="sxs-lookup"><span data-stu-id="d6dfe-129">In this case, the caller cleans the stack.</span></span> <span data-ttu-id="d6dfe-130">To umožňuje volání funkcí s `varargs` (to znamená, funkce, které přijímají proměnný počet parametrů).</span><span class="sxs-lookup"><span data-stu-id="d6dfe-130">This enables calling functions with `varargs` (that is, functions that accept a variable number of parameters).</span></span>|  
|`pmCallConvStdcall`|<span data-ttu-id="d6dfe-131">Použití `StdCall` konvence volání.</span><span class="sxs-lookup"><span data-stu-id="d6dfe-131">Use the `StdCall` calling convention.</span></span> <span data-ttu-id="d6dfe-132">V takovém případě volaný vyčistí zásobník.</span><span class="sxs-lookup"><span data-stu-id="d6dfe-132">In this case, the callee cleans the stack.</span></span> <span data-ttu-id="d6dfe-133">To je výchozí konvence pro vyvolání volání nespravovaných funkcí s platformou.</span><span class="sxs-lookup"><span data-stu-id="d6dfe-133">This is the default convention for calling unmanaged functions with platform invoke.</span></span>|  
|`pmCallConvThiscall`|<span data-ttu-id="d6dfe-134">Použití `ThisCall` konvence volání.</span><span class="sxs-lookup"><span data-stu-id="d6dfe-134">Use the `ThisCall` calling convention.</span></span> <span data-ttu-id="d6dfe-135">V takovém případě je první parametr `this` ukazatel a je uložen v registru ECX.</span><span class="sxs-lookup"><span data-stu-id="d6dfe-135">In this case, the first parameter is the `this` pointer and is stored in register ECX.</span></span> <span data-ttu-id="d6dfe-136">Další parametry jsou vloženy do zásobníku.</span><span class="sxs-lookup"><span data-stu-id="d6dfe-136">Other parameters are pushed on the stack.</span></span> <span data-ttu-id="d6dfe-137">`ThisCall` Konvence volání se používá k volání metod třídy exportované z nespravovaná knihovna DLL.</span><span class="sxs-lookup"><span data-stu-id="d6dfe-137">The `ThisCall` calling convention is used to call methods on classes exported from an unmanaged DLL.</span></span>|  
|`pmCallConvFastcall`|<span data-ttu-id="d6dfe-138">Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="d6dfe-138">Reserved.</span></span>|  
|`pmMaxValue`|<span data-ttu-id="d6dfe-139">Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="d6dfe-139">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d6dfe-140">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d6dfe-140">Requirements</span></span>  
 <span data-ttu-id="d6dfe-141">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6dfe-141">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6dfe-142">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="d6dfe-142">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="d6dfe-143">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6dfe-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6dfe-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d6dfe-144">See also</span></span>

- [<span data-ttu-id="d6dfe-145">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="d6dfe-145">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
