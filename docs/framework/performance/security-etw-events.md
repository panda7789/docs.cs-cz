---
title: Události Trasování událostí pro Windows zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b1dad042595608a805f978673858acaa5c01130f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974881"
---
# <a name="security-etw-events"></a><span data-ttu-id="549ba-102">Události Trasování událostí pro Windows zabezpečení</span><span class="sxs-lookup"><span data-stu-id="549ba-102">Security ETW Events</span></span>

<span data-ttu-id="549ba-103">Události zabezpečení jsou vyvolány během ověřování silných názvů a při ověřování prostřednictvím technologie Authenticode.</span><span class="sxs-lookup"><span data-stu-id="549ba-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  

## <a name="strongnameverificationstart_v1-and-strongnameverificationstop_v1-events"></a><span data-ttu-id="549ba-104">Události StrongNameVerificationStart_V1 a StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="549ba-104">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="549ba-105">Klíčové slovo a úroveň jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="549ba-105">The following table shows the keyword and level.</span></span> <span data-ttu-id="549ba-106">(Další informace najdete v tématu [klíčová slova a úrovně CLR ETW](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="549ba-106">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="549ba-107">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="549ba-107">Keyword for raising the event</span></span>|<span data-ttu-id="549ba-108">Obsah</span><span class="sxs-lookup"><span data-stu-id="549ba-108">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="549ba-109">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="549ba-109">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="549ba-110">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="549ba-110">Informational(4)</span></span>|  
  
 <span data-ttu-id="549ba-111">V následující tabulce jsou uvedeny informace o událostech.</span><span class="sxs-lookup"><span data-stu-id="549ba-111">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="549ba-112">Událost</span><span class="sxs-lookup"><span data-stu-id="549ba-112">Event</span></span>|<span data-ttu-id="549ba-113">ID události</span><span class="sxs-lookup"><span data-stu-id="549ba-113">Event ID</span></span>|<span data-ttu-id="549ba-114">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="549ba-114">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="549ba-115">181</span><span class="sxs-lookup"><span data-stu-id="549ba-115">181</span></span>|<span data-ttu-id="549ba-116">Začátek ověřování se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="549ba-116">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="549ba-117">182</span><span class="sxs-lookup"><span data-stu-id="549ba-117">182</span></span>|<span data-ttu-id="549ba-118">Konec ověřování se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="549ba-118">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="549ba-119">V následující tabulce jsou uvedena data události.</span><span class="sxs-lookup"><span data-stu-id="549ba-119">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="549ba-120">název pole</span><span class="sxs-lookup"><span data-stu-id="549ba-120">Field name</span></span>|<span data-ttu-id="549ba-121">Datový typ</span><span class="sxs-lookup"><span data-stu-id="549ba-121">Data type</span></span>|<span data-ttu-id="549ba-122">Popis</span><span class="sxs-lookup"><span data-stu-id="549ba-122">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="549ba-123">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="549ba-123">VerificationFlags</span></span>|<span data-ttu-id="549ba-124">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="549ba-124">win:UInt32</span></span>|<span data-ttu-id="549ba-125">Příznaky ověřování.</span><span class="sxs-lookup"><span data-stu-id="549ba-125">The verification flags.</span></span>|  
|<span data-ttu-id="549ba-126">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="549ba-126">ErrorCode</span></span>|<span data-ttu-id="549ba-127">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="549ba-127">win:UInt32</span></span>|<span data-ttu-id="549ba-128">Kód chyby HResult.</span><span class="sxs-lookup"><span data-stu-id="549ba-128">The HResult error code.</span></span>|  
|<span data-ttu-id="549ba-129">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="549ba-129">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="549ba-130">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="549ba-130">win:UnicodeString</span></span>|<span data-ttu-id="549ba-131">Plně kvalifikovaný název sestavení.</span><span class="sxs-lookup"><span data-stu-id="549ba-131">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="549ba-132">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="549ba-132">ClrInstanceID</span></span>|<span data-ttu-id="549ba-133">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="549ba-133">win:UInt16</span></span>|<span data-ttu-id="549ba-134">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="549ba-134">Unique ID for the instance of CLR or CoreCLR.</span></span>|  

