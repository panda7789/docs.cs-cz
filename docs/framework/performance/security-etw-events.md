---
title: Události Trasování událostí pro Windows zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e02274b63ddf7df42d26621791de0286df9655b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395509"
---
# <a name="security-etw-events"></a><span data-ttu-id="05558-102">Události Trasování událostí pro Windows zabezpečení</span><span class="sxs-lookup"><span data-stu-id="05558-102">Security ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="05558-103">Události zabezpečení jsou vyvolány během ověřování silných názvů a ověření Authenticode.</span><span class="sxs-lookup"><span data-stu-id="05558-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="05558-104">Tato kategorie se skládá z následujících událostí:</span><span class="sxs-lookup"><span data-stu-id="05558-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="05558-105">StrongNameVerificationStart_V1 a StrongNameVerificationStop_V1 události</span><span class="sxs-lookup"><span data-stu-id="05558-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
-   [<span data-ttu-id="05558-106">AuthenticodeVerificationStart_V1 a AuthenticodeVerificationStop_V1 události</span><span class="sxs-lookup"><span data-stu-id="05558-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a><span data-ttu-id="05558-107">StrongNameVerificationStart_V1 a StrongNameVerificationStop_V1 události</span><span class="sxs-lookup"><span data-stu-id="05558-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="05558-108">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="05558-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="05558-109">(Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="05558-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="05558-110">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="05558-110">Keyword for raising the event</span></span>|<span data-ttu-id="05558-111">úroveň</span><span class="sxs-lookup"><span data-stu-id="05558-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="05558-112">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="05558-112">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="05558-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="05558-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="05558-114">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="05558-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="05558-115">Událost</span><span class="sxs-lookup"><span data-stu-id="05558-115">Event</span></span>|<span data-ttu-id="05558-116">ID události</span><span class="sxs-lookup"><span data-stu-id="05558-116">Event ID</span></span>|<span data-ttu-id="05558-117">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="05558-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="05558-118">181</span><span class="sxs-lookup"><span data-stu-id="05558-118">181</span></span>|<span data-ttu-id="05558-119">Počáteční ověřování silných názvů.</span><span class="sxs-lookup"><span data-stu-id="05558-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="05558-120">182</span><span class="sxs-lookup"><span data-stu-id="05558-120">182</span></span>|<span data-ttu-id="05558-121">Konec ověřování silných názvů.</span><span class="sxs-lookup"><span data-stu-id="05558-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="05558-122">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="05558-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="05558-123">Název pole</span><span class="sxs-lookup"><span data-stu-id="05558-123">Field name</span></span>|<span data-ttu-id="05558-124">Datový typ</span><span class="sxs-lookup"><span data-stu-id="05558-124">Data type</span></span>|<span data-ttu-id="05558-125">Popis</span><span class="sxs-lookup"><span data-stu-id="05558-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="05558-126">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="05558-126">VerificationFlags</span></span>|<span data-ttu-id="05558-127">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="05558-127">win:UInt32</span></span>|<span data-ttu-id="05558-128">Příznaky ověření.</span><span class="sxs-lookup"><span data-stu-id="05558-128">The verification flags.</span></span>|  
|<span data-ttu-id="05558-129">Kód chyby</span><span class="sxs-lookup"><span data-stu-id="05558-129">ErrorCode</span></span>|<span data-ttu-id="05558-130">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="05558-130">win:UInt32</span></span>|<span data-ttu-id="05558-131">Kód chyby HResult.</span><span class="sxs-lookup"><span data-stu-id="05558-131">The HResult error code.</span></span>|  
|<span data-ttu-id="05558-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="05558-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="05558-133">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="05558-133">win:UnicodeString</span></span>|<span data-ttu-id="05558-134">Plně kvalifikovaný název.</span><span class="sxs-lookup"><span data-stu-id="05558-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="05558-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="05558-135">ClrInstanceID</span></span>|<span data-ttu-id="05558-136">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="05558-136">win:UInt16</span></span>|<span data-ttu-id="05558-137">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="05558-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="05558-138">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="05558-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a><span data-ttu-id="05558-139">AuthenticodeVerificationStart_V1 a AuthenticodeVerificationStop_V1 události</span><span class="sxs-lookup"><span data-stu-id="05558-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="05558-140">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="05558-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="05558-141">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="05558-141">Keyword for raising the event</span></span>|<span data-ttu-id="05558-142">úroveň</span><span class="sxs-lookup"><span data-stu-id="05558-142">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="05558-143">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="05558-143">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="05558-144">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="05558-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="05558-145">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="05558-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="05558-146">Událost</span><span class="sxs-lookup"><span data-stu-id="05558-146">Event</span></span>|<span data-ttu-id="05558-147">ID události</span><span class="sxs-lookup"><span data-stu-id="05558-147">Event ID</span></span>|<span data-ttu-id="05558-148">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="05558-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="05558-149">183</span><span class="sxs-lookup"><span data-stu-id="05558-149">183</span></span>|<span data-ttu-id="05558-150">Počáteční ověření Authenticode.</span><span class="sxs-lookup"><span data-stu-id="05558-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="05558-151">184</span><span class="sxs-lookup"><span data-stu-id="05558-151">184</span></span>|<span data-ttu-id="05558-152">Konec Authenticode ověření.</span><span class="sxs-lookup"><span data-stu-id="05558-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="05558-153">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="05558-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="05558-154">Název pole</span><span class="sxs-lookup"><span data-stu-id="05558-154">Field name</span></span>|<span data-ttu-id="05558-155">Datový typ</span><span class="sxs-lookup"><span data-stu-id="05558-155">Data type</span></span>|<span data-ttu-id="05558-156">Popis</span><span class="sxs-lookup"><span data-stu-id="05558-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="05558-157">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="05558-157">VerificationFlags</span></span>|<span data-ttu-id="05558-158">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="05558-158">win:UInt32</span></span>|<span data-ttu-id="05558-159">Příznaky ověření.</span><span class="sxs-lookup"><span data-stu-id="05558-159">The verification flags.</span></span>|  
|<span data-ttu-id="05558-160">Kód chyby</span><span class="sxs-lookup"><span data-stu-id="05558-160">ErrorCode</span></span>|<span data-ttu-id="05558-161">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="05558-161">win:UInt32</span></span>|<span data-ttu-id="05558-162">Kód chyby HResult.</span><span class="sxs-lookup"><span data-stu-id="05558-162">The HResult error code.</span></span>|  
|<span data-ttu-id="05558-163">ModulePath</span><span class="sxs-lookup"><span data-stu-id="05558-163">ModulePath</span></span>|<span data-ttu-id="05558-164">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="05558-164">win:UnicodeString</span></span>|<span data-ttu-id="05558-165">Cesta k modulu.</span><span class="sxs-lookup"><span data-stu-id="05558-165">The module path.</span></span>|  
|<span data-ttu-id="05558-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="05558-166">ClrInstanceID</span></span>|<span data-ttu-id="05558-167">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="05558-167">win:UInt16</span></span>|<span data-ttu-id="05558-168">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="05558-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="05558-169">Viz také</span><span class="sxs-lookup"><span data-stu-id="05558-169">See Also</span></span>  
 [<span data-ttu-id="05558-170">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="05558-170">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
