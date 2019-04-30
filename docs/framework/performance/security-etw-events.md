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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949198"
---
# <a name="security-etw-events"></a><span data-ttu-id="4ac7e-102">Události Trasování událostí pro Windows zabezpečení</span><span class="sxs-lookup"><span data-stu-id="4ac7e-102">Security ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="4ac7e-103">Události zabezpečení jsou aktivovány v průběhu ověřování silných názvů a ověření pomocí technologie Authenticode.</span><span class="sxs-lookup"><span data-stu-id="4ac7e-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="4ac7e-104">Tato kategorie se skládá z následujících událostí:</span><span class="sxs-lookup"><span data-stu-id="4ac7e-104">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="4ac7e-105">StrongNameVerificationStart_V1 a StrongNameVerificationStop_V1 události</span><span class="sxs-lookup"><span data-stu-id="4ac7e-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
- [<span data-ttu-id="4ac7e-106">AuthenticodeVerificationStart_V1 a AuthenticodeVerificationStop_V1 události</span><span class="sxs-lookup"><span data-stu-id="4ac7e-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a><span data-ttu-id="4ac7e-107">StrongNameVerificationStart_V1 a StrongNameVerificationStop_V1 události</span><span class="sxs-lookup"><span data-stu-id="4ac7e-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="4ac7e-108">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="4ac7e-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="4ac7e-109">(Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="4ac7e-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="4ac7e-110">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="4ac7e-110">Keyword for raising the event</span></span>|<span data-ttu-id="4ac7e-111">úroveň</span><span class="sxs-lookup"><span data-stu-id="4ac7e-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="4ac7e-112">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="4ac7e-112">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="4ac7e-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="4ac7e-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="4ac7e-114">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="4ac7e-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="4ac7e-115">Událost</span><span class="sxs-lookup"><span data-stu-id="4ac7e-115">Event</span></span>|<span data-ttu-id="4ac7e-116">ID události</span><span class="sxs-lookup"><span data-stu-id="4ac7e-116">Event ID</span></span>|<span data-ttu-id="4ac7e-117">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="4ac7e-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="4ac7e-118">181</span><span class="sxs-lookup"><span data-stu-id="4ac7e-118">181</span></span>|<span data-ttu-id="4ac7e-119">Začátek ověřování silných názvů.</span><span class="sxs-lookup"><span data-stu-id="4ac7e-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="4ac7e-120">182</span><span class="sxs-lookup"><span data-stu-id="4ac7e-120">182</span></span>|<span data-ttu-id="4ac7e-121">Konec ověřování silných názvů.</span><span class="sxs-lookup"><span data-stu-id="4ac7e-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="4ac7e-122">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="4ac7e-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="4ac7e-123">Název pole</span><span class="sxs-lookup"><span data-stu-id="4ac7e-123">Field name</span></span>|<span data-ttu-id="4ac7e-124">Datový typ</span><span class="sxs-lookup"><span data-stu-id="4ac7e-124">Data type</span></span>|<span data-ttu-id="4ac7e-125">Popis</span><span class="sxs-lookup"><span data-stu-id="4ac7e-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="4ac7e-126">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="4ac7e-126">VerificationFlags</span></span>|<span data-ttu-id="4ac7e-127">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="4ac7e-127">win:UInt32</span></span>|<span data-ttu-id="4ac7e-128">Příznaky ověření.</span><span class="sxs-lookup"><span data-stu-id="4ac7e-128">The verification flags.</span></span>|  
|<span data-ttu-id="4ac7e-129">Kód chyby</span><span class="sxs-lookup"><span data-stu-id="4ac7e-129">ErrorCode</span></span>|<span data-ttu-id="4ac7e-130">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="4ac7e-130">win:UInt32</span></span>|<span data-ttu-id="4ac7e-131">Kód chyby HResult.</span><span class="sxs-lookup"><span data-stu-id="4ac7e-131">The HResult error code.</span></span>|  
|<span data-ttu-id="4ac7e-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="4ac7e-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="4ac7e-133">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="4ac7e-133">win:UnicodeString</span></span>|<span data-ttu-id="4ac7e-134">Plně kvalifikovaný název.</span><span class="sxs-lookup"><span data-stu-id="4ac7e-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="4ac7e-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="4ac7e-135">ClrInstanceID</span></span>|<span data-ttu-id="4ac7e-136">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="4ac7e-136">win:UInt16</span></span>|<span data-ttu-id="4ac7e-137">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4ac7e-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="4ac7e-138">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="4ac7e-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a><span data-ttu-id="4ac7e-139">AuthenticodeVerificationStart_V1 a AuthenticodeVerificationStop_V1 události</span><span class="sxs-lookup"><span data-stu-id="4ac7e-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="4ac7e-140">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="4ac7e-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="4ac7e-141">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="4ac7e-141">Keyword for raising the event</span></span>|<span data-ttu-id="4ac7e-142">úroveň</span><span class="sxs-lookup"><span data-stu-id="4ac7e-142">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="4ac7e-143">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="4ac7e-143">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="4ac7e-144">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="4ac7e-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="4ac7e-145">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="4ac7e-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="4ac7e-146">Událost</span><span class="sxs-lookup"><span data-stu-id="4ac7e-146">Event</span></span>|<span data-ttu-id="4ac7e-147">ID události</span><span class="sxs-lookup"><span data-stu-id="4ac7e-147">Event ID</span></span>|<span data-ttu-id="4ac7e-148">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="4ac7e-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="4ac7e-149">183</span><span class="sxs-lookup"><span data-stu-id="4ac7e-149">183</span></span>|<span data-ttu-id="4ac7e-150">Bylo zahájeno ověřování Authenticode.</span><span class="sxs-lookup"><span data-stu-id="4ac7e-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="4ac7e-151">184</span><span class="sxs-lookup"><span data-stu-id="4ac7e-151">184</span></span>|<span data-ttu-id="4ac7e-152">Konec ověření pomocí technologie Authenticode.</span><span class="sxs-lookup"><span data-stu-id="4ac7e-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="4ac7e-153">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="4ac7e-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="4ac7e-154">Název pole</span><span class="sxs-lookup"><span data-stu-id="4ac7e-154">Field name</span></span>|<span data-ttu-id="4ac7e-155">Datový typ</span><span class="sxs-lookup"><span data-stu-id="4ac7e-155">Data type</span></span>|<span data-ttu-id="4ac7e-156">Popis</span><span class="sxs-lookup"><span data-stu-id="4ac7e-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="4ac7e-157">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="4ac7e-157">VerificationFlags</span></span>|<span data-ttu-id="4ac7e-158">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="4ac7e-158">win:UInt32</span></span>|<span data-ttu-id="4ac7e-159">Příznaky ověření.</span><span class="sxs-lookup"><span data-stu-id="4ac7e-159">The verification flags.</span></span>|  
|<span data-ttu-id="4ac7e-160">Kód chyby</span><span class="sxs-lookup"><span data-stu-id="4ac7e-160">ErrorCode</span></span>|<span data-ttu-id="4ac7e-161">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="4ac7e-161">win:UInt32</span></span>|<span data-ttu-id="4ac7e-162">Kód chyby HResult.</span><span class="sxs-lookup"><span data-stu-id="4ac7e-162">The HResult error code.</span></span>|  
|<span data-ttu-id="4ac7e-163">ModulePath</span><span class="sxs-lookup"><span data-stu-id="4ac7e-163">ModulePath</span></span>|<span data-ttu-id="4ac7e-164">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="4ac7e-164">win:UnicodeString</span></span>|<span data-ttu-id="4ac7e-165">Cesta modulu.</span><span class="sxs-lookup"><span data-stu-id="4ac7e-165">The module path.</span></span>|  
|<span data-ttu-id="4ac7e-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="4ac7e-166">ClrInstanceID</span></span>|<span data-ttu-id="4ac7e-167">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="4ac7e-167">win:UInt16</span></span>|<span data-ttu-id="4ac7e-168">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4ac7e-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4ac7e-169">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4ac7e-169">See also</span></span>

- [<span data-ttu-id="4ac7e-170">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="4ac7e-170">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
