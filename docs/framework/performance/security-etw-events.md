---
title: Události Trasování událostí pro Windows zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11a19dce496423883e5fed62375c6db8ed5efdb1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134027"
---
# <a name="security-etw-events"></a><span data-ttu-id="88405-102">Události Trasování událostí pro Windows zabezpečení</span><span class="sxs-lookup"><span data-stu-id="88405-102">Security ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="88405-103">Události zabezpečení jsou aktivovány v průběhu ověřování silných názvů a ověření pomocí technologie Authenticode.</span><span class="sxs-lookup"><span data-stu-id="88405-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="88405-104">Tato kategorie se skládá z následujících událostí:</span><span class="sxs-lookup"><span data-stu-id="88405-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="88405-105">StrongNameVerificationStart_V1 a StrongNameVerificationStop_V1 události</span><span class="sxs-lookup"><span data-stu-id="88405-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
-   [<span data-ttu-id="88405-106">AuthenticodeVerificationStart_V1 a AuthenticodeVerificationStop_V1 události</span><span class="sxs-lookup"><span data-stu-id="88405-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a><span data-ttu-id="88405-107">StrongNameVerificationStart_V1 a StrongNameVerificationStop_V1 události</span><span class="sxs-lookup"><span data-stu-id="88405-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="88405-108">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="88405-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="88405-109">(Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="88405-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="88405-110">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="88405-110">Keyword for raising the event</span></span>|<span data-ttu-id="88405-111">úroveň</span><span class="sxs-lookup"><span data-stu-id="88405-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="88405-112">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="88405-112">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="88405-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="88405-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="88405-114">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="88405-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="88405-115">Událost</span><span class="sxs-lookup"><span data-stu-id="88405-115">Event</span></span>|<span data-ttu-id="88405-116">ID události</span><span class="sxs-lookup"><span data-stu-id="88405-116">Event ID</span></span>|<span data-ttu-id="88405-117">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="88405-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="88405-118">181</span><span class="sxs-lookup"><span data-stu-id="88405-118">181</span></span>|<span data-ttu-id="88405-119">Začátek ověřování silných názvů.</span><span class="sxs-lookup"><span data-stu-id="88405-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="88405-120">182</span><span class="sxs-lookup"><span data-stu-id="88405-120">182</span></span>|<span data-ttu-id="88405-121">Konec ověřování silných názvů.</span><span class="sxs-lookup"><span data-stu-id="88405-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="88405-122">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="88405-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="88405-123">Název pole</span><span class="sxs-lookup"><span data-stu-id="88405-123">Field name</span></span>|<span data-ttu-id="88405-124">Datový typ</span><span class="sxs-lookup"><span data-stu-id="88405-124">Data type</span></span>|<span data-ttu-id="88405-125">Popis</span><span class="sxs-lookup"><span data-stu-id="88405-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="88405-126">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="88405-126">VerificationFlags</span></span>|<span data-ttu-id="88405-127">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="88405-127">win:UInt32</span></span>|<span data-ttu-id="88405-128">Příznaky ověření.</span><span class="sxs-lookup"><span data-stu-id="88405-128">The verification flags.</span></span>|  
|<span data-ttu-id="88405-129">Kód chyby</span><span class="sxs-lookup"><span data-stu-id="88405-129">ErrorCode</span></span>|<span data-ttu-id="88405-130">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="88405-130">win:UInt32</span></span>|<span data-ttu-id="88405-131">Kód chyby HResult.</span><span class="sxs-lookup"><span data-stu-id="88405-131">The HResult error code.</span></span>|  
|<span data-ttu-id="88405-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="88405-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="88405-133">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="88405-133">win:UnicodeString</span></span>|<span data-ttu-id="88405-134">Plně kvalifikovaný název.</span><span class="sxs-lookup"><span data-stu-id="88405-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="88405-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="88405-135">ClrInstanceID</span></span>|<span data-ttu-id="88405-136">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="88405-136">win:UInt16</span></span>|<span data-ttu-id="88405-137">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="88405-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="88405-138">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="88405-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a><span data-ttu-id="88405-139">AuthenticodeVerificationStart_V1 a AuthenticodeVerificationStop_V1 události</span><span class="sxs-lookup"><span data-stu-id="88405-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="88405-140">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="88405-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="88405-141">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="88405-141">Keyword for raising the event</span></span>|<span data-ttu-id="88405-142">úroveň</span><span class="sxs-lookup"><span data-stu-id="88405-142">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="88405-143">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="88405-143">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="88405-144">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="88405-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="88405-145">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="88405-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="88405-146">Událost</span><span class="sxs-lookup"><span data-stu-id="88405-146">Event</span></span>|<span data-ttu-id="88405-147">ID události</span><span class="sxs-lookup"><span data-stu-id="88405-147">Event ID</span></span>|<span data-ttu-id="88405-148">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="88405-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="88405-149">183</span><span class="sxs-lookup"><span data-stu-id="88405-149">183</span></span>|<span data-ttu-id="88405-150">Bylo zahájeno ověřování Authenticode.</span><span class="sxs-lookup"><span data-stu-id="88405-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="88405-151">184</span><span class="sxs-lookup"><span data-stu-id="88405-151">184</span></span>|<span data-ttu-id="88405-152">Konec ověření pomocí technologie Authenticode.</span><span class="sxs-lookup"><span data-stu-id="88405-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="88405-153">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="88405-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="88405-154">Název pole</span><span class="sxs-lookup"><span data-stu-id="88405-154">Field name</span></span>|<span data-ttu-id="88405-155">Datový typ</span><span class="sxs-lookup"><span data-stu-id="88405-155">Data type</span></span>|<span data-ttu-id="88405-156">Popis</span><span class="sxs-lookup"><span data-stu-id="88405-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="88405-157">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="88405-157">VerificationFlags</span></span>|<span data-ttu-id="88405-158">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="88405-158">win:UInt32</span></span>|<span data-ttu-id="88405-159">Příznaky ověření.</span><span class="sxs-lookup"><span data-stu-id="88405-159">The verification flags.</span></span>|  
|<span data-ttu-id="88405-160">Kód chyby</span><span class="sxs-lookup"><span data-stu-id="88405-160">ErrorCode</span></span>|<span data-ttu-id="88405-161">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="88405-161">win:UInt32</span></span>|<span data-ttu-id="88405-162">Kód chyby HResult.</span><span class="sxs-lookup"><span data-stu-id="88405-162">The HResult error code.</span></span>|  
|<span data-ttu-id="88405-163">ModulePath</span><span class="sxs-lookup"><span data-stu-id="88405-163">ModulePath</span></span>|<span data-ttu-id="88405-164">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="88405-164">win:UnicodeString</span></span>|<span data-ttu-id="88405-165">Cesta modulu.</span><span class="sxs-lookup"><span data-stu-id="88405-165">The module path.</span></span>|  
|<span data-ttu-id="88405-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="88405-166">ClrInstanceID</span></span>|<span data-ttu-id="88405-167">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="88405-167">win:UInt16</span></span>|<span data-ttu-id="88405-168">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="88405-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="88405-169">Viz také:</span><span class="sxs-lookup"><span data-stu-id="88405-169">See also</span></span>

- [<span data-ttu-id="88405-170">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="88405-170">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
