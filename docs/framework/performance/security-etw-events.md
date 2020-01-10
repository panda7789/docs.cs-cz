---
title: Události Trasování událostí pro Windows zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
ms.openlocfilehash: c443bda8cdc2c6b32760e9dcba8b81a29d81660b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715941"
---
# <a name="security-etw-events"></a><span data-ttu-id="6fae9-102">Události Trasování událostí pro Windows zabezpečení</span><span class="sxs-lookup"><span data-stu-id="6fae9-102">Security ETW Events</span></span>

<span data-ttu-id="6fae9-103">Události zabezpečení jsou vyvolány během ověřování silných názvů a při ověřování prostřednictvím technologie Authenticode.</span><span class="sxs-lookup"><span data-stu-id="6fae9-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  

## <a name="strongnameverificationstart_v1-and-strongnameverificationstop_v1-events"></a><span data-ttu-id="6fae9-104">Události StrongNameVerificationStart_V1 a StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="6fae9-104">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="6fae9-105">Klíčové slovo a úroveň jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="6fae9-105">The following table shows the keyword and level.</span></span> <span data-ttu-id="6fae9-106">(Další informace najdete v tématu [klíčová slova a úrovně CLR ETW](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="6fae9-106">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="6fae9-107">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="6fae9-107">Keyword for raising the event</span></span>|<span data-ttu-id="6fae9-108">Úroveň</span><span class="sxs-lookup"><span data-stu-id="6fae9-108">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="6fae9-109">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="6fae9-109">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="6fae9-110">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="6fae9-110">Informational(4)</span></span>|  
  
 <span data-ttu-id="6fae9-111">V následující tabulce jsou uvedeny informace o událostech.</span><span class="sxs-lookup"><span data-stu-id="6fae9-111">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="6fae9-112">Událost</span><span class="sxs-lookup"><span data-stu-id="6fae9-112">Event</span></span>|<span data-ttu-id="6fae9-113">ID události</span><span class="sxs-lookup"><span data-stu-id="6fae9-113">Event ID</span></span>|<span data-ttu-id="6fae9-114">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="6fae9-114">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="6fae9-115">181</span><span class="sxs-lookup"><span data-stu-id="6fae9-115">181</span></span>|<span data-ttu-id="6fae9-116">Začátek ověřování se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="6fae9-116">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="6fae9-117">182</span><span class="sxs-lookup"><span data-stu-id="6fae9-117">182</span></span>|<span data-ttu-id="6fae9-118">Konec ověřování se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="6fae9-118">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="6fae9-119">V následující tabulce jsou uvedena data události.</span><span class="sxs-lookup"><span data-stu-id="6fae9-119">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="6fae9-120">Název pole</span><span class="sxs-lookup"><span data-stu-id="6fae9-120">Field name</span></span>|<span data-ttu-id="6fae9-121">Datový typ</span><span class="sxs-lookup"><span data-stu-id="6fae9-121">Data type</span></span>|<span data-ttu-id="6fae9-122">Popis</span><span class="sxs-lookup"><span data-stu-id="6fae9-122">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="6fae9-123">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="6fae9-123">VerificationFlags</span></span>|<span data-ttu-id="6fae9-124">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6fae9-124">win:UInt32</span></span>|<span data-ttu-id="6fae9-125">Příznaky ověřování.</span><span class="sxs-lookup"><span data-stu-id="6fae9-125">The verification flags.</span></span>|  
|<span data-ttu-id="6fae9-126">Kód chyby</span><span class="sxs-lookup"><span data-stu-id="6fae9-126">ErrorCode</span></span>|<span data-ttu-id="6fae9-127">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6fae9-127">win:UInt32</span></span>|<span data-ttu-id="6fae9-128">Kód chyby HResult.</span><span class="sxs-lookup"><span data-stu-id="6fae9-128">The HResult error code.</span></span>|  
|<span data-ttu-id="6fae9-129">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="6fae9-129">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="6fae9-130">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="6fae9-130">win:UnicodeString</span></span>|<span data-ttu-id="6fae9-131">Plně kvalifikovaný název sestavení.</span><span class="sxs-lookup"><span data-stu-id="6fae9-131">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="6fae9-132">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="6fae9-132">ClrInstanceID</span></span>|<span data-ttu-id="6fae9-133">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="6fae9-133">win:UInt16</span></span>|<span data-ttu-id="6fae9-134">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="6fae9-134">Unique ID for the instance of CLR or CoreCLR.</span></span>|  

