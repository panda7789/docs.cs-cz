---
title: Události Trasování událostí pro Windows zabezpečení
description: Seznamte se s událostmi ETW zabezpečení, které jsou vyvolány při ověřování silného názvu a ověřování technologií Authenticode v rozhraní .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
ms.openlocfilehash: 2fd2d450223cd16a7791b8f6c67afe6bcb954eb3
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474212"
---
# <a name="security-etw-events"></a><span data-ttu-id="f756e-103">Události Trasování událostí pro Windows zabezpečení</span><span class="sxs-lookup"><span data-stu-id="f756e-103">Security ETW Events</span></span>

<span data-ttu-id="f756e-104">Události zabezpečení jsou vyvolány během ověřování silných názvů a při ověřování prostřednictvím technologie Authenticode.</span><span class="sxs-lookup"><span data-stu-id="f756e-104">Security events are raised during strong name verification and Authenticode verification.</span></span>  

## <a name="strongnameverificationstart_v1-and-strongnameverificationstop_v1-events"></a><span data-ttu-id="f756e-105">Události StrongNameVerificationStart_V1 a StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="f756e-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="f756e-106">Klíčové slovo a úroveň jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="f756e-106">The following table shows the keyword and level.</span></span> <span data-ttu-id="f756e-107">(Další informace najdete v tématu [klíčová slova a úrovně CLR ETW](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="f756e-107">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="f756e-108">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="f756e-108">Keyword for raising the event</span></span>|<span data-ttu-id="f756e-109">Úroveň</span><span class="sxs-lookup"><span data-stu-id="f756e-109">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f756e-110">`SecurityKeyword`(0x400)</span><span class="sxs-lookup"><span data-stu-id="f756e-110">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="f756e-111">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="f756e-111">Informational(4)</span></span>|  
  
 <span data-ttu-id="f756e-112">V následující tabulce jsou uvedeny informace o událostech.</span><span class="sxs-lookup"><span data-stu-id="f756e-112">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f756e-113">Událost</span><span class="sxs-lookup"><span data-stu-id="f756e-113">Event</span></span>|<span data-ttu-id="f756e-114">ID události</span><span class="sxs-lookup"><span data-stu-id="f756e-114">Event ID</span></span>|<span data-ttu-id="f756e-115">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="f756e-115">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="f756e-116">181</span><span class="sxs-lookup"><span data-stu-id="f756e-116">181</span></span>|<span data-ttu-id="f756e-117">Začátek ověřování se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="f756e-117">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="f756e-118">182</span><span class="sxs-lookup"><span data-stu-id="f756e-118">182</span></span>|<span data-ttu-id="f756e-119">Konec ověřování se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="f756e-119">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="f756e-120">V následující tabulce jsou uvedena data události.</span><span class="sxs-lookup"><span data-stu-id="f756e-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="f756e-121">Název pole</span><span class="sxs-lookup"><span data-stu-id="f756e-121">Field name</span></span>|<span data-ttu-id="f756e-122">Datový typ</span><span class="sxs-lookup"><span data-stu-id="f756e-122">Data type</span></span>|<span data-ttu-id="f756e-123">Popis</span><span class="sxs-lookup"><span data-stu-id="f756e-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f756e-124">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="f756e-124">VerificationFlags</span></span>|<span data-ttu-id="f756e-125">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="f756e-125">win:UInt32</span></span>|<span data-ttu-id="f756e-126">Příznaky ověřování.</span><span class="sxs-lookup"><span data-stu-id="f756e-126">The verification flags.</span></span>|  
|<span data-ttu-id="f756e-127">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="f756e-127">ErrorCode</span></span>|<span data-ttu-id="f756e-128">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="f756e-128">win:UInt32</span></span>|<span data-ttu-id="f756e-129">Kód chyby HResult.</span><span class="sxs-lookup"><span data-stu-id="f756e-129">The HResult error code.</span></span>|  
|<span data-ttu-id="f756e-130">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="f756e-130">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="f756e-131">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="f756e-131">win:UnicodeString</span></span>|<span data-ttu-id="f756e-132">Plně kvalifikovaný název sestavení.</span><span class="sxs-lookup"><span data-stu-id="f756e-132">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="f756e-133">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f756e-133">ClrInstanceID</span></span>|<span data-ttu-id="f756e-134">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="f756e-134">win:UInt16</span></span>|<span data-ttu-id="f756e-135">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="f756e-135">Unique ID for the instance of CLR or CoreCLR.</span></span>|  

