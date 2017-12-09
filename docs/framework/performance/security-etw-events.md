---
title: "Události Trasování událostí pro Windows zabezpečení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a7e28eeabecfe0f1043328618f6e1be143f198a6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="security-etw-events"></a><span data-ttu-id="fd437-102">Události Trasování událostí pro Windows zabezpečení</span><span class="sxs-lookup"><span data-stu-id="fd437-102">Security ETW Events</span></span>
<a name="top"></a><span data-ttu-id="fd437-103">Události zabezpečení jsou vyvolány během ověřování silných názvů a ověření Authenticode.</span><span class="sxs-lookup"><span data-stu-id="fd437-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="fd437-104">Tato kategorie se skládá z následujících událostí:</span><span class="sxs-lookup"><span data-stu-id="fd437-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="fd437-105">StrongNameVerificationStart_V1 a StrongNameVerificationStop_V1 události</span><span class="sxs-lookup"><span data-stu-id="fd437-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
-   [<span data-ttu-id="fd437-106">AuthenticodeVerificationStart_V1 a AuthenticodeVerificationStop_V1 události</span><span class="sxs-lookup"><span data-stu-id="fd437-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a><span data-ttu-id="fd437-107">StrongNameVerificationStart_V1 a StrongNameVerificationStop_V1 události</span><span class="sxs-lookup"><span data-stu-id="fd437-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="fd437-108">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="fd437-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="fd437-109">(Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="fd437-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="fd437-110">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="fd437-110">Keyword for raising the event</span></span>|<span data-ttu-id="fd437-111">úroveň</span><span class="sxs-lookup"><span data-stu-id="fd437-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="fd437-112">`SecurityKeyword`(0x400)</span><span class="sxs-lookup"><span data-stu-id="fd437-112">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="fd437-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="fd437-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="fd437-114">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="fd437-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="fd437-115">Událost</span><span class="sxs-lookup"><span data-stu-id="fd437-115">Event</span></span>|<span data-ttu-id="fd437-116">ID události</span><span class="sxs-lookup"><span data-stu-id="fd437-116">Event ID</span></span>|<span data-ttu-id="fd437-117">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="fd437-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="fd437-118">181</span><span class="sxs-lookup"><span data-stu-id="fd437-118">181</span></span>|<span data-ttu-id="fd437-119">Počáteční ověřování silných názvů.</span><span class="sxs-lookup"><span data-stu-id="fd437-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="fd437-120">182</span><span class="sxs-lookup"><span data-stu-id="fd437-120">182</span></span>|<span data-ttu-id="fd437-121">Konec ověřování silných názvů.</span><span class="sxs-lookup"><span data-stu-id="fd437-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="fd437-122">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="fd437-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="fd437-123">Název pole</span><span class="sxs-lookup"><span data-stu-id="fd437-123">Field name</span></span>|<span data-ttu-id="fd437-124">Datový typ</span><span class="sxs-lookup"><span data-stu-id="fd437-124">Data type</span></span>|<span data-ttu-id="fd437-125">Popis</span><span class="sxs-lookup"><span data-stu-id="fd437-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="fd437-126">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="fd437-126">VerificationFlags</span></span>|<span data-ttu-id="fd437-127">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="fd437-127">win:UInt32</span></span>|<span data-ttu-id="fd437-128">Příznaky ověření.</span><span class="sxs-lookup"><span data-stu-id="fd437-128">The verification flags.</span></span>|  
|<span data-ttu-id="fd437-129">Kód chyby</span><span class="sxs-lookup"><span data-stu-id="fd437-129">ErrorCode</span></span>|<span data-ttu-id="fd437-130">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="fd437-130">win:UInt32</span></span>|<span data-ttu-id="fd437-131">Kód chyby HResult.</span><span class="sxs-lookup"><span data-stu-id="fd437-131">The HResult error code.</span></span>|  
|<span data-ttu-id="fd437-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="fd437-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="fd437-133">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="fd437-133">win:UnicodeString</span></span>|<span data-ttu-id="fd437-134">Plně kvalifikovaný název.</span><span class="sxs-lookup"><span data-stu-id="fd437-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="fd437-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="fd437-135">ClrInstanceID</span></span>|<span data-ttu-id="fd437-136">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="fd437-136">win:UInt16</span></span>|<span data-ttu-id="fd437-137">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="fd437-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="fd437-138">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="fd437-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a><span data-ttu-id="fd437-139">AuthenticodeVerificationStart_V1 a AuthenticodeVerificationStop_V1 události</span><span class="sxs-lookup"><span data-stu-id="fd437-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="fd437-140">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="fd437-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="fd437-141">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="fd437-141">Keyword for raising the event</span></span>|<span data-ttu-id="fd437-142">úroveň</span><span class="sxs-lookup"><span data-stu-id="fd437-142">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="fd437-143">`SecurityKeyword`(0x400)</span><span class="sxs-lookup"><span data-stu-id="fd437-143">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="fd437-144">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="fd437-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="fd437-145">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="fd437-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="fd437-146">Událost</span><span class="sxs-lookup"><span data-stu-id="fd437-146">Event</span></span>|<span data-ttu-id="fd437-147">ID události</span><span class="sxs-lookup"><span data-stu-id="fd437-147">Event ID</span></span>|<span data-ttu-id="fd437-148">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="fd437-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="fd437-149">183</span><span class="sxs-lookup"><span data-stu-id="fd437-149">183</span></span>|<span data-ttu-id="fd437-150">Počáteční ověření Authenticode.</span><span class="sxs-lookup"><span data-stu-id="fd437-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="fd437-151">184</span><span class="sxs-lookup"><span data-stu-id="fd437-151">184</span></span>|<span data-ttu-id="fd437-152">Konec Authenticode ověření.</span><span class="sxs-lookup"><span data-stu-id="fd437-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="fd437-153">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="fd437-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="fd437-154">Název pole</span><span class="sxs-lookup"><span data-stu-id="fd437-154">Field name</span></span>|<span data-ttu-id="fd437-155">Datový typ</span><span class="sxs-lookup"><span data-stu-id="fd437-155">Data type</span></span>|<span data-ttu-id="fd437-156">Popis</span><span class="sxs-lookup"><span data-stu-id="fd437-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="fd437-157">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="fd437-157">VerificationFlags</span></span>|<span data-ttu-id="fd437-158">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="fd437-158">win:UInt32</span></span>|<span data-ttu-id="fd437-159">Příznaky ověření.</span><span class="sxs-lookup"><span data-stu-id="fd437-159">The verification flags.</span></span>|  
|<span data-ttu-id="fd437-160">Kód chyby</span><span class="sxs-lookup"><span data-stu-id="fd437-160">ErrorCode</span></span>|<span data-ttu-id="fd437-161">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="fd437-161">win:UInt32</span></span>|<span data-ttu-id="fd437-162">Kód chyby HResult.</span><span class="sxs-lookup"><span data-stu-id="fd437-162">The HResult error code.</span></span>|  
|<span data-ttu-id="fd437-163">ModulePath</span><span class="sxs-lookup"><span data-stu-id="fd437-163">ModulePath</span></span>|<span data-ttu-id="fd437-164">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="fd437-164">win:UnicodeString</span></span>|<span data-ttu-id="fd437-165">Cesta k modulu.</span><span class="sxs-lookup"><span data-stu-id="fd437-165">The module path.</span></span>|  
|<span data-ttu-id="fd437-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="fd437-166">ClrInstanceID</span></span>|<span data-ttu-id="fd437-167">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="fd437-167">win:UInt16</span></span>|<span data-ttu-id="fd437-168">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="fd437-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fd437-169">Viz také</span><span class="sxs-lookup"><span data-stu-id="fd437-169">See Also</span></span>  
 [<span data-ttu-id="fd437-170">CLR ETW – události</span><span class="sxs-lookup"><span data-stu-id="fd437-170">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
