---
title: Události Trasování událostí pro Windows zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5cd5e660778b852cfee84359bb4d7253ca8f118d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608073"
---
# <a name="security-etw-events"></a><span data-ttu-id="eeb4f-102">Události Trasování událostí pro Windows zabezpečení</span><span class="sxs-lookup"><span data-stu-id="eeb4f-102">Security ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="eeb4f-103">Události zabezpečení jsou aktivovány v průběhu ověřování silných názvů a ověření pomocí technologie Authenticode.</span><span class="sxs-lookup"><span data-stu-id="eeb4f-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="eeb4f-104">Tato kategorie se skládá z následujících událostí:</span><span class="sxs-lookup"><span data-stu-id="eeb4f-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="eeb4f-105">StrongNameVerificationStart_V1 a StrongNameVerificationStop_V1 události</span><span class="sxs-lookup"><span data-stu-id="eeb4f-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
-   [<span data-ttu-id="eeb4f-106">AuthenticodeVerificationStart_V1 a AuthenticodeVerificationStop_V1 události</span><span class="sxs-lookup"><span data-stu-id="eeb4f-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a><span data-ttu-id="eeb4f-107">StrongNameVerificationStart_V1 a StrongNameVerificationStop_V1 události</span><span class="sxs-lookup"><span data-stu-id="eeb4f-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="eeb4f-108">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="eeb4f-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="eeb4f-109">(Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="eeb4f-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="eeb4f-110">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="eeb4f-110">Keyword for raising the event</span></span>|<span data-ttu-id="eeb4f-111">úroveň</span><span class="sxs-lookup"><span data-stu-id="eeb4f-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="eeb4f-112">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="eeb4f-112">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="eeb4f-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="eeb4f-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="eeb4f-114">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="eeb4f-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="eeb4f-115">Událost</span><span class="sxs-lookup"><span data-stu-id="eeb4f-115">Event</span></span>|<span data-ttu-id="eeb4f-116">ID události</span><span class="sxs-lookup"><span data-stu-id="eeb4f-116">Event ID</span></span>|<span data-ttu-id="eeb4f-117">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="eeb4f-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="eeb4f-118">181</span><span class="sxs-lookup"><span data-stu-id="eeb4f-118">181</span></span>|<span data-ttu-id="eeb4f-119">Začátek ověřování silných názvů.</span><span class="sxs-lookup"><span data-stu-id="eeb4f-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="eeb4f-120">182</span><span class="sxs-lookup"><span data-stu-id="eeb4f-120">182</span></span>|<span data-ttu-id="eeb4f-121">Konec ověřování silných názvů.</span><span class="sxs-lookup"><span data-stu-id="eeb4f-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="eeb4f-122">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="eeb4f-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="eeb4f-123">Název pole</span><span class="sxs-lookup"><span data-stu-id="eeb4f-123">Field name</span></span>|<span data-ttu-id="eeb4f-124">Datový typ</span><span class="sxs-lookup"><span data-stu-id="eeb4f-124">Data type</span></span>|<span data-ttu-id="eeb4f-125">Popis</span><span class="sxs-lookup"><span data-stu-id="eeb4f-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="eeb4f-126">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="eeb4f-126">VerificationFlags</span></span>|<span data-ttu-id="eeb4f-127">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="eeb4f-127">win:UInt32</span></span>|<span data-ttu-id="eeb4f-128">Příznaky ověření.</span><span class="sxs-lookup"><span data-stu-id="eeb4f-128">The verification flags.</span></span>|  
|<span data-ttu-id="eeb4f-129">Kód chyby</span><span class="sxs-lookup"><span data-stu-id="eeb4f-129">ErrorCode</span></span>|<span data-ttu-id="eeb4f-130">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="eeb4f-130">win:UInt32</span></span>|<span data-ttu-id="eeb4f-131">Kód chyby HResult.</span><span class="sxs-lookup"><span data-stu-id="eeb4f-131">The HResult error code.</span></span>|  
|<span data-ttu-id="eeb4f-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="eeb4f-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="eeb4f-133">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="eeb4f-133">win:UnicodeString</span></span>|<span data-ttu-id="eeb4f-134">Plně kvalifikovaný název.</span><span class="sxs-lookup"><span data-stu-id="eeb4f-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="eeb4f-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="eeb4f-135">ClrInstanceID</span></span>|<span data-ttu-id="eeb4f-136">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="eeb4f-136">win:UInt16</span></span>|<span data-ttu-id="eeb4f-137">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="eeb4f-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="eeb4f-138">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="eeb4f-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a><span data-ttu-id="eeb4f-139">AuthenticodeVerificationStart_V1 a AuthenticodeVerificationStop_V1 události</span><span class="sxs-lookup"><span data-stu-id="eeb4f-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="eeb4f-140">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="eeb4f-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="eeb4f-141">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="eeb4f-141">Keyword for raising the event</span></span>|<span data-ttu-id="eeb4f-142">úroveň</span><span class="sxs-lookup"><span data-stu-id="eeb4f-142">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="eeb4f-143">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="eeb4f-143">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="eeb4f-144">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="eeb4f-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="eeb4f-145">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="eeb4f-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="eeb4f-146">Událost</span><span class="sxs-lookup"><span data-stu-id="eeb4f-146">Event</span></span>|<span data-ttu-id="eeb4f-147">ID události</span><span class="sxs-lookup"><span data-stu-id="eeb4f-147">Event ID</span></span>|<span data-ttu-id="eeb4f-148">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="eeb4f-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="eeb4f-149">183</span><span class="sxs-lookup"><span data-stu-id="eeb4f-149">183</span></span>|<span data-ttu-id="eeb4f-150">Bylo zahájeno ověřování Authenticode.</span><span class="sxs-lookup"><span data-stu-id="eeb4f-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="eeb4f-151">184</span><span class="sxs-lookup"><span data-stu-id="eeb4f-151">184</span></span>|<span data-ttu-id="eeb4f-152">Konec ověření pomocí technologie Authenticode.</span><span class="sxs-lookup"><span data-stu-id="eeb4f-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="eeb4f-153">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="eeb4f-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="eeb4f-154">Název pole</span><span class="sxs-lookup"><span data-stu-id="eeb4f-154">Field name</span></span>|<span data-ttu-id="eeb4f-155">Datový typ</span><span class="sxs-lookup"><span data-stu-id="eeb4f-155">Data type</span></span>|<span data-ttu-id="eeb4f-156">Popis</span><span class="sxs-lookup"><span data-stu-id="eeb4f-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="eeb4f-157">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="eeb4f-157">VerificationFlags</span></span>|<span data-ttu-id="eeb4f-158">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="eeb4f-158">win:UInt32</span></span>|<span data-ttu-id="eeb4f-159">Příznaky ověření.</span><span class="sxs-lookup"><span data-stu-id="eeb4f-159">The verification flags.</span></span>|  
|<span data-ttu-id="eeb4f-160">Kód chyby</span><span class="sxs-lookup"><span data-stu-id="eeb4f-160">ErrorCode</span></span>|<span data-ttu-id="eeb4f-161">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="eeb4f-161">win:UInt32</span></span>|<span data-ttu-id="eeb4f-162">Kód chyby HResult.</span><span class="sxs-lookup"><span data-stu-id="eeb4f-162">The HResult error code.</span></span>|  
|<span data-ttu-id="eeb4f-163">ModulePath</span><span class="sxs-lookup"><span data-stu-id="eeb4f-163">ModulePath</span></span>|<span data-ttu-id="eeb4f-164">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="eeb4f-164">win:UnicodeString</span></span>|<span data-ttu-id="eeb4f-165">Cesta modulu.</span><span class="sxs-lookup"><span data-stu-id="eeb4f-165">The module path.</span></span>|  
|<span data-ttu-id="eeb4f-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="eeb4f-166">ClrInstanceID</span></span>|<span data-ttu-id="eeb4f-167">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="eeb4f-167">win:UInt16</span></span>|<span data-ttu-id="eeb4f-168">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="eeb4f-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eeb4f-169">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eeb4f-169">See also</span></span>
- [<span data-ttu-id="eeb4f-170">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="eeb4f-170">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
