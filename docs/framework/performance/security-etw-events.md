---
title: Události Trasování událostí pro Windows zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8d09b5b76c39f33848d44beb43d9b09c5e6ed13b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046180"
---
# <a name="security-etw-events"></a><span data-ttu-id="c4e42-102">Události Trasování událostí pro Windows zabezpečení</span><span class="sxs-lookup"><span data-stu-id="c4e42-102">Security ETW Events</span></span>
<a name="top"></a><span data-ttu-id="c4e42-103">Události zabezpečení jsou vyvolány během ověřování silných názvů a při ověřování prostřednictvím technologie Authenticode.</span><span class="sxs-lookup"><span data-stu-id="c4e42-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="c4e42-104">Tato kategorie se skládá z následujících událostí:</span><span class="sxs-lookup"><span data-stu-id="c4e42-104">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="c4e42-105">Události StrongNameVerificationStart_V1 a StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="c4e42-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
- [<span data-ttu-id="c4e42-106">Události AuthenticodeVerificationStart_V1 a AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="c4e42-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstart_v1-and-strongnameverificationstop_v1-events"></a><span data-ttu-id="c4e42-107">Události StrongNameVerificationStart_V1 a StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="c4e42-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="c4e42-108">Klíčové slovo a úroveň jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="c4e42-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="c4e42-109">(Další informace najdete v tématu [klíčová slova a úrovně CLR ETW](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="c4e42-109">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="c4e42-110">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="c4e42-110">Keyword for raising the event</span></span>|<span data-ttu-id="c4e42-111">Level</span><span class="sxs-lookup"><span data-stu-id="c4e42-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="c4e42-112">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="c4e42-112">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="c4e42-113">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="c4e42-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="c4e42-114">V následující tabulce jsou uvedeny informace o událostech.</span><span class="sxs-lookup"><span data-stu-id="c4e42-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="c4e42-115">Událost</span><span class="sxs-lookup"><span data-stu-id="c4e42-115">Event</span></span>|<span data-ttu-id="c4e42-116">ID události</span><span class="sxs-lookup"><span data-stu-id="c4e42-116">Event ID</span></span>|<span data-ttu-id="c4e42-117">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="c4e42-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="c4e42-118">181</span><span class="sxs-lookup"><span data-stu-id="c4e42-118">181</span></span>|<span data-ttu-id="c4e42-119">Začátek ověřování se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="c4e42-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="c4e42-120">182</span><span class="sxs-lookup"><span data-stu-id="c4e42-120">182</span></span>|<span data-ttu-id="c4e42-121">Konec ověřování se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="c4e42-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="c4e42-122">V následující tabulce jsou uvedena data události.</span><span class="sxs-lookup"><span data-stu-id="c4e42-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="c4e42-123">Název pole</span><span class="sxs-lookup"><span data-stu-id="c4e42-123">Field name</span></span>|<span data-ttu-id="c4e42-124">Datový typ</span><span class="sxs-lookup"><span data-stu-id="c4e42-124">Data type</span></span>|<span data-ttu-id="c4e42-125">Popis</span><span class="sxs-lookup"><span data-stu-id="c4e42-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="c4e42-126">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="c4e42-126">VerificationFlags</span></span>|<span data-ttu-id="c4e42-127">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="c4e42-127">win:UInt32</span></span>|<span data-ttu-id="c4e42-128">Příznaky ověřování.</span><span class="sxs-lookup"><span data-stu-id="c4e42-128">The verification flags.</span></span>|  
|<span data-ttu-id="c4e42-129">Kód chyby</span><span class="sxs-lookup"><span data-stu-id="c4e42-129">ErrorCode</span></span>|<span data-ttu-id="c4e42-130">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="c4e42-130">win:UInt32</span></span>|<span data-ttu-id="c4e42-131">Kód chyby HResult.</span><span class="sxs-lookup"><span data-stu-id="c4e42-131">The HResult error code.</span></span>|  
|<span data-ttu-id="c4e42-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="c4e42-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="c4e42-133">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="c4e42-133">win:UnicodeString</span></span>|<span data-ttu-id="c4e42-134">Plně kvalifikovaný název sestavení.</span><span class="sxs-lookup"><span data-stu-id="c4e42-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="c4e42-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c4e42-135">ClrInstanceID</span></span>|<span data-ttu-id="c4e42-136">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="c4e42-136">win:UInt16</span></span>|<span data-ttu-id="c4e42-137">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c4e42-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="c4e42-138">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="c4e42-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstart_v1-and-authenticodeverificationstop_v1-events"></a><span data-ttu-id="c4e42-139">Události AuthenticodeVerificationStart_V1 a AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="c4e42-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="c4e42-140">Klíčové slovo a úroveň jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="c4e42-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="c4e42-141">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="c4e42-141">Keyword for raising the event</span></span>|<span data-ttu-id="c4e42-142">Level</span><span class="sxs-lookup"><span data-stu-id="c4e42-142">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="c4e42-143">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="c4e42-143">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="c4e42-144">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="c4e42-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="c4e42-145">V následující tabulce jsou uvedeny informace o událostech.</span><span class="sxs-lookup"><span data-stu-id="c4e42-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="c4e42-146">Událost</span><span class="sxs-lookup"><span data-stu-id="c4e42-146">Event</span></span>|<span data-ttu-id="c4e42-147">ID události</span><span class="sxs-lookup"><span data-stu-id="c4e42-147">Event ID</span></span>|<span data-ttu-id="c4e42-148">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="c4e42-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="c4e42-149">183</span><span class="sxs-lookup"><span data-stu-id="c4e42-149">183</span></span>|<span data-ttu-id="c4e42-150">Začátek ověřování Authenticode</span><span class="sxs-lookup"><span data-stu-id="c4e42-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="c4e42-151">184</span><span class="sxs-lookup"><span data-stu-id="c4e42-151">184</span></span>|<span data-ttu-id="c4e42-152">Konec ověřování Authenticode</span><span class="sxs-lookup"><span data-stu-id="c4e42-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="c4e42-153">V následující tabulce jsou uvedena data události.</span><span class="sxs-lookup"><span data-stu-id="c4e42-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="c4e42-154">Název pole</span><span class="sxs-lookup"><span data-stu-id="c4e42-154">Field name</span></span>|<span data-ttu-id="c4e42-155">Datový typ</span><span class="sxs-lookup"><span data-stu-id="c4e42-155">Data type</span></span>|<span data-ttu-id="c4e42-156">Popis</span><span class="sxs-lookup"><span data-stu-id="c4e42-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="c4e42-157">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="c4e42-157">VerificationFlags</span></span>|<span data-ttu-id="c4e42-158">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="c4e42-158">win:UInt32</span></span>|<span data-ttu-id="c4e42-159">Příznaky ověřování.</span><span class="sxs-lookup"><span data-stu-id="c4e42-159">The verification flags.</span></span>|  
|<span data-ttu-id="c4e42-160">Kód chyby</span><span class="sxs-lookup"><span data-stu-id="c4e42-160">ErrorCode</span></span>|<span data-ttu-id="c4e42-161">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="c4e42-161">win:UInt32</span></span>|<span data-ttu-id="c4e42-162">Kód chyby HResult.</span><span class="sxs-lookup"><span data-stu-id="c4e42-162">The HResult error code.</span></span>|  
|<span data-ttu-id="c4e42-163">ModulePath nastavte</span><span class="sxs-lookup"><span data-stu-id="c4e42-163">ModulePath</span></span>|<span data-ttu-id="c4e42-164">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="c4e42-164">win:UnicodeString</span></span>|<span data-ttu-id="c4e42-165">Cesta k modulu</span><span class="sxs-lookup"><span data-stu-id="c4e42-165">The module path.</span></span>|  
|<span data-ttu-id="c4e42-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c4e42-166">ClrInstanceID</span></span>|<span data-ttu-id="c4e42-167">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="c4e42-167">win:UInt16</span></span>|<span data-ttu-id="c4e42-168">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c4e42-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c4e42-169">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4e42-169">See also</span></span>

- [<span data-ttu-id="c4e42-170">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="c4e42-170">CLR ETW Events</span></span>](clr-etw-events.md)
