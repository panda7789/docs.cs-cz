---
title: LocalServiceSecuritySettings
ms.date: 03/30/2017
ms.assetid: 490aa0e5-5242-4f8d-b505-5ec6287633b4
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 8f80af782c474ccf3a232ab353125fa223d4f5d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486894"
---
# <a name="localservicesecuritysettings"></a><span data-ttu-id="ee630-102">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="ee630-102">LocalServiceSecuritySettings</span></span>
<span data-ttu-id="ee630-103">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="ee630-103">LocalServiceSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee630-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee630-104">Syntax</span></span>  
  
```  
class LocalServiceSecuritySettings  
{  
  boolean DetectReplays;  
  datetime InactivityTimeout;  
  datetime IssuedCookieLifetime;  
  sint32 MaxCachedCookies;  
  datetime MaxClockSkew;  
  sint32 MaxPendingSessions;  
  sint32 MaxStatefulNegotiations;  
  datetime NegotiationTimeout;  
  boolean ReconnectTransportOnFailure;  
  sint32 ReplayCacheSize;  
  datetime ReplayWindow;  
  datetime SessionKeyRenewalInterval;  
  datetime SessionKeyRolloverInterval;  
  datetime TimestampValidityDuration;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ee630-105">Metody</span><span class="sxs-lookup"><span data-stu-id="ee630-105">Methods</span></span>  
 <span data-ttu-id="ee630-106">Třída LocalServiceSecuritySettings nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="ee630-106">The LocalServiceSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ee630-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ee630-107">Properties</span></span>  
 <span data-ttu-id="ee630-108">Třída LocalServiceSecuritySettings má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="ee630-108">The LocalServiceSecuritySettings class has the following properties:</span></span>  
  
### <a name="detectreplays"></a><span data-ttu-id="ee630-109">DetectReplays</span><span class="sxs-lookup"><span data-stu-id="ee630-109">DetectReplays</span></span>  
 <span data-ttu-id="ee630-110">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="ee630-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="ee630-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ee630-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ee630-112">Logická hodnota, která určuje, jestli jsou před zneužitím útoky na kanál zjistil a řešeny automaticky.</span><span class="sxs-lookup"><span data-stu-id="ee630-112">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="ee630-113">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="ee630-113">InactivityTimeout</span></span>  
 <span data-ttu-id="ee630-114">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="ee630-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="ee630-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ee630-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ee630-116">Maximální počet čekající na vyřízení zabezpečení relací, které služba podporuje.</span><span class="sxs-lookup"><span data-stu-id="ee630-116">The maximum number of pending security sessions that the service supports.</span></span>  
  
### <a name="issuedcookielifetime"></a><span data-ttu-id="ee630-117">IssuedCookieLifetime</span><span class="sxs-lookup"><span data-stu-id="ee630-117">IssuedCookieLifetime</span></span>  
 <span data-ttu-id="ee630-118">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="ee630-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="ee630-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ee630-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ee630-120">Časový interval, který určuje životnost vystaveno pro všechny nové soubory cookie zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="ee630-120">A TimeSpan that specifies the lifetime issued to all new security cookies.</span></span>  
  
### <a name="maxcachedcookies"></a><span data-ttu-id="ee630-121">MaxCachedCookies</span><span class="sxs-lookup"><span data-stu-id="ee630-121">MaxCachedCookies</span></span>  
 <span data-ttu-id="ee630-122">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="ee630-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="ee630-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ee630-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ee630-124">Maximální počet souborů cookie, které mohou být uloženy v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="ee630-124">The maximum number of cookies that can be cached.</span></span>  
  
### <a name="maxclockskew"></a><span data-ttu-id="ee630-125">Maxclockskew –</span><span class="sxs-lookup"><span data-stu-id="ee630-125">MaxClockSkew</span></span>  
 <span data-ttu-id="ee630-126">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="ee630-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="ee630-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ee630-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ee630-128">Časový interval, který určuje maximální časový rozdíl mezi systémovými hodinami dvou komunikujících stran.</span><span class="sxs-lookup"><span data-stu-id="ee630-128">A TimeSpan that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span>  
  
### <a name="maxpendingsessions"></a><span data-ttu-id="ee630-129">MaxPendingSessions</span><span class="sxs-lookup"><span data-stu-id="ee630-129">MaxPendingSessions</span></span>  
 <span data-ttu-id="ee630-130">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="ee630-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="ee630-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ee630-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ee630-132">Maximální počet čekajících připojení služby.</span><span class="sxs-lookup"><span data-stu-id="ee630-132">The maximum number of pending connections on the service.</span></span>  
  
### <a name="maxstatefulnegotiations"></a><span data-ttu-id="ee630-133">MaxStatefulNegotiations</span><span class="sxs-lookup"><span data-stu-id="ee630-133">MaxStatefulNegotiations</span></span>  
 <span data-ttu-id="ee630-134">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="ee630-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="ee630-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ee630-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ee630-136">Počet vyjednávání zabezpečení, které mohou být souběžně aktivní.</span><span class="sxs-lookup"><span data-stu-id="ee630-136">The number of security negotiations that can be active concurrently.</span></span>  
  
### <a name="negotiationtimeout"></a><span data-ttu-id="ee630-137">NegotiationTimeout</span><span class="sxs-lookup"><span data-stu-id="ee630-137">NegotiationTimeout</span></span>  
 <span data-ttu-id="ee630-138">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="ee630-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="ee630-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ee630-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ee630-140">Časový interval, který určuje maximální doba trvání fáze vyjednávání mezi serverem a klientem.</span><span class="sxs-lookup"><span data-stu-id="ee630-140">A TimeSpan that specifies the maximum duration for the security negotiation phase between server and client.</span></span>  
  
### <a name="reconnecttransportonfailure"></a><span data-ttu-id="ee630-141">ReconnectTransportOnFailure</span><span class="sxs-lookup"><span data-stu-id="ee630-141">ReconnectTransportOnFailure</span></span>  
 <span data-ttu-id="ee630-142">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="ee630-142">Data type: boolean</span></span>  
  
 <span data-ttu-id="ee630-143">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ee630-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ee630-144">Logická hodnota, která určuje, zda připojení pomocí protokolu WS-spolehlivé zasílání zpráv se pokusí znovu připojit po selhání přenosu.</span><span class="sxs-lookup"><span data-stu-id="ee630-144">A Boolean value that specifies whether connections using WS-Reliable messaging attempt to reconnect after transport failures.</span></span>  
  
### <a name="replaycachesize"></a><span data-ttu-id="ee630-145">ReplayCacheSize</span><span class="sxs-lookup"><span data-stu-id="ee630-145">ReplayCacheSize</span></span>  
 <span data-ttu-id="ee630-146">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="ee630-146">Data type: sint32</span></span>  
  
 <span data-ttu-id="ee630-147">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ee630-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ee630-148">Počet uložené v mezipaměti náhodně generované identifikátory používá pro rozpoznání opětovného přehrání.</span><span class="sxs-lookup"><span data-stu-id="ee630-148">The number of cached nonces used for replay detection.</span></span>  
  
### <a name="replaywindow"></a><span data-ttu-id="ee630-149">Třída ReplayWindow</span><span class="sxs-lookup"><span data-stu-id="ee630-149">ReplayWindow</span></span>  
 <span data-ttu-id="ee630-150">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="ee630-150">Data type: datetime</span></span>  
  
 <span data-ttu-id="ee630-151">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ee630-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ee630-152">Časový interval, který určuje dobu, ve kterém jsou platné náhodně generované identifikátory jednotlivé zprávy.</span><span class="sxs-lookup"><span data-stu-id="ee630-152">A TimeSpan that specifies the duration in which individual message nonces are valid.</span></span>  
  
### <a name="sessionkeyrenewalinterval"></a><span data-ttu-id="ee630-153">SessionKeyRenewalInterval</span><span class="sxs-lookup"><span data-stu-id="ee630-153">SessionKeyRenewalInterval</span></span>  
 <span data-ttu-id="ee630-154">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="ee630-154">Data type: datetime</span></span>  
  
 <span data-ttu-id="ee630-155">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ee630-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ee630-156">Časový interval, který určuje dobu, po které může iniciátor obnovuje klíč pro relace zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="ee630-156">A TimeSpan that specifies the duration after which the initiator renews the key for the security session.</span></span>  
  
### <a name="sessionkeyrolloverinterval"></a><span data-ttu-id="ee630-157">SessionKeyRolloverInterval</span><span class="sxs-lookup"><span data-stu-id="ee630-157">SessionKeyRolloverInterval</span></span>  
 <span data-ttu-id="ee630-158">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="ee630-158">Data type: datetime</span></span>  
  
 <span data-ttu-id="ee630-159">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ee630-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ee630-160">Časový interval, který určuje časový interval je klíč předchozí relace při obnovení klíče platná pro příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="ee630-160">A TimeSpan that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span>  
  
### <a name="timestampvalidityduration"></a><span data-ttu-id="ee630-161">TimestampValidityDuration</span><span class="sxs-lookup"><span data-stu-id="ee630-161">TimestampValidityDuration</span></span>  
 <span data-ttu-id="ee630-162">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="ee630-162">Data type: datetime</span></span>  
  
 <span data-ttu-id="ee630-163">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ee630-163">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ee630-164">Časový interval, který určuje dobu, ve kterém je platný časové razítko.</span><span class="sxs-lookup"><span data-stu-id="ee630-164">A TimeSpan that specifies the duration in which a time stamp is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee630-165">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ee630-165">Requirements</span></span>  
  
|<span data-ttu-id="ee630-166">MOF</span><span class="sxs-lookup"><span data-stu-id="ee630-166">MOF</span></span>|<span data-ttu-id="ee630-167">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ee630-167">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ee630-168">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="ee630-168">Namespace</span></span>|<span data-ttu-id="ee630-169">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ee630-169">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ee630-170">Viz také</span><span class="sxs-lookup"><span data-stu-id="ee630-170">See Also</span></span>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