## <a name="authenticodeverificationstart_v1-and-authenticodeverificationstop_v1-events"></a><span data-ttu-id="f756e-136">Události AuthenticodeVerificationStart_V1 a AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="f756e-136">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="f756e-137">Klíčové slovo a úroveň jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="f756e-137">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="f756e-138">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="f756e-138">Keyword for raising the event</span></span>|<span data-ttu-id="f756e-139">Úroveň</span><span class="sxs-lookup"><span data-stu-id="f756e-139">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f756e-140">`SecurityKeyword`(0x400)</span><span class="sxs-lookup"><span data-stu-id="f756e-140">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="f756e-141">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="f756e-141">Informational(4)</span></span>|  
  
 <span data-ttu-id="f756e-142">V následující tabulce jsou uvedeny informace o událostech.</span><span class="sxs-lookup"><span data-stu-id="f756e-142">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f756e-143">Událost</span><span class="sxs-lookup"><span data-stu-id="f756e-143">Event</span></span>|<span data-ttu-id="f756e-144">ID události</span><span class="sxs-lookup"><span data-stu-id="f756e-144">Event ID</span></span>|<span data-ttu-id="f756e-145">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="f756e-145">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="f756e-146">183</span><span class="sxs-lookup"><span data-stu-id="f756e-146">183</span></span>|<span data-ttu-id="f756e-147">Začátek ověřování Authenticode</span><span class="sxs-lookup"><span data-stu-id="f756e-147">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="f756e-148">184</span><span class="sxs-lookup"><span data-stu-id="f756e-148">184</span></span>|<span data-ttu-id="f756e-149">Konec ověřování Authenticode</span><span class="sxs-lookup"><span data-stu-id="f756e-149">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="f756e-150">V následující tabulce jsou uvedena data události.</span><span class="sxs-lookup"><span data-stu-id="f756e-150">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="f756e-151">Název pole</span><span class="sxs-lookup"><span data-stu-id="f756e-151">Field name</span></span>|<span data-ttu-id="f756e-152">Datový typ</span><span class="sxs-lookup"><span data-stu-id="f756e-152">Data type</span></span>|<span data-ttu-id="f756e-153">Popis</span><span class="sxs-lookup"><span data-stu-id="f756e-153">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f756e-154">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="f756e-154">VerificationFlags</span></span>|<span data-ttu-id="f756e-155">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="f756e-155">win:UInt32</span></span>|<span data-ttu-id="f756e-156">Příznaky ověřování.</span><span class="sxs-lookup"><span data-stu-id="f756e-156">The verification flags.</span></span>|  
|<span data-ttu-id="f756e-157">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="f756e-157">ErrorCode</span></span>|<span data-ttu-id="f756e-158">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="f756e-158">win:UInt32</span></span>|<span data-ttu-id="f756e-159">Kód chyby HResult.</span><span class="sxs-lookup"><span data-stu-id="f756e-159">The HResult error code.</span></span>|  
|<span data-ttu-id="f756e-160">ModulePath nastavte</span><span class="sxs-lookup"><span data-stu-id="f756e-160">ModulePath</span></span>|<span data-ttu-id="f756e-161">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="f756e-161">win:UnicodeString</span></span>|<span data-ttu-id="f756e-162">Cesta k modulu</span><span class="sxs-lookup"><span data-stu-id="f756e-162">The module path.</span></span>|  
|<span data-ttu-id="f756e-163">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f756e-163">ClrInstanceID</span></span>|<span data-ttu-id="f756e-164">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="f756e-164">win:UInt16</span></span>|<span data-ttu-id="f756e-165">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="f756e-165">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f756e-166">Viz také</span><span class="sxs-lookup"><span data-stu-id="f756e-166">See also</span></span>

- [<span data-ttu-id="f756e-167">Události ETW CLR</span><span class="sxs-lookup"><span data-stu-id="f756e-167">CLR ETW Events</span></span>](clr-etw-events.md)
