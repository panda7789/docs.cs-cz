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
ms.openlocfilehash: 199a649b0481c2a740926636345eefbda6831ef2
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007543"
---
# <a name="corpinvokemap-enumeration"></a><span data-ttu-id="b1752-102">CorPinvokeMap – výčet</span><span class="sxs-lookup"><span data-stu-id="b1752-102">CorPinvokeMap Enumeration</span></span>
<span data-ttu-id="b1752-103">Určuje možnosti pro volání PInvoke.</span><span class="sxs-lookup"><span data-stu-id="b1752-103">Specifies options for a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1752-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1752-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="b1752-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b1752-105">Members</span></span>  
  
|<span data-ttu-id="b1752-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b1752-106">Member</span></span>|<span data-ttu-id="b1752-107">Description</span><span class="sxs-lookup"><span data-stu-id="b1752-107">Description</span></span>|  
|------------|-----------------|  
|`pmNoMangle`|<span data-ttu-id="b1752-108">Použijte název každého člena podle zadání.</span><span class="sxs-lookup"><span data-stu-id="b1752-108">Use each member name as specified.</span></span>|  
|`pmCharSetMask`|<span data-ttu-id="b1752-109">Vyhrazeno.</span><span class="sxs-lookup"><span data-stu-id="b1752-109">Reserved.</span></span>|  
|`pmCharSetNotSpec`|<span data-ttu-id="b1752-110">Vyhrazeno.</span><span class="sxs-lookup"><span data-stu-id="b1752-110">Reserved.</span></span>|  
|`pmCharSetAnsi`|<span data-ttu-id="b1752-111">Zařazování řetězců jako řetězce znaků s více bajty.</span><span class="sxs-lookup"><span data-stu-id="b1752-111">Marshal strings as multiple-byte character strings.</span></span>|  
|`pmCharSetUnicode`|<span data-ttu-id="b1752-112">Zařazování řetězců jako znaků Unicode 2 bajtů.</span><span class="sxs-lookup"><span data-stu-id="b1752-112">Marshal strings as Unicode 2-byte characters.</span></span>|  
|`pmCharSetAuto`|<span data-ttu-id="b1752-113">Pro cílový operační systém jsou automaticky zařazeny řetězce odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="b1752-113">Automatically marshal strings appropriately for the target operating system.</span></span> <span data-ttu-id="b1752-114">Výchozí hodnota je Unicode v systémech Windows NT, Windows 2000, Windows XP a Windows Server 2003. Výchozí hodnota je ANSI v systému Windows 98 a Windows Millennium.</span><span class="sxs-lookup"><span data-stu-id="b1752-114">The default is Unicode on Windows NT, Windows 2000, Windows XP, and the Windows Server 2003 family; the default is ANSI on Windows 98 and Windows Me.</span></span>|  
|`pmBestFitUseAssem`|<span data-ttu-id="b1752-115">Vyhrazeno.</span><span class="sxs-lookup"><span data-stu-id="b1752-115">Reserved.</span></span>|  
|`pmBestFitEnabled`|<span data-ttu-id="b1752-116">Proveďte nejvhodnější mapování znaků Unicode, u kterých chybí přesná shoda v sadě znaků ANSI.</span><span class="sxs-lookup"><span data-stu-id="b1752-116">Perform best-fit mapping of Unicode characters that lack an exact match in the ANSI character set.</span></span>|  
|`pmBestFitDisabled`|<span data-ttu-id="b1752-117">Neprovádějte nejlepší mapování znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="b1752-117">Do not perform best-fit mapping of Unicode characters.</span></span> <span data-ttu-id="b1752-118">V takovém případě budou všechny nemapovatelný znaky nahrazeny znakem "?".</span><span class="sxs-lookup"><span data-stu-id="b1752-118">In this case, all unmappable characters will be replaced by a ‘?’.</span></span>|  
|`pmBestFitMask`|<span data-ttu-id="b1752-119">Vyhrazeno.</span><span class="sxs-lookup"><span data-stu-id="b1752-119">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharUseAssem`|<span data-ttu-id="b1752-120">Vyhrazeno.</span><span class="sxs-lookup"><span data-stu-id="b1752-120">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharEnabled`|<span data-ttu-id="b1752-121">Vyvolat výjimku, když zařazovací modul Interop nalezne nemapovatelný znak.</span><span class="sxs-lookup"><span data-stu-id="b1752-121">Throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharDisabled`|<span data-ttu-id="b1752-122">Nevyvolejte výjimku, když zařazovací modul Interop nalezne nemapovatelný znak.</span><span class="sxs-lookup"><span data-stu-id="b1752-122">Do not throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharMask`|<span data-ttu-id="b1752-123">Vyhrazeno</span><span class="sxs-lookup"><span data-stu-id="b1752-123">Reserved</span></span>|  
|`pmSupportsLastError`|<span data-ttu-id="b1752-124">Umožňuje volanému volat `SetLastError` funkci Win32 před vrácením z metody s atributy.</span><span class="sxs-lookup"><span data-stu-id="b1752-124">Allow the callee to call the Win32 `SetLastError` function before returning from the attributed method.</span></span>|  
|`pmCallConvMask`|<span data-ttu-id="b1752-125">Vyhrazeno</span><span class="sxs-lookup"><span data-stu-id="b1752-125">Reserved</span></span>|  
|`pmCallConvWinapi`|<span data-ttu-id="b1752-126">Použijte výchozí konvenci volání platformy.</span><span class="sxs-lookup"><span data-stu-id="b1752-126">Use the default platform calling convention.</span></span> <span data-ttu-id="b1752-127">Například ve Windows je výchozí nastavení `StdCall` a v systém Windows CE .NET je `Cdecl` .</span><span class="sxs-lookup"><span data-stu-id="b1752-127">For example, on Windows the default is `StdCall` and on Windows CE .NET it is `Cdecl`.</span></span>|  
|`pmCallConvCdecl`|<span data-ttu-id="b1752-128">Použijte `Cdecl` konvenci volání.</span><span class="sxs-lookup"><span data-stu-id="b1752-128">Use the `Cdecl` calling convention.</span></span> <span data-ttu-id="b1752-129">V tomto případě volající vyčistí zásobník.</span><span class="sxs-lookup"><span data-stu-id="b1752-129">In this case, the caller cleans the stack.</span></span> <span data-ttu-id="b1752-130">To umožňuje volání funkcí s `varargs` (to znamená, funkce, které přijímají proměnný počet parametrů).</span><span class="sxs-lookup"><span data-stu-id="b1752-130">This enables calling functions with `varargs` (that is, functions that accept a variable number of parameters).</span></span>|  
|`pmCallConvStdcall`|<span data-ttu-id="b1752-131">Použijte `StdCall` konvenci volání.</span><span class="sxs-lookup"><span data-stu-id="b1752-131">Use the `StdCall` calling convention.</span></span> <span data-ttu-id="b1752-132">V tomto případě volaný vyčistí zásobník.</span><span class="sxs-lookup"><span data-stu-id="b1752-132">In this case, the callee cleans the stack.</span></span> <span data-ttu-id="b1752-133">Toto je výchozí konvence pro volání nespravovaných funkcí s voláním platformy.</span><span class="sxs-lookup"><span data-stu-id="b1752-133">This is the default convention for calling unmanaged functions with platform invoke.</span></span>|  
|`pmCallConvThiscall`|<span data-ttu-id="b1752-134">Použijte `ThisCall` konvenci volání.</span><span class="sxs-lookup"><span data-stu-id="b1752-134">Use the `ThisCall` calling convention.</span></span> <span data-ttu-id="b1752-135">V tomto případě je prvním parametrem `this` ukazatel a je uložen v registru ecx.</span><span class="sxs-lookup"><span data-stu-id="b1752-135">In this case, the first parameter is the `this` pointer and is stored in register ECX.</span></span> <span data-ttu-id="b1752-136">Další parametry jsou vloženy do zásobníku.</span><span class="sxs-lookup"><span data-stu-id="b1752-136">Other parameters are pushed on the stack.</span></span> <span data-ttu-id="b1752-137">`ThisCall`Konvence volání se používá pro volání metod u tříd exportovaných z nespravované knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="b1752-137">The `ThisCall` calling convention is used to call methods on classes exported from an unmanaged DLL.</span></span>|  
|`pmCallConvFastcall`|<span data-ttu-id="b1752-138">Vyhrazeno.</span><span class="sxs-lookup"><span data-stu-id="b1752-138">Reserved.</span></span>|  
|`pmMaxValue`|<span data-ttu-id="b1752-139">Vyhrazeno.</span><span class="sxs-lookup"><span data-stu-id="b1752-139">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b1752-140">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b1752-140">Requirements</span></span>  
 <span data-ttu-id="b1752-141">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1752-141">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1752-142">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="b1752-142">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b1752-143">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1752-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1752-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1752-144">See also</span></span>

- [<span data-ttu-id="b1752-145">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="b1752-145">Metadata Enumerations</span></span>](metadata-enumerations.md)