## <a name="authenticodeverificationstart_v1-and-authenticodeverificationstop_v1-events"></a><span data-ttu-id="549ba-135">Události AuthenticodeVerificationStart_V1 a AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="549ba-135">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="549ba-136">Klíčové slovo a úroveň jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="549ba-136">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="549ba-137">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="549ba-137">Keyword for raising the event</span></span>|<span data-ttu-id="549ba-138">Obsah</span><span class="sxs-lookup"><span data-stu-id="549ba-138">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="549ba-139">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="549ba-139">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="549ba-140">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="549ba-140">Informational(4)</span></span>|  
  
 <span data-ttu-id="549ba-141">V následující tabulce jsou uvedeny informace o událostech.</span><span class="sxs-lookup"><span data-stu-id="549ba-141">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="549ba-142">Událost</span><span class="sxs-lookup"><span data-stu-id="549ba-142">Event</span></span>|<span data-ttu-id="549ba-143">ID události</span><span class="sxs-lookup"><span data-stu-id="549ba-143">Event ID</span></span>|<span data-ttu-id="549ba-144">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="549ba-144">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="549ba-145">183</span><span class="sxs-lookup"><span data-stu-id="549ba-145">183</span></span>|<span data-ttu-id="549ba-146">Začátek ověřování Authenticode</span><span class="sxs-lookup"><span data-stu-id="549ba-146">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="549ba-147">184</span><span class="sxs-lookup"><span data-stu-id="549ba-147">184</span></span>|<span data-ttu-id="549ba-148">Konec ověřování Authenticode</span><span class="sxs-lookup"><span data-stu-id="549ba-148">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="549ba-149">V následující tabulce jsou uvedena data události.</span><span class="sxs-lookup"><span data-stu-id="549ba-149">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="549ba-150">název pole</span><span class="sxs-lookup"><span data-stu-id="549ba-150">Field name</span></span>|<span data-ttu-id="549ba-151">Datový typ</span><span class="sxs-lookup"><span data-stu-id="549ba-151">Data type</span></span>|<span data-ttu-id="549ba-152">Popis</span><span class="sxs-lookup"><span data-stu-id="549ba-152">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="549ba-153">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="549ba-153">VerificationFlags</span></span>|<span data-ttu-id="549ba-154">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="549ba-154">win:UInt32</span></span>|<span data-ttu-id="549ba-155">Příznaky ověřování.</span><span class="sxs-lookup"><span data-stu-id="549ba-155">The verification flags.</span></span>|  
|<span data-ttu-id="549ba-156">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="549ba-156">ErrorCode</span></span>|<span data-ttu-id="549ba-157">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="549ba-157">win:UInt32</span></span>|<span data-ttu-id="549ba-158">Kód chyby HResult.</span><span class="sxs-lookup"><span data-stu-id="549ba-158">The HResult error code.</span></span>|  
|<span data-ttu-id="549ba-159">ModulePath nastavte</span><span class="sxs-lookup"><span data-stu-id="549ba-159">ModulePath</span></span>|<span data-ttu-id="549ba-160">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="549ba-160">win:UnicodeString</span></span>|<span data-ttu-id="549ba-161">Cesta k modulu</span><span class="sxs-lookup"><span data-stu-id="549ba-161">The module path.</span></span>|  
|<span data-ttu-id="549ba-162">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="549ba-162">ClrInstanceID</span></span>|<span data-ttu-id="549ba-163">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="549ba-163">win:UInt16</span></span>|<span data-ttu-id="549ba-164">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="549ba-164">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="549ba-165">Viz také:</span><span class="sxs-lookup"><span data-stu-id="549ba-165">See also</span></span>

- [<span data-ttu-id="549ba-166">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="549ba-166">CLR ETW Events</span></span>](clr-etw-events.md)
