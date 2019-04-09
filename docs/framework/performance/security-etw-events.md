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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134027"
---
# <a name="security-etw-events"></a><span data-ttu-id="99cde-102">Události Trasování událostí pro Windows zabezpečení</span><span class="sxs-lookup"><span data-stu-id="99cde-102">Security ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="99cde-103">Události zabezpečení jsou aktivovány v průběhu ověřování silných názvů a ověření pomocí technologie Authenticode.</span><span class="sxs-lookup"><span data-stu-id="99cde-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="99cde-104">Tato kategorie se skládá z následujících událostí:</span><span class="sxs-lookup"><span data-stu-id="99cde-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="99cde-105">StrongNameVerificationStart_V1 a StrongNameVerificationStop_V1 události</span><span class="sxs-lookup"><span data-stu-id="99cde-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
-   [<span data-ttu-id="99cde-106">AuthenticodeVerificationStart_V1 a AuthenticodeVerificationStop_V1 události</span><span class="sxs-lookup"><span data-stu-id="99cde-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a><span data-ttu-id="99cde-107">StrongNameVerificationStart_V1 a StrongNameVerificationStop_V1 události</span><span class="sxs-lookup"><span data-stu-id="99cde-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="99cde-108">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="99cde-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="99cde-109">(Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="99cde-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="99cde-110">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="99cde-110">Keyword for raising the event</span></span>|<span data-ttu-id="99cde-111">úroveň</span><span class="sxs-lookup"><span data-stu-id="99cde-111">Level</span></span>|  
|-----------------------------------|-----------|  
|`SecurityKeyword` <span data-ttu-id="99cde-112">(0x400)</span><span class="sxs-lookup"><span data-stu-id="99cde-112">(0x400)</span></span>|<span data-ttu-id="99cde-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="99cde-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="99cde-114">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="99cde-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="99cde-115">Událost</span><span class="sxs-lookup"><span data-stu-id="99cde-115">Event</span></span>|<span data-ttu-id="99cde-116">ID události</span><span class="sxs-lookup"><span data-stu-id="99cde-116">Event ID</span></span>|<span data-ttu-id="99cde-117">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="99cde-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="99cde-118">181</span><span class="sxs-lookup"><span data-stu-id="99cde-118">181</span></span>|<span data-ttu-id="99cde-119">Začátek ověřování silných názvů.</span><span class="sxs-lookup"><span data-stu-id="99cde-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="99cde-120">182</span><span class="sxs-lookup"><span data-stu-id="99cde-120">182</span></span>|<span data-ttu-id="99cde-121">Konec ověřování silných názvů.</span><span class="sxs-lookup"><span data-stu-id="99cde-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="99cde-122">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="99cde-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="99cde-123">Název pole</span><span class="sxs-lookup"><span data-stu-id="99cde-123">Field name</span></span>|<span data-ttu-id="99cde-124">Datový typ</span><span class="sxs-lookup"><span data-stu-id="99cde-124">Data type</span></span>|<span data-ttu-id="99cde-125">Popis</span><span class="sxs-lookup"><span data-stu-id="99cde-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="99cde-126">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="99cde-126">VerificationFlags</span></span>|<span data-ttu-id="99cde-127">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="99cde-127">win:UInt32</span></span>|<span data-ttu-id="99cde-128">Příznaky ověření.</span><span class="sxs-lookup"><span data-stu-id="99cde-128">The verification flags.</span></span>|  
|<span data-ttu-id="99cde-129">Kód chyby</span><span class="sxs-lookup"><span data-stu-id="99cde-129">ErrorCode</span></span>|<span data-ttu-id="99cde-130">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="99cde-130">win:UInt32</span></span>|<span data-ttu-id="99cde-131">Kód chyby HResult.</span><span class="sxs-lookup"><span data-stu-id="99cde-131">The HResult error code.</span></span>|  
|<span data-ttu-id="99cde-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="99cde-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="99cde-133">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="99cde-133">win:UnicodeString</span></span>|<span data-ttu-id="99cde-134">Plně kvalifikovaný název.</span><span class="sxs-lookup"><span data-stu-id="99cde-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="99cde-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="99cde-135">ClrInstanceID</span></span>|<span data-ttu-id="99cde-136">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="99cde-136">win:UInt16</span></span>|<span data-ttu-id="99cde-137">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="99cde-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="99cde-138">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="99cde-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a><span data-ttu-id="99cde-139">AuthenticodeVerificationStart_V1 a AuthenticodeVerificationStop_V1 události</span><span class="sxs-lookup"><span data-stu-id="99cde-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="99cde-140">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="99cde-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="99cde-141">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="99cde-141">Keyword for raising the event</span></span>|<span data-ttu-id="99cde-142">úroveň</span><span class="sxs-lookup"><span data-stu-id="99cde-142">Level</span></span>|  
|-----------------------------------|-----------|  
|`SecurityKeyword` <span data-ttu-id="99cde-143">(0x400)</span><span class="sxs-lookup"><span data-stu-id="99cde-143">(0x400)</span></span>|<span data-ttu-id="99cde-144">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="99cde-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="99cde-145">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="99cde-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="99cde-146">Událost</span><span class="sxs-lookup"><span data-stu-id="99cde-146">Event</span></span>|<span data-ttu-id="99cde-147">ID události</span><span class="sxs-lookup"><span data-stu-id="99cde-147">Event ID</span></span>|<span data-ttu-id="99cde-148">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="99cde-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="99cde-149">183</span><span class="sxs-lookup"><span data-stu-id="99cde-149">183</span></span>|<span data-ttu-id="99cde-150">Bylo zahájeno ověřování Authenticode.</span><span class="sxs-lookup"><span data-stu-id="99cde-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="99cde-151">184</span><span class="sxs-lookup"><span data-stu-id="99cde-151">184</span></span>|<span data-ttu-id="99cde-152">Konec ověření pomocí technologie Authenticode.</span><span class="sxs-lookup"><span data-stu-id="99cde-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="99cde-153">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="99cde-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="99cde-154">Název pole</span><span class="sxs-lookup"><span data-stu-id="99cde-154">Field name</span></span>|<span data-ttu-id="99cde-155">Datový typ</span><span class="sxs-lookup"><span data-stu-id="99cde-155">Data type</span></span>|<span data-ttu-id="99cde-156">Popis</span><span class="sxs-lookup"><span data-stu-id="99cde-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="99cde-157">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="99cde-157">VerificationFlags</span></span>|<span data-ttu-id="99cde-158">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="99cde-158">win:UInt32</span></span>|<span data-ttu-id="99cde-159">Příznaky ověření.</span><span class="sxs-lookup"><span data-stu-id="99cde-159">The verification flags.</span></span>|  
|<span data-ttu-id="99cde-160">Kód chyby</span><span class="sxs-lookup"><span data-stu-id="99cde-160">ErrorCode</span></span>|<span data-ttu-id="99cde-161">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="99cde-161">win:UInt32</span></span>|<span data-ttu-id="99cde-162">Kód chyby HResult.</span><span class="sxs-lookup"><span data-stu-id="99cde-162">The HResult error code.</span></span>|  
|<span data-ttu-id="99cde-163">ModulePath</span><span class="sxs-lookup"><span data-stu-id="99cde-163">ModulePath</span></span>|<span data-ttu-id="99cde-164">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="99cde-164">win:UnicodeString</span></span>|<span data-ttu-id="99cde-165">Cesta modulu.</span><span class="sxs-lookup"><span data-stu-id="99cde-165">The module path.</span></span>|  
|<span data-ttu-id="99cde-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="99cde-166">ClrInstanceID</span></span>|<span data-ttu-id="99cde-167">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="99cde-167">win:UInt16</span></span>|<span data-ttu-id="99cde-168">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="99cde-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="99cde-169">Viz také:</span><span class="sxs-lookup"><span data-stu-id="99cde-169">See also</span></span>

- [<span data-ttu-id="99cde-170">Události ETW CLR</span><span class="sxs-lookup"><span data-stu-id="99cde-170">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