## <a name="authenticodeverificationstart_v1-and-authenticodeverificationstop_v1-events"></a><span data-ttu-id="6fae9-135">Události AuthenticodeVerificationStart_V1 a AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="6fae9-135">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="6fae9-136">Klíčové slovo a úroveň jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="6fae9-136">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="6fae9-137">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="6fae9-137">Keyword for raising the event</span></span>|<span data-ttu-id="6fae9-138">Úroveň</span><span class="sxs-lookup"><span data-stu-id="6fae9-138">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="6fae9-139">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="6fae9-139">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="6fae9-140">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="6fae9-140">Informational(4)</span></span>|  
  
 <span data-ttu-id="6fae9-141">V následující tabulce jsou uvedeny informace o událostech.</span><span class="sxs-lookup"><span data-stu-id="6fae9-141">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="6fae9-142">Událost</span><span class="sxs-lookup"><span data-stu-id="6fae9-142">Event</span></span>|<span data-ttu-id="6fae9-143">ID události</span><span class="sxs-lookup"><span data-stu-id="6fae9-143">Event ID</span></span>|<span data-ttu-id="6fae9-144">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="6fae9-144">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="6fae9-145">183</span><span class="sxs-lookup"><span data-stu-id="6fae9-145">183</span></span>|<span data-ttu-id="6fae9-146">Začátek ověřování Authenticode</span><span class="sxs-lookup"><span data-stu-id="6fae9-146">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="6fae9-147">184</span><span class="sxs-lookup"><span data-stu-id="6fae9-147">184</span></span>|<span data-ttu-id="6fae9-148">Konec ověřování Authenticode</span><span class="sxs-lookup"><span data-stu-id="6fae9-148">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="6fae9-149">V následující tabulce jsou uvedena data události.</span><span class="sxs-lookup"><span data-stu-id="6fae9-149">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="6fae9-150">Název pole</span><span class="sxs-lookup"><span data-stu-id="6fae9-150">Field name</span></span>|<span data-ttu-id="6fae9-151">Datový typ</span><span class="sxs-lookup"><span data-stu-id="6fae9-151">Data type</span></span>|<span data-ttu-id="6fae9-152">Popis</span><span class="sxs-lookup"><span data-stu-id="6fae9-152">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="6fae9-153">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="6fae9-153">VerificationFlags</span></span>|<span data-ttu-id="6fae9-154">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6fae9-154">win:UInt32</span></span>|<span data-ttu-id="6fae9-155">Příznaky ověřování.</span><span class="sxs-lookup"><span data-stu-id="6fae9-155">The verification flags.</span></span>|  
|<span data-ttu-id="6fae9-156">Kód chyby</span><span class="sxs-lookup"><span data-stu-id="6fae9-156">ErrorCode</span></span>|<span data-ttu-id="6fae9-157">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6fae9-157">win:UInt32</span></span>|<span data-ttu-id="6fae9-158">Kód chyby HResult.</span><span class="sxs-lookup"><span data-stu-id="6fae9-158">The HResult error code.</span></span>|  
|<span data-ttu-id="6fae9-159">ModulePath nastavte</span><span class="sxs-lookup"><span data-stu-id="6fae9-159">ModulePath</span></span>|<span data-ttu-id="6fae9-160">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="6fae9-160">win:UnicodeString</span></span>|<span data-ttu-id="6fae9-161">Cesta k modulu</span><span class="sxs-lookup"><span data-stu-id="6fae9-161">The module path.</span></span>|  
|<span data-ttu-id="6fae9-162">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="6fae9-162">ClrInstanceID</span></span>|<span data-ttu-id="6fae9-163">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="6fae9-163">win:UInt16</span></span>|<span data-ttu-id="6fae9-164">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="6fae9-164">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6fae9-165">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6fae9-165">See also</span></span>

- [<span data-ttu-id="6fae9-166">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="6fae9-166">CLR ETW Events</span></span>](clr-etw-events.md)
